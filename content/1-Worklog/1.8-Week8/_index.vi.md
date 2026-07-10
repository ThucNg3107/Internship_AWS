---
title: "Worklog Tuần 8"
date: 2026-06-05
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---
### Mục tiêu tuần 8:

* Hiểu các khái niệm về GraphQL và cách AWS AppSync đơn giản hóa việc tạo API.
* Học cách xây dựng hệ thống nhắn tin thời gian thực và các API bằng AWS AppSync.
* Thực hành tích hợp AWS AppSync với Amazon DynamoDB và các nguồn dữ liệu khác.
* Làm chủ các thao tác CRUD và truy vấn dữ liệu sử dụng GraphQL schemas, resolvers, và queries/mutations.
* Hiểu về bảo mật và riêng tư dữ liệu sử dụng Amazon Macie để phát hiện, giám sát và bảo vệ dữ liệu nhạy cảm trong môi trường AWS.
* Học cách triển khai WordPress trên Amazon EC2 và tự động hóa quy trình triển khai bằng AWS CodeDeploy.
* Hiểu về cơ sở hạ tầng máy tính ảo (VDI) và cách triển khai bằng Amazon WorkSpaces.

### Các công việc cần triển khai trong tuần này:
#### Tuần 8 (Từ 05/06/2026 – 11/06/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Học cách xây dựng hệ thống nhắn tin (messaging) cho ứng dụng web sử dụng AWS AppSync tương tác với GraphQL. <br> - Tìm hiểu các hoạt động của AWS AppSync: <br>&emsp; + Dịch vụ được quản lý toàn phần (managed service) giúp đơn giản hóa việc xây dựng các API GraphQL linh hoạt để truy cập, thao tác và kết hợp dữ liệu từ nhiều nguồn một cách an toàn. <br>&emsp; + Hỗ trợ xây dựng các API GraphQL có khả năng mở rộng, tích hợp với DynamoDB, Lambda, Elasticsearch, cũng như các nguồn dữ liệu HTTP/SQL/REST. <br>&emsp; + Các tính năng nổi bật: đồng bộ hóa dữ liệu ngoại tuyến (offline), cập nhật thời gian thực (real-time updates) và kiểm soát quyền truy cập chi tiết. <br> - Thực hành các thao tác CRUD (tạo, cập nhật, đọc, xóa dữ liệu) trên bảng DynamoDB thông qua API GraphQL của AWS AppSync. | 05/06/2026 | 05/06/2026 | |
| 3 | - Nghiên cứu AWS Toolkit cho Visual Studio Code <br> - Nghiên cứu Amazon Q <br>&emsp; + Viết unit test, sinh mã nguồn, gỡ lỗi, khắc phục sự cố và tối ưu hóa mã nguồn. <br>&emsp; + Gợi ý mã nguồn thời gian thực trên 15+ ngôn ngữ (bao gồm cả CloudFormation, CDK, Terraform). <br>&emsp; + Tối ưu hóa các gợi ý mã nguồn cho các dịch vụ AWS APIs (EC2, Lambda, S3). <br>&emsp; + Quét bảo mật tích hợp để phát hiện các lỗ hổng khó tìm và đề xuất cách khắc phục ngay lập tức. | 06/06/2026 | 06/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Tìm hiểu về Amazon Macie - dịch vụ bảo mật và riêng tư dữ liệu được quản lý toàn phần, sử dụng học máy (machine learning) và so khớp mẫu (pattern matching) để giúp phát hiện, giám sát và bảo vệ dữ liệu nhạy cảm trong môi trường AWS. <br> - Nghiên cứu các tính năng chính của Amazon Macie: <br>&emsp; + Tự động duy trì danh mục các S3 bucket, đánh giá cấu hình bảo mật và tạo policy finding nếu phát hiện rủi ro. <br>&emsp; + Các finding cung cấp báo cáo chi tiết về mức độ nghiêm trọng, tài nguyên bị ảnh hưởng và thông tin liên quan. Quản lý finding trực tiếp trên console hoặc qua API để phân tích chuyên sâu. <br>&emsp; + Tự động gửi các event đến Amazon EventBridge để định tuyến thời gian thực tới Lambda/SNS, hoặc tích hợp với AWS Security Hub để quản lý tập trung trạng thái bảo mật. <br>&emsp; + Tích hợp với AWS Organizations hoặc gửi lời mời thành viên để quản trị viên có thể xem thông tin bucket, policy finding và chạy các job phát hiện dữ liệu nhạy cảm trên nhiều tài khoản. <br>&emsp; + Tương tác với Amazon Macie một cách lập trình thông qua Amazon Macie API, AWS CLI hoặc AWS SDKs | 07/06/2026 | 07/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Học cách triển khai WordPress (mã nguồn mở viết bằng PHP và MySQL dùng làm blog/CMS) trên một EC2 instance chạy Amazon Linux hoặc RHEL. <br> - Tìm hiểu AWS CodeDeploy - dịch vụ triển khai tự động toàn phần: <br>&emsp; + Tự động hóa việc triển khai phần mềm trên các dịch vụ như Amazon EC2, AWS Fargate, AWS Lambda và máy chủ vật lý (on-premises). <br>&emsp; + Giúp phát hành tính năng mới nhanh hơn, tránh downtime khi triển khai và đơn giản hóa việc cập nhật ứng dụng. <br>&emsp; + Loại bỏ các thao tác thủ công dễ xảy ra lỗi bằng các quy trình tự động và tự động mở rộng theo nhu cầu triển khai. | 08/06/2026 | 08/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Tìm hiểu về Amazon WorkSpaces - dịch vụ cơ sở hạ tầng máy tính ảo (VDI) được quản lý toàn phần, cho phép triển khai và quản lý các hệ điều hành máy khách (Windows 10/11, macOS, Ubuntu) hoàn toàn trên đám mây AWS. <br> - Tìm hiểu các phương thức kết nối an toàn để người dùng cuối truy cập WorkSpaces: <br>&emsp; + Cài đặt ứng dụng Amazon WorkSpaces client. <br>&emsp; + Kết nối trực tiếp thông qua trình duyệt web. | 09/06/2026 | 09/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 8:

