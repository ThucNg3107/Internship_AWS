---
title: "Week 11 Worklog"
date: 2026-06-26
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---
### Week 11 Objectives:

* Execute data cleaning, validation, and transformation (ETL) pipelines using AWS Glue integrated with Apache Hudi table formats on S3.
* Perform advanced data analytics using Amazon Athena, build visualization dashboards in QuickSight, and explore Federated Queries connected to Amazon SageMaker.
* Automate Data Lake governance with AWS Lake Formation and standardize visual data preparation using Glue DataBrew.
* Serve as the **Read-only Dashboard Frontend Developer** for the **CloudBrief** project — an automated AI tech news aggregator on AWS.
* Deliver and validate the static Next.js export dashboard interface, enforcing secure read-only controls and zero secret exposures.
* Construct automated unit testing suites for the frontend, auditing source code to strip write/admin controls and prevent API key or secret leakage.

### Tasks to be carried out this week:
#### Week 11 (From 26/06/2026 – 02/07/2026)
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Lab 3: Data Transformation with Glue: <br>&emsp; + Data Validation & ETL: Utilize AWS Glue for data validation, cleaning, and format transformation. <br>&emsp; + Incremental Data Processing with Hudi: Apply Apache Hudi for change data capture (upsert/delete) directly on S3 Data Lakes. <br> - Lab 4: Data Querying & Visualization: <br>&emsp; + Analytics: Query S3 datasets using Amazon Athena and construct analytical dashboards in Amazon QuickSight. <br>&emsp; + Advanced Athena Features: Leverage Federated Queries across hybrid sources and connect SageMaker for ML predictions. | 26/06/2026 | 26/06/2026 | |
| 3 | - Lab 5: Data Lake Automation via AWS Lake Formation: <br>&emsp; + Lake Formation Administration: Register Data Lake storage locations, build centralized Data Catalogs, and enforce fine-grained access policies. <br>&emsp; + Open Table Format Authorization: Manage security permissions for Apache Hudi, Apache Iceberg, and Delta Tables. <br> - Supplemental Lab: AWS Glue DataBrew: <br>&emsp; + Perform visual data cleaning and preparation via Glue DataBrew drag-and-drop interfaces. | 27/06/2026 | 27/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | + Configure Bun 1.3.x runtime environments, executing `bun install`, `bun run build`, and `bun run test` commands successfully. <br> + Provision `frontend/.env` configuration files derived from `.env.example` templates. <br> + Align with project teammates (ReinaMacCredy, RyugaRuki) to standardize `/api/v1/*` route schemas and integrate shared contract packages `@cloudbrief/contracts`. <br> + Review static Next.js source code under `frontend/` (DashboardSidebar, DashboardHeader, DashboardContent) and mock data definitions `frontend/lib/cloudbrief-mocks.ts`. | 28/06/2026 | 28/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | + Develop unit testing suites for frontend modules: `admin-api-client.test.ts`, `api-client.test.ts`, `article-display.test.ts`, `brief-api-client.test.ts`, `brief-display.test.ts`, `dashboard-navigation.test.ts`, `dashboard-store.test.ts`, `fixtures.test.ts`, `social-api-client.test.ts`, `url-safety.test.ts`. <br> + Refactor UI routing into dedicated static page endpoints (`/ops.html`, `/articles.html`, `/runs.html`, `/failures.html`) replacing legacy hash anchor (`#`) navigation. <br> + Implement secure navigation logic, ensuring articles redirect exclusively to valid absolute HTTP/HTTPS links via helper `isSafeUrl`. | 29/06/2026 | 29/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | + Execute full frontend test suites and generate static export builds successfully -> **16/16 tests pass**, outputting to `frontend/out/`. <br> + Read-only UI Sanitization: Strip all write/admin UI controls such as `Admin`, `Open admin`, `Create view`, and `New category`. <br> + Security & Secret Audit: Perform `rg` pattern scans ensuring zero exposure of `x-api-key`, `DEMO_API_KEY`, CSRF tokens, or admin credentials within static client bundles. <br> + XSS Protection Hardening: Enforce pure React text encoding for all dynamic content fields (titles, summaries, errors), forbidding `innerHTML` or `dangerouslySetInnerHTML`. <br> + Configure API Base URLs dynamically via `NEXT_PUBLIC_CLOUDBRIEF_API_BASE_URL` environment variables for Amazon CloudFront CDN deployment. | 30/06/2026 | 30/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

### Week 11 Achievements:

* **AWS Glue ETL & Apache Hudi on S3:**
  * Performed data validation and ETL using AWS Glue; applied Apache Hudi for incremental change data processing (upsert/delete) on S3.

* **Amazon Athena & Amazon QuickSight Visualization:**
  * Queried S3 datasets using Amazon Athena, configured Federated Queries connecting to SageMaker, and built QuickSight Dashboards.

* **AWS Lake Formation Data Lake Automation:**
  * Configured Lake Formation to register storage locations, enforce fine-grained access policies for Apache Hudi, Iceberg, and Delta Tables, and prepared data via Glue DataBrew.

* **Mastered CloudBrief System Architecture on AWS:**
  * Amazon EC2 (ARM64 `t4g.small`) running API server & worker processes.
  * Amazon DynamoDB managing article metadata and deduplication records.
  * Amazon S3 storing raw text `.txt` objects and static frontend web assets.
  * Amazon SQS providing asynchronous message queueing between worker services.
  * Amazon Bedrock (Nova Lite) executing automated AI news summarization.
  * Amazon CloudFront operating as CDN and single-entry reverse proxy for S3 static buckets.

* **Built and Finalized Read-only Dashboard Frontend:**
  * Exported static Next.js dashboard builds (static-export) into `frontend/out/`.
  * Standardized static page routing: Operations Overview (`/ops.html`), Articles (`/articles.html`), Run Logs (`/runs.html`), and Failure Logs (`/failures.html`).
  * Integrated live telemetry from `GET /api/v1/dashboard` endpoints via `use-cloudbrief-dashboard.ts` custom hooks.

* **Executed Automated Frontend Test Suites:**
  * Developed unit tests: `admin-api-client`, `api-client`, `article-display`, `brief-api-client`, `brief-display`, `dashboard-navigation`, `dashboard-store`, `fixtures`, `social-api-client`, `url-safety`.
  * Frontend test suite executed via Bun with **16/16 tests passing**.

* **Enforced Frontend Security and Read-only Compliance:**
  * Completely stripped write-permission controls such as `Admin`, `Open admin`, `Create view`, and `New category`.
  * Hardened secret security: Verified zero embedded API keys (`x-api-key`, `DEMO_API_KEY`), secrets, or CSRF tokens in client bundles.
  * Mitigated XSS vulnerabilities: Enforced pure React string rendering for dynamic article fields, omitting `innerHTML` or `dangerouslySetInnerHTML`.
  * Hardened external hyperlinks: Enforced new tab navigation (`target="_blank"` and `rel="noopener noreferrer"`) restricted strictly to valid HTTP/HTTPS protocols.
