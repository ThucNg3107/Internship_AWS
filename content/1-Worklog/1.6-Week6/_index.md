---
title: "Week 6 Worklog"
date: 2026-05-22
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---
### Week 6 Objectives:

* Construct a Serverless Data Lake architecture and real-time data processing pipelines integrating S3, Kinesis, Athena, and QuickSight.
* Leverage ETL transformation services with AWS Glue and EMR, loading processed data into enterprise data warehouses on Amazon Redshift.
* Implement a distributed Publisher/Subscriber messaging topology using Amazon SNS and SQS.
* Develop serverless solutions with AWS Lambda (automated image processing via S3 triggers, optimized via Lambda Layers) and Amazon DynamoDB integration (CRUD operations, IAM security, X-Ray tracing).

### Tasks to be carried out this week:
#### Week 6 (From 22/05/2026 – 28/05/2026)
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Design end-to-end serverless data lake architecture. <br> - Construct centralized data ingestion pipelines on Amazon S3. <br> - Integrate Amazon Kinesis for real-time data streaming. <br> - Analyze streaming data in real time using Amazon Kinesis Data Analytics. <br> - Perform ad-hoc data queries using Amazon Athena and visualize insights with Amazon QuickSight dashboards. | 22/05/2026 | 22/05/2026 | |
| 3 | - Automate schema discovery and cataloging with AWS Glue Crawlers. <br> - Build ETL data transformation pipelines. <br> - Execute interactive ETL notebook sessions in AWS Glue Studio using Glue Interactive Sessions. <br> - Run and monitor Glue ETL jobs from the Glue Studio console. <br> - Clean and prepare datasets visually with Glue DataBrew. <br> - Execute distributed Spark transformation jobs on Amazon EMR clusters. <br> - Load transformed data into Amazon Redshift from AWS Glue. <br> - Study architectural design best practices for Amazon Redshift data warehouses. | 23/05/2026 | 23/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Study operational mechanics of Amazon SNS (notification service) and Amazon SQS (message queuing). <br> - Implement Pub/Sub topologies and configure Subscription Filter Policies for automated message routing. <br>&emsp; + Provision a dedicated SQS queue for EU regional orders. <br>&emsp; + Subscribe the SQS queue to the Order SNS Topic. <br>&emsp; + Configure subscription filter policies based on `location = eu-west` attributes to route EU messages exclusively. | 24/05/2026 | 24/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Master Serverless Architecture principles, core components (Lambda, S3, DynamoDB), and pattern use cases. <br>&emsp; + Provision and tune Lambda function parameters (runtime, memory, timeout). <br>&emsp; + Configure S3 Event Triggers to automate image processing upon S3 bucket uploads. <br>&emsp; + Leverage Lambda Layers to package external dependencies (Sharp/Jimp for Node.js, Pillow for Python) for image resizing. <br>&emsp; + Apply security best practices (least-privilege IAM Roles) and performance/cost optimizations. | 25/05/2026 | 25/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | <br>&emsp; + Provision DynamoDB tables with optimized Partition and Sort key schemas. <br>&emsp; + Configure IAM roles and policies enabling secure Lambda-DynamoDB interaction. <br>&emsp; + Execute programmatic CRUD operations via DynamoDB SDK within Lambda code. <br>&emsp; + Inspect and analyze application logs in CloudWatch Logs. <br>&emsp; + Monitor key execution metrics (Invocations, Duration, Errors, Throttles) in CloudWatch Metrics. <br>&emsp; + Configure AWS X-Ray distributed tracing for end-to-end request visibility. | 26/05/2026 | 26/05/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 6 Achievements:

* **Serverless Data Lake Architecture & Data Querying:**
  * Designed and successfully built data processing pipelines storing raw and processed data on Amazon S3.
  * Integrated Amazon Kinesis and Kinesis Data Analytics to ingest and analyze real-time streaming data streams.
  * Leveraged Amazon Athena to query data in-place on S3 and visualized metrics via Amazon QuickSight.

* **ETL Automation with AWS Glue & Redshift:**
  * Utilized AWS Glue Crawlers to automatically scan and catalog data schemas in S3.
  * Built and executed ETL jobs using Glue Studio and interactive Spark scripts on Amazon EMR.
  * Cleaned datasets with Glue DataBrew and loaded transformed records into Amazon Redshift data warehouses.

* **Messaging & Pub/Sub Model:**
  * Mastered operational mechanics and architectural patterns of Amazon SNS and SQS.
  * Implemented Pub/Sub messaging and configured Subscription Filter Policies for precise attribute-based message routing.

* **Serverless Architecture with Lambda & DynamoDB:**
  * Developed serverless solutions using AWS Lambda, configuring S3 Event Triggers for automated image processing.
  * Leveraged Lambda Layers to package heavy image manipulation dependencies (Sharp, Pillow), optimizing deployment artifact sizes.
  * Designed DynamoDB tables with optimal Partition and Sort key schemas.
  * Enforced least-privilege IAM security controls and executed programmatic CRUD operations via AWS SDK.
  * Monitored and debugged serverless request flows using CloudWatch Logs, Metrics, and AWS X-Ray distributed tracing.
