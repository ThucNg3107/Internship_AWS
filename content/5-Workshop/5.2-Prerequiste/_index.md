---
title : "Prepare the AWS account and local environment"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

This section follows the same evidence-first structure as the reference workshop, but the account setup, tools, permissions, and screenshots below are for CloudBrief.

#### 1. IAM permissions

The operator who prepares the workshop account must grant the deployment user permission to create and remove the CloudBrief stack. [Download the policy JSON](/files/cloudbrief-workshop-deployer-policy.json) as `cloudbrief-workshop-deployer-policy.json`, or save the following document with that filename.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "CloudBriefInfrastructure",
      "Effect": "Allow",
      "Action": [
        "autoscaling:*",
        "backup:*",
        "bedrock:*",
        "budgets:*",
        "cloudformation:*",
        "cloudfront:*",
        "cloudwatch:*",
        "dynamodb:*",
        "ec2:*",
        "elasticloadbalancing:*",
        "events:*",
        "kms:*",
        "logs:*",
        "s3:*",
        "sns:*",
        "sqs:*",
        "ssm:*",
        "wafv2:*"
      ],
      "Resource": "*"
    },
    {
      "Sid": "CloudBriefDeploymentRoles",
      "Effect": "Allow",
      "Action": [
        "iam:AttachRolePolicy",
        "iam:CreateInstanceProfile",
        "iam:CreatePolicy",
        "iam:CreateRole",
        "iam:DeleteInstanceProfile",
        "iam:DeletePolicy",
        "iam:DeleteRole",
        "iam:DeleteRolePolicy",
        "iam:DetachRolePolicy",
        "iam:GetInstanceProfile",
        "iam:GetPolicy",
        "iam:GetRole",
        "iam:PassRole",
        "iam:PutRolePolicy",
        "iam:RemoveRoleFromInstanceProfile",
        "iam:AddRoleToInstanceProfile",
        "iam:TagInstanceProfile",
        "iam:TagPolicy",
        "iam:TagRole",
        "iam:UntagInstanceProfile",
        "iam:UntagPolicy",
        "iam:UntagRole",
        "iam:UpdateAssumeRolePolicy",
        "sts:AssumeRole"
      ],
      "Resource": [
        "arn:aws:iam::*:role/cloudbrief-*",
        "arn:aws:iam::*:role/cdk-hnb659fds-*",
        "arn:aws:iam::*:instance-profile/cloudbrief-*",
        "arn:aws:iam::*:policy/cloudbrief-*"
      ]
    }
  ]
}
```
{{% notice warning %}}
This policy is intentionally deployment-oriented and uses service-level wildcards because CDK creates resources whose identifiers do not exist yet. Use it only in the workshop account. For production, deploy through AWS IAM Identity Center or a CI role, restrict resources and conditions, and separate deployment from runtime permissions.
{{% /notice %}}

Run these commands with an administrator or account-bootstrap profile. They create the user when absent, create or reuse the customer-managed policy, attach it, and display the final attachment without printing credentials.



```bash
ADMIN_PROFILE=cloudbrief-bootstrap-admin
DEPLOY_USER=cloudbrief-workshop
POLICY_NAME=cloudbrief-workshop-deployer
POLICY_FILE=cloudbrief-workshop-deployer-policy.json

aws iam get-user \
  --user-name "$DEPLOY_USER" \
  --profile "$ADMIN_PROFILE" >/dev/null 2>&1 || \
aws iam create-user \
  --user-name "$DEPLOY_USER" \
  --profile "$ADMIN_PROFILE"

POLICY_ARN=$(aws iam list-policies \
  --scope Local \
  --query "Policies[?PolicyName=='${POLICY_NAME}'].Arn | [0]" \
  --output text \
  --profile "$ADMIN_PROFILE")

if [ "$POLICY_ARN" = "None" ]; then
  POLICY_ARN=$(aws iam create-policy \
    --policy-name "$POLICY_NAME" \
    --policy-document "file://${POLICY_FILE}" \
    --query 'Policy.Arn' \
    --output text \
    --profile "$ADMIN_PROFILE")
fi

