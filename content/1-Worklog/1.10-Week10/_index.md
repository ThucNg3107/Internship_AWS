---
title: "Week 10 Worklog"
date: 2026-06-19
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---
### Week 10 Objectives:

* Automate zero-downtime Operating System patching workflows utilizing EC2 Image Builder, Systems Manager, and CloudFormation policies.
* Master AWS Elastic Disaster Recovery (AWS DRS) architecture to establish block-level replication, non-disruptive drills, Failover, and Failback operations.
* Build real-time streaming ETL data pipelines analyzing clickstream events using Apache Flink, AWS Glue, Kinesis, and MSK.
* Practice database migration and data ingestion pipelines using AWS Database Migration Service (DMS).

### Tasks to be carried out this week:
#### Week 10 (From 19/06/2026 – 25/06/2026)
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Onboard with FCJ community members and review internship security regulations. <br> - Evaluate OS patching criticality for compliance and infrastructure security posture. <br> - Study Blue/Green deployment paradigms for automated AMI generation and replacement. <br> - Automate OS patching cycles utilizing dedicated AWS cloud services: <br>&emsp; * EC2 Image Builder: Automate image pipeline builds and AMI creation. <br>&emsp; * Systems Manager Automation Document: Orchestrate patch execution workflows. <br>&emsp; * AWS CloudFormation: Configure `AutoScalingReplacingUpdate` policies for zero-downtime rolling updates | 19/06/2026 | 19/06/2026 | |
| 3 | - Master core concepts of AWS Elastic Disaster Recovery (AWS DRS): RTO/RPO optimization, point-in-time recovery, and cost efficiency. <br> - Analyze overall AWS DRS topology: source server block-level disk replication, Replication Agent installation, replica instances within Staging Area VPCs. <br> - Provision simulated on-premises environments: Public/Private subnets, DNS resolution, and pre-installed application stacks. <br> - Standardize administrative access: SSH access to Linux hosts and RDP access to Windows Bastion Hosts | 20/06/2026 | 20/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Establish secure management connections to Windows Bastion Hosts (RDP) and Linux nodes (SSH). <br> - Install AWS Replication Agent on simulated on-premises source hosts to initiate block-level continuous data replication. <br> - Configure replication parameters on the AWS DRS console and monitor initial data sync states. <br> - Practice hands-on Disaster Recovery execution: non-disruptive testing drills, Failover execution during simulated outages, and Failback restoration to source environments | 21/06/2026 | 21/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Execute Data Engineering Immersion Day practical lab modules. <br> - Lab 1: Detect anomalous clickstream event patterns using Amazon Managed Service for Apache Flink: <br>&emsp; + Infrastructure setup: Provision S3 buckets, Kinesis Data Streams, and IAM Role policies. <br>&emsp; + Streaming ETL with Glue: Build Data Catalogs and configure real-time Glue ETL transformation jobs. <br>&emsp; + Real-time Streaming via Kinesis: Ingest simulated clickstream telemetry into Kinesis Streams. <br>&emsp; + Clickstream Analytics using MSK: Configure Amazon Managed Streaming for Apache Kafka for real-time event analytics | 22/06/2026 | 22/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Lab 2: Data Ingestion and Database Migration via AWS DMS: <br>&emsp; + Execute DMS Migration Lab: Launch Replication Instances, configure Source/Target Endpoints, and run Database Migration Tasks. <br>&emsp; + Automate lab deployment infrastructure utilizing AWS CloudFormation AutoComplete templates | 23/06/2026 | 23/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 10 Achievements:

* **Automated OS Patching:**
  * Understood OS patching governance for enterprise compliance standards.
  * Automated AMI generation pipelines using EC2 Image Builder and orchestrated execution workflows via Systems Manager Automation.
  * Implemented `AutoScalingReplacingUpdate` CloudFormation policies for zero-downtime Blue/Green AMI replacements.

* **Disaster Recovery with AWS DRS:**
  * Mastered AWS DRS architecture: installed AWS Replication Agents on source servers for continuous block-level replication to Staging Area VPCs.
  * Successfully executed Disaster Recovery lifecycle stages: non-disruptive Drills, Failover (disaster site transition), and Failback (source site restoration).

* **Real-time Clickstream Data Analytics (Data Engineering Immersion Day - Lab 1):**
  * Provisioned complete data infrastructure environments including Amazon S3, Kinesis Streams, and IAM Role policies.
  * Built real-time Streaming ETL pipelines with AWS Glue Data Catalogs and streaming Glue ETL Jobs.
  * Successfully ingested real-time clickstream streams into Amazon Kinesis.
  * Analyzed anomalous user behavior by combining Amazon MSK (Kafka) and Amazon Managed Service for Apache Flink.

* **Database Ingestion and Migration with AWS DMS (Lab 2):**
  * Mastered database migration workflows using AWS Database Migration Service (AWS DMS).
  * Provisioned Replication Instances and configured Source/Target Endpoints accurately.
  * Executed Database Migration Tasks transferring database records securely, leveraging automated CloudFormation scripts.
