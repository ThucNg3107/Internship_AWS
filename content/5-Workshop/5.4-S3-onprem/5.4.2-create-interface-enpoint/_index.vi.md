---
title : "Test pipeline RSS và Hacker News thật"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.4.2 </b> "
---

#### Step 1: Verify the public health route

```bash
curl -i https://d3u5pkyxnd3uus.cloudfront.net/api/health
```

Verified on 16 July 2026: HTTP `200`, project `cloudbrief`, stage `dev`, status `healthy`.

#### Step 2: Verify protected collection

Việc gọi đường dẫn admin collection mà không có thông tin xác thực phải trả về phản hồi không có quyền (unauthorized). Một yêu cầu admin hợp lệ sẽ chấp nhận các nguồn RSS và Hacker News, sau đó đưa công việc vào hàng đợi thông qua thu thập, trích xuất, tóm tắt và xử lý hình ảnh.

```bash
curl -X POST https://d3u5pkyxnd3uus.cloudfront.net/api/v1/collect \
  -H 'content-type: application/json' \
  -d '{"sources":["rss","hackernews"],"limit":5}'
```

Do not place the real admin key in a screenshot or shell history.

#### Step 3: Read a real brief

```bash
curl 'https://d3u5pkyxnd3uus.cloudfront.net/api/v1/brief?limit=5'
```

Expected article contract:

```json
{
  "id": "article-id",
  "title": "Publisher title",
  "summary": "Bedrock or deterministic fallback summary",
  "canonicalUrl": "https://publisher.example/article",
  "imageUrl": "https://cloudfront.example/article-images/cover.webp"
}
```

Worker chấp nhận hình ảnh PNG, JPEG hoặc WebP của nhà xuất bản, xác thực và chuyển đổi chúng sang WebP, tải chúng lên một private S3 bucket và chỉ lưu trữ CloudFront URL trong DynamoDB.

Phản hồi trực tiếp vào ngày 16 tháng 7 đã trả về 5 bài viết Hacker News. Cả 5 bài viết đều có canonical publisher URL, trạng thái `SUMMARIZED` và CloudFront WebP cover URL đã qua xử lý. Một tiêu đề đã được xác minh là **Bluesky Trademarks ATProto** từ trang web AT Protocol.

![api-smoke-ok](/images/5-Workshop/5.4-S3-onprem/api-smoke-ok.png)

#### Bedrock result

Nova Micro được cấu hình làm mô hình chi phí thấp với giới hạn đầu ra 256 token. Trong quá trình triển khai đã ghi lại, tài khoản AWS đã đạt đến giới hạn token Nova hàng ngày. Do đó, CloudBrief đã lưu trữ các bản tóm tắt dự phòng (deterministic fallback summaries) thay vì bỏ qua các bài viết; CloudWatch hiển thị điều kiện này.