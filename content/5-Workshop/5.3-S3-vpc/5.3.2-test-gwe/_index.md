---
title : "Deploy production stack"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.3.2. </b> "
---

{{% notice warning %}}
Bootstrap and deploy commands will create or update AWS resources. Only run when approved, with active budget and a rollback plan.
{{% /notice %}}

#### Step 1: Check identity and current stack

```bash
AWS_PROFILE=cloudbrief-workshop aws sts get-caller-identity
AWS_PROFILE=cloudbrief-workshop aws cloudformation describe-stacks \
  --region us-east-1 --stack-name cloudbrief-dev
```

Mask account IDs and resource identifiers before publishing output.

#### Step 2: Bootstrap CDK

```bash
AWS_PROFILE=cloudbrief-workshop AWS_REGION=us-east-1 \
  bun run cdk bootstrap
```

#### Step 3: Deploy CloudBrief

```bash
AWS_PROFILE=cloudbrief-workshop AWS_REGION=us-east-1 \
  DEMO_API_KEY='<read from protected local storage>' \
  bunx cdk deploy --require-approval never \
  -c originSecretHeaderValue='<new random value>'
```

![CDK Deploy OK](/images/5-Workshop/5.3-S3-vpc/cdk-deploy-ok.png)
Deployment creates CloudFront, WAF, private S3 origin, ALB, VPC, private Auto Scaling compute, NAT, VPC endpoints, SQS queues and DLQ, DynamoDB tables, EventBridge schedule, observability, SNS, Backup, Budgets, IAM, and Systems Manager configuration.

#### Step 4: Publish frontend

```bash
bun run --cwd frontend build
AWS_PROFILE=cloudbrief-workshop aws s3 sync \
  frontend/out s3://<frontend-bucket> --delete
AWS_PROFILE=cloudbrief-workshop aws cloudfront create-invalidation \
  --distribution-id <distribution-id> --paths '/*'
```

#### Step 5: Verify production resources (step by step)

After deployment, verify each resource using read-only AWS CLI. The images below were captured on **July 18, 2026** from the workshop account; sensitive account IDs, private IPs, and identifiers have been redacted.

Set profile before running the commands:

```bash
export AWS_PROFILE=cloudbrief-workshop
export AWS_REGION=us-east-1
```

##### 5.1 CloudFormation stack

Confirm that stack `cloudbrief-dev` is in a stable state.

```bash
aws cloudformation describe-stacks \
  --region us-east-1 \
  --stack-name cloudbrief-dev \
  --query 'Stacks[].{Name:StackName,Status:StackStatus}' \
  --output table
```

Expected: `UPDATE_COMPLETE` (or `CREATE_COMPLETE` for initial deployment).
![cli-cloudformation](/images/5-Workshop/5.3-S3-vpc/cli-cloudformation.png)

##### 5.2 EC2 workers

Two workers in private subnets, without public IP.

```bash
aws ec2 describe-instances \
  --filters Name=instance-state-name,Values=running \
  --query 'Reservations[].Instances[].[Name:Tags[?Key==`Name`]|[0].Value,State:State.Name,Type:InstanceType,PublicIp:PublicIpAddress]' \
  --output table
```

Expected: 2 instances `cloudbrief-dev-api-worker`, state `running`, `PublicIp = None`.

![cli-ec2](/images/5-Workshop/5.3-S3-vpc/cli-ec2.png)

##### 5.3 Auto Scaling group

```bash
aws autoscaling describe-auto-scaling-groups \
  --query 'AutoScalingGroups[].[Name:AutoScalingGroupName,Desired:DesiredCapacity,Min:MinSize,Max:MaxSize,Instances:length(Instances)]' \
  --output table
```

Expected: Desired / Min / Max / Instances = `2`.

![cli-asg](/images/5-Workshop/5.3-S3-vpc/cli-asg.png)

##### 5.4 Application Load Balancer

```bash
aws elbv2 describe-load-balancers \
  --query 'LoadBalancers[].[Name:LoadBalancerName,Type:Type,Scheme:Scheme,State:State.Code]' \
  --output table
```

Expected: type `application`, scheme `internet-facing`, state `active`.

![cli-alb](/images/5-Workshop/5.3-S3-vpc/cli-alb.png)

