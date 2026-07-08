---
title: "Blog 3: Amazon S3 Audit Logging – Part 2: Centralized Analysis and Logging"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# Centralized Analysis and Logging of S3 Data Events in AWS CloudTrail

When a security incident occurs—such as unauthorized downloads or bulk deletion of data in an S3 bucket—the first question is always: **"Who did this?"**. Standard S3 server access logs show which requests were made, but lack IAM identity information needed to pinpoint exactly which user or role performed the action.

This post (Part 2 in the S3 audit logging series) guides you through deploying an identity-based security auditing system using **AWS CloudTrail data events** and **Amazon Athena**.

![Architecture flow diagram: From IAM User/Assumed Role through S3 API Call, Amazon S3, AWS CloudTrail, Central S3 Bucket to Amazon Athena and Security Investigator](/images/3-BlogsTranslated/cloudtrail-s3-flow.svg)

*Flow Diagram: S3 event data is captured by CloudTrail, stored in a centralized S3 bucket, and queried via Athena*

---

## S3 Data Events vs. Server Access Logs

CloudTrail data events provide API-level detail tracking for S3 object operations along with full identity information, serving as a powerful complement to standard access logs.

- **What is recorded:** Detailed IAM user/role identity, API operations (`GetObject`, `PutObject`, `DeleteObject`), authentication context (MFA, role assumption chain), and cross-account access.
- **What is not recorded:** HTTP performance metrics or exact response timestamps (these require server access logs as discussed in Part 1).
- **Latency & Cost:** Compressed JSON logs are delivered within ~5 minutes. Cost is $0.10 per 100,000 data events recorded *(Note: No free tier for data events)*.

---

## Step-by-Step Configuration

To set up centralized S3 audit logging for the entire organization:

1. **Create a CloudTrail Trail:** In the CloudTrail console, create a new trail (e.g., `s3-data-events-trail`) and point it to a central S3 bucket.
2. **Enable for the entire organization:** If using AWS Organizations, select **Enable for all accounts in my organization** from the management account to automatically apply this trail to all member accounts.
3. **Configure Advanced Event Selectors:** Uncheck management events (to avoid duplicate costs if other trails exist) and select **Data Events** with resource type **S3**. You can filter by bucket or prefix.
4. **Set up S3 Lifecycle Policy:** Configure lifecycle rules on the central bucket to move logs to **Standard-IA** after 90 days, **Glacier** after 180 days, and auto-delete after 7 years to optimize storage costs.

---

## Creating an Athena Table with Partition Projection

**Partition projection** allows Athena to dynamically calculate partition values directly from the S3 path, speeding up queries and reducing metadata scan costs. Use the statement below to create the external table:

```sql
CREATE EXTERNAL TABLE cloudtrail_s3_events (
    eventversion STRING,
    useridentity STRUCT<
        type: STRING, principalid: STRING, arn: STRING, accountid: STRING,
        username: STRING, sessioncontext: STRUCT<
            attributes: STRUCT<mfaauthenticated: STRING, creationdate: STRING>,
            sessionissuer: STRUCT<arn: STRING, accountid: STRING, username: STRING>
        >
    >,
    eventtime STRING, eventsource STRING, eventname STRING, awsregion STRING,
    sourceipaddress STRING, useragent STRING, errorcode STRING, errormessage STRING,
    requestparameters STRING, responseelements STRING, additionaleventdata STRING,
    requestaccountid STRING, sharedeventid STRING
)
PARTITIONED BY (
    account STRING,
    region STRING,
    timestamp STRING
)
ROW FORMAT SERDE 'org.apache.hive.hcatalog.data.JsonSerDe'
STORED AS INPUTFORMAT 'com.amazon.emr.cloudtrail.CloudTrailInputFormat'
OUTPUTFORMAT 'org.apache.hadoop.hive.ql.io.HiveIgnoreKeyTextOutputFormat'
LOCATION 's3://centralized-s3-cloudtrail-logs/AWSLogs/'
TBLPROPERTIES (
    'projection.enabled' = 'true',
    'projection.account.type' = 'injected',
    'projection.region.type' = 'injected',
    'projection.timestamp.type' = 'date',
    'projection.timestamp.format' = 'yyyy/MM/dd',
    'projection.timestamp.range' = '2024/01/01,NOW',
    'projection.timestamp.interval' = '1',
    'projection.timestamp.interval.unit' = 'DAYS',
    'storage.location.template' = 's3://centralized-s3-cloudtrail-logs/AWSLogs/${account}/CloudTrail/${region}/${timestamp}/'
);
```

