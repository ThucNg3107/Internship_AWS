---
title: "Week 4 Worklog"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---
### Week 4 Objectives:

* Deploy Java web application (TravelBuddy) to Elastic Beanstalk and study automated CI/CD services on AWS.
* Develop AWS Lambda functions triggered by S3 events, and automate serverless infrastructure with SAM and CloudFormation.
* Interact with Amazon DynamoDB database using AWS SDK for Java, and design workflows using Step Functions.
* Study messaging methods, distinguish between message queues and data streams, and build pub/sub channels via Amazon Kinesis.

### Tasks to be carried out this week:
#### Week 4 (From 08/05/2026 – 14/05/2026)
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Research how to deploy TravelBuddy web application on AWS; use AWS Toolkit for Eclipse to deploy the Java application to Elastic Beanstalk; configure AWS Elastic Beanstalk CLI; use AWS SDK to query and modify AWS environments | 08/05/2026 | 08/05/2026 | |
| 3 | - Apply configuration for automated release services: AWS CodeCommit for secure source control, AWS CodeBuild for building source code, AWS CodeDeploy for application deployment, AWS CodePipeline to integrate CodeCommit, CodeBuild, and CodeDeploy into a seamless CI/CD pipeline, and AWS CodeStar to quickly develop, build, and deploy applications on AWS | 09/05/2026 | 09/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Deploy an AWS Lambda function; modify the provided Java Lambda function to resize images to thumbnails or delete non-image files, and connect an S3 trigger to test it. <br> - Use AWS Serverless Application Model (SAM) and AWS CloudFormation templates to automate the deployment of the Lambda function, S3 trigger, and S3 bucket. <br> - Identify a candidate microservice within a monolithic codebase, and create an AWS CodeStar project to manage the CI/CD pipeline for that microservice hosted on AWS Lambda | 10/05/2026 | 10/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Use AWS SDK for Java to scan Amazon DynamoDB tables and retrieve results; use AWS SDK for Java to query Amazon DynamoDB tables for matching records. <br> - Use indexes in DynamoDB tables to perform lookups on attributes other than the partition key. <br> - Manually create DynamoDB tables via console and seed data. <br> - Create workflows using AWS Step Functions. <br> - Create AWS Lambda functions acting as Task actions for Step Functions | 11/05/2026 | 11/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Understand the operations of different messaging methods on AWS; explain the difference between queues and streams. <br> - Use AWS messaging methods from web browsers and write code using Java SDK. <br> - Learn how to read data from Amazon Kinesis streams using Lambda. <br> - Create a pub/sub communication channel between two EC2 instances via Amazon Kinesis streams using AWS SDK for Java. <br> - Learn how to create repositories in AWS CodeCommit and access them in development environments and EC2 instances | 12/05/2026 | 12/05/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 4 Achievements:

* **Application Deployment & CI/CD Automation:**
  * Gained hands-on experience deploying Java web applications (TravelBuddy) on AWS Elastic Beanstalk.
  * Mastered AWS CI/CD services (CodeCommit, CodeBuild, CodeDeploy, CodePipeline, CodeStar).
  * Mastered version control on AWS by creating Git repositories in CodeCommit and accessing them across multiple environments.

* **Database & Data Management:**
  * Used AWS SDK for Java to query and modify DynamoDB, including scanning, querying, and leveraging indexes.

* **Serverless Computing & Workflows:**
  * Mastered serverless computing with AWS Lambda, SAM, and CloudFormation, including S3 triggers.
  * Designed and executed workflows using AWS Step Functions, seamlessly integrating with Lambda.

* **Messaging & Application Integration:**
  * Studied and implemented various messaging methods on AWS, distinguishing between message queues and data streams.
  * Successfully built a pub/sub communication channel between EC2 instances using Amazon Kinesis and AWS SDK for Java.

