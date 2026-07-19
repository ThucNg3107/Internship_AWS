---
title : "Security, cost, and architecture decisions"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

#### Security controls

| Boundary | Control |
| --- | --- |
| Public edge | AWS WAF in front of CloudFront distribution |
| Frontend | Private, versioned S3 bucket via Origin Access Control |
| API origin | CloudFront origin secret and ALB routing; EC2 has no public IP |
| Compute | Two EC2 in private subnet, managed by fixed-capacity ASG |
| Host access | Systems Manager instead of inbound SSH |
| Managed services | SQS/Bedrock interface endpoint and S3/DynamoDB gateway endpoint |
| Publisher fetches | SSRF-safe fetcher blocks private, loopback, link-local and reserved destinations |
| Article images | Validate, resize, convert to WebP and store in private S3 bucket |
| Admin API | HttpOnly admin session; static frontend does not contain `x-api-key` |
| Reader data | Read public; like/comment require login; edit/delete verify owner |
| Alerts | KMS-encrypted SNS topic with publish permission limited to EC2 |

#### IAM lesson

Screenshot 5.2 shows the `AdministratorAccess` policy used temporarily during the initial student deploy. This is valid historical evidence but too broad for long-term production use. The recommended improvement is a dedicated CDK deployment role with only the service actions and `iam:PassRole` resources the stack needs, enabling MFA for the console and using short-lived credentials via IAM Identity Center whenever possible.

#### Cost model

The current architecture prioritizes high availability and private compute over the cheapest demo option:

- Two EC2 `t4g.small`.
- One Application Load Balancer.
- One NAT Gateway.
- Two paid interface endpoints and two gateway endpoints.
- CloudFront, WAF, S3, DynamoDB on-demand, SQS, CloudWatch, SNS, Backup and Bedrock usage.

Cost controls include Nova Micro, 256 output token limit, article cap, short log retention, S3 lifecycle, DynamoDB on-demand, budget alert and a documented cleanup procedure.

#### Architecture tradeoff

A single public EC2 design would have been cheaper but did not match the final architecture. The deployed design added ALB, private subnet, ASG redundancy, WAF and service endpoints. Cost is higher but the production story is clearer: protected public edge, instance with no public IP, compute across two AZs, limited outbound access, queue isolation and failure handling with observability.
