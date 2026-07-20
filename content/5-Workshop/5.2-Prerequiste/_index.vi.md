---
title : "Chuẩn bị tài khoản AWS và môi trường local"
date : 2024-01-01 
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

Phần này tuân theo cấu trúc dựa trên bằng chứng tương tự như workshop tham khảo, nhưng việc thiết lập tài khoản, công cụ, quyền và ảnh chụp màn hình bên dưới là dành cho CloudBrief.

#### 1. Quyền IAM

Người vận hành chuẩn bị tài khoản workshop phải cấp cho deployment user quyền tạo và xóa CloudBrief stack. [Tải policy JSON](/files/cloudbrief-workshop-deployer-policy.json) với tên `cloudbrief-workshop-deployer-policy.json`, hoặc lưu tài liệu bên dưới bằng tên file đó.

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
Policy này chủ đích phục vụ triển khai và sử dụng wildcard ở cấp dịch vụ vì CDK tạo các tài nguyên chưa có định danh trước khi triển khai. Chỉ sử dụng policy này trong tài khoản workshop. Đối với production, hãy triển khai qua AWS IAM Identity Center hoặc CI role, giới hạn tài nguyên và điều kiện, đồng thời tách biệt quyền triển khai khỏi quyền runtime.
{{% /notice %}}

Chạy các lệnh này bằng administrator profile hoặc account-bootstrap profile. Chúng sẽ tạo user khi chưa có, tạo hoặc sử dụng lại customer-managed policy, attach policy và hiển thị kết quả gắn cuối cùng mà không in credentials.

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

#### 2. Công cụ cần có

| Công cụ | Mục đích |
| --- | --- |
| AWS account và IAM user | Deploy và kiểm tra tài nguyên workshop |
| AWS CLI v2 | Kiểm tra identity và thu thập bằng chứng hạ tầng read-only |
| `Bun 1.3.x` | Cài monorepo, build, test và chạy scripts |
| AWS CDK v2 | Synth và deploy CloudFormation stack |
| Git | Quản lý source và bằng chứng triển khai |

Dự án deploy tại `us-east-1`. Amazon Bedrock cần cho phép model `amazon.nova-micro-v1:0`.

#### 3. Tạo IAM user riêng

Mở **IAM > Users**, sau đó chọn **Create user**.

![IAM 01](/images/5-Workshop/5.2-Prerequisite/iam-01-existing-user.png)

Nhập tên user dành riêng cho workshop. Console access là tùy chọn nếu AWS CLI là công cụ deploy chính.

![IAM 02](/images/5-Workshop/5.2-Prerequisite/iam-02-user-details.png)

Đối với lần triển khai demo ban đầu, nhóm đã tạm thời gán `AdministratorAccess` để CDK có thể tạo toàn bộ stack. Đây là bằng chứng lịch sử của workshop, không phải là khuyến nghị cho production. Tài khoản production nên sử dụng deployment role được giới hạn quyền và gỡ bỏ policy tạm thời sau khi triển khai.

![IAM 03](/images/5-Workshop/5.2-Prerequisite/iam-03-permissions.png)

Kiểm tra lại thông tin user và policy trước khi chọn **Create user**.
![IAM 04](/images/5-Workshop/5.2-Prerequisite/iam-04-review-create.png)

Xác nhận rằng user mới xuất hiện trong danh sách IAM user.
![IAM 05](/images/5-Workshop/5.2-Prerequisite/iam-05-user-created.png)

#### 4. Tạo CLI credentials

Mở tab **Security credentials** của user và chọn **Create access key**.
![IAM 06](/images/5-Workshop/5.2-Prerequisite/iam-06-security-credentials.png)

Chọn **Command Line Interface (CLI)**, xác nhận khuyến nghị và tiếp tục.
![IAM 07](/images/5-Workshop/5.2-Prerequisite/iam-07-cli-use-case.png)

Thêm description tag để key có owner và mục đích rõ ràng.
![IAM 08](/images/5-Workshop/5.2-Prerequisite/iam-08-key-description.png)

Tải CSV một lần và lưu trữ bên ngoài repository. Ảnh chụp màn hình public đã được che vì access-key ID và secret không bao giờ được xuất bản.

![IAM 09](/images/5-Workshop/5.2-Prerequisite/iam-09-key-created.png)

{{% notice warning %}}
Không bao giờ commit file credentials CSV, `backend/.env`, API key, origin secret hoặc AWS account identifier. Hãy rotate hoặc deactivate long-lived key sau workshop.
{{% /notice %}}

#### 5. Cấu hình và kiểm tra AWS CLI

```bash
aws configure --profile cloudbrief-workshop
aws sts get-caller-identity --profile cloudbrief-workshop
aws configure get region --profile cloudbrief-workshop
```

Nhập `us-east-1` làm region mặc định và `json` làm output format. Vào ngày 16 tháng 7 năm 2026, access key được cung cấp đã xác thực thành công dưới danh nghĩa dedicated CloudBrief teammate user. Account identifiers đã được xóa khỏi báo cáo.

#### 6. Chuẩn bị repository

```bash
cd ~/code/Technology-News-Collection-and-Summarization-System
bun install
cp backend/.env.example backend/.env
```

Đặt các giá trị demo local cho `DEMO_API_KEY`, `BUDGET_EMAIL`, `AWS_REGION`, `BEDROCK_REGION` và `SUMMARY_MODEL_ID`. Chỉ giữ các giá trị thực trong môi trường local hoặc kho lưu trữ cấu hình AWS được phê duyệt.

#### Checklist sẵn sàng

- **Đã tạo IAM user và CLI key.**
- **Kiểm tra AWS CLI identity thành công.**
- **Region là `us-east-1`.**
- **Bun và CDK đã sẵn sàng.**
- **Có sẵn quyền truy cập Bedrock Nova Micro.**
- **Credentials và secrets được loại trừ khỏi Git.**
