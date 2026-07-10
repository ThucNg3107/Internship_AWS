---
title: "Worklog Tuần 9"
date: 2026-06-12
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---
### Mục tiêu tuần 9:

* Nghiên cứu và triển khai AWS Managed Microsoft AD để di chuyển hệ thống Active Directory doanh nghiệp lên AWS.
* Thực hành quản trị thư mục AWS Directory Service và tích hợp kết nối miền (domain join) với các máy chủ Windows Server EC2.
* Nghiên cứu và triển khai dịch vụ quản lý thông tin bảo mật AWS Secrets Manager.
* Tích hợp Secrets Manager với Amazon RDS và thiết lập quy trình tự động thay đổi mật khẩu định kỳ (Secret Rotation).
* Triển khai ứng dụng trên AWS Fargate Container truy cập an toàn vào cơ sở dữ liệu RDS thông qua Secrets Manager VPC Endpoint.
* Tìm hiểu và áp dụng các nguyên tắc truy cập xa an toàn trên AWS Cloud bằng cách sử dụng Security Groups và AWS Network Firewall dựa trên khuyến nghị từ CISO Stephan Schmidt.
* Nghiên cứu giải pháp quản lý chính sách bảo mật tập trung thông qua AWS Firewall Manager, AWS Config, AWS Organizations và AWS Resource Access Manager (RAM).
* Tìm hiểu giải pháp phát hiện mối đe dọa và khắc phục tự động bằng Amazon GuardDuty, EventBridge Event Rules và AWS Lambda.

### Các công việc cần triển khai trong tuần này:
#### Tuần 9 (Từ 12/06/2026 – 18/06/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu và nghiên cứu về giải pháp dịch vụ thư mục tích hợp AWS Directory Service. <br> - Nghiên cứu kiến trúc, các tính năng cốt lõi (như Multi-region replication, trust relationship) và sự khác biệt giữa hai phiên bản Standard và Enterprise. <br>&emsp; + Thiết lập hạ tầng mạng VPC, Subnets đáp ứng yêu cầu kỹ thuật của Directory Service. <br>&emsp; + Triển khai thư mục AWS Managed Microsoft AD. <br>&emsp; + Khởi tạo máy chủ Windows Server EC2 và tiến hành gia nhập miền (domain join). <br>&emsp; + Cài đặt công cụ AD Administration Tools trên Windows Server để quản lý miền (tạo Organizational Units, Users, Groups) | 12/06/2026 | 12/06/2026 | |
| 3 | - Nghiên cứu giải pháp bảo mật thông tin đăng nhập cơ sở dữ liệu sử dụng AWS Secrets Manager tích hợp với Amazon RDS. <br> - Tìm hiểu kiến trúc mạng kết nối an toàn (VPC, private subnets, security groups) giữa máy chủ Bastion Host và cơ sở dữ liệu Amazon RDS MySQL (Private). <br>&emsp; + Thiết lập VPC với các Subnet và Route Table cần thiết. <br>&emsp; + Khởi tạo cơ sở dữ liệu Amazon RDS MySQL trong phân vùng private. <br>&emsp; + Cấu hình AWS Secrets Manager để lưu trữ và quản lý thông tin đăng nhập (credentials) của RDS. <br>&emsp; + Khởi tạo Amazon EC2 Bastion Host và thực hiện kết nối cơ sở dữ liệu RDS sử dụng thông tin bảo mật lấy từ Secrets Manager. | 13/06/2026 | 13/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Nghiên cứu quy trình tự động xoay vòng mật khẩu để nâng cao tính bảo mật theo tiêu chuẩn CSF và CAF . <br> - Tìm hiểu cách tích hợp dịch vụ Amazon ECS kết nối an toàn với cơ sở dữ liệu RDS sử dụng Secrets Manager qua Interface VPC Endpoint. <br>&emsp; + Thiết lập và kích hoạt cơ chế Secret Rotation tự động định kỳ cho RDS database và kiểm thử độ chính xác bằng các đoạn mã Shell Script. <br>&emsp; + Đóng gói ứng dụng mẫu vào Docker Container và đẩy lên Amazon ECR. <br>&emsp; + Triển khai AWS Fargate Container trong VPC. <br>&emsp; + Cấu hình Fargate Task Role và Secrets Manager Interface VPC Endpoint để cho phép Container truy xuất mật khẩu an toàn từ Secrets Manager và kết nối trực tiếp đến RDS MySQL. | 14/06/2026 | 14/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Tìm hiểu quy trình bảo mật trên AWS Cloud thông qua 10 lời khuyên hàng đầu của AWS CISO Stephan Schmidt về an toàn thông tin, tập trung vào truy cập từ xa an toàn. <br> - Nghiên cứu giải pháp thiết lập tường lửa và kiểm soát truy cập mạng bằng Security Group và dịch vụ AWS Network Firewall. <br> - Thực hành phân tích các kịch bản bảo mật kết nối từ xa thông qua 2 giao thức phổ biến RDP và SSH. | 15/06/2026 | 15/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Tìm hiểu và thực hành phát hiện mối đe dọa hệ thống và khắc phục tự động với Amazon GuardDuty. <br> - Tái dựng các kịch bản tấn công và tự động khắc phục bằng cách kết hợp EventBridge Event Rules và AWS Lambda. <br>&emsp; + Triển khai CloudFormation Template để thiết lập môi trường thực hành tại us-west-2 (Oregon). <br>&emsp; + Phát hiện và khắc phục máy chủ EC2 bị xâm nhập thông qua GuardDuty, EventBridge và Lambda. <br>&emsp; + Xác định các cuộc gọi API trái phép từ IAM Credentials bị lộ và thực hiện khắc phục thủ công. <br>&emsp; + Phát hiện và ngăn chặn hành vi rò rỉ quyền IAM role gọi API từ máy chủ bên ngoài bằng AWS Lambda. | 16/06/2026 | 16/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 9:

