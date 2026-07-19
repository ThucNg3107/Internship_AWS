---
title: "Worklog Tuần 12"
date: 2026-07-03
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---
### Mục tiêu tuần 12:

* Tổng rà soát, chuẩn hóa và tối ưu toàn bộ các bài báo cáo thực tập của 11 tuần làm việc trước đó.
* Khắc phục triệt để các sự cố định dạng Markdown, giao diện CSS và mã hóa ký tự UTF-8 Tiếng Việt trên nền tảng tĩnh Hugo.
* Đóng gói mã nguồn, biên dịch bản build tĩnh sản phẩm và hoàn tất quy trình triển khai hosting.
* Tổng hợp toàn bộ thành quả thực tập, biên soạn slide thuyết trình sẵn sàng cho buổi bảo vệ kết quả thực tập.
* Đột phá và củng cố kiến thức chuyên sâu về các dịch vụ AWS cấu thành hệ thống **CloudBrief**.
* Hoàn thiện và cập nhật sơ đồ kiến trúc tổng thể (Architecture Workflow Diagram) phản ánh chính xác trạng thái hạ tầng thực tế.
* Nhận diện các điểm nghẽn và đề xuất phương án tối ưu cho kiến trúc hệ thống cùng tài liệu dự án.

### Các công việc cần triển khai trong tuần này:
#### Tuần 12 (Từ 03/07/2026 – 09/07/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - **Nghiên cứu chuyên sâu hệ dịch vụ AWS thuộc kiến trúc CloudBrief**: <br>&emsp; + Amazon EC2 (`t4g.small` ARM64): Vòng đời instance, co giãn Auto Scaling, thiết lập Security Groups, gán IAM Roles. <br>&emsp; + Amazon S3: Lưu trữ static web hosting, Bucket Policies, Versioning và quy tắc Lifecycle rules. <br>&emsp; + Amazon SQS: Phân tích cơ chế Standard vs FIFO Queues, Visibility Timeout, cấu hình Dead-Letter Queue (DLQ). <br>&emsp; + Amazon DynamoDB: Thiết kế cơ sở dữ liệu NoSQL, chiến lược Partition/Sort Keys, TTL, chế độ On-Demand vs Provisioned. <br>&emsp; + Amazon Bedrock: Gọi mô hình AI (Nova Lite), tối ưu prompt engineering, giới hạn token và xử lý nghẽn Throttling. <br>&emsp; + Amazon CloudFront: Cấu hình phân phối CDN, Cache Behaviors, Origin Access Control (OAC) và Custom Secret Headers. | 03/07/2026 | 03/07/2026 | |
| 3 | - **Tái thiết kế sơ đồ luồng công việc (Workflow Diagram) dự án CloudBrief**: <br>&emsp; + Chuẩn hóa toàn bộ đường đi dữ liệu: RSS Feed &rarr; Collector Worker &rarr; SQS &rarr; Content Worker &rarr; S3 &rarr; Summarizer Worker &rarr; DynamoDB &rarr; Frontend. <br>&emsp; + Thiết lập Amazon CloudFront làm cổng truy cập duy nhất phục vụ giao diện tĩnh S3 lẫn API Gateway/EC2. <br>&emsp; + Bổ sung sơ đồ phân quyền IAM Roles & Policies chi tiết giữa các dịch vụ. <br>&emsp; + Chuẩn hóa phân nhánh xử lý lỗi: cấu hình DLQ cho SQS, kịch bản Exponential Backoff khi Bedrock bị rào cản Throttling. <br>&emsp; + Phân định rõ ràng các vùng mạng Public vs Private. <br>&emsp; + Đồng bộ hóa tài liệu kiến trúc phù hợp với bản vẽ sơ đồ mới. | 04/07/2026 | 04/07/2026 | |
| 4 | - **Phát triển module xử lý hình ảnh cho Backend**: <br>&emsp; + Khai thác các thư viện xử lý ảnh hiệu năng cao (Sharp/Jimp). <br>&emsp; + Xây dựng tính năng tải ảnh an toàn lên Amazon S3. <br>&emsp; + Thiết lập các API nhận diện và biến đổi định dạng hình ảnh cơ bản. <br>&emsp; + Tích hợp luồng xử lý hình ảnh vào quy trình tổng thể của CloudBrief. | 05/07/2026 | 05/07/2026 | |
| 5 | - **Gỡ lỗi và tối ưu hóa hệ thống Backend**: <br>&emsp; + Khắc phục sự cố kết nối và truy vấn cơ sở dữ liệu DynamoDB. <br>&emsp; + Sửa lỗi quá thời gian xử lý (Timeout) của Worker khi phân tích bài viết độ dài lớn. <br>&emsp; + Tái cấu trúc (Refactor) mã nguồn xử lý bất đồng bộ Concurrency cho SQS Consumer. <br>&emsp; + Tối ưu hóa thời gian phản hồi API và hoàn thiện cơ chế bắt ngoại lệ (Exception Handling). | 06/07/2026 | 06/07/2026 | |
| 6 | - **Hoàn thiện sơ đồ kiến trúc tổng thể**: <br>&emsp; + Tích hợp Amazon EventBridge để tự động hóa lịch chạy định kỳ cho các Worker. <br>&emsp; + Tối ưu hóa luồng tương tác thông điệp giữa SQS và Amazon Bedrock. <br>&emsp; + Bổ sung cơ chế phát sự kiện kích hoạt (State Change Triggers). <br>&emsp; + Đóng gói bản vẽ kiến trúc hệ thống hoàn chỉnh phục vụ báo cáo tốt nghiệp. | 07/07/2026 | 07/07/2026 | |

