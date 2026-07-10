---
title: "Worklog Tuần 10"
date: 2026-06-19
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---
### Mục tiêu tuần 10:

* Tìm hiểu tầm quan trọng của vá lỗi hệ điều hành và cách thiết lập tự động hóa vá lỗi không gián đoạn (blue/green, EC2 Image Builder, Systems Manager, CloudFormation).
* Nghiên cứu kiến trúc và cơ chế hoạt động của AWS Elastic Disaster Recovery (AWS DRS) để thiết lập sao chép, thử nghiệm và phục hồi thảm họa (Failover/Failback).
* Tìm hiểu quy trình xử lý dữ liệu luồng clickstream thời gian thực (Streaming ETL) với Amazon Managed Service for Apache Flink, AWS Glue, Amazon Kinesis, và MSK.
* Thực hành chuyển đổi cơ sở dữ liệu và nhập dữ liệu (data ingestion) sử dụng dịch vụ AWS Database Migration Service (DMS).

### Các công việc cần triển khai trong tuần này:
#### Tuần 10 (Từ 19/06/2026 – 25/06/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Làm quen với các thành viên FCJ <br> - Đọc và lưu ý các nội quy, quy định tại đơn vị thực tập <br> + Tìm hiểu tầm quan trọng của vá lỗi hệ điều hành đối với bảo mật và tuân thủ (compliance) <br> + Hiểu phương pháp triển khai blue/green để tạo và thay thế AMI <br> + Nghiên cứu tự động hóa vá lỗi sử dụng các dịch vụ AWS: <br>&emsp; * EC2 Image Builder (tạo AMI tự động) <br>&emsp; * Systems Manager Automation Document (điều phối thực thi) <br>&emsp; * CloudFormation với chính sách AutoScalingReplacingUpdate (triển khai không gián đoạn) | 19/06/2026 | 19/06/2026 | |
| 3 | + Tìm hiểu các khái niệm cơ bản về AWS Elastic Disaster Recovery (AWS DRS): cách giảm thiểu thời gian ngừng hoạt động và mất dữ liệu, chỉ số RTO/RPO, tối ưu chi phí và phục hồi về một thời điểm (point-in-time recovery). <br> + Nghiên cứu kiến trúc tổng quan của AWS DRS: sao chép đĩa máy chủ nguồn, cài đặt Replication Agent, máy chủ nhân bản trong vùng Staging Area VPC và các thực thể phục hồi mục tiêu. <br> + Tìm hiểu cấu hình môi trường on-premises mô phỏng: public/private subnets, dịch vụ DNS, các ứng dụng cài sẵn. <br> + Chuẩn bị kiến thức cơ bản: kết nối SSH đến máy chủ Linux và kết nối RDP đến máy chủ Windows bastion. | 20/06/2026 | 20/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | + Kết nối vào máy chủ Windows bastion qua RDP và các máy chủ Linux qua SSH. <br> + Cài đặt AWS Replication Agent lên các máy chủ nguồn on-premises mô phỏng để đồng bộ hóa dữ liệu ở cấp độ block-level. <br> + Cấu hình các thiết lập nhân bản trên bảng điều khiển AWS DRS và giám sát quá trình đồng bộ hóa dữ liệu ban đầu. <br> + Thực hành các thao tác phục hồi thảm họa (Disaster Recovery): chạy thử nghiệm không gián đoạn (drill), Failover (chuyển đổi dự phòng khi có thảm họa) và Failback (phục hồi trở lại môi trường nguồn). | 21/06/2026 | 21/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Tìm hiểu Data Engineering Immersion Day. <br> - Lab 1: Phát hiện luồng click chuột bất thường bằng Amazon Managed Service for Apache Flink: <br>&emsp; + Chuẩn bị môi trường: Khởi tạo các tài nguyên (S3, Kinesis Stream, IAM Role). <br>&emsp; + Streaming ETL với Glue: Tạo Data Catalog, thiết lập ETL Job biến đổi dữ liệu real-time. <br>&emsp; + Real-time Streaming với Kinesis: Đẩy dữ liệu mô phỏng clickstream vào Kinesis. <br>&emsp; + Clickstream Analytics sử dụng MSK: Cấu hình Amazon Managed Streaming for Apache Kafka để phân tích sự kiện. | 22/06/2026 | 22/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Lab 2: Nhập data với DMS: <br>&emsp; + Thực hành DMS Migration Lab: Khởi tạo Replication Instance, cấu hình Source/Target Endpoints và chạy Database Migration Task. <br>&emsp; + Tùy chọn: Dùng CloudFormation để chạy AutoComplete DMS Lab (tự động hóa) hoặc Skip DMS Lab nếu không có thời gian. | 23/06/2026 | 23/06/2026 | <https://cloudjourney.awsstudygroup.com/> |


### Kết quả đạt được tuần 10:

* **Tự động hóa vá lỗi hệ điều hành:**
  * Hiểu rõ vai trò của bảo mật OS patching đối với sự tuân thủ (compliance) trong doanh nghiệp.
  * Nắm vững phương pháp tạo AMI tự động bằng EC2 Image Builder và điều phối quy trình bằng Systems Manager Automation Document.
  * Hiểu cách áp dụng AutoScalingReplacingUpdate trong CloudFormation để thực hiện cập nhật và thay thế AMI theo cơ chế blue/green không gián đoạn.

* **Phục hồi thảm họa với AWS DRS:**
  * Hiểu sâu sắc kiến trúc DRS: cài đặt thành công AWS Replication Agent trên máy chủ nguồn để sao chép block-level về Staging Area VPC trên AWS.
  * Thực hành kiểm thử thảm họa thành công qua các thao tác: drill (chạy thử nghiệm không gián đoạn), Failover (chuyển đổi dự phòng khi thảm họa xảy ra) và Failback (phục hồi trở lại môi trường nguồn).

* **Xử lý dữ liệu thời gian thực (Data Engineering):**
  * Thiết lập thành công luồng xử lý clickstream thời gian thực bằng Flink, Glue Data Catalog, Kinesis Stream, và phân tích sự kiện qua MSK (Kafka).

* **Chuyển đổi dữ liệu với AWS DMS:**
  * Triển khai thành công DMS Migration Lab: cấu hình Replication Instance, Source/Target Endpoints và thực thi các Database Migration Tasks để di chuyển cơ sở dữ liệu lên AWS.

