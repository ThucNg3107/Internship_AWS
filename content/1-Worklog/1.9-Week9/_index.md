---
title: "Week 9 Worklog"
date: 2026-06-12
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---
### Week 9 Objectives:

* Research and deploy AWS Managed Microsoft AD to migrate corporate Active Directory to AWS.
* Practice AWS Directory Service administration and domain joining Windows Server EC2 instances.
* Research and deploy AWS Secrets Manager credential management service.
* Integrate Secrets Manager with Amazon RDS and set up automated database credential rotation.
* Deploy applications on AWS Fargate Containers securely accessing RDS via Secrets Manager VPC Endpoints.
* Understand and apply secure remote access principles on AWS using Security Groups and AWS Network Firewall based on CISO recommendations.
* Research centralized security policy management using AWS Firewall Manager, AWS Config, AWS Organizations, and AWS Resource Access Manager (RAM).
* Study threat detection and auto-remediation using Amazon GuardDuty, EventBridge Event Rules, and AWS Lambda.

### Tasks to be carried out this week:
#### Week 9 (From 12/06/2026 – 18/06/2026)
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Research directory service solutions with AWS Directory Service. <br> - Study architecture, core features (Multi-region replication, trust relationship) and differences between Standard and Enterprise editions. <br>&emsp; + Set up VPC network infrastructure and subnets matching Directory Service requirements. <br>&emsp; + Deploy AWS Managed Microsoft AD. <br>&emsp; + Launch a Windows Server EC2 instance and perform domain join. <br>&emsp; + Install AD Administration Tools on Windows Server to manage domains (create OUs, Users, Groups). | 12/06/2026 | 12/06/2026 | |
| 3 | - Research database credential security using AWS Secrets Manager integrated with Amazon RDS. <br> - Study secure network connection architecture (VPC, private subnets, security groups) between Bastion Host and Amazon RDS MySQL (Private). <br>&emsp; + Set up VPC with required Subnets and Route Tables. <br>&emsp; + Launch Amazon RDS MySQL in private subnet. <br>&emsp; + Configure AWS Secrets Manager to store and manage RDS credentials. <br>&emsp; + Launch Amazon EC2 Bastion Host and connect to RDS using credentials retrieved from Secrets Manager. | 13/06/2026 | 13/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Research automated password rotation process to enhance security based on CSF and CAF standards. <br> - Study ECS integration to securely connect to RDS database using Secrets Manager via Interface VPC Endpoint. <br>&emsp; + Set up and activate automated Secret Rotation for RDS database and verify using Shell Scripts. <br>&emsp; + Package sample application into Docker Container and push to Amazon ECR. <br>&emsp; + Deploy AWS Fargate Container in VPC. <br>&emsp; + Configure Fargate Task Role and Secrets Manager Interface VPC Endpoint to allow Container to securely retrieve secrets and connect to RDS MySQL. | 14/06/2026 | 14/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Study security processes on AWS Cloud through the top 10 security tips from AWS CISO Stephan Schmidt, focusing on secure remote access. <br> - Research network access control and firewalls using Security Groups and AWS Network Firewall. <br> - Practice analyzing remote connection scenarios using RDP and SSH protocols. | 15/06/2026 | 15/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Learn and practice threat detection and auto-remediation with Amazon GuardDuty. <br> - Recreate attack scenarios and automate remediation using EventBridge Event Rules and AWS Lambda. <br>&emsp; + Deploy CloudFormation Template to set up practice environment in us-west-2 (Oregon). <br>&emsp; + Detect and remediate compromised EC2 instance via GuardDuty, EventBridge, and Lambda. <br>&emsp; + Identify unauthorized API calls from exposed IAM Credentials and perform manual remediation. <br>&emsp; + Detect and prevent exfiltration of IAM role credentials via AWS Lambda. | 16/06/2026 | 16/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 9 Achievements:

* **AWS Managed Microsoft AD Deployment & Active Directory Administration:**
  * Understood the concept and architecture of AWS Directory Service, specifically AWS Managed Microsoft AD.
  * Successfully deployed AWS Managed Microsoft AD running in multiple Availability Zones (AZs) for high availability.
  * Practiced domain joining Windows Server EC2 instances.
  * Installed and utilized AD Administration Tools on Windows Server to manage domains, create Users, Groups, and OUs.

* **AWS Secrets Manager, RDS, and AWS Fargate Integration:**
  * Understood the role of Secrets Manager in database security under the CSF (Prevention) and CAF (Preventative) frameworks.
  * Successfully deployed VPC Endpoint for private connection to Secrets Manager.
  * Integrated and configured automated Secret Rotation for RDS MySQL.
  * Packaged Docker application, uploaded to Amazon ECR, and ran on AWS Fargate.
  * Secured connection from Fargate container and EC2 Bastion Host to RDS by dynamically retrieving credentials from Secrets Manager.

* **Secure Remote Access & AWS Network Firewall Integration:**
  * Studied 10 key security recommendations from AWS CISO Stephan Schmidt for securing remote access.
  * Configured Amazon EC2 Security Groups and AWS Network Firewall to restrict remote access by IP, Port, and Protocol.
  * Practiced remote connection scenarios via SSH (Port 22) and RDP (Port 3389).
  * Learned central security policy management for multiple accounts using AWS Firewall Manager, Organizations, Config, and RAM.

* **Threat Detection & Auto-Remediation with Amazon GuardDuty:**
  * Configured Amazon GuardDuty to detect threats and generate security findings.
  * Recreated attack scenarios and set up auto-remediation using CloudFormation, EventBridge, and Lambda.
  * Resolved findings related to compromised EC2 instances, exposed credentials, and credential exfiltration.
  * Applied NIST CSF and AWS CAF principles for prevention, detection, and response.