##### 5.5 NAT Gateway

Worker egress to internet (RSS, Hacker News, article fetching) via NAT.

```bash
aws ec2 describe-nat-gateways \
  --filter Name=state,Values=available \
  --query 'NatGateways[].[Id:NatGatewayId,State:State,Connectivity:ConnectivityType]' \
  --output table
```

Expected: 1 NAT `available`, connectivity `public`.

![cli-nat-gateway](/images/5-Workshop/5.3-S3-vpc/cli-nat-gateway.png)

##### 5.6 VPC endpoints (Interface + gateway)

Internal AWS traffic does not go through public internet: SQS, Bedrock (Interface), S3, DynamoDB (Gateway).

```bash
aws ec2 describe-vpc-endpoints \
  --query 'VpcEndpoints[].[Service:ServiceName,Type:VpcEndpointType,State:State]' \
  --output table
```

Expected: 4 endpoints, all `available`:

| Service | Type |
| --- | --- |
| `sqs` | Interface |
| `bedrock-runtime` | Interface |
| `dynamodb` | Gateway |
| `s3` | Gateway |

![cli-vpc-endpoints](/images/5-Workshop/5.3-S3-vpc/cli-vpc-endpoints.png)

##### 5.7 CloudFront

```bash
aws cloudfront list-distributions \
  --query 'DistributionList.Items[].{Id:Id,Status:Status,Enabled:Enabled,Origins:length(Origins.Items)}' \
  --output table
```

Expected: status `Deployed`, enabled `True`, with origins (S3 frontend + ALB + image bucket).

![cli-cloudfront](/images/5-Workshop/5.3-S3-vpc/cli-cloudfront.png)

##### 5.8 AWS WAF

```bash
aws wafv2 list-web-acls \
  --scope CLOUDFRONT \
  --query 'WebACLs[].{Name:Name}' \
  --output table
```

Expected: Web ACL attached to entry path (name prefixed with `ApiEntryWebAcl...`).

![cli-waf](/images/5-Workshop/5.3-S3-vpc/cli-waf.png)

##### 5.9 S3 buckets

```bash
aws s3api list-buckets \
  --query "Buckets[?contains(Name, 'cloudbrief')].Name" \
  --output table
```

Expected: frontend bucket, cleaned-content bucket, image bucket.

![cli-s3-bucket](/images/5-Workshop/5.3-S3-vpc/cli-s3-bucket.png)

##### 5.10 DynamoDB tables

```bash
aws dynamodb list-tables --output table
```

Expected: 6 CloudBrief tables (articles, search tokens, daily counters, dedupe, social, source runs).

![cli-dynamodb](/images/5-Workshop/5.3-S3-vpc/cli-dynamodb.png)

##### 5.11 SQS queues and DLQs

```bash
aws sqs list-queues --query 'QueueUrls' --output table
```

Expected: 4 main queues + 4 DLQs (collection, extraction, image process, summary).

![cli-sqs](/images/5-Workshop/5.3-S3-vpc/cli-sqs.png)

##### 5.12 Bedrock Nova Micro

```bash
aws bedrock list-foundation-models \
  --query "modelSummaries[?modelId=='amazon.nova-micro-v1:0'].{Id:modelId,Name:modelName}" \
  --output table
```

Expected: model `amazon.nova-micro-v1:0` appears (account is permitted to use the model).

![cli-bedrock](/images/5-Workshop/5.3-S3-vpc/cli-bedrock.png)

#### Post-Step 5 Checklist

| # | Resource | Pass condition |
| --- | --- | --- |
| 5.1 | CloudFormation | `UPDATE_COMPLETE` |
| 5.2 | EC2 | 2 running, no public IP |
| 5.3 | ASG | capacity = 2 |
| 5.4 | ALB | active, internet-facing |
| 5.5 | NAT | available |
| 5.6 | VPC endpoints | 4 available |
| 5.7 | CloudFront | Deployed |
| 5.8 | WAF | Web ACL exists |
| 5.9 | S3 | 3 cloudbrief buckets |
| 5.10 | DynamoDB | 6 tables |
| 5.11 | SQS | 8 queues (4 + 4 DLQ) |
| 5.12 | Bedrock | Nova Micro listed |
