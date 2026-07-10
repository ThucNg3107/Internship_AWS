---
title: "Worklog Tuần 6"
date: 2026-05-22
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---
### Mục tiêu tuần 6:

* Xây dựng kiến trúc Data Lake Serverless và đường ống xử lý dữ liệu với S3, Kinesis, Athena và QuickSight.
* Sử dụng các dịch vụ ETL (AWS Glue, EMR) để biến đổi dữ liệu và lưu trữ vào kho dữ liệu Amazon Redshift.
* Thiết lập mô hình tin nhắn Pub/Sub sử dụng Amazon SNS và SQS.
* Phát triển các ứng dụng Serverless bằng AWS Lambda (xử lý ảnh qua S3 trigger, Lambda Layers) và tích hợp với Amazon DynamoDB (CRUD, IAM, Monitoring & Troubleshooting).

### Các công việc cần triển khai trong tuần này:
#### Tuần 6 (Từ 22/05/2026 – 28/05/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Thiết kế kiến trúc data lake serverless. <br> - Xây dựng đường ống xử lý dữ liệu và Data Lake bằng cách sử dụng Amazon S3 để lưu trữ dữ liệu. <br> - Sử dụng Amazon Kinesis cho dữ liệu truyền phát thời gian thực. <br> - Sử dụng Amazon Kinesis Data Analytics cho phân tích dữ liệu thời gian thực. <br> - Truy vấn dữ liệu bằng Amazon Athena và trực quan hóa dữ liệu bằng Amazon QuickSight. | 22/05/2026 | 22/05/2026 | |
| 3 | - Sử dụng AWS Glue để tự động lập chỉ mục các bộ dữ liệu. <br> - Biến đổi dữ liệu. <br> - Chạy các script ETL tương tác trong một cuốn sổ Jupyter trên AWS Glue Studio sử dụng AWS Glue (interactive sessions). <br> - Sử dụng Glue Studio để chạy và giám sát các ETL jobs trong AWS Glue. <br> - Sử dụng Glue DataBrew để chuẩn bị dữ liệu. <br> - Sử dụng EMR để chạy một job biến đổi Spark. <br> - Tải dữ liệu lên Amazon Redshift từ Glue. <br> - Giới thiệu về các quy thực hành thiết kế tốt cho Amazon Redshift. | 23/05/2026 | 23/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Tìm hiểu cơ chế hoạt động của Amazon SNS (Simple Notification Service) và Amazon SQS (Simple Queue Service). <br> - Triển khai mô hình Pub/Sub và cấu hình chính sách bộ lọc (Subscription Filter Policy) để lọc và định tuyến tin nhắn tự động. <br>&emsp; + Tạo hàng đợi SQS mới cho Đơn đặt hàng ở EU (EU orders). <br>&emsp; + Đăng ký subscribe hàng đợi SQS vào SNS Topic Đơn hàng. <br>&emsp; + Thiết lập chính sách lọc tin nhắn cho subscribe bằng cách chỉ định thuộc tính location với giá trị eu-west để chỉ nhận các thông điệp từ EU. | 24/05/2026 | 24/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Tìm hiểu Kiến trúc Serverless: khái niệm, các thành phần chính (Lambda, S3, DynamoDB) và use cases phổ biến. <br>&emsp; + Tạo và cấu hình Lambda function (runtime, memory, timeout). <br>&emsp; + Thiết lập S3 Event Trigger để tự động kích hoạt Lambda khi có file ảnh được tải lên S3 bucket. <br>&emsp; + Sử dụng Lambda Layers để chứa thư viện bên ngoài (ví dụ: Sharp/Jimp cho Node.js, Pillow cho Python) để thực hiện resize ảnh. <br>&emsp; + Tìm hiểu các Best Practices về bảo mật (IAM Roles tối giản) và tối ưu hiệu năng/chi phí. | 25/05/2026 | 25/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | <br>&emsp; + Tạo bảng DynamoDB với partition key và sort key. <br>&emsp; + Cấu hình IAM roles và permissions cho phép Lambda tương tác với bảng DynamoDB. <br>&emsp; + Thao tác CRUD cơ bản với DynamoDB SDK thông qua Lambda function. <br>&emsp; + Đọc và phân tích log trong CloudWatch Logs. <br>&emsp; + Giám sát các chỉ số (Invocations, Duration, Errors, Throttles) trong CloudWatch Metrics. <br>&emsp; + Cấu hình AWS X-Ray để theo dõi chi tiết (trace) luồng xử lý của hệ thống. | 26/05/2026 | 26/05/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 6:

* **Kiến trúc Data Lake Serverless & Truy vấn dữ liệu:**
  * Thiết kế và xây dựng thành công đường ống xử lý dữ liệu sử dụng Amazon S3 để lưu trữ thô và lưu trữ đã xử lý.
  * Tích hợp Amazon Kinesis và Kinesis Data Analytics để thu thập và phân tích luồng dữ liệu thời gian thực.
  * Sử dụng Amazon Athena để truy vấn dữ liệu trực tiếp trên S3 và trực quan hóa kết quả bằng Amazon QuickSight.

* **Tự động hóa ETL với AWS Glue & Redshift:**
  * Sử dụng AWS Glue Crawler để tự động quét và lập sơ đồ dữ liệu (schema) trong S3.
  * Thiết kế và chạy các công việc ETL (Extract, Transform, Load) bằng cả Glue Studio và script Spark tương tác trên EMR.
  * Làm sạch, chuẩn bị dữ liệu bằng Glue DataBrew và tải dữ liệu đã chuyển đổi vào Amazon Redshift để tối ưu hóa truy vấn phân tích.

* **Mô hình Messaging & Pub/Sub:**
  * Nắm vững cơ chế hoạt động và sự khác biệt giữa Amazon SNS và SQS.
  * Triển khai mô hình truyền tin Pub/Sub và cấu hình Subscription Filter Policies để định tuyến thông điệp chính xác dựa trên thuộc tính.

* **Kiến trúc Serverless với Lambda & DynamoDB:**
  * Làm chủ việc phát triển ứng dụng Serverless bằng AWS Lambda, thiết lập S3 Event Trigger để tự động xử lý hình ảnh tải lên.
  * Sử dụng Lambda Layers để đóng gói thư viện xử lý ảnh (ví dụ: Sharp, Pillow), giúp tối ưu dung lượng của hàm Lambda.
  * Thiết kế bảng DynamoDB với Partition Key và Sort Key tối ưu cho việc truy vấn.
  * Triển khai phân quyền bảo mật tối giản (IAM Roles & Policies) và viết mã nguồn thực hiện CRUD bằng AWS SDK.
  * Giám sát và gỡ lỗi hệ thống Serverless thông qua CloudWatch Logs, Metrics và AWS X-Ray.


