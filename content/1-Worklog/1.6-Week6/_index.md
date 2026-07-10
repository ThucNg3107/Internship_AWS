---
title: "Week 6 Worklog"
date: 2026-05-22
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---
### Week 6 Objectives:

* Build a serverless Data Lake and data processing pipeline using S3, Kinesis, Athena, and QuickSight.
* Use ETL services (AWS Glue, EMR) to transform data and load it into Amazon Redshift data warehouse.
* Set up a Pub/Sub messaging model using Amazon SNS and SQS.
* Develop serverless applications with AWS Lambda (image processing via S3 trigger, Lambda Layers) and integrate with Amazon DynamoDB (CRUD, IAM, Monitoring & Troubleshooting).

### Tasks to be carried out this week:
#### Week 6 (From 22/05/2026 – 28/05/2026)
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Design serverless data lake architecture. <br> - Build data pipeline and Data Lake using Amazon S3 for storage. <br> - Use Amazon Kinesis for real-time streaming data. <br> - Use Amazon Kinesis Data Analytics for real-time analysis. <br> - Query data with Amazon Athena and visualize with Amazon QuickSight. | 22/05/2026 | 22/05/2026 | |
| 3 | - Use AWS Glue to automatically index datasets. <br> - Transform data. <br> - Run interactive ETL scripts in a Jupyter notebook on AWS Glue Studio using AWS Glue (interactive sessions). <br> - Use Glue Studio to run and monitor Glue ETL jobs. <br> - Prep data with Glue DataBrew. <br> - Run Spark transformation job on EMR. <br> - Load data into Amazon Redshift from Glue. <br> - Introduction to Redshift design best practices. | 23/05/2026 | 23/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Learn mechanisms of Amazon SNS (Simple Notification Service) and Amazon SQS (Simple Queue Service). <br> - Implement Pub/Sub model and configure Subscription Filter Policy for automatic message routing. <br>&emsp; + Create SQS queue for EU orders. <br>&emsp; + Subscribe SQS queue to SNS Topic. <br>&emsp; + Set filter policy with location=eu-west to receive only EU messages. | 24/05/2026 | 24/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Learn Serverless Architecture: concepts, key components (Lambda, S3, DynamoDB) and use cases. <br>&emsp; + Create and configure Lambda function (runtime, memory, timeout). <br>&emsp; + Set up S3 Event Trigger to resize images upon upload. <br>&emsp; + Use Lambda Layers for Sharp/Jimp (Node.js) or Pillow (Python). <br>&emsp; + Study security best practices (minimal IAM Roles) and performance/cost optimizations. | 25/05/2026 | 25/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | <br>&emsp; + Create DynamoDB table with partition and sort keys. <br>&emsp; + Configure IAM permissions for Lambda-DynamoDB interaction. <br>&emsp; + Implement CRUD operations with DynamoDB SDK. <br>&emsp; + Analyze logs in CloudWatch Logs/Metrics, configure AWS X-Ray for request tracing. | 26/05/2026 | 26/05/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 6 Achievements:

* **Serverless Data Lake Architecture & Data Querying:**
  * Designed and successfully built a data processing pipeline using Amazon S3 for raw and processed storage.
  * Integrated Amazon Kinesis and Kinesis Data Analytics to ingest and analyze real-time streaming data.
  * Used Amazon Athena to query data directly in S3 and visualized results using Amazon QuickSight.

* **ETL Automation with AWS Glue & Redshift:**
  * Used AWS Glue Crawler to automatically scan and catalog data schemas in S3.
  * Designed and ran ETL jobs using both Glue Studio and interactive Spark scripts on EMR.
  * Cleaned and prepared data using Glue DataBrew and loaded transformed data into Amazon Redshift.

* **Messaging & Pub/Sub Model:**
  * Mastered the core concepts and differences between Amazon SNS and SQS.
  * Implemented a Pub/Sub messaging model and configured Subscription Filter Policies for accurate message routing.

* **Serverless Architecture with Lambda & DynamoDB:**
  * Developed serverless applications using AWS Lambda, configuring S3 Event Triggers for automatic image processing.
  * Utilized Lambda Layers to package image processing libraries (e.g., Sharp, Pillow) to optimize Lambda deployment package size.
  * Designed DynamoDB tables with optimal Partition Keys and Sort Keys.
  * Implemented minimal privilege access control (IAM Roles & Policies) and wrote code using AWS SDK for CRUD operations.
  * Monitored and debugged serverless systems using CloudWatch Logs, Metrics, and AWS X-Ray.
