---
title: "Blog 3: Ghi nhật ký kiểm tra Amazon S3 – Phần 2: Phân tích và ghi nhật ký tập trung"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# Phân Tích và Ghi Nhật Ký Tập Trung S3 Data Events trong AWS CloudTrail

Khi xảy ra sự cố bảo mật—như tải xuống trái phép hoặc xóa hàng loạt dữ liệu trong S3 bucket—câu hỏi đầu tiên luôn là: **"Ai đã làm việc này?"**. Nhật ký truy cập máy chủ S3 thông thường (server access logs) cho thấy yêu cầu nào đã được thực hiện, nhưng lại thiếu thông tin định danh IAM để xác định chính xác người dùng hoặc vai trò đã thực hiện.

Bài viết này (Phần 2 trong chuỗi bài viết về kiểm toán S3) hướng dẫn cách triển khai hệ thống kiểm toán bảo mật dựa trên định danh sử dụng **AWS CloudTrail data events** và **Amazon Athena**.

![Sơ đồ luồng kiến trúc: Từ IAM User/Assumed Role qua S3 API Call, Amazon S3, AWS CloudTrail, Central S3 Bucket đến Amazon Athena và Security Investigator](/images/3-BlogsTranslated/cloudtrail-s3-flow.svg)

*Sơ đồ luồng: Dữ liệu sự kiện S3 được ghi nhận bởi CloudTrail, lưu vào S3 tập trung và truy vấn qua Athena*

---

## S3 Data Events vs. Server Access Logs

CloudTrail data events giúp theo dõi chi tiết ở cấp độ API cho các hoạt động của đối tượng S3 cùng với đầy đủ thông tin định danh, hỗ trợ đắc lực bên cạnh access logs thông thường.

- **Thông tin ghi nhận:** Định danh chi tiết của IAM user/role, các hoạt động API (`GetObject` , `PutObject` , `DeleteObject` ), ngữ cảnh xác thực (MFA, chuỗi vai trò đảm nhận) và truy cập chéo tài khoản.
- **Thông tin không ghi nhận:** Các thông số hiệu năng HTTP hoặc thời gian phản hồi chính xác (các thông tin này yêu cầu server access logs như thảo luận ở Phần 1).
- **Độ trễ & Chi phí:** Nhật ký nén JSON được phân phát trong vòng ~5 phút. Chi phí là $0.10 cho mỗi 100.000 data events được ghi lại *(Lưu ý: Không có hạn mức miễn phí cho data events)*.

---

## Cấu Hình Từng Bước

Để thiết lập ghi nhật ký kiểm toán S3 tập trung cho toàn tổ chức:

1. **Tạo CloudTrail Trail:** Trong bảng điều khiển CloudTrail, tạo một trail mới (ví dụ: `s3-data-events-trail` ) và hướng dẫn về một S3 bucket trung tâm.
2. **Kích hoạt cho toàn tổ chức:** Nếu sử dụng AWS Organizations, chọn **Enable for all accounts in my organization** từ tài khoản quản trị để tự động áp dụng trail này cho toàn bộ tài khoản thành viên.
3. **Cấu hình Advanced Event Selectors:** Bỏ chọn management events (tránh trùng lặp chi phí nếu đã có trail khác) và chọn **Data Events** với loại tài nguyên là **S3**. Bạn có thể lọc theo bucket hoặc tiền tố.
4. **Thiết lập S3 Lifecycle Policy:** Cấu hình quy tắc vòng đời trên bucket trung tâm để chuyển nhật ký sang **Standard-IA** sau 90 ngày, **Glacier** sau 180 ngày và tự động xóa sau 7 năm để tối ưu hóa chi phí lưu trữ.

---

## Tạo Bảng Athena với Partition Projection

**Partition projection** giúp Athena tính toán các giá trị phân vùng một cách động trực tiếp từ đường dẫn S3, tăng tốc độ truy vấn và giảm chi phí quét siêu dữ liệu (metadata scan). Sử dụng câu lệnh dưới đây để tạo bảng ngoài:

```sql
CREATE EXTERNAL TABLE cloudtrail_s3_events (
    eventversion STRING,
    useridentity STRUCT<
        type: STRING, principalid: STRING, arn: STRING, accountid: STRING,
        username: STRING, sessioncontext: STRUCT<
            attributes: STRUCT<mfaauthenticated: STRING, creationdate: STRING>,
            sessionissuer: STRUCT<arn: STRING, accountid: STRING, username: STRING>
        >
    >,
    eventtime STRING, eventsource STRING, eventname STRING, awsregion STRING,
    sourceipaddress STRING, useragent STRING, errorcode STRING, errormessage STRING,
    requestparameters STRING, responseelements STRING, additionaleventdata STRING,
    requestaccountid STRING, sharedeventid STRING
)
PARTITIONED BY (
    account STRING,
    region STRING,
    timestamp STRING
)
ROW FORMAT SERDE 'org.apache.hive.hcatalog.data.JsonSerDe'
STORED AS INPUTFORMAT 'com.amazon.emr.cloudtrail.CloudTrailInputFormat'
OUTPUTFORMAT 'org.apache.hadoop.hive.ql.io.HiveIgnoreKeyTextOutputFormat'
LOCATION 's3://centralized-s3-cloudtrail-logs/AWSLogs/'
TBLPROPERTIES (
    'projection.enabled' = 'true',
    'projection.account.type' = 'injected',
    'projection.region.type' = 'injected',
    'projection.timestamp.type' = 'date',
    'projection.timestamp.format' = 'yyyy/MM/dd',
    'projection.timestamp.range' = '2024/01/01,NOW',
    'projection.timestamp.interval' = '1',
    'projection.timestamp.interval.unit' = 'DAYS',
    'storage.location.template' = 's3://centralized-s3-cloudtrail-logs/AWSLogs/${account}/CloudTrail/${region}/${timestamp}/'
);
```

