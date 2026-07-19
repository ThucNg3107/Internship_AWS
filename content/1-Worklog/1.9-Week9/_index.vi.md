---
title: "Worklog Tuần 9"
date: 2026-06-12
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---
### Mục tiêu tuần 9:

* Nghiên cứu và triển khai dịch vụ quản trị thư mục AWS Managed Microsoft AD hỗ trợ chuyển dịch hạ tầng Active Directory lên Cloud.
* Thực hành quản trị danh bạ AWS Directory Service và thực hiện gia nhập miền (Domain Join) cho các máy chủ Windows Server EC2.
* Xây dựng giải pháp quản lý thông tin bảo mật tập trung với AWS Secrets Manager.
* Tích hợp Secrets Manager với Amazon RDS và tự động hóa quy trình xoay vòng mật khẩu (Secret Rotation) theo tiêu chuẩn an ninh mạng.
* Triển khai ứng dụng container hóa trên AWS Fargate truy cập cơ sở dữ liệu RDS an toàn thông qua Secrets Manager Interface VPC Endpoint.
* Khai thác quy chuẩn bảo mật truy cập từ xa trên AWS Cloud với Security Groups và AWS Network Firewall dựa trên khuyến nghị từ CISO Stephan Schmidt.
* Chuẩn hóa quản trị chính sách bảo mật đa tài khoản với AWS Firewall Manager, AWS Config, AWS Organizations và AWS RAM.
* Triển khai hệ thống tự động phát hiện mối đe dọa và khắc phục sự cố an ninh mạng bằng Amazon GuardDuty, EventBridge và AWS Lambda.

### Các công việc cần triển khai trong tuần này:
#### Tuần 9 (Từ 12/06/2026 – 18/06/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Nghiên cứu hệ giải pháp quản trị thư mục AWS Directory Service. <br> - Phân tích kiến trúc, tính năng cao cấp (Multi-region replication, Trust Relationship) và sự khác biệt giữa hai phiên bản Standard & Enterprise. <br>&emsp; + Thiết lập mạng VPC và Subnets đáp ứng điều kiện hạ tầng cho Directory Service. <br>&emsp; + Khởi tạo dịch vụ thư mục AWS Managed Microsoft AD. <br>&emsp; + Khởi tạo máy chủ Windows Server EC2 và thực hiện quy trình gia nhập miền (Domain Join). <br>&emsp; + Cài đặt công cụ AD Administration Tools trên Windows Server để quản lý danh bạ (tạo OUs, Users, Groups). | 12/06/2026 | 12/06/2026 | |
| 3 | - Triển khai giải pháp mã hóa và quản lý thông tin truy cập cơ sở dữ liệu AWS Secrets Manager kết nối Amazon RDS MySQL. <br> - Xây dựng mô hình kết nối mạng bảo mật (Private Subnets, Security Groups) giữa Bastion Host và RDS MySQL. <br>&emsp; + Khởi tạo VPC với phân vùng Private Subnets và Route Tables phù hợp. <br>&emsp; + Khởi tạo cụm cơ sở dữ liệu Amazon RDS MySQL trong phân vùng nội bộ (Private). <br>&emsp; + Cấu hình AWS Secrets Manager lưu trữ thông tin tài khoản (Credentials) RDS. <br>&emsp; + Khởi tạo máy chủ EC2 Bastion Host và truy vấn dữ liệu RDS bằng secret lấy từ Secrets Manager. | 13/06/2026 | 13/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Tự động hóa quy trình xoay vòng mật khẩu (Secret Rotation) nhằm tuân thủ tiêu chuẩn an toàn thông tin NIST CSF và AWS CAF. <br> - Tích hợp dịch vụ container Amazon ECS/Fargate truy xuất an toàn cơ sở dữ liệu RDS qua Interface VPC Endpoint. <br>&emsp; + Kích hoạt cơ chế tự động xoay vòng mật khẩu định kỳ cho RDS MySQL và kiểm thử tính đúng đắn qua các kịch bản Shell Script. <br>&emsp; + Đóng gói ứng dụng vào Docker Container và đẩy Image lên Amazon ECR. <br>&emsp; + Khai thác AWS Fargate triển khai Container trong hạ tầng VPC. <br>&emsp; + Cấu hình Fargate Task Role kết hợp Secrets Manager Interface VPC Endpoint để Container truy xuất mật khẩu an toàn và truy vấn trực tiếp RDS. | 14/06/2026 | 14/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Tiếp thu 10 khuyến nghị bảo mật hàng đầu từ AWS CISO Stephan Schmidt tập trung vào mảng bảo vệ truy cập từ xa. <br> - Thiết lập lớp tường lửa kiểm soát lưu lượng mạng chuyên sâu với Security Groups và AWS Network Firewall. <br> - Mô phỏng và phân tích các kịch bản bảo mật truy cập từ xa qua giao thức RDP (cổng 3389) và SSH (cổng 22). | 15/06/2026 | 15/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Triển khai hệ thống tự động phát hiện mối đe dọa an ninh mạng và khắc phục sự cố bằng Amazon GuardDuty. <br> - Giả lập các kịch bản tấn công thực tế và tự động xử lý sự cố qua EventBridge Event Rules và AWS Lambda. <br>&emsp; + Khởi tạo môi trường diễn tập bằng CloudFormation Template tại vùng `us-west-2` (Oregon). <br>&emsp; + Phát hiện và tự động cách ly máy chủ EC2 bị xâm nhập thông qua GuardDuty, EventBridge và Lambda. <br>&emsp; + Nhận diện và thu hồi các yêu cầu API bất thường do rò rỉ IAM Credentials. <br>&emsp; + Ngăn chặn và vô hiệu hóa hành vi lấy cắp quyền IAM Role từ máy chủ ngoài qua AWS Lambda. | 16/06/2026 | 16/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 9:

