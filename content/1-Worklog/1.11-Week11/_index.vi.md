---
title: "Worklog Tuần 11"
date: 2026-06-26
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---
### Mục tiêu tuần 11:

* Thực hành làm sạch, kiểm tra và chuyển đổi dữ liệu sử dụng AWS Glue ETL, Apache Hudi trên S3.
* Phân tích dữ liệu bằng Amazon Athena, trực quan hóa qua QuickSight Dashboard, và tìm hiểu truy vấn liên kết (Federated query), tích hợp SageMaker.
* Quản trị hồ dữ liệu tự động với AWS Lake Formation và chuẩn bị dữ liệu bằng Glue DataBrew.
* Thực hiện vai trò **Read-only dashboard frontend** trong dự án **CloudBrief** — hệ thống thu thập & tóm tắt tin tức công nghệ tự động trên AWS.
* Hoàn thiện và xác thực giao diện bảng điều khiển tĩnh (Next.js static-export), đảm bảo tính năng chỉ đọc (read-only) và không chứa mã bảo mật.
* Thực hiện kiểm thử (unit tests) cho frontend, rà soát mã nguồn loại bỏ các tính năng quản trị (admin/write controls) và rò rỉ khóa (API key/secrets).

### Các công việc cần triển khai trong tuần này:
#### Tuần 11 (Từ 26/06/2026 – 02/07/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Lab 3: Transforming data with Glue: <br>&emsp; + Data Validation và ETL: Sử dụng AWS Glue để làm sạch, kiểm tra và chuyển đổi dữ liệu. <br>&emsp; + Incremental Data Processing với Hudi: Áp dụng Apache Hudi xử lý dữ liệu thay đổi (upsert/delete) trên S3. <br> - Lab 4: Query và Visualize: <br>&emsp; + Phân tích dữ liệu: Truy vấn dữ liệu S3 bằng Amazon Athena và tạo Dashboard trực quan bằng QuickSight. <br>&emsp; + Athena nâng cao: Sử dụng Federated query để truy cập đa nguồn và kết nối với SageMaker để dự đoán. | 26/06/2026 | 26/06/2026 | |
| 3 | - Lab 5: Data Lake Automation: <br>&emsp; + Lake Formation cơ bản: Đăng ký data lake location, thiết lập Data Catalog và cấp quyền truy cập. <br>&emsp; + Áp dụng Lake Formation: Quản lý quyền cho các định dạng dữ liệu mở như Apache Hudi, Iceberg, Delta Tables. <br> - Bonus Lab: Glue DataBrew: <br>&emsp; + Sử dụng Glue DataBrew để làm sạch và chuẩn bị dữ liệu (Data Preparation) thông qua giao diện trực quan. | 27/06/2026 | 27/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | + Cài đặt Bun 1.3.x, chạy `bun install`, `bun run build`, `bun run test` thành công. <br> + Tạo file `frontend/.env` từ `frontend/.env.example` (nếu có). <br> + Trao đổi với team (ReinaMacCredy, RyugaRuki) thống nhất toàn bộ route `/api/v1/*`, JSON schema và tích hợp shared contract `@cloudbrief/contracts` cho dashboard. <br> + Review cấu trúc mã nguồn Next.js tĩnh dưới `frontend/` (DashboardSidebar, DashboardHeader, DashboardContent) và file giả lập dữ liệu `frontend/lib/cloudbrief-mocks.ts`. | 28/06/2026 | 28/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | + Viết và cấu hình các bộ kiểm thử unit test cho frontend: `admin-api-client.test.ts`, `api-client.test.ts`, `article-display.test.ts`, `brief-api-client.test.ts`, `brief-display.test.ts`, `dashboard-navigation.test.ts`, `dashboard-store.test.ts`, `fixtures.test.ts`, `social-api-client.test.ts`, `url-safety.test.ts`. <br> + Tách trang giao diện theo các route riêng biệt (`/ops.html`, `/articles.html`, `/runs.html`, `/failures.html`) thay vì sử dụng cơ chế hash anchor (`#`) của dashboard cũ. <br> + Xây dựng logic điều hướng an toàn, xác nhận bài viết chỉ chuyển hướng đến link HTTP/HTTPS tuyệt đối hợp lệ thông qua helper `isSafeUrl`. | 29/06/2026 | 29/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | + Chạy toàn bộ test suite frontend và thực hiện build thành công -> 16/16 tests pass, xuất thư mục tĩnh `frontend/out/`. <br> + Dọn dẹp giao diện (Cleanup): Loại bỏ các nhãn viết/quản trị như `Admin`, `Open admin`, `Create view`, `New category` để đảm bảo dashboard hoàn toàn chỉ đọc (read-only). <br> + Rà soát mã nguồn (Security/Build Audit): Sử dụng `rg` quét tìm `x-api-key`, `DEMO_API_KEY`, các CSRF token hoặc admin credentials trong bundle build tĩnh. <br> + Xác nhận hiển thị an toàn chống XSS: Các trường văn bản như tiêu đề, nguồn, tóm tắt và lỗi phải hiển thị dưới dạng văn bản React thuần, tuyệt đối không dùng `innerHTML` hay `dangerouslySetInnerHTML`. <br> + Tích hợp API base URL thông qua biến môi trường `NEXT_PUBLIC_CLOUDBRIEF_API_BASE_URL` phục vụ triển khai CloudFront thực tế. | 30/06/2026 | 30/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Kết quả đạt được tuần 11:

