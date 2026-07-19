---
title: "Worklog Tuần 10"
date: 2026-06-19
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---
### Mục tiêu tuần 10:

* Tự động hóa quy trình cập nhật bản vá hệ điều hành (OS Patching) không gián đoạn dịch vụ với EC2 Image Builder, Systems Manager và CloudFormation.
* Khai thác giải pháp phục hồi thảm họa AWS Elastic Disaster Recovery (AWS DRS) để thiết lập cơ chế sao chép dữ liệu block-level, kiểm thử Failover và Failback.
* Xây dựng hệ thống xử lý luồng dữ liệu thời gian thực (Streaming ETL) phân tích sự kiện Clickstream qua Apache Flink, AWS Glue, Kinesis và MSK.
* Thực hành dịch chuyển cơ sở dữ liệu và nạp dữ liệu (Data Ingestion) an toàn bằng AWS Database Migration Service (DMS).

### Các công việc cần triển khai trong tuần này:
#### Tuần 10 (Từ 19/06/2026 – 25/06/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Hội nhập cùng cộng đồng FCJ và nắm vững nội quy an toàn tại đơn vị thực tập. <br> - Đánh giá tầm quan trọng của việc cập nhật bản vá OS Patching trong bảo mật và tuân thủ tiêu chuẩn an toàn thông tin. <br> - Tiếp cận phương pháp phát hành Blue/Green trong việc khởi tạo và thay thế phiên bản AMI. <br> - Tự động hóa chu kỳ vá lỗi với bộ dịch vụ AWS chuyên dụng: <br>&emsp; * EC2 Image Builder: Tự động hóa đóng gói và tạo bản đóng băng AMI. <br>&emsp; * Systems Manager Automation Document: Điều phối kịch bản thực thi công việc. <br>&emsp; * AWS CloudFormation: Cấu hình chính sách `AutoScalingReplacingUpdate` phục vụ nâng cấp hệ thống Zero-downtime. | 19/06/2026 | 19/06/2026 | |
| 3 | - Thấu hiểu các khái niệm cốt lõi trong AWS Elastic Disaster Recovery (AWS DRS): tối ưu chỉ số RTO/RPO, phục hồi mốc thời gian (Point-in-time recovery) và tiết kiệm chi phí hạ tầng. <br> - Phân tích kiến trúc tổng thể AWS DRS: cơ chế sao chép ổ đĩa máy chủ nguồn, cài đặt Replication Agent, tạo máy chủ nhân bản trong Staging Area VPC. <br> - Khởi tạo mô hình môi trường On-premises giả lập: phân vùng Public/Private Subnets, dịch vụ DNS và ứng dụng phụ trợ. <br> - Chuẩn hóa các thao tác điều khiển: kết nối SSH đến máy chủ Linux và RDP đến máy chủ Windows Bastion Host. | 20/06/2026 | 20/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Kết nối bảo mật vào máy chủ Windows Bastion (RDP) và các nốt máy chủ Linux (SSH). <br> - Cài đặt phần mềm AWS Replication Agent lên các máy chủ nguồn On-premises mô phỏng để tự động đồng bộ hóa dữ liệu ở cấp độ khối (Block-level replication). <br> - Chuẩn hóa cấu hình nhân bản dữ liệu trên AWS DRS Console và theo dõi trạng thái đồng bộ ban đầu. <br> - Diễn tập thực chiến quy trình Phục hồi Thảm họa (Disaster Recovery): chạy kịch bản diễn tập không ảnh hưởng sản xuất (Drill), thực thi chuyển đổi dự phòng khi gặp thảm họa (Failover) và khôi phục về môi trường gốc (Failback). | 21/06/2026 | 21/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Thao tác chuỗi bài thực hành Data Engineering Immersion Day. <br> - Lab 1: Nhận diện luồng clickstream bất thường bằng Amazon Managed Service cho Apache Flink: <br>&emsp; + Chuẩn bị hạ tầng: Khởi tạo S3 Buckets, Kinesis Data Streams và phân quyền IAM Roles. <br>&emsp; + Triển khai Streaming ETL với AWS Glue: Thiết lập Data Catalog và Glue ETL Jobs xử lý dữ liệu thời gian thực. <br>&emsp; + Đẩy dữ liệu thời gian thực với Kinesis: Đưa luồng clickstream giả lập vào Kinesis Stream. <br>&emsp; + Phân tích Clickstream Analytics sử dụng MSK: Cấu hình Amazon Managed Streaming for Apache Kafka phục vụ phân tích sự kiện. | 22/06/2026 | 22/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Lab 2: Thu thập và nạp dữ liệu với AWS DMS: <br>&emsp; + Thực hành bài lab dịch chuyển cơ sở dữ liệu DMS: Khởi tạo Replication Instance, cấu hình Source/Target Endpoints và chạy Database Migration Task. <br>&emsp; + Thực thi tự động hóa hạ tầng lab qua AWS CloudFormation kịch bản AutoComplete DMS Lab. | 23/06/2026 | 23/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 10:

* **Tự động hóa vá lỗi hệ điều hành:**
  * Thấu hiểu triết lý bảo mật OS Patching phục vụ đáp ứng quy chuẩn tuân thủ an toàn doanh nghiệp.
  * Tự động hóa quy trình tạo bản đóng băng AMI bằng EC2 Image Builder và điều phối công việc qua Systems Manager Automation.
  * Ứng dụng chính sách `AutoScalingReplacingUpdate` trong CloudFormation triển khai thay thế AMI theo chiến lược Blue/Green không gián đoạn dịch vụ.

* **Phục hồi thảm họa với AWS DRS:**
  * Làm chủ kiến trúc AWS DRS: cài đặt AWS Replication Agent trên máy chủ nguồn để tự động đồng bộ hóa khối (Block-level) về Staging Area VPC.
  * Thực hành diễn tập thảm họa thành công qua 3 giai đoạn: Drill (diễn tập không gián đoạn), Failover (chuyển đổi dự phòng thảm họa) và Failback (khôi phục hệ thống nguồn).

* **Phân tích dữ liệu thời gian thực (Data Engineering Immersion Day - Lab 1):**
  * Thiết lập môi trường hạ tầng dữ liệu hoàn chỉnh với Amazon S3, Kinesis Stream và phân quyền IAM Roles chuẩn mực.
  * Xây dựng luồng Streaming ETL trên AWS Glue với Data Catalog và Glue ETL Jobs xử lý dữ liệu trực tiếp.
  * Đẩy luồng dữ liệu thời gian thực clickstream vào Kinesis Stream thành công.
  * Phân tích luồng hành vi bất thường bằng cách kết hợp Amazon MSK (Kafka) và Amazon Managed Service cho Apache Flink.

* **Nhập dữ liệu và chuyển dịch cơ sở dữ liệu với AWS DMS (Lab 2):**
  * Thực hành thành thạo quy trình chuyển dịch dữ liệu bằng AWS Database Migration Service (AWS DMS).
  * Khởi tạo Replication Instance, thiết lập chính xác các điểm truy cập Nguồn/Đích (Source/Target Endpoints).
  * Vận hành thành công Database Migration Task truyền tải dữ liệu an toàn và tự động hóa qua CloudFormation.