* **Triển khai AWS Managed Microsoft AD & Quản trị Active Directory:**
  * Thấu hiểu kiến trúc và cơ chế vận hành của AWS Directory Service (AWS Managed Microsoft AD).
  * Khai thác thư mục AWS Managed Microsoft AD phân bổ đa vùng sẵn sàng (Multi-AZ) đạt tiêu chuẩn tính sẵn sàng cao.
  * Thực hiện thành công thao tác gia nhập miền (Domain Join) cho máy chủ Windows Server EC2.
  * Sử dụng thành thạo AD Administration Tools để quản trị danh bạ, khởi tạo tài khoản (Users), nhóm quyền (Groups) và đơn vị quản lý (OUs).

* **Tích hợp AWS Secrets Manager, RDS & AWS Fargate:**
  * Áp dụng thành công giải pháp quản lý thông tin bảo mật AWS Secrets Manager theo khung chuẩn NIST CSF và AWS CAF.
  * Thiết lập Interface VPC Endpoint bảo vệ đường truyền truy xuất Secret riêng tư.
  * Tự động hóa quy trình xoay vòng mật khẩu (Secret Rotation) định kỳ cho cụm RDS MySQL.
  * Triển khai ứng dụng container hóa từ Amazon ECR lên hạ tầng AWS Fargate.
  * Kết nối an toàn từ Fargate Container và EC2 Bastion Host đến RDS MySQL thông qua việc truy xuất secret tự động.

* **Truy cập từ xa an toàn & Tích hợp AWS Network Firewall:**
  * Áp dụng 10 quy tắc an ninh mạng từ AWS CISO Stephan Schmidt vào việc bảo vệ kênh kết nối truy cập từ xa.
  * Chuẩn hóa cấu hình Security Groups và AWS Network Firewall để kiểm soát cổng, giao thức và dải IP nguồn.
  * Vận hành kênh kết nối bảo mật RDP (Port 3389) và SSH (Port 22).
  * Chuẩn hóa quản trị bảo mật tập trung quy mô đa tài khoản qua AWS Firewall Manager, Organizations, Config và RAM.

* **Phát hiện mối đe dọa & Khắc phục tự động với Amazon GuardDuty:**
  * Vận hành Amazon GuardDuty để liên tục quét và phát hiện các dấu hiệu tấn công an ninh mạng.
  * Tự động hóa quy trình phản hồi sự cố (Auto-Remediation) kết hợp CloudFormation, EventBridge Event Rules và Lambda.
  * Xử lý triệt để các tình huống máy chủ EC2 bị chiếm quyền, rò rỉ IAM Credentials và lạm dụng IAM Roles.
  * Thực thi hiệu quả mô hình quản trị an toàn thông tin NIST CSF và AWS CAF (Prevent, Detect, Respond).
