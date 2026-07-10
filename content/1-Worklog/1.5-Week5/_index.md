---
title: "Week 5 Worklog"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---
### Week 5 Objectives:

* Learn and use AWS Systems Manager Session Manager for secure server management.
* Study Amazon ElastiCache (Redis) service to improve caching/in-memory storage performance.
* Understand and manage service limits using AWS Service Quotas.
* Install tools, initialize and deploy applications, and build CI/CD pipelines on OpenShift clusters (ROSA).

### Tasks to be carried out this week:
#### Week 5 (From 15/05/2026 – 21/05/2026)
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Learn about Session Manager under AWS Systems Manager to securely manage servers without opening SSH ports, using Bastion Hosts, or managing SSH keys. <br> - Understand how Session Manager simplifies compliance with security policies, centralizes access control using AWS IAM, and logs connection sessions and executed commands. <br> - Understand key benefits: configuring connection without exposing to the internet, quick and simple access to servers with a single click. <br> - Leverage cross-platform support (Linux, Windows, MacOS) of Session Manager to grant user access | 15/05/2026 | 15/05/2026 | |
| 3 | - Learn about Amazon ElastiCache to easily set up, manage, and scale distributed in-memory data stores or cache environments. <br> - Explore features of ElastiCache for Redis such as automatic failover and node recovery, sharding, flexible Availability Zone placement, and integration with other AWS services (EC2, CloudWatch, SNS, CloudTrail). <br> - Master the architecture and components of ElastiCache: <br>&emsp; - Clusters: Basic collections of cache nodes running Redis, providing compute and data hierarchy, with standard or memory-optimized node types running within a VPC | 16/05/2026 | 16/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | - Learn about AWS Service Quotas to view and manage limits for AWS services from a central interface. <br> - Understand that quotas (service limits) are the maximum resource values or actions allowed for specific resources within an AWS account. <br> - Note that each AWS service defines and sets default values for these quotas. <br> - Learn how to look up current quotas and submit limit increase requests via Service Quotas | 17/05/2026 | 17/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | - Install required tools for ROSA including AWS CLI, ROSA CLI, OpenShift CLI (oc), and configure necessary IAM permissions. <br> - Initialize and set up OpenShift clusters on AWS (ROSA). <br> - Deploy containerized applications to the ROSA cluster. <br> - Implement and automate CI/CD workflows on ROSA using AWS CodePipeline, AWS CodeCommit, and AWS CodeBuild | 18/05/2026 | 18/05/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | - Practice inspecting and monitoring applications and OpenShift clusters using OpenShift Web Console. <br> - Perform cleanup of all created resources including ROSA cluster, IAM Roles, and related AWS resources to avoid unexpected charges | 19/05/2026 | 19/05/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 5 Achievements:

* **Server Management & Security (Systems Manager Session Manager):**
  * Understood the operation of Session Manager under AWS Systems Manager to securely connect and manage servers without opening SSH ports or using Bastion Hosts.
  * Learned how to authorize access via IAM and track/log user session histories.

* **Caching & Performance Optimization (Amazon ElastiCache):**
  * Mastered the architecture and operations of Amazon ElastiCache for Redis (Clusters, Nodes, Shards).
  * Understood how to configure, auto-failover, and scale in-memory data stores to improve application response times.

* **Resource & Limit Management (AWS Service Quotas):**
  * Learned to inspect, manage, and submit service quota increase requests for AWS resources from a central console.

* **Container Deployment & CI/CD on AWS ROSA (Red Hat OpenShift on AWS):**
  * Successfully installed required command-line tools: AWS CLI, ROSA CLI, and OpenShift CLI (oc).
  * Initialized and configured an OpenShift Cluster on AWS (ROSA).
  * Successfully deployed containerized applications to the OpenShift Cluster.
  * Established and successfully operated automated CI/CD pipelines using AWS CodeCommit (source control), AWS CodeBuild (container image compilation and deployment), and AWS CodePipeline (release pipeline orchestration).
  * Practiced resource cleanup for clusters and IAM roles to avoid unwanted charges.

