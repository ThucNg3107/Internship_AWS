---
title: "Worklog Tuần 7"
date: 2026-05-29
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---
### Mục tiêu tuần 7:

* Tìm hiểu và thực hành xây dựng ứng dụng không máy chủ (serverless) bằng AWS SAM.
* Hiểu cách xác thực và ủy quyền người dùng bằng Amazon Cognito.
* Cấu hình lưu trữ web an toàn bằng chứng chỉ SSL, Route 53 và CloudFront.
* Tích hợp các dịch vụ nhắn tin (Amazon SQS và Amazon SNS) để tách rời các thành phần ứng dụng.
* Tìm hiểu cách giám sát và theo vết ứng dụng bằng Amazon CloudWatch và AWS X-Ray.

### Các công việc cần triển khai trong tuần này:
#### Tuần 7 (Từ 29/05/2026 – 04/06/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Ôn tập cách xây dựng ứng dụng web đơn giản theo mô hình serverless bằng bảng điều khiển AWS. <br> - Tìm hiểu AWS Serverless Application Model (SAM) - một open-source framework hỗ trợ xây dựng ứng dụng serverless nhanh hơn. <br> - Học cú pháp YAML của SAM để định nghĩa các hàm, API, cơ sở dữ liệu và event source mappings. <br> - Tìm hiểu cách SAM chuyển đổi và mở rộng cú pháp thành AWS CloudFormation để tự động cung cấp tài nguyên. | 29/05/2026 | 29/05/2026 | |
| 3 | - Tìm hiểu về Amazon Cognito - dịch vụ cung cấp giải pháp xác thực, ủy quyền và quản lý người dùng cho ứng dụng web và di động. <br> - Nghiên cứu hai thành phần chính của Amazon Cognito: <br>&emsp; + Thư mục người dùng cung cấp tính năng đăng ký và đăng nhập (trực tiếp hoặc qua bên thứ ba như Facebook, Google, Apple,...) và kiểm soát quyền truy cập ứng dụng. <br>&emsp; + Cung cấp thông tin xác thực AWS tạm thời để cấp quyền cho người dùng truy cập trực tiếp vào các tài nguyên AWS khác. <br> - Tìm hiểu ví dụ về cách kết hợp User pools và Identity pools cùng nhau trong kiến trúc ứng dụng. | 30/05/2026 | 30/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Tìm hiểu cách bảo mật ứng dụng web trong quá trình truyền tải dữ liệu bằng chứng chỉ SSL để mã hóa lưu lượng giữa người dùng và trang web tĩnh được lưu trữ trên Amazon S3 (in-flight encryption). <br> - Nghiên cứu các dịch vụ cốt lõi trong kiến trúc lưu trữ web an toàn không máy chủ (serverless): <br>&emsp; + Quản lý việc tạo, lưu trữ và gia hạn chứng chỉ cũng như khóa SSL/TLS X.509 công khai và riêng tư để bảo vệ các trang web và ứng dụng AWS. <br>&emsp; + Dịch vụ Hệ thống Phân giải Tên miền (DNS) đám mây có độ sẵn sàng và khả năng mở rộng cao, giúp định tuyến người dùng đến các tài nguyên và quản lý Hosted zone. <br>&emsp; + Dịch vụ phân phối nội dung (CDN) giúp tăng tốc độ truyền tải nội dung web tĩnh và động qua mạng lưới điểm biên, hỗ trợ cấu hình HTTPS với chứng chỉ SSL. <br> - Tìm hiểu lợi ích của việc kết hợp Amazon S3 với Amazon CloudFront, bao gồm việc sử dụng Origin Access Control (OAC) để giới hạn quyền truy cập trực tiếp vào nội dung S3. | 31/05/2026 | 31/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Học cách xử lý đơn đặt hàng của người dùng bằng cách tích hợp Amazon SQS và Amazon SNS vào ứng dụng web serverless. <br> - Tìm hiểu kiến trúc xử lý đơn hàng bao gồm: <br>&emsp; + API POST `/books/order` gửi thông tin đơn hàng vào hàng đợi SQS và phát tin nhắn qua SNS topic. <br>&emsp; + API GET `/books/order` giúp admin lấy các đơn hàng chưa xử lý trong hàng đợi và các đơn hàng đã xử lý trong DynamoDB. <br>&emsp; + API POST `/books/order/handle` lưu thông tin vào DynamoDB và xóa đơn hàng khỏi hàng đợi. <br>&emsp; + API DELETE `/books/order` xóa đơn hàng khỏi hàng đợi. <br> - Tìm hiểu các dịch vụ nhắn tin (messaging) của AWS: <br>&emsp; + Dịch vụ hàng đợi tin nhắn an toàn, bền vững để tích hợp và tách rời các thành phần phần mềm phân tán, hỗ trợ hàng đợi Standard và FIFO. <br>&emsp; + Dịch vụ gửi tin nhắn từ nhà xuất bản (publishers) đến người đăng ký (subscribers) theo cơ chế pub/sub không đồng bộ qua các topic giao tiếp. | 01/06/2026 | 01/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Tìm hiểu tầm quan trọng của việc giám sát và quan sát ứng dụng để đảm bảo hoạt động ổn định và khả năng xử lý khi xảy ra sự cố. <br> - Tìm hiểu các công cụ hỗ trợ của AWS như AWS CloudWatch, AWS X-Ray và AWS CloudTrail. <br> - Nghiên cứu Amazon CloudWatch để giám sát tài nguyên và ứng dụng theo thời gian thực: <br>&emsp; + Thu thập và theo dõi các chỉ số đo lường hiệu năng tài nguyên và ứng dụng. <br>&emsp; + Thu thập và lưu trữ các tệp log (ví dụ: gỡ lỗi AWS Lambda). <br>&emsp; + Gửi thông báo phản hồi khi có sự kiện xảy ra. <br>&emsp; +Thiết lập các ngưỡng kích hoạt (cảnh báo) để thực hiện một hành động cụ thể. <br> - Nghiên cứu AWS X-Ray để phân tích và gỡ lỗi các ứng dụng phân tán/microservices: <br>&emsp; + Xác định và khắc phục nguyên nhân gốc rễ của các vấn đề hiệu năng và sự cố. <br>&emsp; + Cung cấp góc nhìn toàn diện từ đầu đến cuối (end-to-end) của các yêu cầu đi qua ứng dụng. <br>&emsp; + Trực quan hóa bản đồ các thành phần cơ bản của ứng dụng. | 02/06/2026 | 02/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 7:

