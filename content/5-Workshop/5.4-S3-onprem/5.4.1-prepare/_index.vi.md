---
title : "Verify network và compute"
date : 2024-01-01
weight : 1
chapter : false
pre : " <b> 5.4.1 </b> "
---

Sử dụng các lệnh AWS CLI read-only để việc kiểm tra không làm thay đổi bản triển khai.

#### Stack và compute

```bash
aws cloudformation describe-stacks --profile cloudbrief-workshop \
  --region us-east-1 --stack-name cloudbrief-dev

aws autoscaling describe-auto-scaling-groups \
  --profile cloudbrief-workshop --region us-east-1

aws ec2 describe-instances --profile cloudbrief-workshop \
  --region us-east-1
```

Verified result on 16 July 2026:

- **CloudFormation status: `UPDATE_COMPLETE`.**
- **Auto Scaling desired/min/max capacity: `2/2/2` trên hai Availability Zones.**
- **Hai EC2 instances đang chạy; cả hai chỉ sử dụng địa chỉ IP nội bộ (private IP).**
- **Một Application Load Balancer hướng ra internet đang hoạt động.**

#### Network path

```bash
aws ec2 describe-nat-gateways --profile cloudbrief-workshop \
  --region us-east-1
aws ec2 describe-vpc-endpoints --profile cloudbrief-workshop \
  --region us-east-1
```

Verified result:

- **Một NAT Gateway có sẵn cho lưu lượng truy cập nguồn tin bên ngoài.**
- **Hai interface endpoints có sẵn cho SQS và Bedrock Runtime.**
- **Hai gateway endpoints có sẵn cho S3 và DynamoDB.**

Sự phân tách này cho phép worker truy cập các nguồn RSS/bài viết công khai trong khi lưu lượng dịch vụ được quản lý bởi AWS vẫn nằm trên mạng nội bộ AWS.
