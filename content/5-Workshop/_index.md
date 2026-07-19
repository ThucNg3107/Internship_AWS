---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

## EC2-first technology news collection and summarization system

This workshop documents my personal implementation within the CloudBrief team project. The goal is to present a practical AWS use case from architecture, deployment, testing to resource cleanup using self-written content.

CloudBrief collects technology news from RSS feeds and Hacker News, removes duplicates, extracts clean content, summarizes with Amazon Bedrock, processes cover images to WebP, and provides a public magazine along with an authenticated reader/admin workflow.

#### Workshop content

1. [Project overview and architecture](5.1-Workshop-overview/)
2. [AWS account and local environment setup](5.2-Prerequiste/)
3. [Build and deploy CloudBrief](5.3-S3-vpc/)
4. [Verify production system](5.4-S3-onprem/)
5. [Security, cost, and architecture decisions](5.5-Policy/)
6. [Cleanup and recovery plan](5.6-Cleanup/)

#### Requirement mapping

The workshop meets the project rubric:

* Practical AWS use-case: technology news summarization dashboard.
* Uses more than 3 AWS services: WAF, CloudFront, S3, ALB, EC2 Auto Scaling, VPC, SQS, DynamoDB, Bedrock, EventBridge, CloudWatch, SNS, SSM, Backup, Budgets, and IAM.
* Includes architecture diagrams and service selection rationale.
* Includes step-by-step deployment and testing guide.
* Includes logs, metrics, alarms, cost controls, security controls, backup, and cleanup.