* **AWS Serverless Application Model (SAM):**
  * Làm chủ cú pháp YAML của SAM để định nghĩa các hàm, API, cơ sở dữ liệu và ánh xạ nguồn sự kiện (event source mapping).
  * Khởi tạo và triển khai thành công ứng dụng không máy chủ, hiểu cách SAM biên dịch thành các tài nguyên CloudFormation.

* **Amazon Cognito User & Identity Pools:**
  * Hiểu vai trò của Amazon Cognito trong quản lý thư mục người dùng (User Pools) và cung cấp thông tin xác thực tạm thời (Identity Pools).
  * Triển khai luồng đăng ký/đăng nhập an toàn cho ứng dụng.

* **Lưu trữ ứng dụng Web bảo mật:**
  * Tạo và cấu hình chứng chỉ SSL/TLS thông qua AWS Certificate Manager (ACM) để mã hóa dữ liệu truyền tải.
  * Định tuyến lưu lượng tên miền qua Route 53 và tối ưu hóa phân phối nội dung toàn cầu qua CloudFront.
  * Bảo mật truy cập trực tiếp đến S3 bucket bằng cách cấu hình Origin Access Control (OAC).

* **Giao tiếp bất đồng bộ (SQS & SNS):**
  * Xây dựng hệ thống xử lý tin nhắn bất đồng bộ bằng hàng đợi SQS và SNS topic.
  * Tích hợp thành công luồng xử lý đơn hàng: API gửi thông tin vào SQS/SNS và lưu trữ kết quả xử lý vào DynamoDB.

* **Giám sát và Theo vết ứng dụng:**
  * Hiểu vai trò của AWS CloudWatch (Metrics, Logs, Events, Alarms) để gỡ lỗi và quan sát ứng dụng serverless.
  * Sử dụng AWS X-Ray để thiết lập theo vết từ đầu đến cuối (end-to-end) và phân tích vòng đời yêu cầu giữa các thành phần.


