---
title : "Check monitoring, queue, and operations"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.4.4 </b> "
---

#### CloudWatch and SNS

The deployed stack has alarms for Auto Scaling capacity, ALB target health and 5xx responses, EC2 CPU, all four DLQs, and Bedrock fallback. Alarm notifications publish to KMS-encrypted SNS topics.

![CloudWatch Alarms](/images/5-Workshop/5.4-S3-onprem/cloudwatch-alarms.png)

![SNS Topic](/images/5-Workshop/5.4-S3-onprem/sns-topic.png)

#### Read-only audit on July 16, 2026

| Check | Result |
| --- | --- |
| CloudWatch alarms | 9 total: 5 OK, 3 insufficient data, 1 ALARM |
| SQS queues | 8 total |
| Non-empty queues | Image-processing DLQ, 3 visible messages |
| DynamoDB | 6 CloudBrief tables |
| WAF | 1 CloudFront Web ACL |
| Budget records in account | 3 |

The Image-processing DLQ alarm is honest residual evidence, not a claim that everything is all green. It proves that the alarm path works and defines the next operational tasks: inspect failed image messages, fix retryability if needed, redrive only valid messages, and verify DLQ returns to zero. No queue mutation was executed while writing the workshop.

#### Backup and account event

AWS Backup protects durable DynamoDB tables. Notifications for account registration and admin role/status changes publish only user identifier and state; no email or display-name PII is included.

#### Budget evidence

![Budget Evidence](/images/5-Workshop/5.4-S3-onprem/budget.png)
Budget notifications act as deployment gates because ALB, NAT Gateway, interface endpoints, WAF, and two EC2 instances incur recurring costs.