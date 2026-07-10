---
title: "Week 8 Worklog"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---
### Week 8 Objectives:

* Understand GraphQL concepts and how AWS AppSync simplifies API creation.
* Learn how to build real-time messaging systems and APIs using AWS AppSync.
* Practice integrating AWS AppSync with Amazon DynamoDB and other data sources.
* Master CRUD operations and data querying using GraphQL schemas, resolvers, and queries/mutations.
* Understand data security and privacy using Amazon Macie to detect, monitor, and protect sensitive data in AWS environments.
* Learn how to deploy WordPress on Amazon EC2 and automate the deployment process using AWS CodeDeploy.
* Understand virtual desktop infrastructure (VDI) and how to deploy it using Amazon WorkSpaces.

### Tasks to be carried out this week:
#### Week 8 (From 05/06/2026 – 11/06/2026)
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Learn how to build a messaging system for web applications using AWS AppSync interacting with GraphQL. <br> - Study AWS AppSync operations: <br>&emsp; + Fully managed service that simplifies building flexible GraphQL APIs to securely access, manipulate, and combine data from multiple sources. <br>&emsp; + Supports building scalable GraphQL APIs, integrating with DynamoDB, Lambda, Elasticsearch, as well as HTTP/SQL/REST data sources. <br>&emsp; + Key features: offline data synchronization, real-time updates, and fine-grained access control. <br> - Practice CRUD operations (create, read, update, delete) on a DynamoDB table via AWS AppSync's GraphQL API | 05/06/2026 | 05/06/2026 | |
| 3 | - Research AWS Toolkit for Visual Studio Code <br> - Research Amazon Q <br>&emsp; + Write unit tests, generate source code, debug, troubleshoot, and optimize code. <br>&emsp; + Real-time code suggestions in 15+ languages (including CloudFormation, CDK, Terraform). <br>&emsp; + Optimize code suggestions for AWS service APIs (EC2, Lambda, S3). <br>&emsp; + Integrated security scan to detect hard-to-find vulnerabilities and suggest instant fixes | 06/06/2026 | 06/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Learn about Amazon Macie - a fully managed data security and data privacy service that uses machine learning and pattern matching to discover, monitor, and protect sensitive data in AWS. <br> - Study core features of Amazon Macie: <br>&emsp; + Automatically maintains an inventory of S3 buckets, evaluates security configurations, and generates policy findings if risks are detected. <br>&emsp; + Findings provide detailed reports on severity, affected resources, and related information. Manage findings directly on the console or via API for in-depth analysis. <br>&emsp; + Automatically sends events to Amazon EventBridge for real-time routing to Lambda/SNS, or integrates with AWS Security Hub for centralized security status management. <br>&emsp; + Integrates with AWS Organizations or sends member invitations for administrators to view bucket information, policy findings, and run sensitive data discovery jobs across multiple accounts. <br>&emsp; + Programmatically interact with Amazon Macie via Amazon Macie API, AWS CLI, or AWS SDKs | 07/06/2026 | 07/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Learn how to deploy WordPress (open-source blogging platform/CMS written in PHP and MySQL) on an EC2 instance running Amazon Linux or RHEL. <br> - Study AWS CodeDeploy - a fully automated deployment service: <br>&emsp; + Automates software deployments to services such as Amazon EC2, AWS Fargate, AWS Lambda, and on-premises servers. <br>&emsp; + Helps release new features faster, avoids downtime during deployment, and simplifies application updates. <br>&emsp; + Eliminates error-prone manual operations with automated workflows and scales according to deployment needs | 08/06/2026 | 08/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Learn about Amazon WorkSpaces - a fully managed virtual desktop infrastructure (VDI) service that enables provisioning and managing client operating systems (Windows 10/11, macOS, Ubuntu) entirely in the AWS cloud. <br> - Learn secure connection methods for end-users to access WorkSpaces: <br>&emsp; + Install Amazon WorkSpaces client application. <br>&emsp; + Connect directly through web browsers | 09/06/2026 | 09/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 8 Achievements:

* **AWS AppSync & GraphQL Integration:**
  * Mastered creating scalable and responsive GraphQL APIs using AWS AppSync.
  * Designed flexible GraphQL schemas with appropriate Queries, Mutations, and Subscriptions.
  * Connected AppSync resolvers directly to DynamoDB tables to perform secure CRUD operations.

* **Real-time & Offline Synchronization:**
  * Understood the mechanism of real-time updates using GraphQL Subscriptions.
  * Explored offline data synchronization and fine-grained access control features in AWS AppSync.

* **Amazon Macie & Data Security:**
  * Understood how Amazon Macie automates the discovery of sensitive data (PII, financial data) in S3.
  * Learned to configure sensitive data discovery jobs, custom data identifiers, and allow lists.
  * Explored S3 bucket security monitoring, policy findings, and integration with EventBridge/Security Hub.

* **WordPress Deployment & AWS CodeDeploy:**
  * Successfully deployed WordPress on an Amazon EC2 instance running Amazon Linux/RHEL.
  * Configured and used AWS CodeDeploy to automate software deployments, minimizing manual errors and managing application updates effectively.

* **Amazon WorkSpaces & Virtual Desktop Infrastructure (VDI):**
  * Explored deploying and managing secure virtual desktops (Windows, macOS, Ubuntu) in the cloud.
  * Understood secure connection options for end-users via client apps and web browsers.

