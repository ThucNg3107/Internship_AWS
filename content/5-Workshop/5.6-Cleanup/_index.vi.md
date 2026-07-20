---
title : "Kế hoạch cleanup và recovery"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

#### 1. Preserve evidence

Trước khi dọn dẹp, hãy xuất bằng chứng đã được làm sạch cho CloudFormation, CloudFront/WAF, ALB target health, ASG instances, VPC endpoints, queues/DLQs, DynamoDB, S3, CloudWatch, SNS, Backup, Budgets, API responses và các bài kiểm tra trình duyệt.

#### 2. Resolve outstanding operations

Đợt kiểm tra ngày 16 tháng 7 đã tìm thấy 3 thông điệp hiển thị trong image-processing DLQ. Hãy kiểm tra và phân loại các thông điệp đó trước khi phá hủy để báo cáo ghi lại nguyên nhân thất bại và quyết định khắc phục. Không xuất bản nội dung bài viết từ một thông điệp bị lỗi.

#### 3. Destroy the CDK stack

```bash
cd ~/Code/Technology-News-Collection-and-Summarization-System
AWS_PROFILE=cloudbrief-workshop AWS_REGION=us-east-1 \
  bun run cdk destroy
```

Thao tác này mang tính phá hủy (destructive) và yêu cầu phê duyệt rõ ràng tại thời điểm thực thi.

#### 4. Handle retained data

Nếu CDK cố ý giữ lại các đối tượng S3 được đánh phiên bản (versioned S3 objects), điểm khôi phục sao lưu (backup recovery points) hoặc dữ liệu bền vững khác, hãy quyết định xem mỗi mục phải được giữ lại làm bằng chứng hay xóa bỏ. Việc làm rỗng một bucket được đánh phiên bản yêu cầu loại bỏ cả object versions và delete markers.

#### 5. Verify cleanup read-only

Xác nhận rằng các tài nguyên dự kiến không còn tồn tại:

- **CloudFormation stack, CloudFront distribution, và WAF Web ACL.**
- **ALB, target group, ASG, EC2 instances, EBS volumes, và NAT Gateway.**
- **VPC endpoints, SQS queues/DLQs, DynamoDB tables, và S3 buckets.**
- **CloudWatch alarms/log groups, SNS topic, Backup resources, và project budget.**

#### Current status

Dọn dẹp đang ở trạng thái **pending** (chờ xử lý) vì CloudBrief vẫn là bản demo sản xuất đang hoạt động. Báo cáo không được tuyên bố thành công dọn dẹp cho đến khi việc phá hủy (destroy) được phê duyệt, thực thi và xác minh.