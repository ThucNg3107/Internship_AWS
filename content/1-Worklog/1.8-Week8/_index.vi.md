---
title: "Worklog Tuần 8"
date: 2026-06-05
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---
### Mục tiêu tuần 8:

* Thấu hiểu kiến trúc GraphQL và phương pháp xây dựng API linh hoạt thông qua dịch vụ managed AWS AppSync.
* Phát triển ứng dụng truyền tin thời gian thực (Real-time Messaging) và thiết lập API GraphQL chuẩn mực với AWS AppSync.
* Tích hợp AWS AppSync với Amazon DynamoDB cùng các nguồn dữ liệu đa dạng trong hệ sinh thái AWS.
* Làm chủ quy trình thao tác dữ liệu qua GraphQL Schemas, Resolvers, Queries, Mutations và Subscriptions.
* Tăng cường bảo mật dữ liệu nhạy cảm (PII) trên môi trường Cloud với Amazon Macie bằng công nghệ Machine Learning.
* Thực hành phát hành ứng dụng WordPress trên máy chủ Amazon EC2 và tự động hóa chu kỳ triển khai qua AWS CodeDeploy.
* Khai thác dịch vụ hạ tầng máy tính ảo đám mây (Cloud VDI) với Amazon WorkSpaces.

### Các công việc cần triển khai trong tuần này:
#### Tuần 8 (Từ 05/06/2026 – 11/06/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Nghiên cứu giải pháp xây dựng tính năng truyền tin ứng dụng web dựa trên AWS AppSync và chuẩn GraphQL. <br> - Tìm hiểu cơ chế vận hành của AWS AppSync: <br>&emsp; + Dịch vụ được quản trị toàn phần (Managed Service) giúp đơn giản hóa việc tổng hợp, truy vấn và thao tác dữ liệu từ nhiều nguồn an toàn. <br>&emsp; + Khả năng mở rộng API GraphQL linh hoạt, kết nối trực tiếp với DynamoDB, Lambda, OpenSearch/Elasticsearch và các HTTP/SQL/REST endpoints. <br>&emsp; + Các tính năng cao cấp: đồng bộ hóa dữ liệu ngoại tuyến (Offline Sync), cập nhật dữ liệu thời gian thực (Real-time Subscriptions) và phân quyền truy cập hạt mịn (Fine-grained access control). <br> - Thực thi các câu lệnh GraphQL CRUD (Create, Read, Update, Delete) tương tác dữ liệu DynamoDB qua AppSync API. | 05/06/2026 | 05/06/2026 | |
| 3 | - Khai thác tiện ích mở rộng AWS Toolkit cho môi trường lập trình Visual Studio Code. <br> - Ứng dụng trợ lý AI Amazon Q Developer: <br>&emsp; + Hỗ trợ viết Unit Test tự động, tạo mã nguồn, gỡ lỗi và tối ưu hóa đoạn mã lập trình. <br>&emsp; + Gợi ý mã nguồn thời gian thực trên 15+ ngôn ngữ lập trình phổ biến (bao gồm cả CloudFormation, CDK và Terraform). <br>&emsp; + Tối ưu hóa gợi ý mã nguồn cho các thư viện SDK/API của dịch vụ AWS (EC2, Lambda, S3). <br>&emsp; + Quét bảo mật tự động nhằm phát hiện các lỗ hổng mã nguồn tiềm ẩn và đề xuất phương án khắc phục tức thì. | 06/06/2026 | 06/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Khai thác Amazon Macie - dịch vụ tự động hóa bảo mật và quyền riêng tư dữ liệu sử dụng Machine Learning và Pattern Matching để phát hiện dữ liệu nhạy cảm (PII, thẻ tín dụng) trên AWS. <br> - Làm chủ các tính năng cốt lõi của Amazon Macie: <br>&emsp; + Tự động lập danh mục S3 Buckets, đánh giá rủi ro cấu hình và tạo thông báo bảo mật (Policy Findings). <br>&emsp; + Xuất báo cáo chi tiết về mức độ nghiêm trọng, đối tượng chịu tác động và đưa ra khuyến nghị khắc phục. <br>&emsp; + Tự động đẩy sự kiện đến Amazon EventBridge để kích hoạt xử lý qua Lambda/SNS hoặc tích hợp AWS Security Hub để quản lý bảo mật tập trung. <br>&emsp; + Hỗ trợ tích hợp AWS Organizations quản trị bảo mật dữ liệu trên quy mô đa tài khoản (Multi-Account). <br>&emsp; + Tương tác lập trình linh hoạt với Macie thông qua API, AWS CLI hoặc AWS SDKs. | 07/06/2026 | 07/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Thực hành đóng gói và triển khai nền tảng quản trị nội dung WordPress (PHP/MySQL) trên máy chủ Amazon EC2 (Amazon Linux / RHEL). <br> - Tìm hiểu công cụ tự động hóa phát hành phần mềm AWS CodeDeploy: <br>&emsp; + Tự động hóa quá trình triển khai ứng dụng trên Amazon EC2, AWS Fargate, AWS Lambda và máy chủ vật lý On-premises. <br>&emsp; + Tăng tốc độ phát hành tính năng mới, triệt tiêu thời gian gián đoạn dịch vụ (Zero-downtime deployment) và đơn giản hóa quy trình cập nhật. <br>&emsp; + Loại bỏ hoàn toàn thao tác thủ công dễ gây sai sót nhờ các quy trình tự động hóa có khả năng co giãn linh hoạt. | 08/06/2026 | 08/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Nghiên cứu dịch vụ Amazon WorkSpaces - hạ tầng máy tính ảo đám mây (Cloud VDI) được quản trị toàn phần, hỗ trợ cấp phát máy tính cá nhân (Windows, macOS, Ubuntu) trên đám mây AWS. <br> - Tìm hiểu các phương thức kết nối an toàn cho người dùng cuối: <br>&emsp; + Kết nối qua ứng dụng Amazon WorkSpaces Client dedicated. <br>&emsp; + Truy cập trực tiếp qua trình duyệt web chuẩn mã hóa. | 09/06/2026 | 09/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 8:

