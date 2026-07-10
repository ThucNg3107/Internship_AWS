---
title: "Week 10 Worklog"
date: 2026-06-19
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---
### Week 10 Objectives:

* Understand the importance of OS patching and design zero-downtime automated patching (blue/green, EC2 Image Builder, Systems Manager, CloudFormation).
* Study the architecture and operations of AWS Elastic Disaster Recovery (AWS DRS) to implement replication, drills, Failover, and Failback.
* Learn real-time clickstream data processing (Streaming ETL) using Amazon Managed Service for Apache Flink, AWS Glue, Amazon Kinesis, and MSK.
* Practice database migration and data ingestion using AWS Database Migration Service (DMS).

### Tasks to be carried out this week:
#### Week 10 (From 19/06/2026 – 25/06/2026)
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Get acquainted with FCJ members <br> - Read and take note of internship unit rules and regulations <br> + Understand the importance of OS patching for security and compliance <br> + Understand Blue/Green deployment methods for AMI creation and replacement <br> + Study automated patching using AWS services: <br>&emsp; * EC2 Image Builder (automated AMI creation) <br>&emsp; * Systems Manager Automation Document (orchestration and execution) <br>&emsp; * CloudFormation with AutoScalingReplacingUpdate policy (zero-downtime deployment) | 19/06/2026 | 19/06/2026 | |
| 3 | + Study basic concepts of AWS Elastic Disaster Recovery (AWS DRS): minimizing downtime and data loss, RTO/RPO metrics, cost optimization, and point-in-time recovery. <br> + Research general AWS DRS architecture: source server disk replication, Replication Agent installation, replica servers in Staging Area VPC, and recovery target instances. <br> + Understand configuration of simulated on-premises environments: public/private subnets, DNS services, pre-installed applications. <br> + Prepare fundamental knowledge: SSH connection to Linux servers and RDP connection to Windows bastion host. | 20/06/2026 | 20/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | + Connect to Windows bastion host via RDP and Linux servers via SSH. <br> + Install AWS Replication Agent on simulated on-premises source servers for block-level data synchronization. <br> + Configure replication settings on the AWS DRS console and monitor initial data synchronization. <br> + Practice Disaster Recovery operations: running non-disruptive drills, Failover (disaster recovery transition), and Failback (restoring to source environment). | 21/06/2026 | 21/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Explore Data Engineering Immersion Day. <br> - Lab 1: Detect anomalous clickstream events using Amazon Managed Service for Apache Flink: <br>&emsp; + Environment preparation: Initialize resources (S3, Kinesis Stream, IAM Role). <br>&emsp; + Streaming ETL with Glue: Create Data Catalog, establish real-time ETL transformation jobs. <br>&emsp; + Real-time Streaming with Kinesis: Ingest simulated clickstream data into Kinesis. <br>&emsp; + Clickstream Analytics using MSK: Configure Amazon Managed Streaming for Apache Kafka to analyze events. | 22/06/2026 | 22/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Lab 2: Data Ingestion with DMS: <br>&emsp; + Practice DMS Migration Lab: Launch Replication Instance, configure Source/Target Endpoints, and run Database Migration Tasks. <br>&emsp; + Optional: Use CloudFormation to run AutoComplete DMS Lab (automation) or Skip DMS Lab if time is limited. | 23/06/2026 | 23/06/2026 | <https://cloudjourney.awsstudygroup.com/> |


### Week 10 Achievements:

* **Automated OS Patching:**
  * Understood the role of OS patching in security compliance.
  * Mastered automated AMI creation with EC2 Image Builder and orchestrated the workflow using Systems Manager Automation Documents.
  * Implemented blue/green updates using CloudFormation's AutoScalingReplacingUpdate policy for zero-downtime deployments.

* **Disaster Recovery with AWS DRS:**
  * Mastered DRS architecture: successfully installed AWS Replication Agent on source servers for block-level replication to Staging Area VPC on AWS.
  * Practiced disaster recovery workflows: conducted non-disruptive drills, Failover (transition during disaster), and Failback (restoring to source environment).

* **Real-time Data Engineering:**
  * Built a real-time clickstream analytics pipeline using Apache Flink, Glue Data Catalog, Kinesis Streams, and MSK (Kafka).

* **Database Migration with AWS DMS:**
  * Deployed a DMS Migration Lab: configured Replication Instances, Source/Target Endpoints, and executed Database Migration Tasks for data ingestion on AWS.

