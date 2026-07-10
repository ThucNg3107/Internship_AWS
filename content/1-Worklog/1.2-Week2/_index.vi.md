---
title: "Worklog Tuần 2"
date: 2026-04-27
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---
### Mục tiêu tuần 2:

* Quản trị máy chủ EC2 (Linux & Windows), quản lý EBS volume/snapshot, AMI và phân quyền qua IAM Role cho EC2.
* Thiết lập môi trường lập trình Cloud9, hosting web tĩnh trên S3 và cấu hình cơ bản Amazon RDS.
* Tìm hiểu ảo hóa container với Docker trên ECR, ECS và giám sát với CloudWatch, Container Insights, Security Hub, AWS Backup.
* Xây dựng mạng nâng cao (VPC Peering, Transit Gateway) và thiết lập quy trình CI/CD qua GitLab, GitHub Actions, CodeBuild.

### Các công việc cần triển khai trong tuần này:
#### Tuần 2 (Từ 24/04/2026 - 30/04/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tạo VPC cho Linux và Windows Instance; cấu hình Security Group cho từng máy <br> - Ôn tập EC2 căn bản và triển khai Node.js trên Amazon Linux/Windows <br> - Thực hành đổi loại instance EC2, tạo/quản lý EBS snapshot, AMI và khôi phục truy cập Windows instance | 24/04/2026 | 24/04/2026 | <https://000004.awsstudygroup.com/> |
| 3 | - Thực hành cấp quyền EC2 Role thông qua IAM Role <br> - Tìm hiểu và sử dụng Cloud9 cho môi trường phát triển/làm việc | 25/04/2026 | 25/04/2026 | <https://000048.awsstudygroup.com/> |
| 4 | - Tìm hiểu và triển khai web hosting tĩnh bằng S3 bucket <br> - Thiết lập cơ bản Amazon RDS | 26/04/2026 | 26/04/2026 | <https://000049.awsstudygroup.com/> |
| 5 | - Thực hành workshop AWS CloudWatch, theo dõi metrics <br> - Triển khai AWS Backup và cấu hình gửi thông báo email <br> - Nhập/xuất máy ảo (VM) với Amazon S3 bucket và EC2 <br> - Thực hành Docker container để làm việc với ECR, RDS... <br> - Tìm hiểu cách triển khai ứng dụng trên Amazon ECS | 27/04/2026 | 27/04/2026 | <https://000057.awsstudygroup.com/> <https://000005.awsstudygroup.com/> |
| 6 | - Triển khai CI/CD với GitLab, GitHub Actions và AWS CodeBuild; cấu hình giám sát bằng Container Insights <br> - Tìm hiểu AWS Security Hub <br> - Thiết lập VPC Peering để kết nối các VPC <br> - Thiết lập AWS Transit Gateway để kết nối nhiều VPC thay cho mô hình chỉ dùng VPC Peering | 28/04/2026 | 28/04/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 2:

* **Lưu trữ và cơ sở dữ liệu:**
  * Triển khai thành công website tĩnh (static web hosting) bằng Amazon S3 bucket.
  * Thiết lập và vận hành cơ sở dữ liệu với Amazon RDS.
  * Thực hiện thao tác import/export máy ảo (VM) qua Amazon S3 và EC2.

* **Giám sát hệ thống và mạng nâng cao:**
  * Theo dõi hiệu suất hệ thống bằng AWS CloudWatch (metrics, logs, math expressions) và Container Insights.
  * Hoàn thiện kết nối mạng đa VPC thông qua VPC Peering và AWS Transit Gateway.

* **Công cụ quản trị và sao lưu:**
  * Sử dụng thành thạo AWS CLI để tương tác và quản lý tài nguyên AWS.
  * Triển khai AWS Backup, tạo backup plan tự động và thiết lập thông báo email.

* **Containerization và CI/CD:**
  * Ứng dụng Docker container kết hợp các dịch vụ Amazon ECR, RDS và EC2.
  * Triển khai ứng dụng trên Amazon ECS, gồm cluster, service và namespace với Cloud Map.
  * Xây dựng pipeline CI/CD bằng GitLab, GitHub Actions và AWS CodeBuild.

* **Bảo mật đám mây:**
  * Củng cố kiến thức quản trị bảo mật tập trung trên AWS thông qua AWS Security Hub.
  * Sử dụng IAM Role cho EC2 để phân quyền truy cập tài nguyên AWS một cách an toàn.
  * Thiết lập môi trường lập trình từ xa tiện lợi bằng AWS Cloud9.
