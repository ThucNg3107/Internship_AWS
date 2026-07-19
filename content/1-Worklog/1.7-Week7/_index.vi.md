---
title: "Worklog Tuần 7"
date: 2026-05-29
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---
### Mục tiêu tuần 7:

* Nghiên cứu và thực hành thiết kế ứng dụng không máy chủ (Serverless) chuẩn mực với framework AWS SAM.
* Nắm vững cơ chế xác thực, phân quyền và quản trị danh tính người dùng bằng Amazon Cognito.
* Cấu hình giải pháp lưu trữ web bảo mật cao tích hợp chứng chỉ SSL/TLS (ACM), quản trị tên miền Route 53 và mạng phân phối CloudFront.
* Tích hợp các dịch vụ nhắn tin Asynchronous (Amazon SQS, SNS) nhằm tách rời mối liên kết (decoupling) giữa các microservices.
* Thiết lập giải pháp quan sát hạ tầng (Observability) và truy vết luồng xử lý với Amazon CloudWatch và AWS X-Ray.

### Các công việc cần triển khai trong tuần này:
#### Tuần 7 (Từ 29/05/2026 – 04/06/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Đánh giá quy trình khởi tạo ứng dụng Serverless thủ công qua AWS Console. <br> - Tiếp cận AWS Serverless Application Model (SAM) - khung làm việc mã nguồn mở hỗ trợ tăng tốc độ đóng gói và phát hành ứng dụng Serverless. <br> - Thành thạo cú pháp khai báo YAML của SAM để định nghĩa Lambda Functions, API Gateway, DynamoDB và Event Source Mappings. <br> - Thấu hiểu cơ chế biên dịch tự động từ cú pháp rút gọn SAM sang mẫu tài nguyên AWS CloudFormation để cung cấp tài nguyên tự động. | 29/05/2026 | 29/05/2026 | |
| 3 | - Khai thác Amazon Cognito - giải pháp tập trung cung cấp tính năng xác thực, phân quyền và quản lý tài khoản cho ứng dụng Web/Mobile. <br> - Phân tích chuyên sâu 2 thành phần nòng cốt của Cognito: <br>&emsp; + User Pools: Quản lý thư mục tài khoản, xử lý luồng Đăng ký/Đăng nhập (trực tiếp hoặc qua các nhà cung cấp OAuth2 như Google, Facebook, Apple) và kiểm soát phân quyền truy cập. <br>&emsp; + Identity Pools: Cấp phát thông tin xác thực AWS tạm thời (Temporary Credentials) để người dùng truy cập trực tiếp vào các tài nguyên Cloud như S3 hay DynamoDB. <br> - Thiết kế kịch bản kết hợp linh hoạt giữa User Pools và Identity Pools trong kiến trúc tổng thể. | 30/05/2026 | 30/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Thiết lập cơ chế mã hóa lưu lượng đường truyền (In-flight Encryption) bằng chứng chỉ SSL/TLS nhằm bảo mật dữ liệu trao đổi giữa người dùng và trang web tĩnh trên Amazon S3. <br> - Làm chủ các dịch vụ then chốt trong mô hình Serverless Web Hosting an toàn: <br>&emsp; + AWS Certificate Manager (ACM): Tự động cấp phát, quản lý và gia hạn chứng chỉ SSL/TLS công khai/riêng tư. <br>&emsp; + Amazon Route 53: Hệ thống phân giải tên miền (DNS) độ sẵn sàng cao, quản trị Hosted Zones và định tuyến truy cập người dùng. <br>&emsp; + Amazon CloudFront: Mạng phân phối nội dung (CDN) tăng tốc độ tải trang qua các Edge Locations và bắt buộc giao thức bảo mật HTTPS. <br> - Triển khai Origin Access Control (OAC) để chặn truy cập trực tiếp vào S3 Bucket, bắt buộc lưu lượng phải đi qua CloudFront CDN. | 31/05/2026 | 31/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Xây dựng quy trình xử lý đơn hàng bất đồng bộ bằng việc tích hợp Amazon SQS và Amazon SNS vào kiến trúc Serverless. <br> - Thực thi luồng xử lý đơn hàng chi tiết: <br>&emsp; + Endpoint `POST /books/order`: Đẩy dữ liệu đơn hàng vào SQS Queue và phát thông báo qua SNS Topic. <br>&emsp; + Endpoint `GET /books/order`: Hỗ trợ Admin truy vấn các đơn hàng chờ xử lý trong SQS và các đơn hàng đã hoàn tất từ DynamoDB. <br>&emsp; + Endpoint `POST /books/order/handle`: Ghi nhận dữ liệu vào DynamoDB và thu hồi đơn hàng khỏi hàng đợi SQS. <br>&emsp; + Endpoint `DELETE /books/order`: Xóa đơn hàng khỏi hàng đợi SQS. <br> - Làm chủ hai mô thức truyền tin nâng cao: <br>&emsp; + Amazon SQS: Dịch vụ hàng đợi tin nhắn an toàn, bền vững giúp tách rời các microservices (hỗ trợ loại Standard và FIFO Queue). <br>&emsp; + Amazon SNS: Dịch vụ truyền tin Pub/Sub bất đồng bộ cho phép phát thông điệp từ Publisher tới hàng loạt Subscriber thông qua các Topic. | 01/06/2026 | 01/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Đánh giá vai trò của năng lực quan sát hệ thống (Observability) trong việc bảo đảm độ ổn định và tối ưu hóa thời gian xử lý sự cố. <br> - Làm chủ bộ công cụ giám sát toàn diện của AWS bao gồm CloudWatch, AWS X-Ray và CloudTrail. <br> - Khai thác Amazon CloudWatch để theo dõi thời gian thực: <br>&emsp; + Thu thập và theo dõi các chỉ số đo lường hiệu năng hạ tầng (Metrics). <br>&emsp; + Lưu trữ và phân tích các tệp nhật ký sự kiện (Logs). <br>&emsp; + Thiết lập kịch bản thông báo tự động khi phát sinh sự cố. <br>&emsp; + Cấu hình ngưỡng cảnh báo (Alarms) kích hoạt các hành động khắc phục tự động. <br> - Khai thác AWS X-Ray để theo vết và gỡ lỗi microservices phân tán: <br>&emsp; + Phân tích và truy tìm nguyên nhân gốc rễ (Root Cause) của các lỗi hiệu năng hoặc sự cố gián đoạn. <br>&emsp; + Trực quan hóa bản đồ tổng thể luồng yêu cầu từ đầu đến cuối (End-to-End Tracing). <br>&emsp; + Cung cấp Service Map hiển thị mối tương quan giữa các thành phần ứng dụng. | 02/06/2026 | 02/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 7:

