---
title : "Test real RSS and Hacker News pipeline"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.4.2 </b> "
---

#### Step 1: Verify public health route

```bash
curl -i https://d3uspkyxnd3uus.cloudfront.net/api/health
```

Verification result on July 16, 2026: HTTP `200`, project `cloudbrief`, stage `dev`, status `healthy`.

#### Step 2: Verify protected collection

When calling the admin collection route without credentials, the API must return unauthorized. A valid admin request receives RSS and Hacker News sources, then queues work through collection, extraction, summarization, and image processing.

```bash
curl -X POST https://d3uspkyxnd3uus.cloudfront.net/api/v1/collect \
  -H 'content-type: application/json' \
  -d '{"sources":["rss","hackernews"],"limit":5}'
```

Do not include real admin keys in screenshots or shell history.

#### Step 3: Read real brief

```bash
curl 'https://d3uspkyxnd3uus.cloudfront.net/api/v1/brief?limit=5'
```

Expected article contract:

```json
{
  "id": "article-id",
  "title": "Publisher title",
  "summary": "Bedrock or deterministic fallback summary",
  "canonicalUrl": "https://publisher.example/article",
  "imageUrl": "https://cloudfront.example/article-images/cover.webp"
}
```

Workers receive publisher PNG, JPEG, or WebP images, validate and convert them to WebP, upload to private S3 bucket, and store only the CloudFront URL in DynamoDB.

Live response on July 16 returned five Hacker News articles. All five have canonical publisher URLs, `SUMMARIZED` status, and processed CloudFront WebP cover URLs. One verified title is Bluesky Trademarks ATProto from the AT Protocol page.

![API Smoke OK](/images/5-Workshop/5.4-S3-onprem/api-smoke-ok.png)

#### Bedrock results

Nova Micro is configured as a low-cost model with a 256 output token limit. In recorded deployments, the AWS account hit the daily Nova token allowance. CloudBrief therefore stores a deterministic fallback summary instead of losing the article; CloudWatch displays this status.