---
title : "Verify production system"
date : 2024-01-01 
weight : 4 
chapter : false
pre : " <b> 5.4. </b> "
---

This section verifies the deployed system from infrastructure to a real article on the reader UI.

1. [Verify network and compute](5.4.1-prepare/)
2. [Test real RSS and Hacker News pipeline](5.4.2-create-interface-enpoint/)
3. [Verify public magazine and article reader](5.4.3-test-endpoint/)
4. [Check monitoring, queue, and operations](5.4.4-dns-simulation/)

#### Acceptance results

| Layer | Evidence |
| --- | --- |
| Edge | CloudFront distribution and WAF present |
| Compute | ALB active; two private EC2 managed by ASG |
| Network | NAT available; four VPC endpoints available |
| Data plane | Eight SQS queues and six DynamoDB tables |
| API | CloudFront `/api/health` and real brief endpoint responding |
| Content | Real RSS/Hacker News article, summary, cleaned text, and WebP image |
| Frontend | Magazine and article-reader load via CloudFront |
| Operations | CloudWatch alarm, SNS, Backup, and Budgets configured |
