---
title : "Build và deploy CloudBrief"
date : 2024-01-01 
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Kiến trúc triển khai

![CloudBrief Architecture](/images/5-Workshop/5.3-S3-vpc/cloudbrief.png)

CloudFront là điểm truy cập công khai duy nhất. AWS WAF bảo vệ distribution; S3 phục vụ private frontend thông qua Origin Access Control; `/api/*` được chuyển tiếp đến Application Load Balancer hướng ra internet. ALB gửi request đến hai EC2 instances trong private subnets. NAT Gateway xử lý việc lấy tin RSS, Hacker News và bài viết bên ngoài, trong khi bốn VPC endpoints giữ lưu lượng truy cập SQS, Bedrock, S3 và DynamoDB trên mạng nội bộ AWS.

#### Các chương triển khai

1. [Build and synthesize locally](5.3.1-create-gwe/)
2. [Deploy the production stack](5.3.2-test-gwe/)

#### Verified production target

| Setting | Verified value |
| --- | --- |
| Stack | `cloudbrief-dev` |
| Region | `us-east-1` |
| CloudFormation status | `UPDATE_COMPLETE` |
| Compute | 2 private EC2 instances across 2 AZs |
| Entry | CloudFront + WAF + ALB |
| Network egress | 1 NAT Gateway |
| VPC endpoints | 2 interface + 2 gateway endpoints |
| Worker queues | 4 queues + 4 DLQs |
| DynamoDB | 6 CloudBrief tables |
| Summary model | `amazon.nova-micro-v1:0`, 256 output tokens |

Các giá trị này đã được kiểm tra bằng các lệnh AWS CLI read-only vào ngày 16 tháng 7 năm 2026.