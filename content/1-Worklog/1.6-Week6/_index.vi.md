---
title: "Worklog Tuần 6"
date: 2026-05-22
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---
### Mục tiêu tuần 6:

* Xây dựng hạ tầng Data Lake Serverless và thiết lập luồng xử lý dữ liệu thời gian thực tích hợp S3, Kinesis, Athena và QuickSight.
* Khai thác các dịch vụ trích xuất và biến đổi dữ liệu (ETL) chuyên sâu với AWS Glue, EMR và tải dữ liệu lên kho lưu trữ doanh nghiệp Amazon Redshift.
* Thiết lập mô hình truyền tin phân tán Publisher/Subscriber kết hợp Amazon SNS và SQS.
* Phát triển giải pháp không máy chủ (Serverless) với AWS Lambda (tự động xử lý ảnh qua S3 event trigger, tối ưu qua Lambda Layers) và kết nối cơ sở dữ liệu Amazon DynamoDB (thao tác CRUD, phân quyền IAM, giám sát với X-Ray).

### Các công việc cần triển khai trong tuần này:
#### Tuần 6 (Từ 22/05/2026 – 28/05/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Thiết kế tổng thể kiến trúc Data Lake Serverless. <br> - Xây dựng luồng thu thập và xử lý dữ liệu tập trung trên Amazon S3. <br> - Tích hợp Amazon Kinesis phục vụ tiếp nhận luồng dữ liệu thời gian thực (Data Streaming). <br> - Xử lý và phân tích trực tiếp dữ liệu truyền phát bằng Amazon Kinesis Data Analytics. <br> - Truy vấn dữ liệu tức thì bằng Amazon Athena và thiết lập báo cáo biểu đồ trực quan trên Amazon QuickSight. | 22/05/2026 | 22/05/2026 | |
| 3 | - Tự động hóa quét sơ đồ dữ liệu (Data Catalog & Schema) bằng AWS Glue Crawler. <br> - Xây dựng kịch bản trích xuất và biến đổi dữ liệu ETL. <br> - Thực thi các phiên xử lý ETL tương tác (Interactive Sessions) qua Jupyter Notebook trên AWS Glue Studio. <br> - Vận hành và theo dõi trạng thái các Glue ETL Jobs từ bảng điều khiển Glue Studio. <br> - Chuẩn hóa và làm sạch dữ liệu trực quan bằng Glue DataBrew. <br> - Thực thi công việc xử lý dữ liệu phân tán Spark trên cụm máy chủ Amazon EMR. <br> - Tải luồng dữ liệu đã biến đổi từ AWS Glue vào kho dữ liệu Amazon Redshift. <br> - Tiếp cận các nguyên lý thiết kế tối ưu kiến trúc cho Amazon Redshift. | 23/05/2026 | 23/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Nghiên cứu chuyên sâu cơ chế truyền tin thông báo Amazon SNS và hàng chờ thông điệp Amazon SQS. <br> - Triển khai mô hình truyền tin Pub/Sub và thiết lập chính sách lọc thông điệp (Subscription Filter Policy) để tự động hóa phân luồng dữ liệu. <br>&emsp; + Khởi tạo hàng đợi SQS mới dành riêng cho các đơn hàng khu vực Châu Âu (EU orders). <br>&emsp; + Đăng ký hàng đợi SQS làm subscriber nhận tin từ SNS Topic Đơn hàng. <br>&emsp; + Thiết lập chính sách lọc thông điệp dựa trên thuộc tính `location = eu-west` để chỉ tiếp nhận thông điệp từ thị trường EU. | 24/05/2026 | 24/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Thấu hiểu bản chất Kiến trúc Serverless, các thành phần nòng cốt (Lambda, S3, DynamoDB) và mô hình bài toán áp dụng. <br>&emsp; + Khởi tạo và tối ưu thông số cho Lambda function (Runtime, Memory, Timeout). <br>&emsp; + Cấu hình S3 Event Trigger để tự động hóa kích hoạt xử lý ngay khi có tệp ảnh tải lên S3 bucket. <br>&emsp; + Khai thác Lambda Layers để đóng gói các thư viện mã nguồn phụ thuộc (Sharp/Jimp cho Node.js, Pillow cho Python) giúp xử lý co giãn kích thước ảnh. <br>&emsp; + Thực hành quy chuẩn an toàn thông tin (IAM Roles tối giản) và tối ưu hóa hiệu năng chi phí vận hành. | 25/05/2026 | 25/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | <br>&emsp; + Thiết kế bảng DynamoDB tối ưu với cấu trúc Partition Key và Sort Key. <br>&emsp; + Thiết lập quyền hạn IAM Roles & Policies cho phép Lambda tương tác an toàn với DynamoDB. <br>&emsp; + Thực thi các thao tác CRUD cơ bản thông qua DynamoDB SDK tích hợp trong Lambda. <br>&emsp; + Phân tích nhật ký ghi vết sự kiện trên CloudWatch Logs. <br>&emsp; + Giám sát các chỉ số vận hành chính (Invocations, Duration, Errors, Throttles) qua CloudWatch Metrics. <br>&emsp; + Cấu hình AWS X-Ray để theo dõi truy vết (Tracing) chi tiết luồng xử lý của hệ thống. | 26/05/2026 | 26/05/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 6:

* **Kiến trúc Data Lake Serverless & Truy vấn dữ liệu:**
  * Thiết kế và xây dựng thành công đường ống xử lý dữ liệu lưu trữ tập trung trên Amazon S3 (Raw & Processed Data).
  * Tích hợp Amazon Kinesis và Kinesis Data Analytics để thu thập, phân tích luồng dữ liệu thời gian thực.
  * Phân tích dữ liệu trực tiếp trên S3 bằng Amazon Athena và xây dựng bảng biểu đồ trực quan hóa dữ liệu qua Amazon QuickSight.

* **Tự động hóa ETL với AWS Glue & Redshift:**
  * Sử dụng AWS Glue Crawler để tự động quét cấu trúc và lập sơ đồ dữ liệu (Data Catalog) trên S3.
  * Xây dựng và thực thi các công việc ETL (Extract, Transform, Load) tự động bằng Glue Studio và script Spark trên Amazon EMR.
  * Làm sạch và chuẩn hóa dữ liệu với Glue DataBrew, đẩy dữ liệu đã biến đổi vào kho Amazon Redshift phục vụ báo cáo doanh nghiệp.

* **Mô hình Messaging & Pub/Sub:**
  * Nắm vững cơ chế hoạt động và mô thức phối hợp giữa Amazon SNS (Push) và SQS (Pull).
  * Triển khai mô hình Pub/Sub và cấu hình bộ lọc Subscription Filter Policy giúp phân luồng thông điệp chính xác theo tiêu chí kinh doanh.

* **Kiến trúc Serverless với Lambda & DynamoDB:**
  * Xây dựng giải pháp Serverless với AWS Lambda, tự động kích hoạt xử lý hình ảnh dựa trên sự kiện S3 Event Trigger.
  * Sử dụng Lambda Layers để đóng gói thư viện phụ thuộc (Sharp, Pillow), giúp tối ưu hóa kích thước gói triển khai.
  * Thiết kế sơ đồ cơ sở dữ liệu DynamoDB chuẩn mực với Partition Key và Sort Key.
  * Thực thi nguyên tắc phân quyền tối giản (Least Privilege IAM Roles) và viết mã nguồn xử lý CRUD qua AWS SDK.
  * Theo dõi chỉ số, giám sát sự cố và phân tích vết luồng xử lý hệ thống bằng CloudWatch Logs, Metrics và AWS X-Ray.
