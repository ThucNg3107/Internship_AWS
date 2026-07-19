---
title: "Worklog Tuần 3"
date: 2026-05-01
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---
### Mục tiêu tuần 3:

* Thiết lập quy trình tự động hóa và đường ống CI/CD bằng AWS Lambda, EventBridge, CodePipeline và CodeDeploy.
* Vận hành lưu trữ lai (hybrid) với AWS Storage Gateway, tăng cường phòng thủ lớp ứng dụng qua AWS WAF và quản lý tài nguyên khoa học bằng Tags cùng Resource Groups.
* Xây dựng hệ thống theo dõi chuyên sâu kết hợp Grafana và CloudWatch, áp dụng cơ chế phân quyền kiểm soát với IAM Permission Boundary và tự động hóa cập nhật bản vá bằng Systems Manager.
* Thực thi bảo mật dữ liệu toàn diện với AWS KMS và CloudTrail, khởi tạo hạ tầng Data Lake và ứng dụng bộ đôi AWS Glue - Athena để truy vấn dữ liệu hiệu năng cao.

### Các công việc cần triển khai trong tuần này:
#### Tuần 3 (Từ 01/05/2026 – 07/05/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Nghiên cứu và tối ưu chi phí vận hành với hàm Serverless Lambda, tích hợp luồng sự kiện EventBridge trong CloudWatch <br> - Xây dựng quy trình tự động hóa triển khai ứng dụng lên EC2 thông qua AWS CodePipeline, cấu hình Git Connection, Git Credential và CodeDeploy Agent | 01/05/2026 | 01/05/2026 | |
| 3 | - Cấu hình giải pháp AWS Storage Gateway, thiết lập các vùng chia sẻ tệp (File Share) và kết nối ổ đĩa mạng để đồng bộ dữ liệu lai <br> - Triển khai tường lửa ứng dụng web AWS WAF, thiết lập bộ quy tắc bảo mật ngăn chặn các nguy cơ an ninh mạng <br> - Chuẩn hóa việc gán thẻ (Tags) cho tài nguyên và khai thác AWS Resource Groups để tự động hóa công tác quản trị | 02/05/2026 | 02/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Cài đặt và tích hợp Grafana với CloudWatch phục vụ mục đích trực quan hóa các chỉ số giám sát hạ tầng AWS <br> - Thiết lập chính sách giới hạn quyền IAM Permission Boundary và chính sách quản trị tổ chức Organization Policy để tối ưu chi phí lẫn an toàn hệ thống <br> - Tự động hóa quy trình cập nhật bản vá trên quy mô nhiều máy chủ bằng công cụ Systems Manager Run Command | 03/05/2026 | 03/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Thực hành cơ chế mã hóa dữ liệu an toàn với AWS KMS, ghi vết nhật ký hệ thống qua CloudTrail và phân tích dữ liệu bằng Athena, thiết lập chia sẻ dữ liệu mã hóa trên S3 <br> - Phân tích, theo dõi chỉ số chi phí chi tiết và tối ưu hóa ngân sách theo từng dịch vụ AWS sử dụng | 04/05/2026 | 04/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Tiếp cận kiến trúc lưu trữ, biến đổi và phân tích dữ liệu tập trung với mô hình Data Lake <br> - Tìm hiểu và triển khai kịch bản khởi tạo hạ tầng cơ bản bằng mã nguồn với AWS CDK <br> - Kết hợp AWS Glue Crawler/Catalog với Athena để truy vấn dữ liệu, đánh giá chi phí và hiệu năng xử lý hệ thống | 05/05/2026 | 05/05/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 3:

* **Điện toán Máy chủ ảo (Serverless) & Tự động hóa Triển khai**
  * Làm chủ cấu hình các xử lý bất đồng bộ qua Lambda và kịch bản EventBridge.
  * Hoàn thiện đường ống tự động hóa đóng gói và triển khai ứng dụng lên EC2 với AWS CodePipeline & CodeDeploy.

* **Bảo mật, Lưu trữ & Quản lý Tài nguyên**
  * Triển khai giải pháp đồng bộ dữ liệu lai hai chiều sử dụng AWS Storage Gateway.
  * Thiết lập lớp bảo vệ an toàn cho ứng dụng web thông qua bộ quy tắc AWS WAF.
  * Phân loại và quản trị tài nguyên chuyên nghiệp nhờ chính sách gán thẻ (Tags) và AWS Resource Groups.
  * Kiểm soát ranh giới phân quyền nghiêm ngặt với IAM Permission Boundaries và Organization Policies.
  * Đảm bảo an toàn dữ liệu lưu trữ (Encryption at rest) bằng AWS KMS và kiểm vết truy cập qua CloudTrail.

* **Giám sát & Vận hành Hệ thống**
  * Xây dựng bảng điều khiển trực quan hóa hạ tầng linh hoạt bằng cách tích hợp Grafana với CloudWatch.
  * Tự động hóa công tác quản lý và cập nhật bản vá lỗi cho máy chủ với AWS Systems Manager (Run Command).
  * Kiểm soát chính xác cấu trúc chi phí và phân tích báo cáo sử dụng tài nguyên AWS.

* **Data Engineering & Infrastructure as Code (IaC)**
  * Thiết lập mô hình Data Lake cơ bản thông qua hạ tầng dưới dạng mã với AWS CDK.
  * Khai thác AWS Glue và Athena để tự động hóa trích xuất, biến đổi và truy vấn phân tích dữ liệu.
  * Đảm bảo an toàn khi chia sẻ dữ liệu đã mã hóa trên môi trường Amazon S3.
