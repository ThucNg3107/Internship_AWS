---
title : "Cleanup and recovery plan"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

{{% notice warning %}}
Production demo is still live. The commands below are reviewed cleanup procedures and have not been executed while writing the workshop.
{{% /notice %}}

#### 1. Save evidence

Before cleanup, export sanitized evidence for CloudFormation, CloudFront/WAF, ALB target health, ASG instances, VPC endpoints, queues/DLQs, DynamoDB, S3, CloudWatch, SNS, Backup, Budgets, API responses, and browser tests.

#### 2. Handle outstanding operations

The July 16 audit identified three visible messages in the image-processing DLQ. Inspect and triage these messages before destroying the stack so the report documents failure causes and remediation decisions. Do not publish article content from failed messages.

#### 3. Destroy CDK stack

```bash
cd ~/Code/Technology-News-Collection-and-Summarization-System
AWS_PROFILE=cloudbrief-workshop AWS_REGION=us-east-1 \
  bun run cdk destroy
```

This is a destructive operation and requires explicit approval at execution time.

#### 4. Handle retained data

If CDK intentionally retains versioned S3 objects, backup recovery points, or other durable data, decide whether each item will be kept as evidence or deleted. Emptying a versioned bucket requires deleting both object versions and delete markers.

#### 5. Verify cleanup read-only

Confirm expected resources no longer exist:

- CloudFormation stack, CloudFront distribution, and WAF Web ACL.
- ALB, target group, ASG, EC2 instance, EBS volume, and NAT Gateway.
- VPC endpoint, SQS queue/DLQ, DynamoDB table, and S3 bucket.
- CloudWatch alarm/log group, SNS topic, Backup resource, and project budget.

#### Current status

Cleanup is **pending** because CloudBrief is still an active production demo. Reports must not claim successful cleanup until destroy is approved, executed, and verified.