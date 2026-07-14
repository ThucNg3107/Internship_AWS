---
title: "Worklog Tuần 12"
date: 2026-07-03
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---
### Mục tiêu tuần 12:

* Rà soát, chuẩn hóa và tối ưu hóa toàn bộ nội dung báo cáo thực tập 11 tuần trước đó.
* Sửa lỗi định dạng, CSS và khắc phục các vấn đề hiển thị font tiếng Việt (mã hóa UTF-8) trên website tĩnh Hugo.
* Đóng gói mã nguồn, biên dịch dự án static site và thực hiện deploy lên môi trường lưu trữ.
* Tổng hợp kiến thức thực tập và biên soạn slide báo cáo để sẵn sàng bảo vệ kết quả thực tập.
* Ôn tập và củng cố lại kiến thức về các dịch vụ AWS đã sử dụng trong project **CloudBrief**.
* Vẽ lại và hoàn thiện sơ đồ workflow của hệ thống để phản ánh đúng kiến trúc hiện tại.
* Xác định các điểm còn thiếu hoặc có thể cải thiện trong kiến trúc và tài liệu dự án.

### Các công việc cần triển khai trong tuần này:
#### Tuần 12 (Từ 03/07/2026 – 09/07/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - **Nghiên cứu lại các dịch vụ AWS trong project CloudBrief**: <br>&emsp; + EC2 (`t4g.small` ARM64): Vòng đời instance, Auto Scaling, Security Groups, gắn IAM Role <br>&emsp; + Amazon S3: Static hosting, bucket policy, versioning, lifecycle rules <br>&emsp; + Amazon SQS: Phân biệt Standard vs FIFO, message visibility timeout, cấu hình DLQ <br>&emsp; + Amazon DynamoDB: Thiết kế bảng, chiến lược partition key, TTL, chế độ On-demand vs Provisioned <br>&emsp; + Amazon Bedrock: Gọi model (Nova Lite), cấu hình prompt, giới hạn token, xử lý throttling <br>&emsp; + Amazon CloudFront: Cấu hình distribution, cache behaviors, origin access control (OAC), custom headers | 03/07/2026 | 03/07/2026 | |
| 3 | - **Vẽ lại sơ đồ workflow của project CloudBrief**: <br>&emsp; + Vẽ toàn bộ luồng dữ liệu: RSS Feed &rarr; Collector Worker &rarr; SQS &rarr; Content Worker &rarr; S3 &rarr; Summarizer Worker &rarr; DynamoDB &rarr; Frontend <br>&emsp; + Thêm CloudFront là điểm vào duy nhất phục vụ cả frontend tĩnh (S3) và API (EC2) <br>&emsp; + Bổ sung luồng IAM roles & policies giữa các dịch vụ <br>&emsp; + Thêm các nhánh xử lý lỗi: DLQ cho SQS, retry logic khi Bedrock bị throttle <br>&emsp; + Ghi chú rõ dịch vụ nào public, dịch vụ nào private <br>&emsp; + Cập nhật tài liệu kiến trúc cho khớp với sơ đồ đã vẽ lại | 04/07/2026 | 04/07/2026 | |
| 4 | - **Lập trình Backend xử lý hình ảnh**: <br>&emsp; + Nghiên cứu các thư viện xử lý ảnh phù hợp (Sharp, Jimp...) <br>&emsp; + Code chức năng upload ảnh lên S3 <br>&emsp; + Tạo API nhận diện/xử lý ảnh cơ bản <br>&emsp; + Tích hợp luồng xử lý ảnh vào quy trình chung của CloudBrief | 05/07/2026 | 05/07/2026 | |
| 5 | - **Fix lỗi code Backend**: <br>&emsp; + Debug lỗi kết nối database DynamoDB <br>&emsp; + Sửa lỗi timeout khi worker xử lý các bài viết dài <br>&emsp; + Refactor code phần xử lý concurrency cho SQS consumer <br>&emsp; + Tối ưu hóa API response time và bắt lỗi exception | 06/07/2026 | 06/07/2026 | |
| 6 | - **Chỉnh sửa luồng sơ đồ kiến trúc (Diagram)**: <br>&emsp; + Bổ sung EventBridge để lên lịch chạy worker tự động <br>&emsp; + Điều chỉnh luồng tương tác giữa SQS và Bedrock <br>&emsp; + Thêm cơ chế trigger khi có thay đổi trạng thái <br>&emsp; + Hoàn thiện bản vẽ hệ thống cuối cùng cho báo cáo | 07/07/2026 | 07/07/2026 | |

