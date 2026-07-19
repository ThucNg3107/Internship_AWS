---
title: "Worklog Tuần 4"
date: 2026-05-08
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---
### Mục tiêu tuần 4:

* Triển khai ứng dụng web Java (TravelBuddy) trên nền tảng PaaS Elastic Beanstalk và nâng cao hiểu biết về hệ sinh thái CI/CD tự động hóa của AWS.
* Xây dựng các hàm AWS Lambda xử lý sự kiện tự động từ Amazon S3, chuẩn hóa quy trình hạ tầng không máy chủ với SAM và CloudFormation.
* Lập trình tương tác với cơ sở dữ liệu NoSQL Amazon DynamoDB qua AWS SDK cho Java và điều phối quy trình công việc phức tạp bằng AWS Step Functions.
* Làm chủ các mô thức truyền tin (Messaging), phân biệt hàng chờ (Message Queue) và luồng dữ liệu thời gian thực (Data Stream), đồng thời thiết lập kênh truyền tin Publisher/Subscriber qua Amazon Kinesis.

### Các công việc cần triển khai trong tuần này:
#### Tuần 4 (Từ 08/05/2026 – 14/05/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Thực hành quy trình đóng gói và phát hành ứng dụng web TravelBuddy lên AWS Elastic Beanstalk bằng AWS Toolkit cho Eclipse, cấu hình công cụ EB CLI và ứng dụng AWS SDK để điều khiển môi trường ứng dụng | 08/05/2026 | 08/05/2026 | |
| 3 | - Thiết lập chuỗi công cụ tự động hóa chu kỳ phát triển ứng dụng: lưu trữ mã nguồn an toàn với CodeCommit, biên dịch dự án qua CodeBuild, tự động triển khai bằng CodeDeploy, liên kết toàn bộ luồng công việc tự động qua CodePipeline và quản trị nhanh dự án với CodeStar | 09/05/2026 | 09/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Triển khai dịch vụ Serverless AWS Lambda; tùy chỉnh mã nguồn Java Lambda xử lý tự động sự kiện tạo ảnh thu nhỏ (thumbnail) hoặc xóa tệp không tương thích, liên kết sự kiện kích hoạt (Event Trigger) từ S3 Bucket. <br> - Đóng gói và tự động hóa quy trình khởi tạo Lambda, S3 Bucket và Event Trigger bằng mẫu khai báo hạ tầng AWS SAM và CloudFormation. <br> - Tách dịch vụ nhỏ (Microservice) từ kiến trúc Monolithic và xây dựng đường ống CI/CD tự động hóa trên CodeStar cho Lambda. | 10/05/2026 | 10/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Khai thác thư viện AWS SDK cho Java để thực thi các thao tác quét (Scan) và truy vấn (Query) dữ liệu trên Amazon DynamoDB. <br> - Tối ưu hóa tốc độ tìm kiếm thuộc tính phụ bằng việc cấu hình và sử dụng Chỉ mục (Indexes) trên DynamoDB. <br> - Khởi tạo bảng DynamoDB thủ công và thực thi kịch bản điền dữ liệu mẫu. <br> - Xây dựng sơ đồ điều phối công việc đa bước với AWS Step Functions tích hợp các hàm Lambda làm tác vụ xử lý (Task Actions). | 11/05/2026 | 11/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Nghiên cứu cơ chế vận hành của các mô hình truyền tin trên AWS Cloud, phân tích điểm khác biệt bản chất giữa Message Queue (SQS) và Data Stream (Kinesis). <br> - Lập trình gửi và nhận thông điệp truyền tin qua trình duyệt và AWS SDK cho Java. <br> - Xây dựng cơ chế cho phép Lambda tiêu thụ luồng dữ liệu từ Amazon Kinesis Stream. <br> - Xây dựng mô hình giao tiếp Publisher/Subscriber giữa hai máy chủ EC2 thông qua Kinesis Stream sử dụng AWS SDK cho Java. <br> - Quản trị kho lưu trữ Git bảo mật trên AWS CodeCommit và kết nối truy cập từ môi trường phát triển cục bộ và máy chủ EC2. | 12/05/2026 | 12/05/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 4:

* **Triển khai Ứng dụng & Tự động hóa CI/CD**
  * Tích lũy kinh nghiệm triển khai thực chiến ứng dụng Java (TravelBuddy) trên nền tảng AWS Elastic Beanstalk.
  * Làm chủ bộ công cụ DevOps chuyên sâu của AWS (CodeCommit, CodeBuild, CodeDeploy, CodePipeline, CodeStar).
  * Làm chủ quy trình quản lý phiên bản mã nguồn bảo mật trên cloud bằng AWS CodeCommit.

* **Cơ sở Dữ liệu & Quản lý Dữ liệu**
  * Thành thạo thao tác lập trình tương tác NoSQL DynamoDB qua Java SDK (Scan, Query, Global/Local Secondary Indexes).

* **Điện toán Không máy chủ (Serverless) & Quy trình (Workflows)**
  * Làm chủ mô hình kiến trúc Serverless với AWS Lambda, tự động hóa đóng gói với SAM và CloudFormation.
  * Thiết kế và vận hành thành công luồng xử lý công việc tự động đa bước sử dụng AWS Step Functions và Lambda.

* **Truyền tin & Tích hợp Ứng dụng**
  * Phân biệt và ứng dụng linh hoạt các phương thức truyền tin Asynchronous Messaging (Message Queue vs. Data Stream).
  * Thiết lập thành công hệ thống truyền tin thời gian thực Publisher/Subscriber giữa các EC2 instance qua Amazon Kinesis.