* **AWS Serverless Application Model (SAM):**
  * Làm chủ ngôn ngữ khai báo SAM YAML để tự động hóa định nghĩa Lambda Functions, API Gateway, DynamoDB và Event Sources.
  * Đóng gói và phát hành thành công ứng dụng Serverless, nắm rõ cơ chế SAM chuyển đổi sang mẫu mã khai báo AWS CloudFormation.

* **Amazon Cognito User & Identity Pools:**
  * Phân biệt và ứng dụng chính xác Amazon Cognito User Pools (quản trị thư mục tài khoản) và Identity Pools (cấp phát AWS credentials tạm thời).
  * Xây dựng luồng Đăng ký/Đăng nhập chuẩn an toàn thông tin cho ứng dụng Web.

* **Lưu trữ ứng dụng Web bảo mật:**
  * Quản lý và cấp phát chứng chỉ mã hóa SSL/TLS qua AWS Certificate Manager (ACM) để bảo vệ dữ liệu truyền tải.
  * Thiết lập hệ thống phân giải tên miền Route 53 và tối ưu tốc độ phân phối nội dung toàn cầu qua mạng lưới CloudFront CDN.
  * Tăng cường an ninh mạng bằng việc cấu hình Origin Access Control (OAC) vô hiệu hóa truy cập S3 trực tiếp.

* **Giao tiếp bất đồng bộ (SQS & SNS):**
  * Thiết kế hệ thống truyền tin bất đồng bộ giúp tách rời mối phụ thuộc giữa các dịch vụ qua SQS Queue và SNS Topic.
  * Xây dựng thành công luồng xử lý đơn hàng tự động: tiếp nhận đơn qua SQS/SNS và lưu trữ trạng thái xử lý vào DynamoDB.

* **Giám sát và Theo vết ứng dụng:**
  * Làm chủ Amazon CloudWatch (Metrics, Logs, Events, Alarms) phục vụ quan sát và gỡ lỗi ứng dụng Serverless.
  * Ứng dụng AWS X-Ray thiết lập sơ đồ truy vết từ đầu đến cuối (End-to-End Tracing) nhằm phân tích chuyên sâu vòng đời xử lý yêu cầu.
