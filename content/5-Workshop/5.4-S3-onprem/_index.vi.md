---
title : "Verify hệ thống production"
date : 2024-01-01 
weight : 4 
chapter : false
pre : " <b> 5.4. </b> "
---

Phần này kiểm tra hệ thống đã triển khai từ hạ tầng đến một bài viết thực tế được hiển thị trên giao diện người đọc (reader UI).

1. [Verify network and compute](5.4.1-prepare/)
2. [Test the real RSS and Hacker News pipeline](5.4.2-create-interface-enpoint/)
3. [Verify the public magazine and article reader](5.4.3-test-endpoint/)
4. [Inspect monitoring, queues, and operations](5.4.4-dns-simulation/)

#### Acceptance result

| Layer | Bằng chứng |
| --- | --- |
| Edge | CloudFront distribution và WAF tồn tại |
| Compute | ALB active; hai private EC2 instances hoạt động tốt thông qua ASG |
| Network | NAT available; bốn VPC endpoints available |
| Data plane | Tám SQS queues và sáu DynamoDB tables |
| API | CloudFront `/api/health` và các real brief endpoints phản hồi |
| Content | Bài viết RSS/Hacker News thật, summary, cleaned text và ảnh WebP |
| Frontend | Các trang Magazine và article-reader tải thông qua CloudFront |
| Operations | CloudWatch alarms, SNS, Backup và Budgets đã được cấu hình |