aws iam attach-user-policy \
  --user-name "$DEPLOY_USER" \
  --policy-arn "$POLICY_ARN" \
  --profile "$ADMIN_PROFILE"

aws iam list-attached-user-policies \
  --user-name "$DEPLOY_USER" \
  --profile "$ADMIN_PROFILE"
```

{{% notice warning %}}
This policy is intentionally intended for deployment and uses service-level wildcards because CDK needs to create resources that do not have identifiers prior to deployment. Use this policy only in workshop accounts. For production, deploy via AWS IAM Identity Center or CI roles, limit resources and conditions, and separate deployment permissions from runtime permissions.
{{% /notice %}}

#### 2. Required tools

| Tool | Purpose |
| --- | --- |
| AWS account and IAM user | Deploy and test workshop resources |
| AWS CLI v2 | Verify identity and collect read-only infrastructure evidence |
| `Bun 1.3.x` | Install monorepo, build, test, and run scripts |
| AWS CDK v2 | Synth and deploy CloudFormation stack |
| Git | Manage source code and deployment evidence |

The project is deployed in `us-east-1`. Amazon Bedrock needs access to model `amazon.nova-micro-v1:0`.

#### 3. Create a dedicated IAM user

Open **IAM > Users**, then select **Create user**.

![IAM 01](/images/5-Workshop/5.2-Prerequisite/iam-01-existing-user.png)

Enter the dedicated user name for the workshop. Console access is optional if AWS CLI is the primary deployment tool.

![IAM 02](/images/5-Workshop/5.2-Prerequisite/iam-02-user-details.png)

For the original demo deployment, the team attached `AdministratorAccess` temporarily so CDK could create the complete stack. This is historical workshop evidence, not a production recommendation. A production account should use a scoped deployment role and remove the temporary policy after deployment.

![IAM 03](/images/5-Workshop/5.2-Prerequisite/iam-03-permissions.png)

Review the user and policy details before selecting **Create user**.
![IAM 04](/images/5-Workshop/5.2-Prerequisite/iam-04-review-create.png)

Confirm that the new user appears in the IAM user list.
![IAM 05](/images/5-Workshop/5.2-Prerequisite/iam-05-user-created.png)

#### 4. Create CLI credentials

Open the user's **Security credentials** tab and select **Create access key**.
![IAM 06](/images/5-Workshop/5.2-Prerequisite/iam-06-security-credentials.png)

Select **Command Line Interface (CLI)**, acknowledge the recommendation, and continue .
![IAM 07](/images/5-Workshop/5.2-Prerequisite/iam-07-cli-use-case.png)

Add a description tag so the key has a clear owner and purpose.
![IAM 08](/images/5-Workshop/5.2-Prerequisite/iam-08-key-description.png)

Download the CSV once and store it outside the repository. The public screenshot is redacted because an access-key ID and secret must never be published.


![IAM 09](/images/5-Workshop/5.2-Prerequisite/iam-09-key-created.png)

{{% notice warning %}}
Never commit either credentials CSV, `backend/.env`, an API key, an origin secret, or an AWS account identifier. Rotate or deactivate long-lived keys after the workshop.
{{% /notice %}}

#### 5. Configure and verify the AWS CLI

```bash
aws configure --profile cloudbrief-workshop
aws sts get-caller-identity --profile cloudbrief-workshop
aws configure get region --profile cloudbrief-workshop
```

Enter `us-east-1` as the default region and `json` as the output format. On 16 July 2026, the supplied key authenticated successfully as the dedicated CloudBrief teammate user. Account identifiers were removed from the report.

#### 6. Prepare the repository

```bash
cd ~/code/Technology-News-Collection-and-Summarization-System
bun install
cp backend/.env.example backend/.env
```

Set local demo values for `DEMO_API_KEY`, `BUDGET_EMAIL`, `AWS_REGION`, `BEDROCK_REGION`, and `SUMMARY_MODEL_ID`. Keep the real values only in the local environment or approved AWS configuration stores.

#### Readiness checklist

- **IAM user and CLI key created.**
- **AWS CLI identity check succeeds.**
- **Region is `us-east-1`.**
- **Bun and CDK are available.**
- **Bedrock Nova Micro access is available.**
- **Credentials and secrets are excluded from Git.**