* **Tích hợp AWS AppSync & GraphQL:**
  * Làm chủ việc tạo các API GraphQL có khả năng mở rộng và phản hồi nhanh chóng bằng AWS AppSync.
  * Thiết kế các schema GraphQL linh hoạt với các Query, Mutation và Subscription phù hợp.
  * Kết nối trực tiếp các resolver của AppSync với bảng DynamoDB để thực hiện các thao tác CRUD an toàn.

* **Đồng bộ hóa thời gian thực & Ngoại tuyến (Offline):**
  * Hiểu cơ chế cập nhật thời gian thực bằng GraphQL Subscriptions.
  * Khám phá các tính năng đồng bộ hóa dữ liệu ngoại tuyến và kiểm soát quyền truy cập chi tiết trong AWS AppSync.

* **Amazon Macie & Bảo mật dữ liệu:**
  * Hiểu cách Amazon Macie tự động hóa việc phát hiện dữ liệu nhạy cảm (PII, dữ liệu tài chính) trong S3.
  * Học cách cấu hình job phát hiện dữ liệu nhạy cảm, custom data identifier và allow list.
  * Tìm hiểu cách giám sát bảo mật S3 bucket, xem policy finding và tích hợp với EventBridge/Security Hub.

* **Triển khai WordPress & AWS CodeDeploy:**
  * Triển khai WordPress thành công trên một Amazon EC2 instance chạy Amazon Linux/RHEL.
  * Cấu hình và sử dụng AWS CodeDeploy để tự động hóa việc triển khai phần mềm, giảm thiểu lỗi thủ công và quản lý các đợt cập nhật ứng dụng hiệu quả.

* **Amazon WorkSpaces & Cơ sở hạ tầng máy tính ảo (VDI):**
  * Khám phá cách triển khai và quản lý máy tính ảo (Windows, macOS, Ubuntu) an toàn trên đám mây.
  * Hiểu các tùy chọn kết nối an toàn cho người dùng cuối qua client và trình duyệt web.


