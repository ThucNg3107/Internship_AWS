---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# AI-POWERED DATA EXTRACTION & SUMMARIZATION PLATFORM

### Group Project: Automated Data Collection and Summarization Solution using AWS & Amazon Bedrock

### 1. Executive Summary
The "AI-Powered Data Extraction & Summarization Platform" is designed and developed by our team to solve the problem of automatically collecting, extracting, and summarizing large volumes of data from external APIs. Instead of time-consuming manual processing, the platform leverages the power of Amazon Bedrock (Generative AI) combined with a highly scalable AWS architecture (EC2 Auto Scaling, SQS, EventBridge) to process data periodically in a fully automated, secure, and cost-optimized manner.

### 2. Problem Statement
*Current Problem*  
Currently, collecting information from external APIs and summarizing content is done manually or through separate, disjointed scripts. This leads to instability, difficulty in scaling as data volume grows, and consumes a lot of time for personnel to read and analyze data.

*Our Solution*  
Our team proposes a fully automated system on AWS. The user interface is distributed via CloudFront. The data processing backend runs on EC2 instances (located in Private Subnets for security) managed by an Auto Scaling Group. The data collection and processing workflow is automatically scheduled every 8 hours by EventBridge and SQS. The core strength of the solution is the integration of Amazon Bedrock to automatically read, clean, and summarize data using AI. The results are persistently stored on S3 and DynamoDB.

*Benefits and Return on Investment (ROI)*  
The solution achieves 100% automation of the periodic data collection and reporting process, saving dozens of working hours per week for the analysis team. By using Auto Scaling and resource constraints, the system optimizes operational costs as resources are only allocated when data processing tasks are active.

### 3. Solution Architecture and Execution Flow
The architecture of the project is designed by our team to comply with security standards and high availability on AWS. It ensures that the data flow is processed in a closed and secure loop.

![CloudBrief Architecture](/images/2-Proposal/cloudbrief.png)

*Detailed Execution Flow:*
1. **User Interface (Frontend)**: Users access the application through **CloudFront** (protected by **AWS WAF**). CloudFront securely distributes static content from an **S3 bucket (frontend, private, versioned)** using **OAC (Origin Access Control)** with configured behaviors.
2. **Trigger Automation**: **EventBridge Trigger** is configured to fire every **8 hours**, sending messages to the **SQS** queue to start the data extraction process.
3. **Compute Network**: The system utilizes an **Auto Scaling Group** to manage **EC2 Workers**. These instances are distributed across **Private Subnets (A and B)** (with no Public IPs) to ensure security. These Workers continuously pull jobs from the queue via the **SQS VPC Endpoint**.
4. **Data Collection (Outbound Traffic)**: To retrieve data from the **External API**, **EC2 Workers** connect to the internet through a **NAT Gateway** (placed in the Public Subnet) and exit via the **Internet Gateway**.
5. **Generative AI Integration**: After retrieving the data, the **EC2 Worker** pushes the content to **Amazon Bedrock** via the **Bedrock VPC Endpoint** for the AI language model to perform information extraction and summarization.
6. **Secure Result Storage**:
   * Cleaned text data is pushed directly to the **S3 bucket** by the Worker via the **S3 Gateway Endpoint**.
   * Structured metadata is saved to **DynamoDB** via the **DynamoDB VPC Endpoint**. This database is configured with automatic Backup.
   * Status messages or advanced failed jobs can be pushed to the **SQS Summarize** queue also via the **SQS Endpoint**.
7. **Monitoring & Alerting**:
   * **EC2 Workers** are managed via **Systems Manager (Session Manager - SSM)**, requiring no open SSH ports.
   * All logs and metrics are collected by **CloudWatch**.
   * If the system detects abnormalities exceeding thresholds (**CloudWatch Alarm**), a notification is sent via **SNS Topic** to the **Admin's Email**.
8. **Security and Cost**:
   * Uses **Security Groups** and **IAM Roles** for ASG with the principle of least privilege (least scoped).
   * Configures **AWS Budgets** to automatically send email alerts when system costs exceed control limits.

### 4. Technical Implementation
Team's implementation phases:
* **Phase 1 (Design & Initialization)**: Build the foundational VPC network with full Public/Private Subnets and NAT Gateway. Setup secure S3 Frontend via CloudFront and WAF.
* **Phase 2 (AI Integration & Scheduling)**: Configure Auto Scaling Group for EC2 Workers. Build EventBridge and SQS schedule. Develop source code for EC2 Workers calling External API and Amazon Bedrock.
* **Phase 3 (Internal Storage)**: Setup VPC Endpoints (S3, DynamoDB, SQS, Bedrock) to ensure traffic does not traverse the public internet. Create corresponding DynamoDB tables and S3 buckets.
* **Phase 4 (Monitoring & Completion)**: Integrate CloudWatch, SNS, Systems Manager. Review and test IAM Roles and Security Groups for project acceptance.

