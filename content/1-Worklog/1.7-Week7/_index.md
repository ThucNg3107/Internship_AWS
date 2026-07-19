---
title: "Week 7 Worklog"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---
### Week 7 Objectives:

* Master serverless application architecture and deployment automation utilizing the AWS SAM framework.
* Understand centralized user identity management, authentication, and authorization mechanisms via Amazon Cognito.
* Configure secure web hosting architectures combining SSL/TLS certificates (ACM), Route 53 DNS routing, and CloudFront CDN.
* Integrate asynchronous messaging services (Amazon SQS & SNS) to decouple distributed application components.
* Establish full-stack application observability and distributed request tracing using Amazon CloudWatch and AWS X-Ray.

### Tasks to be carried out this week:
#### Week 7 (From 29/05/2026 – 04/06/2026)
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Review manual serverless application build workflows via AWS Console. <br> - Study AWS Serverless Application Model (SAM) - an open-source framework accelerating serverless application packaging and deployment. <br> - Master SAM YAML specification syntax to define Lambda functions, API Gateways, DynamoDB tables, and event source mappings. <br> - Understand SAM compilation mechanics into expanded AWS CloudFormation infrastructure stacks for automated provisioning | 29/05/2026 | 29/05/2026 | |
| 3 | - Leverage Amazon Cognito for centralized authentication, authorization, and user directory management across Web/Mobile applications. <br> - Analyze core Amazon Cognito architecture components: <br>&emsp; + User Pools: Manage user directories, registration/authentication flows (native or OAuth2 federated via Google, Facebook, Apple), and app access control. <br>&emsp; + Identity Pools: Provision temporary AWS IAM credentials to grant users authorized access to downstream AWS resources. <br> - Design architectures combining User Pools and Identity Pools for secure resource authorization | 30/05/2026 | 30/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Implement in-flight SSL/TLS traffic encryption to secure user communications with static web content hosted on Amazon S3. <br> - Master core services in secure serverless web hosting architectures: <br>&emsp; + AWS Certificate Manager (ACM): Automate creation, storage, and renewal of public/private SSL/TLS X.509 certificates. <br>&emsp; + Amazon Route 53: Highly available cloud DNS service managing Hosted Zones and routing user traffic. <br>&emsp; + Amazon CloudFront: Global CDN accelerating static and dynamic web content delivery over edge locations with enforced HTTPS. <br> - Implement Origin Access Control (OAC) to block direct public S3 bucket access, forcing all traffic through CloudFront edge nodes | 31/05/2026 | 31/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Construct asynchronous order processing workflows by integrating Amazon SQS and Amazon SNS into serverless web applications. <br> - Implement end-to-end order processing APIs: <br>&emsp; + `POST /books/order`: Publish order events to SQS Queues and broadcast messages over SNS Topics. <br>&emsp; + `GET /books/order`: Allow admin retrieval of pending SQS orders and processed DynamoDB order records. <br>&emsp; + `POST /books/order/handle`: Persist completed order state to DynamoDB and purge processed items from SQS. <br>&emsp; + `DELETE /books/order`: Remove cancelled orders from the SQS queue. <br> - Master AWS messaging paradigms: <br>&emsp; + Amazon SQS: Fully managed, durable message queuing service decoupling microservices (supporting Standard and FIFO queues). <br>&emsp; + Amazon SNS: Asynchronous Pub/Sub messaging service broadcasting messages from publishers to subscribers over topics | 01/06/2026 | 01/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Evaluate the importance of system observability in ensuring operational stability and accelerating incident response times. <br> - Master AWS observability tools: Amazon CloudWatch, AWS X-Ray, and AWS CloudTrail. <br> - Leverage Amazon CloudWatch for real-time operational monitoring: <br>&emsp; + Track infrastructure and application performance metrics. <br>&emsp; + Aggregate and store application log streams (e.g., Lambda execution logs). <br>&emsp; + Configure automated notifications reacting to system events. <br>&emsp; + Set metric alarm thresholds triggering automated remediation actions. <br> - Leverage AWS X-Ray for distributed tracing and microservice debugging: <br>&emsp; + Identify and resolve performance bottlenecks and root-cause failures. <br>&emsp; + Provide end-to-end request lifecycle visualization. <br>&emsp; + Generate Service Maps displaying inter-component dependency topologies | 02/06/2026 | 02/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 7 Achievements:

* **AWS Serverless Application Model (SAM):**
  * Mastered SAM YAML syntax to define serverless Lambda functions, API Gateway endpoints, DynamoDB schemas, and event source bindings.
  * Provisioned serverless applications successfully, understanding SAM transform compilation into native CloudFormation templates.

* **Amazon Cognito User & Identity Pools:**
  * Differentiated and applied Amazon Cognito User Pools (directory management) and Identity Pools (temporary AWS credential delegation).
  * Implemented secure authentication and authorization flows for web applications.

* **Secure Web Application Hosting:**
  * Provisioned and configured SSL/TLS certificates via AWS Certificate Manager (ACM) to enforce transport-layer security.
  * Managed DNS routing via Route 53 and optimized global static asset delivery using CloudFront CDN edge distribution.
  * Hardened S3 bucket security by enforcing Origin Access Control (OAC) to prevent direct public access.

* **Asynchronous Communication (SQS & SNS):**
  * Constructed decoupled asynchronous messaging architectures utilizing SQS message queues and SNS topics.
  * Successfully integrated order processing pipelines: API handlers writing to SQS/SNS and persisting state to DynamoDB.

* **Application Monitoring and Tracing:**
  * Mastered Amazon CloudWatch (Metrics, Logs, Events, Alarms) for serverless application observability and debugging.
  * Leveraged AWS X-Ray to establish distributed end-to-end tracing and analyze request execution lifecycles across microservices.
