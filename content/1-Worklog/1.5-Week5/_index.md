---
title: "Week 5 Worklog"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---
### Week 5 Objectives:

* Utilize AWS Systems Manager Session Manager for secure, centralized remote server administration.
* Optimize application response times and throughput using Amazon ElastiCache (Redis) distributed in-memory data stores.
* Standardize resource governance and monitor cloud service quota limits via AWS Service Quotas console.
* Provision Managed Red Hat OpenShift clusters on AWS (ROSA), deploy containerized workloads, and automate CI/CD release pipelines.

### Tasks to be carried out this week:
#### Week 5 (From 15/05/2026 – 21/05/2026)
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Study secure server administration using AWS Systems Manager Session Manager, eliminating inbound SSH port exposure, Bastion hosts, or manual SSH key management. <br> - Evaluate Session Manager's role in security compliance, centralized IAM access control, and comprehensive audit logging of active sessions and command histories. <br> - Understand core advantages: zero public IP internet exposure, instant single-click server connectivity. <br> - Leverage cross-platform support (Linux, Windows, macOS) to enforce flexible user authorization | 15/05/2026 | 15/05/2026 | |
| 3 | - Study Amazon ElastiCache architecture for provisioning, managing, and scaling distributed in-memory caching layers. <br> - Explore advanced ElastiCache for Redis capabilities including automatic node failover, data sharding, Multi-AZ deployment flexibility, and seamless integration with EC2, CloudWatch, SNS, and CloudTrail. <br> - Master core ElastiCache components: <br>&emsp; - Clusters: Collections of Redis cache nodes providing compute and memory tiering (Standard or Memory-Optimized) operating within VPC boundaries | 16/05/2026 | 16/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Leverage central AWS Service Quotas interfaces to view and manage cloud service resource limits. <br> - Understand service quotas as upper bounds on resource allocations or API actions permitted within an AWS account. <br> - Recognize AWS default quota settings across cloud services. <br> - Practice looking up active quotas and submitting quota increase requests via console | 17/05/2026 | 17/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Install ROSA management toolsets: AWS CLI, ROSA CLI, OpenShift CLI (oc), and configure required IAM roles. <br> - Provision and configure Managed Red Hat OpenShift clusters on AWS (ROSA). <br> - Package and deploy containerized applications onto ROSA clusters. <br> - Automate CI/CD workflows on ROSA utilizing AWS CodePipeline, CodeCommit, and CodeBuild | 18/05/2026 | 18/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Inspect and monitor application health and cluster status using OpenShift Web Console. <br> - Execute complete teardown scripts for provisioned assets (ROSA cluster, IAM roles, VPC resources) to prevent unwanted charges | 19/05/2026 | 19/05/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 5 Achievements:

* **Server Management & Security (Systems Manager Session Manager):**
  * Mastered secure server management with Session Manager, removing inbound SSH port requirements and Bastion host overhead.
  * Centralized IAM authorization boundaries and recorded complete audit session histories.

* **Caching & Performance Optimization (Amazon ElastiCache):**
  * Understood ElastiCache for Redis architecture (Clusters, Nodes, Shards, Multi-AZ).
  * Mastered in-memory caching setups and automatic failover configurations to reduce application response latency.

* **Resource & Limit Management (AWS Service Quotas):**
  * Managed and requested service quota limit increases proactively from a centralized interface.

* **Container Deployment & CI/CD on AWS ROSA (Red Hat OpenShift on AWS):**
  * Installed and standardized toolchain environments with AWS CLI, ROSA CLI, and OpenShift CLI (oc).
  * Successfully initialized and operated Red Hat OpenShift clusters on AWS (ROSA).
  * Deployed containerized applications to ROSA Clusters with high availability.
  * Constructed fully automated CI/CD release pipelines using AWS CodeCommit, CodeBuild, and CodePipeline.
  * Executed thorough teardown procedures for clusters and IAM roles to prevent unexpected cloud charges.