* **Triển khai AWS Managed Microsoft AD & Quản trị Active Directory:**
  * Hiểu rõ khái niệm và kiến trúc hoạt động của AWS Directory Service, đặc biệt là AWS Managed Microsoft AD.
  * Triển khai thành công bộ thư mục AWS Managed Microsoft AD hoạt động song song trên nhiều Availability Zones (AZs) để đảm bảo tính sẵn sàng cao.
  * Thực hành kết nối miền (domain join) thành công cho máy chủ Windows Server EC2.
  * Cài đặt và sử dụng thành thạo các công cụ AD Administration Tools trên Windows Server để quản lý danh bạ, tạo tài khoản người dùng (Users), phân nhóm (Groups) và tổ chức các đơn vị Organizational Units (OUs).

* **Tích hợp AWS Secrets Manager, RDS & AWS Fargate:**
  * Hiểu rõ vai trò kiểm soát an ninh của Secrets Manager đối với cơ sở dữ liệu theo khung bảo mật CSF (Prevention) và CAF (Preventative).
  * Triển khai thành công VPC Endpoint kết nối riêng tư đến Secrets Manager.
  * Tích hợp thành công và cấu hình tính năng xoay vòng mật khẩu tự động (Secret Rotation) định kỳ cho RDS MySQL.
  * Đóng gói ứng dụng Docker, tải lên Amazon ECR và chạy ứng dụng trên AWS Fargate Container.
  * Kết nối an toàn từ tầng ứng dụng Fargate container và EC2 Bastion Host đến cơ sở dữ liệu RDS thông qua việc truy xuất thông tin từ Secrets Manager một cách tự động và bảo mật.

* **Truy cập từ xa an toàn & Tích hợp AWS Network Firewall:**
  * Tìm hiểu 10 lời khuyên bảo mật quan trọng từ AWS CISO Stephan Schmidt về việc đảm bảo an toàn truy cập từ xa cho các máy chủ và dịch vụ.
  * Nắm vững cách cấu hình Amazon EC2 Security Groups và AWS Network Firewall để giới hạn truy cập từ xa theo địa chỉ IP, cổng kết nối (Port) và giao thức (Protocol).
  * Thực hành các kịch bản kết nối từ xa an toàn qua giao thức SSH (Cổng 22) và RDP (Cổng 3389).
  * Tìm hiểu cách triển khai chính sách bảo mật tập trung cho nhiều tài khoản AWS sử dụng AWS Firewall Manager, AWS Organizations, AWS Config và AWS Resource Access Manager (RAM).

* **Phát hiện mối đe dọa & Khắc phục tự động với Amazon GuardDuty:**
  * Cấu hình thành công Amazon GuardDuty để phát hiện các mối đe dọa hệ thống và tạo các findings bảo mật.
  * Tái dựng các kịch bản tấn công và thiết lập cơ chế tự động khắc phục bằng CloudFormation, EventBridge Event Rules và AWS Lambda.
  * Xử lý thành công các mối nguy hại liên quan đến EC2 bị xâm nhập, thông tin đăng nhập IAM bị lộ và rò rỉ quyền IAM role ra bên ngoài.
  * Áp dụng hiệu quả các nguyên tắc NIST CSF (Bảo vệ, Phát hiện, Phản hồi) và AWS CAF (Ngăn ngừa, Phát hiện, Phản hồi).