### Kết quả đạt được tuần 12:

* **Nghiên cứu sâu từng dịch vụ AWS trong stack CloudBrief**, tập trung vào hiểu *tại sao* mỗi dịch vụ được lựa chọn:
  * **EC2** `t4g.small` (ARM64): Tối ưu chi phí tính toán; chạy API server (Express/Bun) và các worker process dưới dạng daemon nền
  * **Amazon SQS (Standard Queue)**: Tách rời Collector, Content và Summarizer worker — hỗ trợ retry qua visibility timeout và dead-letter queue (DLQ) cho các message lỗi
  * **Amazon DynamoDB**: Lưu bản ghi bài viết và hash deduplication; chế độ On-demand xử lý tốt các đỉnh thu thập RSS không đều
  * **Amazon S3**: Lưu file `.txt` nội dung sạch (do Content Worker ghi) và bản build frontend tĩnh (phục vụ qua CloudFront)
  * **Amazon Bedrock (Nova Lite)**: Tạo tóm tắt AI qua InvokeModel API; hiểu giới hạn token và cơ chế throttling là yếu tố quan trọng cho thiết kế retry
  * **Amazon CloudFront**: Là điểm vào public duy nhất — định tuyến `/` tới S3 (frontend) và `/api/*` tới EC2 (backend) qua cache behaviors và cơ chế Origin Secret Header

* **Vẽ lại sơ đồ workflow của CloudBrief**, bao gồm:
  * Toàn bộ pipeline dữ liệu: RSS Feeds &rarr; Collector &rarr; SQS &rarr; Content Worker &rarr; S3 + SQS &rarr; Summarizer &rarr; DynamoDB
  * Định tuyến CloudFront: asset tĩnh từ S3 và API request chuyển tiếp tới EC2
  * Phân công IAM role: EC2 instance role với quyền giới hạn cho S3, SQS, DynamoDB và Bedrock
  * Các nhánh xử lý lỗi: DLQ cho message lỗi, exponential backoff khi Bedrock throttle
  * Ranh giới bảo mật: EC2 không public, được bảo vệ bởi Origin Secret Header qua CloudFront

* **Cập nhật tài liệu kiến trúc** cho khớp với sơ đồ đã vẽ lại, đảm bảo mô tả chính xác tất cả các luồng tương tác giữa dịch vụ và cấu hình bảo mật.

* **Hoàn thiện Backend xử lý hình ảnh:** Đã nghiên cứu và tích hợp thành công thư viện xử lý ảnh, tạo API nhận diện và upload hình ảnh lên S3 một cách trơn tru vào quy trình hiện tại.

* **Khắc phục triệt để các lỗi Backend:** Đã debug thành công lỗi kết nối DynamoDB, xử lý tình trạng timeout của worker và refactor lại phần concurrency cho SQS consumer, giúp API hoạt động ổn định và tối ưu hơn.

* **Hoàn thiện sơ đồ luồng hệ thống:** Đã điều chỉnh và bổ sung các thành phần EventBridge, tối ưu tương tác giữa SQS và Bedrock, cho ra bản vẽ diagram kiến trúc hoàn chỉnh nhất phục vụ cho báo cáo.

* **Xác định các điểm có thể cải thiện trong kiến trúc hiện tại:**
  * Cân nhắc thêm CloudWatch Alarms cho số lượng message trong DLQ
  * Đánh giá lifecycle policy trên S3 để tối ưu chi phí lưu trữ file `.txt` cũ
  * ...