*Note: For an Organization trail, add the `organization_id STRING` partition column first and update the `storage.location.template` accordingly.*

---

## Key Security Query Patterns

Athena tables using partition projection require you to specify the `account`, `region`, and `timestamp` partition values in the `WHERE` clause to narrow the scope of data and avoid full table scans that generate large costs.

### 1. Tracing Activity of a Specific User

Find all S3 data plane operations performed by a specific IAM user/role on a given day:

```sql
SELECT eventtime, useridentity.arn as user_arn, eventname, sourceipaddress,
    JSON_EXTRACT_SCALAR(requestparameters, '$.bucketName') as bucket,
    JSON_EXTRACT_SCALAR(requestparameters, '$.key') as object_key
FROM cloudtrail_s3_events
WHERE account = '123456789012' AND region = 'us-east-1' AND timestamp = '2026/05/15'
AND (useridentity.username = 'specific-user' OR useridentity.arn LIKE '%specific-user%')
AND eventname IN ('GetObject', 'PutObject', 'DeleteObject')
ORDER BY eventtime DESC;
```

### 2. Monitoring Cross-Account Access

Detect S3 access requests originating from external AWS accounts:

```sql
SELECT eventtime, useridentity.accountid as source_account, recipientaccountid as target_account,
    useridentity.arn as user_arn, eventname, sourceipaddress
FROM cloudtrail_s3_events
WHERE account = '123456789012' AND region = 'us-east-1' AND timestamp = '2026/05/15'
    AND useridentity.accountid != recipientaccountid
ORDER BY eventtime DESC;
```

### 3. Tracking Failed Access Attempts

List operations that encountered permission errors (`AccessDenied`, `ForbiddenKey`), helping identify unauthorized resource scanning behavior:

```sql
SELECT eventtime, useridentity.arn as user_arn, eventname, sourceipaddress, errorcode, errormessage
FROM cloudtrail_s3_events
WHERE account = '123456789012' AND region = 'us-east-1' AND timestamp = '2026/05/15'
    AND errorcode IS NOT NULL
ORDER BY eventtime DESC LIMIT 100;
```

### 4. Auditing Object Deletion Operations

Track deletion operations within a time window, recording the role and MFA authentication status:

```sql
SELECT eventtime, useridentity.arn as user_arn, sourceipaddress,
    JSON_EXTRACT_SCALAR(requestparameters, '$.bucketName') as bucket,
    JSON_EXTRACT_SCALAR(requestparameters, '$.key') as deleted_object,
    sessioncontext.attributes.mfaauthenticated as mfa_used
FROM cloudtrail_s3_events
WHERE account = '123456789012' AND region = 'us-east-1'
    AND timestamp BETWEEN '2026/05/15' AND '2026/05/27'
    AND eventname IN ('DeleteObject', 'DeleteObjects')
ORDER BY eventtime DESC;
```

---

## Best Practices & Troubleshooting

- **Prioritize Partition Filtering:** Always filter by partition columns (`account`, `region`, `timestamp`) first. Using `eventtime` to filter time will cause a full data scan, increasing costs.
- **HiveHeadObject Error:** If costs increase due to metadata operations, configure CloudTrail advanced event selectors to exclude the `HeadObject` API call.
- **Integrity and Security:** Enable log file validation to prevent tampering. Store all logs in a dedicated AWS account (Log Archive account in AWS Organization).
- **HIVE_PARTITION_SCHEMA_MISMATCH Error:** When encountering this error, verify that `storage.location.template` exactly matches the actual folder structure in S3.

---

## Conclusion

Centralizing S3 data events through CloudTrail provides rich identity and authorization context critical for security and compliance. Combined with Athena partition projection, you can conduct efficient security investigations at trillion-event scale at very low cost per operation.
