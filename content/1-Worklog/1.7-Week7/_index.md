---
title: "Week 7 Worklog"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---
### Week 7 Objectives:

* Learn and practice building serverless applications using AWS SAM.
* Understand user authentication and authorization with Amazon Cognito.
* Configure secure web hosting using SSL certificates, Route 53, and CloudFront.
* Integrate messaging services (Amazon SQS and Amazon SNS) to decouple application components.
* Learn how to monitor and trace applications using Amazon CloudWatch and AWS X-Ray.

### Tasks to be carried out this week:
#### Week 7 (From 29/05/2026 – 04/06/2026)
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Review how to build simple serverless web applications using the AWS Console <br> - Learn about AWS Serverless Application Model (SAM) - an open-source framework to build serverless applications faster <br> - Learn SAM YAML syntax to define functions, APIs, databases, and event source mappings <br> - Understand how SAM translates and expands syntax into AWS CloudFormation to automatically provision resources | 29/05/2026 | 29/05/2026 | |
| 3 | - Learn about Amazon Cognito - a service providing authentication, authorization, and user management for web and mobile apps. <br> - Study two main components of Amazon Cognito: <br>&emsp; + User pools providing sign-up and sign-in (direct or via third parties like Facebook, Google, Apple) and application access control. <br>&emsp; + Identity pools providing temporary AWS credentials to grant users direct access to other AWS resources. <br> - Learn examples of combining User pools and Identity pools in application architectures | 30/05/2026 | 30/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Learn how to secure web applications in transit using SSL certificates to encrypt traffic between users and static websites hosted on Amazon S3 (in-flight encryption). <br> - Study core services in a secure serverless web hosting architecture: <br>&emsp; + Certificate manager to create, store, and renew public and private SSL/TLS X.509 certificates. <br>&emsp; + Route 53 DNS service to route users to resources and manage Hosted zones. <br>&emsp; + CloudFront CDN to speed up delivery of static and dynamic web content, supporting HTTPS configuration with SSL certificates. <br> - Understand the benefits of combining Amazon S3 with Amazon CloudFront, including utilizing Origin Access Control (OAC) to restrict direct S3 access | 31/05/2026 | 31/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Learn how to process user orders by integrating Amazon SQS and Amazon SNS into serverless web applications. <br> - Study order processing architectures including: <br>&emsp; + API POST /books/order ➡️ send order info to SQS queue and publish message via SNS topic. <br>&emsp; + API GET /books/order ➡️ help admin retrieve unprocessed orders from SQS and processed orders from DynamoDB. <br>&emsp; + API POST /books/order/handle ➡️ save info to DynamoDB and delete order from queue. <br>&emsp; + API DELETE /books/order ➡️ delete order from queue. <br> - Learn about AWS messaging services: <br>&emsp; + SQS secure, durable message queue to integrate and decouple distributed software components, supporting Standard and FIFO queues. <br>&emsp; + SNS Pub/Sub messaging service to asynchronously send messages from publishers to subscribers via communication topics | 01/06/2026 | 01/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Learn the importance of application monitoring and observability to ensure stability and troubleshooting capability. <br> - Learn AWS observability tools: AWS CloudWatch, AWS X-Ray, and AWS CloudTrail. <br> - Study Amazon CloudWatch to monitor resources and applications in real-time: <br>&emsp; + Collect and track performance metrics. <br>&emsp; + Collect and store log files (e.g., debugging AWS Lambda). <br>&emsp; + Send notifications in response to events. <br>&emsp; + Configure alarms to trigger specific actions. <br> - Study AWS X-Ray to analyze and debug distributed applications/microservices: <br>&emsp; + Identify and resolve performance bottlenecks and errors. <br>&emsp; + Provide end-to-end request tracing. <br>&emsp; + Visualize application component maps | 02/06/2026 | 02/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 7 Achievements:

* **AWS Serverless Application Model (SAM):**
  * Mastered SAM YAML syntax to define functions, APIs, databases, and event source mappings.
  * Successfully initialized and deployed serverless applications, understanding how SAM compiles to CloudFormation templates.

* **Amazon Cognito User & Identity Pools:**
  * Understood the roles of Amazon Cognito in managing user directories (User Pools) and providing temporary credentials (Identity Pools).
  * Implemented secure sign-up/sign-in flows for applications.

* **Secure Web Application Hosting:**
  * Created and configured SSL/TLS certificates via AWS Certificate Manager (ACM) to encrypt data in transit.
  * Routed domain traffic via Route 53 and optimized global content delivery via CloudFront.
  * Secured direct S3 bucket access by configuring Origin Access Control (OAC).

* **Asynchronous Communication (SQS & SNS):**
  * Built asynchronous message processing systems using SQS queues and SNS topics.
  * Successfully integrated order processing flows: APIs writing to SQS/SNS and persisting results to DynamoDB.

* **Application Monitoring and Tracing:**
  * Understood AWS CloudWatch (Metrics, Logs, Events, Alarms) to debug and observe serverless applications.
  * Used AWS X-Ray to establish end-to-end tracing and analyze request lifecycles across components.

