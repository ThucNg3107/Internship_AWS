---
title: "Week 9 Worklog"
date: 2026-06-12
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---
### Week 9 Objectives:

* Deploy AWS Managed Microsoft AD directory services to migrate corporate Active Directory workloads to AWS Cloud.
* Master AWS Directory Service management and perform domain joining operations for Windows Server EC2 instances.
* Architect centralized secrets management solutions using AWS Secrets Manager.
* Integrate Secrets Manager with Amazon RDS and automate database credential rotation processes.
* Deploy containerized workloads on AWS Fargate securely connecting to RDS via Secrets Manager Interface VPC Endpoints.
* Enforce secure remote access standards on AWS using Security Groups and AWS Network Firewall per CISO guidance.
* Centralize security policy governance across multi-account environments using AWS Firewall Manager, Config, Organizations, and RAM.
* Implement automated threat detection and incident remediation pipelines combining Amazon GuardDuty, EventBridge, and Lambda.

### Tasks to be carried out this week:
#### Week 9 (From 12/06/2026 – 18/06/2026)
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Research directory service architectures with AWS Directory Service. <br> - Analyze core capabilities (Multi-region replication, Trust relationships) and differences between Standard and Enterprise editions. <br>&emsp; + Provision VPC subnets meeting Directory Service networking prerequisites. <br>&emsp; + Deploy AWS Managed Microsoft AD directories. <br>&emsp; + Launch Windows Server EC2 instances and execute domain join procedures. <br>&emsp; + Install AD Administration Tools on Windows Server to manage Active Directory objects (OUs, Users, Groups) | 12/06/2026 | 12/06/2026 | |
| 3 | - Implement database credential encryption and management using AWS Secrets Manager integrated with Amazon RDS MySQL. <br> - Design secure network topologies (Private Subnets, Security Groups) connecting EC2 Bastion Hosts to private RDS MySQL databases. <br>&emsp; + Configure VPC subnets and route tables for isolated database tiers. <br>&emsp; + Provision Amazon RDS MySQL database clusters within private subnets. <br>&emsp; + Configure AWS Secrets Manager to store and manage RDS database credentials. <br>&emsp; + Launch EC2 Bastion Hosts and query RDS databases using credentials retrieved from Secrets Manager | 13/06/2026 | 13/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Automate secret rotation workflows to align with NIST CSF and AWS CAF security compliance frameworks. <br> - Integrate Amazon ECS/Fargate container workloads with RDS databases via Secrets Manager Interface VPC Endpoints. <br>&emsp; + Configure automated periodic Secret Rotation for RDS MySQL and validate via Shell Scripts. <br>&emsp; + Package container applications into Docker Images and push to Amazon ECR. <br>&emsp; + Deploy AWS Fargate containers within VPC boundaries. <br>&emsp; + Configure Fargate Task Roles and Secrets Manager Interface VPC Endpoints for secure secret retrieval and RDS database connectivity | 14/06/2026 | 14/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Review top 10 cloud security practices recommended by AWS CISO Stephan Schmidt, focusing on remote access protection. <br> - Implement network access control and perimeter firewalling using Security Groups and AWS Network Firewall. <br> - Analyze secure remote connection topology scenarios for RDP (Port 3389) and SSH (Port 22) protocols | 15/06/2026 | 15/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Implement automated threat detection and security incident auto-remediation workflows with Amazon GuardDuty. <br> - Simulate attack vectors and execute automated remediation via EventBridge Event Rules and AWS Lambda. <br>&emsp; + Provision practice environments via CloudFormation templates in `us-west-2` (Oregon). <br>&emsp; + Detect and automatically isolate compromised EC2 instances using GuardDuty, EventBridge, and Lambda. <br>&emsp; + Identify unauthorized API calls originating from leaked IAM credentials and perform manual remediation. <br>&emsp; + Detect and prevent IAM role credential exfiltration using AWS Lambda functions | 16/06/2026 | 16/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 9 Achievements:

* **AWS Managed Microsoft AD Deployment & Active Directory Administration:**
  * Understood AWS Directory Service architecture and operational mechanics for AWS Managed Microsoft AD.
  * Deployed AWS Managed Microsoft AD across multiple Availability Zones (Multi-AZ) ensuring high availability.
  * Executed domain join procedures successfully for Windows Server EC2 instances.
  * Mastered AD Administration Tools to manage Active Directory objects, including Users, Groups, and Organizational Units (OUs).

* **AWS Secrets Manager, RDS, and AWS Fargate Integration:**
  * Applied Secrets Manager security controls aligned with NIST CSF and AWS CAF framework standards.
  * Provisioned Interface VPC Endpoints for private connectivity to Secrets Manager.
  * Automated periodic database credential rotation (Secret Rotation) for RDS MySQL.
  * Containerized applications, uploaded artifacts to Amazon ECR, and executed workloads on AWS Fargate.
  * Secured database connectivity from Fargate Containers and EC2 Bastion Hosts to RDS MySQL using dynamic credential retrieval.

* **Secure Remote Access & AWS Network Firewall Integration:**
  * Applied top 10 security guidelines from AWS CISO Stephan Schmidt to harden remote access vectors.
  * Configured EC2 Security Groups and AWS Network Firewall to restrict remote traffic by IP, Port, and Protocol.
  * Established secure SSH (Port 22) and RDP (Port 3389) remote connectivity scenarios.
  * Standardized multi-account security policy management utilizing AWS Firewall Manager, Organizations, Config, and RAM.

* **Threat Detection & Auto-Remediation with Amazon GuardDuty:**
  * Configured Amazon GuardDuty to continuously scan and generate security findings for threat activities.
  * Automated incident response workflows leveraging CloudFormation, EventBridge Event Rules, and AWS Lambda.
  * Remediated compromised EC2 instances, exposed IAM credentials, and IAM role exfiltration events.
  * Applied NIST CSF and AWS CAF security lifecycle controls (Prevent, Detect, Respond).
