---
title : "Project overview and architecture"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

#### Project overview

CloudBrief is an EC2-first AWS application for collecting and summarizing technology news. The project serves students, researchers, reviewers, and dashboard users who need to track cloud, software, and security news faster.

The application collects articles from RSS feeds and Hacker News, removes duplicates, extracts clean content, summarizes using Amazon Bedrock Nova Micro or deterministic fallback, processes cover images to WebP, and provides a public magazine, article reader, reader community, along with a protected operations page.

#### Architecture diagram

![CloudBrief Architecture](/images/5-Workshop/5.1-Workshop-overview/cloudbrief.png)


#### Main data flow

1. Reader opens the AWS WAF-protected CloudFront distribution.
2. CloudFront serves private S3 frontend or forwards `/api/*` to ALB.
3. ALB distributes API traffic to two EC2 instances in private subnets.
4. EventBridge or protected admin request queues collection from RSS and Hacker News.
5. Worker extracts cleaned text, processes cover image to WebP, and queues summary via SQS.
6. Amazon Bedrock Nova Micro or deterministic fallback creates article summary.
7. DynamoDB stores article/social state; private S3 bucket stores cleaned text and processed images.
8. CloudWatch, SNS, Systems Manager, AWS Backup, Budgets, and IAM provide operations/recovery controls.

#### Personal scope

The team project is CloudBrief. My report scope is the deployable workshop section: architecture explanation, CDK deployment flow, API/dashboard testing, cost/security controls, monitoring evidence, backup evidence, and cleanup verification.