* **Tích hợp AWS AppSync & GraphQL:**
  * Xây dựng thành công các cổng API GraphQL chuẩn mực, hiệu năng cao và co giãn linh hoạt với AWS AppSync.
  * Định nghĩa Schemas GraphQL hoàn chỉnh với đầy đủ các mẫu định dạng Query, Mutation và Subscription.
  * Tích hợp trực tiếp AppSync Resolvers với Amazon DynamoDB để thực thi các thao tác dữ liệu an toàn.

* **Đồng bộ hóa thời gian thực & Ngoại tuyến (Offline):**
  * Làm chủ cơ chế đẩy dữ liệu thời gian thực đến client thông qua GraphQL Subscriptions.
  * Khai thác tính năng lưu trữ đồng bộ dữ liệu ngoại tuyến (Offline Data Sync) và phân quyền truy cập hạt mịn trong AppSync.

* **Amazon Macie & Bảo mật dữ liệu:**
  * Tự động hóa công tác rà soát dữ liệu nhạy cảm (PII, thông tin tài chính) lưu trữ trên Amazon S3 nhờ Amazon Macie.
  * Cấu hình thành công các tác vụ quét dữ liệu (Discovery Jobs), thiết lập Custom Data Identifiers và Allow Lists.
  * Theo dõi tình trạng an toàn S3 buckets, xử lý Policy Findings và tích hợp cảnh báo với EventBridge/Security Hub.

* **Triển khai WordPress & AWS CodeDeploy:**
  * Khởi tạo và phát hành thành công ứng dụng WordPress trên máy chủ Amazon EC2.
  * Áp dụng thành công AWS CodeDeploy để tự động hóa quy trình phát hành mã nguồn, nâng cao độ tin cậy và loại bỏ rủi ro cập nhật thủ công.

* **Amazon WorkSpaces & Cơ sở hạ tầng máy tính ảo (VDI):**
  * Làm chủ quy trình khởi tạo và quản trị máy tính làm việc ảo (Virtual Desktops) bảo mật trên hạ tầng AWS.
  * Đánh giá và thiết lập các phương thức kết nối an toàn cho nhân sự từ xa qua Client App và Web Browser.
