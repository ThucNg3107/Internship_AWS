---
title : "Quyết định security, cost và architecture"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

#### Security controls

| Ranh giới | Control |
| --- | --- |
| Public edge | AWS WAF ở trước CloudFront distribution |
| Frontend | Private, versioned S3 bucket thông qua Origin Access Control |
| API origin | CloudFront origin secret và ALB routing; không có EC2 public IP trực tiếp |
| Compute | Hai EC2 instances trong private subnets, được quản lý bởi fixed-capacity ASG |
| Host access | Systems Manager thay vì SSH vào trực tiếp (inbound SSH) |
| Managed services | SQS/Bedrock interface endpoints và S3/DynamoDB gateway endpoints |
| Publisher fetches | SSRF-safe fetcher chặn các điểm đến private, loopback, link-local và reserved |
| Article images | Đã xác thực, thay đổi kích thước, chuyển đổi sang WebP và lưu trong private S3 bucket |
| Admin API | Phân phiên admin HttpOnly; static frontend không chứa `x-api-key` |
| Reader data | Đọc công khai; lượt thích/bình luận cần xác thực; kiểm tra quyền sở hữu khi sửa/xóa |
| Alerts | KMS-encrypted SNS topic với quyền phát hành (publish) bị giới hạn cho EC2 |

#### IAM lesson

Ảnh chụp màn hình phần 5.2 cho thấy policy `AdministratorAccess` tạm thời được sử dụng cho đợt triển khai ban đầu của sinh viên. Điều đó có thể chấp nhận được dưới dạng bằng chứng lịch sử nhưng quá rộng để làm cơ chế kiểm soát sản xuất lâu dài. Cải tiến được khuyến nghị là một CDK deployment role riêng biệt chỉ có các hành động dịch vụ và tài nguyên `iam:PassRole` do stack này yêu cầu, MFA cho truy cập console và credentials ngắn hạn thông qua IAM Identity Center khi có sẵn.

#### Cost model

Kiến trúc hiện tại ưu tiên tính sẵn sàng cao (high availability) và private compute hơn là bản demo rẻ nhất có thể:

- **Hai `t4g.small` EC2 instances.**
- **Một Application Load Balancer.**
- **Một NAT Gateway.**
- **Hai paid interface endpoints cộng với hai gateway endpoints.**
- **Sử dụng CloudFront, WAF, S3, DynamoDB on-demand, SQS, CloudWatch, SNS, Backup và Bedrock.**

Các biện pháp kiểm soát chi phí bao gồm Nova Micro, giới hạn đầu ra 256 token, giới hạn số bài viết, thời gian lưu trữ log ngắn, các quy tắc lifecycle của S3, DynamoDB on-demand, cảnh báo ngân sách và quy trình dọn dẹp đã được ghi lại.

#### Architecture tradeoff

Topoplogy demo trước đây rẻ hơn nhưng không khớp với kiến trúc cuối cùng. Thiết kế đã triển khai bổ sung thêm ALB, private subnets, tính dự phòng ASG, WAF và các service endpoints. Chi phí cao hơn, nhưng mang lại câu chuyện sản xuất rõ ràng hơn: bảo vệ public edge, không có IP công khai cho instance, compute trên hai AZ, truy cập hướng ra ngoài có giới hạn, cô lập hàng đợi và xử lý thất bại có thể quan sát được.
