---
title : "Build and synth local"
date : 2024-01-01 
weight : 1
chapter : false
pre : " <b> 5.3.1. </b> "
---

#### Step 1: Install dependencies

```bash
cd ~/Code/Technology-News-Collection-and-Summarization-System
bun install
```

#### Step 2: Run production build

```bash
bun run build
```

![Build OK](/images/5-Workshop/5.3-S3-vpc/build-ok.png)

#### Step 3: Run regression tests

```bash
bun run test
```

![Tests OK](/images/5-Workshop/5.3-S3-vpc/tests-ok.png)

The test suite covers route validation, API-key protection, SSRF-safe fetching, collection, extraction, image processing, social actions, and infrastructure assertions.

#### Step 4: Synth CloudFormation

```bash
bun run cdk synth
```

![CDK Synth OK](/images/5-Workshop/5.3-S3-vpc/cdk-synth-ok.png)

Synth is the final local gate before deployment. This step verifies that the CDK app generates the CloudFormation template without altering AWS resources.

#### Step 5: Verify sensitive values

Before deploying, confirm that the following values come from local configuration, Keychain, or approved AWS store and are excluded from Git:

- Admin API key and hash.
- CloudFront origin header secret.
- Google OAuth client configuration.
- Notification email.
- AWS access key.