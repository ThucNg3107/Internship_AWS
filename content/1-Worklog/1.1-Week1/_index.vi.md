---
title: "Worklog Tuần 1"
date: 2026-04-20
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---
### Mục tiêu tuần 1:

* Kết nối, làm quen với các thành viên trong First Cloud Journey.
* Hiểu dịch vụ AWS cơ bản, cách dùng console & CLI.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Làm quen với các thành viên FCJ <br> - Đọc và lưu ý các nội quy, quy định tại đơn vị thực tập                                                                                             | 20/04/2026   | 20/04/2026      |
| 3   | - Tìm hiểu AWS và các loại dịch vụ <br>&emsp; + Compute <br>&emsp; + Storage <br>&emsp; + Networking <br>&emsp; + Database <br>&emsp; + ... <br>                                            | 21/04/2026   | 21/04/2026      | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Tạo AWS Free Tier account <br> - Tìm hiểu AWS Console & AWS CLI <br> - **Thực hành:** <br>&emsp; + Tạo AWS account <br>&emsp; + Cài AWS CLI & cấu hình <br> &emsp; + Cách sử dụng AWS CLI | 22/04/2026   | 22/04/2026      | <https://000001.awsstudygroup.com/> |
| 5   | - Quản lý chi phí AWS Budgets <br> - Tìm hiểu về các loại AWS Budgets <br> - Lợi ích và các bước thiết lập để sử dụng hiểu quả <br> - **Thực hành:** <br>&emsp; +Tạo các loại AWS Budgets <br>&emsp; + Xử lí các Budgets khi không cần thiết| 23/04/2026   | 23/04/2026      | <https://000007.awsstudygroup.com/> |
| 6   | - Tìm hiểu AWS Support <br> &emsp; + Các gói hỗ trợ từ thấp tới cao với từng mục đích sử dụng khác nhau <br>&emsp; + Các loại yêu cầu được phép hỗ trợ: Tài khoản, dịch vụ, kỹ thuật.... <br>&emsp; + Cách thay đổi giữa các gói hỗ trợ <br>&emsp; + Khởi tạo yêu cầu hỗ trợ, mức độ nghiêm trọng và thời gian phản hồi của AWS Support <br> - **Thực hành:** <br>&emsp; + Thay đổi gói hỗ trợ <br>&emsp; + Cách tạo yêu cầu hỗ trợ <br>| 24/04/2026   | 24/04/2026      | <https://000009.awsstudygroup.com/> |
| 7   | - Kiểm soát chi tiết quyền truy cập tài nguyên <br> - Quản lý người dùng <br> - Triển khai bảo mật  <br> &emsp; + Tạo và quản lý IAM Groups để tổ chức người dùng <br>&emsp; + Sử dụng IAM Policies để phân quyền <br>&emsp; + Quản lý IAM Users theo nhóm để dể dàng kiểm soát <br>&emsp; + Cách chuyển đồi IAM Role  <br> - **Thực hành:** <br>&emsp; + Tạo IAM Group  <br>&emsp; + Tạo IAM User  <br>&emsp; + Tạo IAM Role<br>&emsp; + Chuyển đổi IAM Role<br>| 25/04/2026  | 25/04/2026      | <https://000002.awsstudygroup.com/> |
| 8  | - Thiết kế và triển khai VPC theo tiêu chuẩn AWS Well-Architected Framework  <br> &emsp; + Cấu hình các thành phần bảo mật mạng  <br>&emsp; + Thiết lập kết nối an toàn giữa môi trường on-premise và AWS  <br> - **Thực hành:** <br>&emsp; + Triển khai Amazon EC2  <br>&emsp;+ Tạo máy chủ EC2  <br>&emsp;+ Tạo Nat Gateway  <br>&emsp; + Sử dụng EC2 instance endpoint để kết nối server<br>&emsp; + Cấu hình Site to Site VPN  <br>&emsp; + Tường lửa VPC <br> | 26/04/2026  | 26/04/2026      | <https://000003.awsstudygroup.com/> |
### Kết quả đạt được tuần 1:

* Hiểu AWS là gì và nắm được các nhóm dịch vụ cơ bản: 
  * Compute
  * Storage
  * Networking 
  * Database
  * ...

* Đã tạo và cấu hình AWS Free Tier account thành công.

* Làm quen với AWS Management Console và biết cách tìm, truy cập, sử dụng dịch vụ từ giao diện web.

* Hội nhập & giao lưu AWS bao gồm
  * Làm quen với các thành viên nhóm FCJ, nắm vững nội quy thực tập và hiểu được các khái niệm cốt lõi về dịch vụ đám mây của AWS (Điện toán, Lưu trữ, Mạng, Cơ sở dữ liệu).
* Quản lý Danh tính & Truy cập (IAM):
  * Thành thạo việc khởi tạo và quản lý IAM User, Group, Role và Policy.
  * Hiểu sâu về các cơ chế bảo mật nâng cao như chuyển đổi quyền (Assume Role), phân biệt các loại Policy, và cách áp dụng IAM Instance Profile cho máy chủ ảo EC2.
* Có khả năng kết nối giữa giao diện web và CLI để quản lý tài nguyên AWS song song.
* Mạng đám mây (VPC):
  * Tự thiết kế và triển khai thành công một mạng riêng ảo (VPC) hoàn chỉnh..
  * Cấu hình chi tiết các thành phần mạng cốt lõi bao gồm Subnet, Route Table, Internet Gateway, NAT Gateway, Security Group, VPC Flow Logs, Elastic IP và tìm hiểu về kết nối Site-to-Site VPN.



