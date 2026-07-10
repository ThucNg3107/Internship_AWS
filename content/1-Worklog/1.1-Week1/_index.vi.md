---
title: "Worklog Tuần 1"
date: 2026-04-20
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---
### Mục tiêu tuần 1:

* Hòa nhập với môi trường thực tập, làm quen các thành viên và nắm bắt quy định tại First Cloud Journey.
* Tiếp cận và làm quen với các khái niệm dịch vụ cơ bản của AWS cùng phương pháp quản lý truy cập và chi phí trong giai đoạn đầu.
* Thực hành thiết lập nền tảng mạng và bảo mật cơ bản cho tài nguyên đám mây.

### Các công việc cần triển khai trong tuần này:
#### Tuần 1 (Từ 17/04/2026 – 23/04/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Làm quen với các thành viên FCJ <br> - Đọc và lưu ý các nội quy, quy định tại đơn vị thực tập | 17/04/2026 | 17/04/2026 | |
| 3 | - Tìm hiểu AWS và các loại dịch vụ <br>&emsp; + Compute <br>&emsp; + Storage <br>&emsp; + Networking <br>&emsp; + Database <br>&emsp; + ... <br> | 18/04/2026 | 18/04/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Tạo AWS Free Tier account <br> - Tìm hiểu AWS Console & AWS CLI <br> - **Thực hành:** <br>&emsp; + Tạo AWS account <br>&emsp; + Cài AWS CLI & cấu hình <br> &emsp; + Cách sử dụng AWS CLI | 19/04/2026 | 19/04/2026 | <https://000001.awsstudygroup.com/> |
| 5 | - Quản lý chi phí AWS Budgets <br> - Tìm hiểu về các loại AWS Budgets <br> - Lợi ích và các bước thiết lập để sử dụng hiệu quả <br> - **Thực hành:** <br>&emsp; + Tạo các loại AWS Budgets <br>&emsp; + Xử lí các Budgets khi không cần thiết | 20/04/2026 | 20/04/2026 | <https://000007.awsstudygroup.com/> |
| 6 | - Tìm hiểu AWS Support <br>&emsp; + Các gói hỗ trợ từ thấp tới cao với từng mục đích sử dụng khác nhau <br>&emsp; + Các loại yêu cầu được phép hỗ trợ: Tài khoản, dịch vụ, kỹ thuật.... <br>&emsp; + Cách thay đổi giữa các gói hỗ trợ <br>&emsp; + Khởi tạo yêu cầu hỗ trợ, mức độ nghiêm trọng và thời gian phản hồi của AWS Support <br> - **Thực hành:** <br>&emsp; + Thay đổi gói hỗ trợ <br>&emsp; + Cách tạo yêu cầu hỗ trợ | 21/04/2026 | 21/04/2026 | <https://000009.awsstudygroup.com/> |
| 7 | - Kiểm soát chi tiết quyền truy cập tài nguyên <br> - Quản lý người dùng <br> - Triển khai bảo mật <br>&emsp; + Tạo và quản lý IAM Groups để tổ chức người dùng <br>&emsp; + Sử dụng IAM Policies để phân quyền <br>&emsp; + Quản lý IAM Users theo nhóm để dể dàng kiểm soát <br>&emsp; + Cách chuyển đồi IAM Role <br> - **Thực hành:** <br>&emsp; + Tạo IAM Group <br>&emsp; + Tạo IAM User <br>&emsp; + Tạo IAM Role <br>&emsp; + Chuyển đổi IAM Role | 22/04/2026 | 22/04/2026 | <https://000002.awsstudygroup.com/> |
| 8 | - Thiết kế và triển khai VPC theo tiêu chuẩn AWS Well-Architected Framework <br>&emsp; + Cấu hình các thành phần bảo mật mạng <br>&emsp; + Thiết lập kết nối an toàn giữa môi trường on-premise và AWS <br> - **Thực hành:** <br>&emsp; + Triển khai Amazon EC2 <br>&emsp; + Tạo máy chủ EC2 <br>&emsp; + Tạo Nat Gateway <br>&emsp; + Sử dụng EC2 instance endpoint để kết nối server <br>&emsp; + Cấu hình Site to Site VPN <br>&emsp; + Tường lửa VPC | 23/04/2026 | 23/04/2026 | <https://000003.awsstudygroup.com/> |

### Kết quả đạt được tuần 1:

* **Hội nhập và Làm quen:**
  * Hoàn thành hội nhập văn hóa làm việc và nội quy thực tập của FCJ cùng các thành viên trong nhóm.

* **Nền tảng AWS & Quản lý chi phí:**
  * Thiết lập và cấu hình tài khoản AWS Free Tier thành công, làm quen với bảng điều khiển quản trị đám mây AWS Management Console.
  * Hiểu sâu sắc và thực hành cấu hình công cụ AWS Budgets để thiết lập các cảnh báo chi phí hợp lý.
  * Tiếp cận dịch vụ AWS Support để biết cách gửi yêu cầu hỗ trợ kỹ thuật theo các cấp độ nghiêm trọng.

* **Bảo mật và Quản lý quyền truy cập (IAM):**
  * Làm chủ dịch vụ AWS IAM thông qua việc cấu hình Group, User, Role, Policy và áp dụng cơ chế Assume Role.
  * Hiểu sâu về các cơ chế bảo mật như chuyển đổi quyền (Assume Role), phân biệt các loại Policy (Identity-based, Resource-based) và áp dụng IAM Instance Profile cho máy chủ ảo EC2.
  * Cài đặt và cấu hình thành công AWS CLI trên máy tính cá nhân để tương tác với tài nguyên AWS một cách lập trình.

* **Thiết lập mạng đám mây (VPC):**
  * Tự thiết kế và triển khai thành công một mạng riêng ảo (VPC) hoàn chỉnh theo tiêu chuẩn AWS Well-Architected Framework.
  * Cấu hình chi tiết các thành phần mạng cốt lõi bao gồm Subnet (Public/Private), Route Table, Internet Gateway, NAT Gateway, Security Group.
  * Sử dụng EC2 Instance Connect Endpoint để kết nối an toàn tới các máy chủ ảo trong mạng private.
  * Tìm hiểu lý thuyết về kết nối Site-to-Site VPN và giám sát mạng bằng VPC Flow Logs.