* **AWS Glue ETL & Apache Hudi trên S3:**
  * Thực hiện thành công Data Validation và ETL với AWS Glue; áp dụng Apache Hudi xử lý dữ liệu thay đổi (upsert/delete) trên S3.

* **Amazon Athena & Amazon QuickSight Visualization:**
  * Truy vấn dữ liệu S3 bằng Amazon Athena, thiết lập Federated query kết nối SageMaker, và xây dựng QuickSight Dashboard trực quan hóa dữ liệu.

* **AWS Lake Formation Data Lake Automation:**
  * Cấu hình Lake Formation đăng ký data lake location, phân quyền truy cập cho Apache Hudi, Iceberg, Delta Tables, và chuẩn bị dữ liệu qua Glue DataBrew.

* **Nắm vững kiến trúc hệ thống CloudBrief trên AWS:**
  * EC2 (ARM64 `t4g.small`) chạy API server + worker processes
  * Amazon DynamoDB lưu trữ bài viết và dedupe records
  * Amazon S3 lưu file nội dung thuần `.txt` và frontend tĩnh
  * Amazon SQS làm queue trung gian giữa các worker
  * Amazon Bedrock Nova Lite cho tóm tắt AI
  * CloudFront làm CDN và reverse proxy duy nhất kết nối với Frontend S3 bucket

* **Xây dựng và hoàn thiện Read-only Dashboard Frontend:**
  * Triển khai giao diện tĩnh sử dụng Next.js (static-export) đặt trong thư mục `frontend/`, xuất ra build `frontend/out/`.
  * Thiết kế bảng điều khiển chia trang rõ ràng: Tổng quan vận hành (`/ops.html`), danh sách bài viết (`/articles.html`), lịch sử chạy (`/runs.html`), và danh sách lỗi (`/failures.html`).
  * Tích hợp thành công dữ liệu thật từ API `GET /api/v1/dashboard` và các endpoints thông qua hook `use-cloudbrief-dashboard.ts`.

* **Viết và vận hành bộ kiểm thử frontend tự động:**
  * Unit tests kiểm thử: `admin-api-client`, `api-client`, `article-display`, `brief-api-client`, `brief-display`, `dashboard-navigation`, `dashboard-store`, `fixtures`, `social-api-client`, `url-safety`.
  * Bộ test frontend chạy thành công bằng Bun với **16/16 tests pass**.

* **Đảm bảo bảo mật và tính năng Read-only an toàn:**
  * Loại bỏ hoàn toàn các nút/nhãn có quyền ghi như `Admin`, `Open admin`, `Create view`, và `New category` trên giao diện demo.
  * Đảm bảo không chứa bất kỳ API key (`x-api-key`, `DEMO_API_KEY`), thông tin bảo mật hay CSRF token nhúng trực tiếp trong bundle tĩnh của client.
  * Triển khai hiển thị an toàn chống tấn công XSS: mã hóa văn bản React thuần cho tất cả các trường dữ liệu bài viết (tiêu đề, tóm tắt, lỗi), tuyệt đối không dùng `innerHTML` hay `dangerouslySetInnerHTML`.
  * Giới hạn liên kết ngoài của bài viết: mở tab mới (`target="_blank"` và `rel="noopener noreferrer"`) và chỉ chấp nhận URL giao thức an toàn HTTP/HTTPS.**