### 5. Timeline & Milestones
* **Week 10**:
  * *Architecture Design & Foundation*: Agree on the overall architecture diagram, set up the VPC network (Public/Private Subnets, NAT Gateway, Internet Gateway), and basic security infrastructure (Security Groups, IAM Roles).
  * *Core Logic Development*: Write source code (Node.js/Python) for the data collection worker (Collector Worker) and design the DynamoDB table structure to store metadata. Perform initial integration testing with Amazon Bedrock via SDK.
* **Week 11**:
  * *Automation & Integration*: Configure EC2 Auto Scaling Group combined with Launch Templates. Set up EventBridge to automatically trigger the process on a schedule (cron job) and use SQS as a fault-tolerant message queue between workers.
  * *Internal Network Security*: Set up and verify traffic flow through VPC Endpoints (S3, DynamoDB, SQS, Bedrock) to ensure no data is transmitted over the public internet.
* **Week 12**:
  * *Frontend & Content Delivery*: Deploy the static user interface to Amazon S3 and configure CloudFront (OAC) with AWS WAF for protection and page load speed optimization.
  * *Monitoring & Completion*: Configure CloudWatch Dashboard to track system performance, set up SNS to send email alerts on issues. Conduct security testing (internal penetration testing) and prepare slides to present the group project's final results.

### 6. Budget Estimation
You can view the detailed calculation sheet on [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=621f38b12a1ef026842ba2ddfe46ff936ed4ab01).

*Infrastructure Costs (AWS Services)*
* **Amazon EC2 (t4g.small)**: ~6.00 USD/month (running Auto Scaling, estimated part-time operation).
* **NAT Gateway & Data Transfer**: ~15.00 USD/month (for Worker calling External API).
* **Amazon Bedrock (Nova Lite)**: ~2.50 USD/month (estimated tokens for summarizing text).
* **Amazon S3**: ~0.15 USD/month (storing static frontend and content files).
* **Amazon DynamoDB**: 0.00 USD/month (within Free Tier limits).
* **Amazon SQS & EventBridge**: 0.00 USD/month (within Free Tier limits).
* **Amazon CloudFront & WAF**: ~5.00 USD/month (WAF WebACL maintenance fee, CloudFront is within Free Tier).

**Total Estimated Cost**: ~28.65 USD/month

### 7. Risk Assessment and Contingency Plan
* **Connection Error or Structure Change from External API**: External APIs may encounter rate limit errors or sudden JSON structure changes.
  * *Contingency*: Implement Exponential Backoff & Retry mechanisms in the Worker code. Use SQS Dead-Letter Queue (DLQ) to store failed requests, allowing reprocessing after engineers fix the API structure issue.
* **Unexpected Costs from Amazon Bedrock & NAT Gateway**: Since Bedrock charges per token and NAT Gateway charges hourly/by data volume, Workers falling into an infinite loop can cause substantial financial damage.
  * *Contingency*: Set strict thresholds in AWS Budgets to alert the team immediately via email/SMS if costs reach 50%, 80%, and 100% of the budget limit (e.g., $30/month).
* **Server Security Risk & Data Leak**: Hackers could scan and attack EC2 instances if ports are open to the internet.
  * *Contingency*: Never assign Public IPs to EC2 (place them in Private Subnets). Only access and manage servers via AWS Systems Manager (Session Manager). Use IAM Roles with least privilege.
* **Data Loss during Processing**: Hardware or software failures causing an EC2 Worker to crash while analyzing an article.
  * *Contingency*: SQS has a Visibility Timeout locking mechanism. If an EC2 instance crashes before deleting the message, the message will reappear in the queue for another EC2 Worker (created by Auto Scaling) to process, ensuring data integrity.

### 8. Expected Outcomes
The team's AWS architecture project expects to achieve comprehensive goals in terms of both technology and operational efficiency:
* **Fully Automated Workflow**: Convert manual information collection and summarization processes into a 100% automated system. Save up to 80% of daily data processing time for business analysis teams.
* **High Scalability**: Through EC2 Auto Scaling and SQS integration, the system can handle sudden spikes in text processing demands and automatically scale down when idle to maximize cost savings.
* **GenAI in Practice**: Successfully harness the power of Amazon Bedrock (Nova Lite/Claude) to read and condense thousands of pages of documents into brief, accurate summaries with low latency.
* **Enterprise-Grade Security**: The VPC network is designed to standard specifications with Private Subnets, VPC Endpoints, S3/DynamoDB data encryption, and Frontend protection using CloudFront + WAF. This solution is not just for a group assignment but can be fully utilized as a highly reliable SaaS product in real-world environments.