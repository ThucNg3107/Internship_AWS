---
title: "Week 12 Worklog"
date: 2026-07-03
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---
### Week 12 Objectives:

* Review, standardize, and optimize all internship report content from the previous 11 weeks.
* Resolve formatting issues, custom CSS bugs, and Vietnamese UTF-8 encoding/font errors on the Hugo static site.
* Bundle, compile, and deploy the Hugo static site project.
* Summarize internship outcomes and prepare the final presentation/slides for the internship defense.
* Review and consolidate knowledge of AWS services used in the CloudBrief project.
* Redraw and complete the system workflow diagram to reflect the current architecture.
* Identify gaps or areas of improvement in the current architecture and project documentation.

### Tasks to be carried out this week:
#### Week 12 (From 03/07/2026 – 09/07/2026)
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Re-examine AWS services used in the CloudBrief project: <br>&emsp; + EC2 (`t4g.small` ARM64): Instance lifecycle, Auto Scaling, Security Groups, IAM Role association <br>&emsp; + Amazon S3: Static hosting, bucket policy, versioning, lifecycle rules <br>&emsp; + Amazon SQS: Standard vs FIFO queues, message visibility timeout, DLQ configuration <br>&emsp; + Amazon DynamoDB: Table design, partition key strategy, TTL, On-demand vs Provisioned capacity modes <br>&emsp; + Amazon Bedrock: Model invocation (Nova Lite), prompt construction, token limits, throttling management <br>&emsp; + Amazon CloudFront: Distribution configuration, cache behaviors, origin access control (OAC), custom headers | 03/07/2026 | 03/07/2026 | |
| 3 | - Redraw the system workflow diagram for the CloudBrief project: <br>&emsp; + Map out the entire data flow: RSS Feed &rarr; Collector Worker &rarr; SQS &rarr; Content Worker &rarr; S3 &rarr; Summarizer Worker &rarr; DynamoDB &rarr; Frontend <br>&emsp; + Introduce CloudFront as the single public entry point serving both static frontend (S3) and APIs (EC2) <br>&emsp; + Supplement IAM roles & policies flows between services <br>&emsp; + Add error handling flows: DLQ for SQS, retry logic when Bedrock throttles <br>&emsp; + Clearly label public vs private services <br>&emsp; + Update architecture documents to align with the redrawn diagram | 04/07/2026 | 04/07/2026 | |
| 4 | - Backend development for image processing: <br>&emsp; + Research suitable image processing libraries (Sharp, Jimp...) <br>&emsp; + Code image upload functionality to S3 <br>&emsp; + Create basic image recognition/processing APIs <br>&emsp; + Integrate the image processing flow into the main CloudBrief pipeline | 05/07/2026 | 05/07/2026 | |
| 5 | - Fix Backend bugs: <br>&emsp; + Debug DynamoDB database connection errors <br>&emsp; + Fix timeout errors when worker processes long articles <br>&emsp; + Refactor SQS consumer concurrency handling code <br>&emsp; + Optimize API response times and catch exceptions | 06/07/2026 | 06/07/2026 | |
| 6 | - Modify system architecture diagram: <br>&emsp; + Incorporate EventBridge to schedule automated worker runs <br>&emsp; + Adjust interaction flow between SQS and Bedrock <br>&emsp; + Add trigger mechanisms on state changes <br>&emsp; + Complete the final system architecture diagram for report inclusion | 07/07/2026 | 07/07/2026 | |

### Week 12 Achievements:

* **Deep dive into AWS services in the CloudBrief stack**, focusing on *why* each service was chosen:
  * **EC2** `t4g.small` (ARM64): Optimizes compute costs; runs the API server (Express/Bun) and worker processes as background daemons
  * **Amazon SQS (Standard Queue)**: Decouples the Collector, Content, and Summarizer workers - supports retries via visibility timeouts and Dead-Letter Queues (DLQ) for failed messages
  * **Amazon DynamoDB**: Stores article records and hash deduplication; On-demand mode handles unpredictable RSS collection peaks efficiently
  * **Amazon S3**: Stores cleaned text (`.txt` files written by the Content Worker) and the static frontend build (served via CloudFront)
  * **Amazon Bedrock (Nova Lite)**: Generates AI summaries via InvokeModel API; understanding token limits and throttling mechanisms is key to the retry design
  * **Amazon CloudFront**: Acts as the single public entry point - routes `/` to S3 (frontend) and `/api/*` to EC2 (backend) using cache behaviors and Origin Secret Headers

* **Redraw the CloudBrief workflow diagram**, including:
  * End-to-end data pipeline: RSS Feeds &rarr; Collector &rarr; SQS &rarr; Content Worker &rarr; S3 + SQS &rarr; Summarizer &rarr; DynamoDB
  * CloudFront routing: static assets from S3 and API request forwarding to EC2
  * IAM role assignment: EC2 instance role with restricted permissions for S3, SQS, DynamoDB, and Bedrock
  * Error handling branches: DLQ for failed messages, exponential backoff for Bedrock throttling
  * Security boundary: EC2 is not public, protected by Origin Secret Headers via CloudFront

* **Update architecture documentation** to match the redrawn diagram, ensuring precise description of all service interactions and security configurations.

* **Complete backend image processing:** Successfully researched and integrated the image processing library, creating APIs to recognize and upload images to S3 smoothly within the current pipeline.

* **Resolve backend bugs thoroughly:** Debugged DynamoDB connection issues, handled worker timeouts, and refactored SQS consumer concurrency, leading to optimized API response times and overall system stability.

* **Finalize system flow diagrams:** Adjusted and added EventBridge components, optimized the SQS-Bedrock interaction flow, and completed the architectural diagram for the final presentation and report.

* **Identify potential improvements in the current architecture:**
  * Configure CloudWatch Alarms for the number of messages in the DLQ
  * Evaluate S3 lifecycle policies to optimize the storage cost of old `.txt` files
  * ...
