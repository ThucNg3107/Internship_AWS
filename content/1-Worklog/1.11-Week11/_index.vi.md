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
* Thực hiện vai trò **API Contract QA** trong dự án **CloudBrief** — hệ thống thu thập & tóm tắt tin tức công nghệ tự động trên AWS.
* Viết bộ kiểm thử tự động (unit tests, integration tests), xây dựng **Postman** collection phục vụ demo.
* Rà soát bảo mật (SSRF, XXE, XSS, API Key leakage) và hoàn thiện tài liệu API.

### Các công việc cần triển khai trong tuần này:
#### Tuần 11 (Từ 26/06/2026 – 02/07/2026)
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Lab 3: Transforming data with Glue: <br>&emsp; + Data Validation và ETL: Sử dụng AWS Glue để làm sạch, kiểm tra và chuyển đổi dữ liệu. <br>&emsp; + Incremental Data Processing với Hudi: Áp dụng Apache Hudi xử lý dữ liệu thay đổi (upsert/delete) trên S3. <br> - Lab 4: Query và Visualize: <br>&emsp; + Phân tích dữ liệu: Truy vấn dữ liệu S3 bằng Amazon Athena và tạo Dashboard trực quan bằng QuickSight. <br>&emsp; + Athena nâng cao: Sử dụng Federated query để truy cập đa nguồn và kết nối với SageMaker để dự đoán. | 26/06/2026 | 26/06/2026 | |
| 3 | - Lab 5: Data Lake Automation: <br>&emsp; + Lake Formation cơ bản: Đăng ký data lake location, thiết lập Data Catalog và cấp quyền truy cập. <br>&emsp; + Áp dụng Lake Formation: Quản lý quyền cho các định dạng dữ liệu mở như Apache Hudi, Iceberg, Delta Tables. <br> - Bonus Lab: Glue DataBrew: <br>&emsp; + Sử dụng Glue DataBrew để làm sạch và chuẩn bị dữ liệu (Data Preparation) thông qua giao diện trực quan. | 27/06/2026 | 27/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | + Cài đặt Bun 1.3.x, chạy `bun install`, `bun run build`, `bun run test` thành công. <br> + coppy `backend/.env.example` -> `backend/.env` <br> + Trao đổi với team (ReinaMacCredy, RyugaRuki) thống nhất toàn bộ route `/api/v1/*`, JSON schema, định nghĩa trạng thái bài viết (`PENDING_CONTENT`, `CONTENT_FAILED`, `SUMMARY_FAILED`, `SUMMARIZED`). <br> + Review `contracts/src/index.ts`, `frontend/lib/cloudbrief-mocks.ts`, `backend/src/app/routes/v1.ts`. | 28/06/2026 | 28/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | + `apiKey.test.ts`: Test SHA-256 hash, constant-time comparison, reject key thiếu/sai -> 401, không log plaintext key. <br> + `apiRoutes.test.ts`: Test 400 Bad Request, public routes không cần key, origin secret header -> reject ở production mode. <br> + `apiV1Routes.test.ts`: Test toàn bộ `/api/v1/*` public routes + admin session/CSRF flow. <br> + `rssClient.test.ts`: Xác nhận parser XML tắt DTD & External Entity (chống XXE). <br> + `dedupe.test.ts`: Test canonical URL hash & title hash, chặn collect URL trùng. <br> + `localPayloads.test.ts`: Test state transitions & retry logic (`CONTENT_FAILED` / `SUMMARY_FAILED` -> reset; `SUMMARIZED` -> 409; vượt `MAX_RETRY_COUNT` -> 409). <br> + Xây dựng `CloudBrief_API_Tests.postman_collection.json` với đầy đủ endpoint, placeholder `{{API_KEY}}`, `{{CSRF_TOKEN}}` -> 51/51 tests pass. | 29/06/2026 | 29/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | + Chạy toàn bộ test suite sau khi team merge code -> 53/53 tests pass. <br> + Security Audit: xác nhận `.env` / `cdk.context.json` trong `.gitignore`, không có plaintext API key trong response/log. <br> + Xác nhận safe-fetch chống SSRF: pin IP sau DNS resolve, chặn redirect > 3, chặn IP nội bộ/IMDS `169.254.169.254`. <br> + Xác nhận Dashboard chống XSS: hiển thị summary qua text encoding, không dùng `innerHTML`. <br> + Xác nhận Origin Secret Header reject request không hợp lệ ở production mode. <br> + Cập nhật `docs/api.md` khớp 100% với `/api/v1` routes đã implement, tách biệt deployed-only cases. | 30/06/2026 | 30/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

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
  * CloudFront làm CDN và reverse proxy duy nhất

* **Viết và vận hành bộ kiểm thử tự động:**
  * Unit tests: `apiKey`, `apiRoutes`, `apiV1Routes`, `rssClient`, `dedupe`
  * Integration tests: `localPayloads` (state transitions & retry logic)
  * Tất cả chạy `local` mà không cần AWS deploy thật (53/53 tests pass)

* **Xây dựng Postman Collection đầy đủ cho buổi demo:**
  * Bao gồm tất cả các public routes và admin routes
  * Sử dụng placeholder `{{API_KEY}}`, `{{CSRF_TOKEN}}` (không commit secret thật) -> 51/51 tests pass

* **Thực hiện Security Audit và xác nhận hệ thống an toàn với:**
  * Chống SSRF (safe-fetch với IP pinning, chặn IMDS `169.254.169.254`)
  * Chống XXE (tắt DTD và External Entity trong RSS parser)
  * Chống XSS (Dashboard dùng text encoding, không dùng `innerHTML`)
  * Không rò rỉ API key trong response, log hay frontend assets
  * Origin Secret Header bảo vệ EC2 khỏi bypass CloudFront

* **Hoàn thiện `docs/api.md` khớp 100% với `/api/v1` routes đã implement.**