### Kết quả đạt được tuần 12:

* **Nghiên cứu chuyên sâu hệ dịch vụ AWS trong stack CloudBrief**, làm chủ lý do lựa chọn từng dịch vụ:
  * **Amazon EC2** `t4g.small` (ARM64): Tối ưu hóa chi phí vận hành; chạy API Server và các tiến trình Worker dưới dạng background daemons.
  * **Amazon SQS (Standard Queue)**: Tách rời liên kết giữa Collector, Content và Summarizer worker; hỗ trợ cơ chế retry qua Visibility Timeout và bộ lưu trữ thông điệp lỗi DLQ.
  * **Amazon DynamoDB**: Lưu trữ dữ liệu bài viết và mã hash chống trùng lặp; chế độ On-demand đáp ứng linh hoạt các đợt bùng nổ dữ liệu RSS.
  * **Amazon S3**: Lưu trữ các tập tin `.txt` nội dung sạch và chứa bản build tĩnh của Frontend (phân phối bảo mật qua CloudFront).
  * **Amazon Bedrock (Nova Lite)**: Sinh tóm tắt bài viết tự động qua `InvokeModel` API; thấu hiểu cơ chế quản lý token và xử lý Throttling.
  * **Amazon CloudFront**: Đóng vai trò điểm truy cập công cộng duy nhất — định tuyến `/` tới S3 (Frontend) và `/api/*` tới EC2 (Backend) thông qua Origin Secret Headers.

* **Hoàn thiện sơ đồ luồng công việc (Workflow Diagram) của CloudBrief**:
  * Chuẩn hóa đường ống dữ liệu toàn vẹn: RSS Feeds &rarr; Collector &rarr; SQS &rarr; Content Worker &rarr; S3 + SQS &rarr; Summarizer &rarr; DynamoDB.
  * Định tuyến CloudFront: Phân phối tài nguyên tĩnh từ S3 và chuyển tiếp API requests tới EC2.
  * Thiết lập phân quyền IAM Roles tối giản (Least Privilege) cho EC2 Instance Role.
  * Thiết kế luồng xử lý lỗi an toàn: DLQ cho thông điệp hỏng, Exponential Backoff retry khi Bedrock nghẽn.
  * Xác định rõ ranh giới bảo mật: Cách ly hoàn toàn EC2 khỏi internet công cộng nhờ CloudFront Origin Secret Header.

* **Cập nhật tài liệu kiến trúc**: Đồng bộ tài liệu kỹ thuật khớp với sơ đồ kiến trúc mới, đảm bảo mô tả chính xác mọi tương tác dịch vụ và cấu hình bảo mật.

* **Hoàn thiện Module Backend xử lý hình ảnh**: Tích hợp thành công thư viện xử lý ảnh chuyên dụng, phát hành API upload hình ảnh lên Amazon S3 mượt mà vào luồng xử lý chính.

* **Khắc phục triệt để các lỗi Backend**: Xử lý triệt để sự cố kết nối DynamoDB, giải quyết lỗi Timeout bài viết dài và tái cấu trúc luồng Concurrency cho SQS Consumer giúp hệ thống đạt độ ổn định cao.

* **Hoàn chỉnh sơ đồ hệ thống**: Bổ sung Amazon EventBridge tự động hóa lịch chạy, tối ưu hóa phối hợp SQS - Bedrock và phát hành bản vẽ kiến trúc hoàn chỉnh nhất cho báo cáo.

* **Xác định các định hướng cải tiến hạ tầng tương lai**:
  * Cấu hình CloudWatch Alarms theo dõi số lượng thông điệp tích tụ trong DLQ.
  * Áp dụng Lifecycle Policies trên S3 để tự động lưu trữ/xóa các tệp nội dung `.txt` cũ nhằm tối ưu ngân sách.
