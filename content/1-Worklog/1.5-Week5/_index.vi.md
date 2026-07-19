---
title: "Worklog Tuần 5"
date: 2026-05-15
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---
### Mục tiêu tuần 5:

* Khai thác giải pháp AWS Systems Manager Session Manager phục vụ công tác quản trị máy chủ từ xa an toàn, bảo mật.
* Tối ưu tốc độ xử lý và hiệu năng ứng dụng thông qua bộ nhớ đệm phân tán Amazon ElastiCache (Redis).
* Chuẩn hóa hoạt động quản trị tài nguyên và theo dõi hạn mức dịch vụ đám mây qua bảng điều khiển AWS Service Quotas.
* Khởi tạo cụm OpenShift trên đám mây (ROSA), triển khai ứng dụng container hóa và tự động hóa chu kỳ CI/CD.

### Các công việc cần triển khai trong tuần này:
#### Tuần 5 (Từ 15/05/2026 – 21/05/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu cơ chế quản trị máy chủ an toàn với AWS Systems Manager Session Manager, loại bỏ nhu cầu mở cổng SSH, dùng Bastion Host hoặc quản lý khóa SSH Key thủ công. <br> - Đánh giá vai trò của Session Manager trong việc tuân thủ quy chuẩn an toàn thông tin, tập trung hóa phân quyền qua IAM và lưu vết toàn bộ lịch sử lệnh/phiên kết nối. <br> - Nắm bắt các lợi thế nổi bật: kết nối bảo mật không cần public IP ra internet, truy cập máy chủ tức thì chỉ với một thao tác. <br> - Khai thác khả năng tương thích đa nền tảng (Linux, Windows, macOS) của Session Manager để phân quyền người dùng linh hoạt. | 15/05/2026 | 15/05/2026 | |
| 3 | - Tìm hiểu kiến trúc bộ nhớ đệm Amazon ElastiCache, quy trình khởi tạo, quản lý và mở rộng hệ thống cache in-memory phân tán. <br> - Khám phá các tính năng cao cấp của ElastiCache cho Redis như tự động khắc phục sự cố node (auto-failover), phân vùng dữ liệu (sharding), phân bổ đa vùng sẵn sàng (Multi-AZ) và tích hợp liền mạch với EC2, CloudWatch, SNS, CloudTrail. <br> - Nắm vững các thành phần cốt lõi của ElastiCache: <br>&emsp; - Clusters: Tập hợp các nút cache chạy Redis, cung cấp năng lực tính toán và bộ nhớ đệm tối ưu (Standard hoặc Memory-Optimized) vận hành trong VPC. | 16/05/2026 | 16/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Khai thác giao diện trung tâm AWS Service Quotas để theo dõi và quản lý hạn mức tài nguyên trên các dịch vụ Đám mây. <br> - Thấu hiểu bản chất của Service Quotas là giới hạn tối đa số lượng tài nguyên hoặc hành động được phép trong một tài khoản AWS. <br> - Nắm rõ cơ chế thiết lập giá trị mặc định cho từng dịch vụ từ phía AWS. <br> - Thực hành tra cứu hạn mức thực tế và gửi yêu cầu nâng giới hạn tài nguyên (Quota increase request) qua console. | 17/05/2026 | 17/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Cài đặt bộ công cụ điều khiển ROSA gồm AWS CLI, ROSA CLI, OpenShift CLI (oc) và phân quyền IAM Roles tương ứng. <br> - Khởi tạo và cấu hình cụm máy chủ Red Hat OpenShift trên hạ tầng AWS (ROSA). <br> - Đóng gói và phát hành ứng dụng Container hóa lên cụm ROSA Cluster. <br> - Thiết lập đường ống CI/CD tự động hóa trên ROSA với chuỗi dịch vụ AWS CodePipeline, CodeCommit và CodeBuild. | 18/05/2026 | 18/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Thực hành công tác theo dõi, giám sát ứng dụng và tình trạng sức khỏe của ROSA cluster bằng OpenShift Web Console. <br> - Thực thi kịch bản hủy bỏ và dọn dẹp triệt để các tài nguyên đã tạo (ROSA cluster, IAM roles, VPC resources) để tối ưu chi phí. | 19/05/2026 | 19/05/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 5:

* **Quản lý & Bảo mật Máy chủ (Systems Manager Session Manager):**
  * Làm chủ phương thức kết nối máy chủ an toàn với Session Manager, loại bỏ hoàn toàn việc mở cổng SSH inbound hay duy trì máy chủ Bastion.
  * Phân quyền truy cập tập trung qua IAM và lưu trữ nhật ký truy vết (Audit logs) cho toàn bộ phiên làm việc.

* **Môi trường Cache & Tối ưu hiệu năng (Amazon ElastiCache):**
  * Thấu hiểu kiến trúc hạ tầng ElastiCache cho Redis (Clusters, Nodes, Shards, Multi-AZ).
  * Nắm vững phương pháp thiết lập đệm dữ liệu (caching), cơ chế tự động chuyển vùng sự cố (auto-failover) nhằm giảm độ trễ phản hồi cho ứng dụng.

* **Quản lý Tài nguyên & Giới hạn (AWS Service Quotas):**
  * Quản trị và đề xuất nâng hạn mức tài nguyên (Service Quotas) chủ động từ bảng điều khiển tập trung.

* **Triển khai Container & CI/CD trên AWS ROSA (Red Hat OpenShift on AWS):**
  * Cài đặt và chuẩn hóa môi trường làm việc với AWS CLI, ROSA CLI, OpenShift CLI (oc).
  * Khởi tạo và vận hành thành công cụm máy chủ OpenShift (ROSA) trên hạ tầng AWS.
  * Triển khai ứng dụng container hóa lên ROSA Cluster đạt độ ổn định cao.
  * Xây dựng luồng CI/CD tự động hóa hoàn chỉnh với CodeCommit (lưu trữ mã nguồn), CodeBuild (biên dịch image) và CodePipeline (điều phối release).
  * Thực thi quy trình dọn dẹp tài nguyên và IAM roles đúng chuẩn nhằm phòng tránh chi phí ngoài phát sinh.
