---
title: "Worklog Tuần 4"
date: 2026-05-08
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---
### Mục tiêu tuần 4:

* Triển khai ứng dụng web Java (TravelBuddy) lên Elastic Beanstalk và tìm hiểu các dịch vụ CI/CD tự động hóa trên AWS.
* Phát triển các hàm AWS Lambda xử lý sự kiện S3, tự động hóa hạ tầng không máy chủ với SAM và CloudFormation.
* Tương tác với cơ sở dữ liệu Amazon DynamoDB sử dụng AWS SDK cho Java và thiết kế quy trình xử lý dữ liệu với Step Functions.
* Tìm hiểu các phương thức truyền tin (Messaging), phân biệt hàng chờ (Queue) với luồng dữ liệu (Stream), và xây dựng kênh pub/sub qua Amazon Kinesis.

### Các công việc cần triển khai trong tuần này:
#### Tuần 4 (Từ 08/05/2026 – 14/05/2026)
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Nghiên cứu cách triển khai ứng dụng web TravelBuddy lên AWS, Sử dụng AWS Tools cho Eclipse để deploy ứng dụng Java lên môi trường Elastic Beanstalk, Cấu hình công cụ AWS Elastic Beanstalk CLI, Sử dụng AWS SDK để truy vấn và chỉnh sửa môi trường AWS | 08/05/2026 | 08/05/2026 | |
| 3   | - Áp dụng cấu hình các dịch vụ tự động phát hành ứng dụng kết hợp AWS CodeCommit để lưu trữ mã nguồn an toàn, AWS CodeBuild để xây dựng mã nguồn, AWS CodeDeploy để triển khai ứng dụng lên máy chủ, AWS CodePipeline để liên kết CodeCommit, CodeBuild và CodeDeploy với nhau thành một quy trình làm việc tự động và liền mạch, và AWS CodeStar để cho phép bạn nhanh chóng phát triển, xây dựng và triển khai các ứng dụng trên AWS | 09/05/2026 | 09/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4   | - Triển khai một AWS Lambda function. <br> - Chỉnh sửa mã nguồn hàm Java Lambda đã được cung cấp để thay đổi kích thước hình ảnh dưới dạng hình thu nhỏ hoặc xóa tập tin không phải hình ảnh và kết nối trình kích hoạt vào S3 bucket để kiểm tra tính năng. <br> - Sử dụng AWS Serverless Application Model (SAM) và AWS CloudFormation để tạo template nhằm tự động hóa việc triển khai hàm Lambda, một trình kích hoạt S3 và một S3 bucket. <br> - Xác định microservice candidate trong monolithic codebase và tạo dự án AWS CodeStar để quản lý CI/CD pipeline cho microservice đó được lưu trữ trong AWS Lambda. | 10/05/2026 | 10/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5   | - Sử dụng AWS SDK cho Java để quét Bảng Amazon DynamoDB để trả về kết quả. <br> - Sử dụng AWS SDK cho Java để truy vấn Amazon DynamoDB Table để trả về kết quả phù hợp. <br> - Sử dụng Chỉ mục trong bảng DynamoDB để thực hiện tra cứu các thuộc tính khác với khóa phân vùng. <br> - Tạo bảng DynamoDB theo cách thủ công bằng bảng điều khiển và điền dữ liệu theo cách thủ công. <br> - Tạo workflow bằng các AWS Step Functions. <br> - Tạo các hàm AWS Lambda cung cấp các hành động Tác vụ cho các Step Functions. | 11/05/2026 | 11/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6   | - Hiểu các hoạt động của các phương thức truyền tin khác nhau trên nền tảng AWS. <br> - Giải thích sự khác biệt giữa hàng chờ và luồng dữ liệu. <br> - Sử dụng các phương thức truyền tin AWS từ trình duyệt web và lập trình bằng Java SDK. <br> - Hiểu cách đọc dữ liệu từ Amazon Kinesis stream bằng Amazon Lambda. <br> - Tạo kênh giao tiếp pub/sub giữa hai EC2 instance, thông qua Amazon Kinesis stream, sử dụng AWS SDK cho Java. <br> - Tìm hiểu cách tạo kho lưu trữ trong AWS CodeCommit và truy cập kho lưu trữ trong môi trường phát triển và EC2 instance. | 12/05/2026 | 12/05/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 4:

* **Triển khai Ứng dụng & Tự động hóa CI/CD**
  * Có kinh nghiệm thực tế trong việc triển khai ứng dụng web Java (TravelBuddy) lên môi trường AWS Elastic Beanstalk.
  * Nắm vững các dịch vụ CI/CD của AWS (CodeCommit, CodeBuild, CodeDeploy, CodePipeline, CodeStar).
  * Làm chủ kiểm soát phiên bản trên AWS bằng cách tạo kho lưu trữ Git trong CodeCommit và truy cập trên nhiều môi trường.

* **Cơ sở Dữ liệu & Quản lý Dữ liệu**
  * Sử dụng AWS SDK cho Java để truy vấn và sửa đổi DynamoDB, bao gồm quét, truy vấn và tận dụng các chỉ mục (indexes).

* **Điện toán Không máy chủ (Serverless) & Quy trình (Workflows)**
  * Làm chủ điện toán serverless với AWS Lambda, SAM, và CloudFormation, bao gồm các trình kích hoạt (trigger) từ S3.
  * Thiết kế và thực thi các quy trình làm việc bằng AWS Step Functions, tích hợp liền mạch với Lambda.

* **Truyền tin & Tích hợp Ứng dụng**
  * Tìm hiểu và triển khai các phương thức truyền tin khác nhau trên AWS, phân biệt giữa hàng chờ (message queues) và luồng dữ liệu (data streams).
  * Xây dựng thành công kênh giao tiếp pub/sub giữa các EC2 instance sử dụng Amazon Kinesis và AWS SDK cho Java.


