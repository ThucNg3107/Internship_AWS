---
title : "Verify magazine và article reader public"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.4.3 </b> "
---

Open the production site:

[https://d3u5pkyxnd3uus.cloudfront.net/](https://d3u5pkyxnd3uus.cloudfront.net/)

#### Public behavior

- **Tạp chí (magazine) có thể đọc được mà không cần tài khoản.**
- **Thẻ bài viết (article cards) sử dụng CloudFront WebP URL đã qua xử lý do API trả về.**
- **Người đọc có thể mở toàn bộ văn bản bài viết sạch, bản tóm tắt được tạo, nguồn dẫn và liên kết gốc của nhà xuất bản.**
- **Chỉ yêu cầu đăng nhập đối với lượt thích (likes) và bình luận (comments).**
- **Trang vận hành (operations page) sử dụng phiên admin riêng biệt và không bao giờ chèn admin API key.**

![article-reader](/images/5-Workshop/5.4-S3-onprem/article-reader.png)

#### Bằng chứng article thật

Browser test đã mở một bài Hacker News thật, hiển thị cleaned full text, summary, source URL, processed cover image và reader discussion controls. Kiểm tra desktop và mobile không có horizontal overflow.

#### Ranh giới frontend/API

Frontend không download hoặc convert ảnh publisher. Frontend chỉ nhận `imageUrl` cuối từ API. Việc file validation, resize, conversion, S3 upload và CDN URL thuộc trách nhiệm backend worker.
