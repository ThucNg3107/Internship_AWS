---
title : "Verify network and compute"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.4.1 </b> "
---

Use read-only AWS CLI so the verification process does not alter deployment.

#### Stack and compute

```bash
aws cloudformation describe-stacks --profile cloudbrief-workshop \
  --region us-east-1 --stack-name cloudbrief-dev

aws autoscaling describe-auto-scaling-groups \
  --profile cloudbrief-workshop --region us-east-1

aws ec2 describe-instances --profile cloudbrief-workshop \
  --region us-east-1
```

Verification results on July 16, 2026:

- CloudFormation status: `UPDATE_COMPLETE`.
- Auto Scaling desired/min/max capacity: `2/2/2` across two Availability Zones.
- Two EC2 instances running, both using private IP only.
- One active internet-facing Application Load Balancer.

#### Network path

```bash
aws ec2 describe-nat-gateways --profile cloudbrief-workshop \
  --region us-east-1
aws ec2 describe-vpc-endpoints --profile cloudbrief-workshop \
  --region us-east-1
```

Verification results:

- One NAT Gateway available for traffic to external publishers.
- Two interface endpoints available for SQS and Bedrock Runtime.
- Two gateway endpoints available for S3 and DynamoDB.

This isolation allows workers to access public RSS/articles while traffic to AWS managed services stays inside the AWS network.
