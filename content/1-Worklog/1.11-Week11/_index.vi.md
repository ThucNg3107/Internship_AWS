---
title: "Worklog Tuần 11"
date: 2026-06-26
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---
### Mục tiêu tuần 11:

* Thực thi quy trình làm sạch, kiểm thử và biến đổi dữ liệu (ETL) bằng AWS Glue tích hợp chuẩn bảng Apache Hudi trên S3.
* Phân tích chuyên sâu dữ liệu với Amazon Athena, thiết lập bảng điều khiển trực quan trên QuickSight và khai thác tính năng Federated Query kết nối Amazon SageMaker.
* Tự động hóa quản trị Data Lake bằng AWS Lake Formation và chuẩn hóa dữ liệu trực quan bằng Glue DataBrew.
* Đảm nhận vai trò **Phát triển giao diện bảng điều khiển tĩnh chỉ đọc (Read-only Dashboard Frontend)** trong dự án **CloudBrief** — ứng dụng thu thập và tổng hợp tin tức công nghệ tự động bằng AI trên hạ tầng AWS.
* Hoàn thiện và đóng gói giao diện Dashboard tĩnh (Next.js Static Export), bảo đảm tính năng Read-only an toàn và triệt tiêu nguy cơ lộ secrets.
* Viết kịch bản unit test tự động cho frontend, rà soát mã nguồn loại bỏ toàn bộ các điều khiển ghi/quản trị (Write/Admin controls) và khóa bảo mật.

### Các công việc cần triển khai trong tuần này:
#### Tuần 11 (Từ 26/06/2026 – 02/07/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Lab 3: Khai thác AWS Glue biến đổi dữ liệu: <br>&emsp; + Thẩm định dữ liệu (Data Validation) và quy trình ETL: Sử dụng AWS Glue để làm sạch, kiểm tra chất lượng và biến đổi định dạng dữ liệu. <br>&emsp; + Xử lý dữ liệu thay đổi tăng dần (Incremental Data Processing) với Apache Hudi: Thực thi các thao tác cập nhật/xóa (Upsert/Delete) trực tiếp trên S3 Data Lake. <br> - Lab 4: Truy vấn và Trực quan hóa dữ liệu: <br>&emsp; + Phân tích dữ liệu: Khai thác Amazon Athena truy vấn dữ liệu S3 và xây dựng Dashboard chuyên nghiệp trên Amazon QuickSight. <br>&emsp; + Tính năng Athena nâng cao: Khai thác Federated Query truy vấn đa nguồn dữ liệu và tích hợp Amazon SageMaker phục vụ dự đoán ML. | 26/06/2026 | 26/06/2026 | |
| 3 | - Lab 5: Tự động hóa Data Lake với AWS Lake Formation: <br>&emsp; + Quản trị Lake Formation: Đăng ký vùng lưu trữ Data Lake, xây dựng Data Catalog tập trung và phân quyền truy cập hạt mịn. <br>&emsp; + Phân quyền cho Open Table Formats: Quản lý chính sách bảo mật cho Apache Hudi, Apache Iceberg và Delta Tables. <br> - Lab bổ sung: AWS Glue DataBrew: <br>&emsp; + Chuẩn hóa và làm sạch dữ liệu trực quan qua giao diện kéo thả của Glue DataBrew. | 27/06/2026 | 27/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | + Cài đặt môi trường runtime Bun 1.3.x, thực thi thành công các lệnh `bun install`, `bun run build`, `bun run test`. <br> + Cấu hình file `frontend/.env` chuẩn từ bản mẫu `.env.example`. <br> + Thống nhất cùng nhóm dự án (ReinaMacCredy, RyugaRuki) chuẩn hóa định tuyến API `/api/v1/*`, JSON Schemas và tích hợp gói hợp đồng dữ liệu `@cloudbrief/contracts`. <br> + Rà soát cấu trúc mã nguồn Next.js dưới thư mục `frontend/` (DashboardSidebar, DashboardHeader, DashboardContent) và file giả lập dữ liệu `frontend/lib/cloudbrief-mocks.ts`. | 28/06/2026 | 28/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | + Phát triển bộ kịch bản Unit Test cho frontend: `admin-api-client.test.ts`, `api-client.test.ts`, `article-display.test.ts`, `brief-api-client.test.ts`, `brief-display.test.ts`, `dashboard-navigation.test.ts`, `dashboard-store.test.ts`, `fixtures.test.ts`, `social-api-client.test.ts`, `url-safety.test.ts`. <br> + Tách giao diện thành các tuyến đường trang tĩnh riêng biệt (`/ops.html`, `/articles.html`, `/runs.html`, `/failures.html`) thay thế cho cơ chế chuyển trang hash anchor (`#`) cũ. <br> - Xây dựng logic điều hướng an toàn, xác nhận bài viết chỉ chuyển hướng đến link HTTP/HTTPS tuyệt đối hợp lệ thông qua helper `isSafeUrl`. | 29/06/2026 | 29/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | + Thực thi toàn bộ bộ kiểm thử Frontend test suite và xuất bản bản build tĩnh thành công -> **16/16 tests pass**, xuất thư mục tĩnh `frontend/out/`. <br> + Chuẩn hóa giao diện Read-only: Gỡ bỏ hoàn toàn các nút thao tác có quyền ghi/quản trị như `Admin`, `Open admin`, `Create view`, `New category`. <br> + Kiểm tra an ninh mã nguồn (Security Audit): Sử dụng `rg` rà soát tuyệt đối không để rò rỉ `x-api-key`, `DEMO_API_KEY`, CSRF tokens hay admin credentials trong gói tĩnh client. <br> + Đảm bảo an toàn chống lỗ hổng XSS: Mã hóa hiển thị các trường dữ liệu bằng chuỗi React thuần, tuyệt đối không dùng `innerHTML` hay `dangerouslySetInnerHTML`. <br> + Khấu trừ API Base URL linh hoạt qua biến môi trường `NEXT_PUBLIC_CLOUDBRIEF_API_BASE_URL` phục vụ phân phối qua Amazon CloudFront CDN. | 30/06/2026 | 30/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 11:

* **AWS Glue ETL & Apache Hudi trên S3:**
  * Thực hiện thành công Data Validation và ETL với AWS Glue; ứng dụng Apache Hudi xử lý dữ liệu thay đổi (upsert/delete) trực tiếp trên S3 Data Lake.

* **Amazon Athena & Amazon QuickSight Visualization:**
  * Truy vấn dữ liệu S3 với Amazon Athena, thiết lập Federated Query kết nối SageMaker và xây dựng QuickSight Dashboard trực quan hóa chỉ số.

* **AWS Lake Formation Data Lake Automation:**
  * Cấu hình Lake Formation đăng ký vị trí Data Lake, phân quyền truy cập cho các định dạng Apache Hudi, Iceberg, Delta Tables và chuẩn bị dữ liệu qua Glue DataBrew.

* **Thấu hiểu toàn diện kiến trúc dự án CloudBrief trên AWS:**
  * Máy chủ Amazon EC2 (ARM64 `t4g.small`) vận hành API Server & Worker Processes.
  * Amazon DynamoDB lưu trữ danh mục bài viết và kiểm soát trùng lặp (Deduplication).
  * Amazon S3 lưu trữ nội dung văn bản thuần `.txt` và mã nguồn Frontend tĩnh.
  * Amazon SQS làm hàng đợi chuyển giao thông điệp giữa các tiến trình Worker.
  * Amazon Bedrock (Nova Lite) thực thi tổng hợp và tóm tắt nội dung tự động bằng AI.
  * Amazon CloudFront đóng vai trò CDN và Reverse Proxy duy nhất kết nối với Frontend S3 Bucket.

* **Hoàn thiện Read-only Dashboard Frontend:**
  * Phát hành thành công giao diện tĩnh bằng Next.js (Static Export) trong thư mục `frontend/out/`.
  * Chuẩn hóa cấu trúc điều hướng tĩnh: Tổng quan vận hành (`/ops.html`), Bài viết (`/articles.html`), Lịch sử chạy (`/runs.html`), Lịch sử lỗi (`/failures.html`).
  * Tích hợp dữ liệu thời gian thực từ API `GET /api/v1/dashboard` qua custom hook `use-cloudbrief-dashboard.ts`.

* **Vận hành bộ kiểm thử Frontend tự động:**
  * Viết đầy đủ Unit Tests: `admin-api-client`, `api-client`, `article-display`, `brief-api-client`, `brief-display`, `dashboard-navigation`, `dashboard-store`, `fixtures`, `social-api-client`, `url-safety`.
  * Bộ kiểm thử frontend chạy thành công với kết quả **16/16 tests pass**.

* **Bảo mật giao diện & Tuân thủ tính năng Read-only:**
  * Triệt tiêu hoàn toàn các phím chức năng ghi dữ liệu như `Admin`, `Open admin`, `Create view`, `New category`.
  * Bảo mật mã nguồn: Không chứa bất kỳ API key (`x-api-key`, `DEMO_API_KEY`), secrets hay CSRF token trong gói tĩnh client.
  * Chống tấn công XSS: Mã hóa chuỗi React thuần cho tất cả các trường dữ liệu, không dùng `innerHTML` hay `dangerouslySetInnerHTML`.
  * An toàn liên kết: Mở liên kết bài viết ở tab mới (`target="_blank"` và `rel="noopener noreferrer"`) và chỉ chấp nhận URL hợp lệ sử dụng giao thức HTTP/HTTPS.
