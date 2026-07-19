---
title: "Week 4 Worklog"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---
### Week 4 Objectives:

* Deploy Java web application (TravelBuddy) to Elastic Beanstalk PaaS and expand understanding of AWS automated CI/CD release engineering services.
* Develop AWS Lambda functions triggered by Amazon S3 events, standardizing serverless infrastructure provisioning with SAM and CloudFormation.
* Interact with Amazon DynamoDB NoSQL databases using AWS SDK for Java, and orchestrate complex multi-step workflows with AWS Step Functions.
* Master cloud messaging paradigms, distinguishing message queues from real-time data streams, and establish a Publisher/Subscriber channel via Amazon Kinesis.

### Tasks to be carried out this week:
#### Week 4 (From 08/05/2026 – 14/05/2026)
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Practice packaging and deploying TravelBuddy Java web application to AWS Elastic Beanstalk using AWS Toolkit for Eclipse; configure EB CLI tools and leverage AWS SDK to programmatically manage application environments | 08/05/2026 | 08/05/2026 | |
| 3 | - Configure automated release pipelines: secure source code hosting with CodeCommit, automated builds via CodeBuild, deployment automation with CodeDeploy, end-to-end integration using CodePipeline, and rapid project management with CodeStar | 09/05/2026 | 09/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Deploy AWS Lambda serverless functions; customize Java Lambda source code to automate thumbnail resizing or non-image cleanup, integrating S3 Bucket event triggers. <br> - Package and automate Lambda, S3 Bucket, and Event Trigger provisioning using infrastructure templates with AWS SAM and CloudFormation. <br> - Extract microservice candidates from a monolithic codebase and construct automated CI/CD pipelines via CodeStar for Lambda-hosted microservices | 10/05/2026 | 10/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Utilize AWS SDK for Java to perform Scan and Query operations on Amazon DynamoDB tables. <br> - Optimize non-partition key attribute lookups by configuring and leveraging DynamoDB Secondary Indexes. <br> - Manually provision DynamoDB tables via console and execute data seeding scripts. <br> - Design multi-step workflow orchestration using AWS Step Functions integrated with Lambda Task Actions | 11/05/2026 | 11/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Study operational mechanics of AWS messaging architectures, analyzing core differences between Message Queues (SQS) and Data Streams (Kinesis). <br> - Programmatically publish and consume messages via browser interfaces and Java SDK. <br> - Implement Lambda event source mappings to process Amazon Kinesis data streams in real time. <br> - Construct Publisher/Subscriber messaging channels between EC2 instances via Kinesis Streams using AWS SDK for Java. <br> - Manage secure Git repositories in AWS CodeCommit and configure repository access from local IDEs and EC2 instances | 12/05/2026 | 12/05/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 4 Achievements:

* **Application Deployment & CI/CD Automation:**
  * Accumulated practical experience deploying Java applications (TravelBuddy) on AWS Elastic Beanstalk.
  * Mastered AWS specialized DevOps services (CodeCommit, CodeBuild, CodeDeploy, CodePipeline, CodeStar).
  * Controlled secure version control practices on AWS Cloud using CodeCommit Git repositories.

* **Database & Data Management:**
  * Proficiently executed NoSQL DynamoDB programmatic operations via Java SDK (Scan, Query, Secondary Indexes).

* **Serverless Computing & Workflows:**
  * Mastered serverless application patterns with AWS Lambda, SAM templates, and CloudFormation infrastructure automation.
  * Designed and executed automated multi-step state machines using AWS Step Functions integrated with Lambda tasks.

* **Messaging & Application Integration:**
  * Differentiated and flexibly applied asynchronous messaging models (Message Queues vs. Data Streams).
  * Successfully established real-time Publisher/Subscriber data streaming pipelines across EC2 instances via Amazon Kinesis.
