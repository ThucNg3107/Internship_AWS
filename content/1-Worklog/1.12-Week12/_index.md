---
title: "Week 12 Worklog"
date: 2026-07-03
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---
### Week 12 Objectives:

* Review, standardize, and optimize all internship report documentation compiled across the preceding 11 weeks.
* Resolve formatting discrepancies, custom CSS rendering, and Vietnamese UTF-8 character encoding issues on the Hugo static engine.
* Bundle, compile, and deploy the production Hugo static site deployment package.
* Consolidate internship technical outcomes and author presentation slide decks for the internship defense evaluation.
* Conduct deep-dive analysis of AWS cloud services comprising the **CloudBrief** system architecture.
* Redraw and finalize overall system architecture workflow diagrams reflecting production infrastructure states accurately.
* Identify architectural bottlenecks and articulate future optimization proposals for project documentation.

### Tasks to be carried out this week:
#### Week 12 (From 03/07/2026 – 09/07/2026)
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - **Deep-dive analysis of AWS services within CloudBrief architecture**: <br>&emsp; + Amazon EC2 (`t4g.small` ARM64): Instance lifecycle, Auto Scaling groups, Security Groups, IAM Role bindings. <br>&emsp; + Amazon S3: Static website hosting, Bucket Policies, Versioning, and Lifecycle rules. <br>&emsp; + Amazon SQS: Standard vs FIFO queue mechanics, Visibility Timeout, Dead-Letter Queue (DLQ) setups. <br>&emsp; + Amazon DynamoDB: NoSQL schema design, Partition/Sort key strategies, TTL, On-Demand vs Provisioned capacity. <br>&emsp; + Amazon Bedrock: Model invocation (Nova Lite), prompt engineering, token limits, and Throttling management. <br>&emsp; + Amazon CloudFront: Distribution configs, Cache Behaviors, Origin Access Control (OAC), and Custom Secret Headers | 03/07/2026 | 03/07/2026 | |
| 3 | - **Redraw CloudBrief project system workflow diagrams**: <br>&emsp; + Map end-to-end data pipeline flow: RSS Feed &rarr; Collector Worker &rarr; SQS &rarr; Content Worker &rarr; S3 &rarr; Summarizer Worker &rarr; DynamoDB &rarr; Frontend. <br>&emsp; + Position Amazon CloudFront as the single public ingress serving static frontend (S3) and APIs (EC2). <br>&emsp; + Detail IAM roles & policies authorization boundaries across services. <br>&emsp; + Standardize exception handling branches: DLQ for SQS, Exponential Backoff retry logic when Bedrock throttles. <br>&emsp; + Clearly demarcate Public vs Private subnet network boundaries. <br>&emsp; + Synchronize architecture documentation matching newly updated diagrams | 04/07/2026 | 04/07/2026 | |
| 4 | - **Backend image processing module development**: <br>&emsp; + Research high-performance image manipulation libraries (Sharp/Jimp). <br>&emsp; + Implement secure image upload functionality to Amazon S3. <br>&emsp; + Create image processing and transformation API endpoints. <br>&emsp; + Integrate image processing workflows into main CloudBrief pipelines | 05/07/2026 | 05/07/2026 | |
| 5 | - **Backend bug resolution and performance optimization**: <br>&emsp; + Debug DynamoDB connection pooling and query exceptions. <br>&emsp; + Resolve worker execution timeouts when parsing long-form articles. <br>&emsp; + Refactor asynchronous concurrency models for SQS consumers. <br>&emsp; + Optimize API latency responses and complete exception handling frameworks | 06/07/2026 | 06/07/2026 | |
| 6 | - **Finalize system architecture diagrams**: <br>&emsp; + Incorporate Amazon EventBridge for automated worker execution scheduling. <br>&emsp; + Optimize message interaction patterns between SQS queues and Amazon Bedrock. <br>&emsp; + Add state change event triggers. <br>&emsp; + Export final system architecture diagrams for internship report inclusion | 07/07/2026 | 07/07/2026 | |

### Week 12 Achievements:

* **Deep-dive analysis of AWS services in the CloudBrief stack**, mastering design rationales:
  * **Amazon EC2** `t4g.small` (ARM64): Optimizes compute costs; runs API server and worker daemon processes efficiently.
  * **Amazon SQS (Standard Queue)**: Decouples Collector, Content, and Summarizer workers; supports retry mechanics via Visibility Timeout and Dead-Letter Queues (DLQ).
  * **Amazon DynamoDB**: Manages article records and hash deduplication; On-Demand capacity handles unpredictable RSS feed spikes smoothly.
  * **Amazon S3**: Stores cleaned `.txt` text payloads and static frontend build artifacts (served securely via CloudFront).
  * **Amazon Bedrock (Nova Lite)**: Generates automated AI summaries via `InvokeModel` APIs; managed token quotas and throttling retries.
  * **Amazon CloudFront**: Serves as the single public entry point — routing `/` to S3 (Frontend) and `/api/*` to EC2 (Backend) via Origin Secret Headers.

* **Finalized CloudBrief system workflow diagrams**:
  * End-to-end data pipeline: RSS Feeds &rarr; Collector &rarr; SQS &rarr; Content Worker &rarr; S3 + SQS &rarr; Summarizer &rarr; DynamoDB.
  * CloudFront routing: Static asset delivery from S3 and API request forwarding to EC2.
  * Enforced least-privilege IAM instance roles for EC2.
  * Exception handling pathways: DLQs for poison messages and Exponential Backoff for Bedrock API throttling.
  * Security perimeter isolation: Enclosed EC2 within private boundaries protected by CloudFront Origin Secret Headers.

* **Synchronized architecture documentation**: Updated technical docs to match the redrawn architecture diagrams, accurately reflecting service interactions and security controls.

* **Completed Backend Image Processing Module**: Integrated dedicated image manipulation libraries, releasing smooth S3 image upload APIs integrated into main pipelines.

* **Resolved Backend Outages and Bugs**: Debugged DynamoDB connection pooling issues, eliminated worker timeout exceptions, and refactored SQS consumer concurrency models for enhanced system stability.

* **Finalized Architectural Diagrams**: Integrated EventBridge automated scheduling, optimized SQS-Bedrock messaging, and exported the complete architecture diagram for defense reports.

* **Identified Future Architectural Improvements**:
  * Configure CloudWatch Alarms tracking message accumulation within Dead-Letter Queues (DLQs).
  * Enforce S3 Lifecycle Policies to automatically archive/delete legacy `.txt` files to optimize storage budgets.
