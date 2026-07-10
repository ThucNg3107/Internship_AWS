---
title: "Worklog Tuần 5"
date: 2026-05-15
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---
### Mục tiêu tuần 5:

* Tìm hiểu và sử dụng AWS Systems Manager Session Manager để quản lý máy chủ an toàn.
* Nghiên cứu dịch vụ Amazon ElastiCache (Redis) để cải thiện hiệu năng lưu trữ cache/in-memory.
* Tìm hiểu và quản lý giới hạn dịch vụ thông qua AWS Service Quotas.
* Cài đặt công cụ, khởi tạo và triển khai ứng dụng, xây dựng quy trình CI/CD trên OpenShift cluster (ROSA).

### Các công việc cần triển khai trong tuần này:
#### Tuần 5 (Từ 15/05/2026 – 21/05/2026)
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Tìm hiểu chức năng Session Manager thuộc dịch vụ AWS Systems Manager để quản lý máy chủ an toàn mà không cần mở port SSH, không cần Bastion Host hay quản lý SSH key. <br> - Hiểu cách Session Manager giúp dễ dàng tuân thủ các chính sách bảo mật, kiểm soát quyền truy cập tập trung bằng AWS IAM và ghi log lại các phiên kết nối, câu lệnh đã thực thi. <br> - Nắm bắt các ưu điểm: cấu hình kết nối không cần đi ra ngoài internet, truy cập tới server nhanh chóng, đơn giản bằng một cú click chuột. <br> - Tận dụng khả năng hỗ trợ đa nền tảng (Linux, Windows, MacOS) của Session Manager để cấp quyền truy cập cho người dùng . | 15/05/2026 | 15/05/2026 | |
| 3   | - Tìm hiểu về dịch vụ Amazon ElastiCache để dễ dàng thiết lập, quản lý và mở rộng kho dữ liệu in-memory phân tán hoặc môi trường cache. <br> - Khám phá các tính năng của ElastiCache for Redis như tự động phát hiện và phục hồi lỗi node, phân vùng dữ liệu , linh hoạt vị trí Availability Zone và tích hợp với các dịch vụ AWS khác (EC2, CloudWatch, SNS, CloudTrail). <br> - Nắm vững kiến trúc và thành phần của ElastiCache: <br>&emsp; - Clusters: Thành phần cơ bản tập hợp các cache node chạy Redis, cung cấp khả năng tính toán, phân cấp dữ liệu, có thể chọn loại node standard hoặc memory-optimized và hoạt động trong VPC | 16/05/2026 | 16/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Tìm hiểu về AWS Service Quotas để xem và quản lý mức giới hạn cho các dịch vụ AWS từ một giao diện trung tâm. <br> - Hiểu mức giới hạn (giới hạn dịch vụ) là giá trị tối đa của tài nguyên, hành động trên tài nguyên cụ thể trong tài khoản AWS. <br> - Nắm bắt việc mỗi dịch vụ AWS tự xác định và thiết lập giá trị mặc định cho các mức giới hạn đó. <br> - Biết cách tra cứu mức giới hạn hiện tại và gửi yêu cầu tăng giới hạn thông qua Service Quotas | 17/05/2026 | 17/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Cài đặt các công cụ cần thiết cho ROSA bao gồm: AWS CLI, ROSA CLI, OpenShift CLI (oc) và cấu hình các quyền IAM cần thiết. <br> - Khởi tạo và thiết lập OpenShift cluster trên AWS . <br> - Triển khai ứng dụng container hóa lên ROSA cluster. <br> - Triển khai và tự động hóa quy trình CI/CD trên ROSA sử dụng AWS CodePipeline, AWS CodeCommit, và AWS CodeBuild. | 18/05/2026 | 18/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Thực hành kiểm tra, giám sát ứng dụng và OpenShift cluster bằng OpenShift Web Console. <br> - Thực hiện dọn dẹp toàn bộ tài nguyên đã tạo bao gồm ROSA cluster, IAM Roles và các tài nguyên AWS liên quan để tránh phát sinh chi phí. | 19/05/2026 | 19/05/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 5:

* **Quản lý & Bảo mật Máy chủ (Systems Manager Session Manager):**
  * Hiểu cách hoạt động của Session Manager thuộc dịch vụ AWS Systems Manager để quản lý và kết nối máy chủ an toàn mà không cần mở cổng SSH hay sử dụng Bastion Host.
  * Biết cách phân quyền truy cập thông qua IAM và theo dõi, ghi nhật ký (log) lịch sử phiên làm việc của người dùng.

* **Môi trường Cache & Tối ưu hiệu năng (Amazon ElastiCache):**
  * Nắm vững kiến trúc và cách thức hoạt động của Amazon ElastiCache for Redis (Clusters, Nodes, Shards).
  * Hiểu cách thiết lập, tự động phát hiện lỗi và mở rộng quy mô dữ liệu in-memory để cải thiện tốc độ phản hồi cho ứng dụng.

* **Quản lý Tài nguyên & Giới hạn (AWS Service Quotas):**
  * Biết cách kiểm tra, quản lý và gửi yêu cầu nâng cao hạn mức sử dụng (Service Quotas) tài nguyên dịch vụ AWS từ một bảng điều khiển trung tâm.

* **Triển khai Container & CI/CD trên AWS ROSA (Red Hat OpenShift on AWS):**
  * Cài đặt thành công các công cụ dòng lệnh cần thiết: AWS CLI, ROSA CLI, OpenShift CLI (oc).
  * Thực hiện khởi tạo và cấu hình OpenShift Cluster trên môi trường AWS (ROSA).
  * Triển khai thành công ứng dụng container hóa lên OpenShift Cluster.
  * Thiết lập và vận hành trơn tru quy trình CI/CD tự động sử dụng AWS CodeCommit (kho lưu trữ mã nguồn), AWS CodeBuild (build container image và deploy), và AWS CodePipeline (điều phối toàn bộ quy trình release).
  * Thực hành dọn dẹp các tài nguyên cluster và IAM roles để tránh phát sinh chi phí phát sinh ngoài ý muốn.


