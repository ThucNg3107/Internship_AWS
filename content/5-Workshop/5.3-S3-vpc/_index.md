---
title : "Build and deploy CloudBrief"
date : 2024-01-01 
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Deployment architecture

![CloudBrief Architecture](/images/5-Workshop/5.3-S3-vpc/cloudbrief.png)

CloudFront is the only public entry point. AWS WAF protects the distribution; S3 serves the private frontend via Origin Access Control; `/api/*` is forwarded to the internet-facing Application Load Balancer. ALB sends requests to two EC2 instances in private subnets. NAT Gateway is used to fetch external RSS feeds, Hacker News, and articles, while four VPC endpoints keep traffic to SQS, Bedrock, S3, and DynamoDB inside the AWS network.

#### Deployment chapters

1. [Build and synth local](5.3.1-create-gwe/)
2. [Deploy production stack](5.3.2-test-gwe/)

#### Verified production target

| Configuration | Verified value |
| --- | --- |
| Stack | `cloudbrief-dev` |
| Region | `us-east-1` |
| CloudFormation status | `UPDATE_COMPLETE` |
| Compute | 2 private EC2 across 2 AZs |
| Entry | CloudFront + WAF + ALB |
| Network egress | 1 NAT Gateway |
| VPC endpoints | 2 interface + 2 gateway endpoints |
| Worker queues | 4 queues + 4 DLQ |
| DynamoDB | 6 CloudBrief tables |
| Summary model | `amazon.nova-micro-v1:0`, 256 output tokens |

The above values were verified using read-only AWS CLI on July 16, 2026.