*Lưu ý: Đối với Organization trail, bổ sung cột phân vùng `organization_id STRING`  đầu tiên và chỉnh nó vào cấu trúc: `storage.location.template` .*

---

## Các Mẫu Truy Vấn Bảo Mật Chính

Bảng Athena sử dụng partition projection yêu cầu bạn phải chỉ định phân vùng `account` , `region`  và `timestamp`  trong mệnh đề `WHERE` để thu hẹp phạm vi dữ liệu, tránh quét toàn bộ bảng bằng cách gây phát sinh chi phí lớn.

### 1. Truy Vết Hoạt Động của Người Dùng Cụ Thể

Tìm các hoạt động trên mặt phẳng dữ liệu S3 được thực hiện bởi một IAM user/role trong ngày:

```sql
SELECT eventtime, useridentity.arn as user_arn, eventname, sourceipaddress,
    JSON_EXTRACT_SCALAR(requestparameters, '$.bucketName') as bucket,
    JSON_EXTRACT_SCALAR(requestparameters, '$.key') as object_key
FROM cloudtrail_s3_events
WHERE account = '123456789012' AND region = 'us-east-1' AND timestamp = '2026/05/15'
AND (useridentity.username = 'specific-user' OR useridentity.arn LIKE '%specific-user%')
AND eventname IN ('GetObject', 'PutObject', 'DeleteObject')
ORDER BY eventtime DESC;
```

### 2. Giám Sát Truy Cập Chéo Tài Khoản

Phát hiện các yêu cầu truy cập S3 bắt nguồn từ tài khoản AWS bên ngoài:

```sql
SELECT eventtime, useridentity.accountid as source_account, recipientaccountid as target_account,
    useridentity.arn as user_arn, eventname, sourceipaddress
FROM cloudtrail_s3_events
WHERE account = '123456789012' AND region = 'us-east-1' AND timestamp = '2026/05/15'
    AND useridentity.accountid != recipientaccountid
ORDER BY eventtime DESC;
```

### 3. Thống Kê Các Lần Truy Cập Thất Bại

Liệt kê các thao tác gặp lỗi phân quyền (`AccessDenied` , `ForbiddenKey` ), giúp nhận diện hành vi do quét tài nguyên trái phép:

```sql
SELECT eventtime, useridentity.arn as user_arn, eventname, sourceipaddress, errorcode, errormessage
FROM cloudtrail_s3_events
WHERE account = '123456789012' AND region = 'us-east-1' AND timestamp = '2026/05/15'
    AND errorcode IS NOT NULL
ORDER BY eventtime DESC LIMIT 100;
```

### 4. Kiểm Toán Thao Tác Xóa Đối Tượng

Theo dõi các thao tác xóa trong một khoảng thời gian, ghi nhận vai trò và trạng thái xác thực MFA:

```sql
SELECT eventtime, useridentity.arn as user_arn, sourceipaddress,
    JSON_EXTRACT_SCALAR(requestparameters, '$.bucketName') as bucket,
    JSON_EXTRACT_SCALAR(requestparameters, '$.key') as deleted_object,
    sessioncontext.attributes.mfaauthenticated as mfa_used
FROM cloudtrail_s3_events
WHERE account = '123456789012' AND region = 'us-east-1'
    AND timestamp BETWEEN '2026/05/15' AND '2026/05/27'
    AND eventname IN ('DeleteObject', 'DeleteObjects')
ORDER BY eventtime DESC;
```

---

## Thực Hành Tốt Nhất & Khắc Phục Lỗi

- **Ưu Tiên Lọc Phân Vùng:** Luôn lọc theo cột phân vùng (`account` , `region` , `timestamp` ) trước. Việc dùng `eventtime`  để lọc thời gian sẽ gây quét toàn bộ dữ liệu, tăng chi phí.
- **Lỗi HiveHeadObject:** Nếu chi phí tăng cao do các tác vụ siêu dữ liệu, hãy cấu hình CloudTrail advanced event selectors để loại trừ cuộc API `HeadObject` .
- **Tính Toàn Vẹn và Bảo Mật:** Kích hoạt tính năng log file validation để ngăn ngừa giả mạo. Mọn lưu trữ nhật ký tại một tài khoản AWS chuyên biệt (Log Archive account trong AWS Organization).
- **Lỗi HIVE_PARTITION_SCHEMA_MISMATCH:** Khi gặp lỗi này, hãy đối chiếu `storage.location.template`  xem có khớp hoàn toàn với đường dẫn thư mục thực tế trên S3 chưa.

---

## Kết luận

Việc tập trung hóa S3 data events qua CloudTrail cung cấp ngữ cảnh định danh và ủy quyền vô cùng quan trọng cho công tác bảo mật và tuân thủ. Bằng cách kết hợp với Athena partition projection, bạn có thể thực hiện các cuộc điều tra bảo mật hiệu quả và tối ưu chi phí trên hàng nghìn tỷ sự kiện hành động.
