---
title: "Week 11 Worklog"
date: 2026-06-26
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---
### Week 11 Objectives:

* Clean, validate, and transform data using AWS Glue ETL and Apache Hudi on S3.
* Analyze data using Amazon Athena, visualize via QuickSight Dashboards, and research Federated query and SageMaker integration.
* Administer automated data lakes with AWS Lake Formation and prepare data using Glue DataBrew.
* Act as **API Contract QA** for the **CloudBrief** project — a serverless automated tech news aggregator on AWS.
* Write automated test suites (unit tests, integration tests) and build a **Postman** collection for demos.
* Audit security (SSRF, XXE, XSS, API Key leakage) and complete API documentation.

### Tasks to be carried out this week:
#### Week 11 (From 26/06/2026 – 02/07/2026)
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Lab 3: Transforming data with Glue: <br>&emsp; + Data Validation and ETL: Clean, validate, and transform data using AWS Glue. <br>&emsp; + Incremental Data Processing with Hudi: Apply Apache Hudi for change data processing (upsert/delete) on S3. <br> - Lab 4: Query and Visualize: <br>&emsp; + Data Analysis: Query S3 data with Amazon Athena and create a QuickSight Dashboard. <br>&emsp; + Advanced Athena: Use Federated queries for multi-source access and connect to SageMaker for predictions. | 26/06/2026 | 26/06/2026 | |
| 3 | - Lab 5: Data Lake Automation: <br>&emsp; + Lake Formation basics: Register data lake location, set up Data Catalog, and grant permissions. <br>&emsp; + Apply Lake Formation: Manage permissions for open table formats like Apache Hudi, Iceberg, and Delta Tables. <br> - Bonus Lab: Glue DataBrew: <br>&emsp; + Clean and prepare data (Data Preparation) using visual interface. | 27/06/2026 | 27/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | + Install Bun 1.3.x, run `bun install`, `bun run build`, `bun run test` successfully. <br> + Copy `backend/.env.example` -> `backend/.env`. <br> + Align with team (ReinaMacCredy, RyugaRuki) on `/api/v1/*` routes, JSON schema, and article state definitions (`PENDING_CONTENT`, `CONTENT_FAILED`, `SUMMARY_FAILED`, `SUMMARIZED`). <br> + Review `contracts/src/index.ts`, `frontend/lib/cloudbrief-mocks.ts`, `backend/src/app/routes/v1.ts`. | 28/06/2026 | 28/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | + `apiKey.test.ts`: Test SHA-256 hash, constant-time comparison, reject key missing/invalid -> 401, do not log plaintext key. <br> + `apiRoutes.test.ts`: Test 400 Bad Request, public routes do not need key, origin secret header -> reject in production mode. <br> + `apiV1Routes.test.ts`: Test all `/api/v1/*` public routes + admin session/CSRF flow. <br> + `rssClient.test.ts`: Confirm XML parser disables DTD & External Entity (XXE prevention). <br> + `dedupe.test.ts`: Test canonical URL hash & title hash, block duplicate collection. <br> + `localPayloads.test.ts`: Test state transitions & retry logic (`CONTENT_FAILED` / `SUMMARY_FAILED` -> reset; `SUMMARIZED` -> 409; exceeding `MAX_RETRY_COUNT` -> 409). <br> + Build `CloudBrief_API_Tests.postman_collection.json` with placeholders (`{{API_KEY}}`, `{{CSRF_TOKEN}}`) -> 51/51 tests pass. | 29/06/2026 | 29/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | + Run entire test suite after merge -> 53/53 tests pass. <br> + Security Audit: Verify `.env` / `cdk.context.json` are ignored, check for plaintext credentials in logs/responses. <br> + Verify SSRF prevention (DNS IP pinning, redirect limit, block internal IP/IMDS `169.254.169.254`). <br> + Verify XSS prevention (text encoding for summaries, no `innerHTML`). <br> + Verify Origin Secret Header rejects direct calls to EC2 in production. <br> + Update `docs/api.md` to match `/api/v1` implementation. | 30/06/2026 | 30/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 11 Achievements:

* **AWS Glue ETL & Apache Hudi on S3:**
  * Successfully performed Data Validation and ETL with AWS Glue; applied Apache Hudi to process change data (upsert/delete) on S3.

* **Amazon Athena & Amazon QuickSight Visualization:**
  * Queried S3 data using Amazon Athena, set up Federated queries connecting to SageMaker, and built a QuickSight Dashboard to visualize data.

* **AWS Lake Formation Data Lake Automation:**
  * Configured Lake Formation to register data lake locations, grant access permissions for Apache Hudi, Iceberg, and Delta Tables, and prepared data using Glue DataBrew.

* **Mastered CloudBrief System Architecture on AWS:**
  * EC2 (ARM64 `t4g.small`) running API server + worker processes.
  * Amazon DynamoDB storing articles and dedupe records.
  * Amazon S3 storing raw text content `.txt` and static frontend assets.
  * Amazon SQS acting as message queue between worker services.
  * Amazon Bedrock Nova Lite utilized for automated AI summaries.
  * CloudFront configured as CDN and single entry reverse proxy.

* **Wrote and Operated Automated Test Suites:**
  * Unit tests: `apiKey`, `apiRoutes`, `apiV1Routes`, `rssClient`, `dedupe`.
  * Integration tests: `localPayloads` (state transitions & retry logic).
  * All tests run locally without needing real AWS deployment (53/53 tests pass).

* **Built a Complete Postman Collection for Demos:**
  * Includes all public routes and admin routes.
  * Uses placeholders like `{{API_KEY}}` and `{{CSRF_TOKEN}}` (without committing real secrets) -> 51/51 tests pass.

* **Performed Security Audit and Confirmed System Safety with:**
  * SSRF prevention (safe-fetch with IP pinning, blocking IMDS `169.254.169.254`).
  * XXE prevention (disabled DTD and External Entities in RSS parser).
  * XSS prevention (Dashboard using text encoding instead of `innerHTML`).
  * No API key leaks in responses, logs, or frontend assets.
  * Origin Secret Header protecting EC2 from CloudFront bypass.

* **Completed `docs/api.md` matching 100% with the implemented `/api/v1` routes.**

