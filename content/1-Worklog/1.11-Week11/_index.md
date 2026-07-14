---
title: "Week 11 Worklog"
date: 2026-06-26
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---
### Week 11 Objectives:

* Practical data cleaning, validation, and transformation using AWS Glue ETL and Apache Hudi on S3.
* Data analysis using Amazon Athena, visualization via QuickSight Dashboards, and research on Federated queries and SageMaker integration.
* Automated data lake management using AWS Lake Formation and data preparation with Glue DataBrew.
* Act as **Read-only dashboard frontend** in the **CloudBrief** project — a serverless automated tech news aggregator on AWS.
* Complete and validate the static dashboard interface (Next.js static-export), ensuring read-only functionality and no security secrets.
* Perform unit tests for the frontend, audit source code to remove write/administration controls and prevent credential/secret leakage.

### Tasks to be carried out this week:
#### Week 11 (From 26/06/2026 – 02/07/2026)
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Lab 3: Transforming data with Glue: <br>&emsp; + Data Validation and ETL: Clean, validate, and transform data using AWS Glue. <br>&emsp; + Incremental Data Processing with Hudi: Apply Apache Hudi for change data processing (upsert/delete) on S3. <br> - Lab 4: Query and Visualize: <br>&emsp; + Data Analysis: Query S3 data with Amazon Athena and create a QuickSight Dashboard. <br>&emsp; + Advanced Athena: Use Federated queries for multi-source access and connect to SageMaker for predictions. | 26/06/2026 | 26/06/2026 | |
| 3 | - Lab 5: Data Lake Automation: <br>&emsp; + Lake Formation basics: Register data lake location, set up Data Catalog, and grant permissions. <br>&emsp; + Apply Lake Formation: Manage permissions for open table formats like Apache Hudi, Iceberg, and Delta Tables. <br> - Bonus Lab: Glue DataBrew: <br>&emsp; + Clean and prepare data (Data Preparation) using visual interface. | 27/06/2026 | 27/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 4 | + Install Bun 1.3.x, run `bun install`, `bun run build`, `bun run test` successfully. <br> + Create `frontend/.env` file from `frontend/.env.example` (if any). <br> + Discuss with team (ReinaMacCredy, RyugaRuki) to align on all `/api/v1/*` routes, JSON schema, and integrate shared contract `@cloudbrief/contracts` for dashboard. <br> + Review static Next.js source code under `frontend/` (DashboardSidebar, DashboardHeader, DashboardContent) and mock data file `frontend/lib/cloudbrief-mocks.ts`. | 28/06/2026 | 28/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 5 | + Write and configure unit test suites for frontend: `admin-api-client.test.ts`, `api-client.test.ts`, `article-display.test.ts`, `brief-api-client.test.ts`, `brief-display.test.ts`, `dashboard-navigation.test.ts`, `dashboard-store.test.ts`, `fixtures.test.ts`, `social-api-client.test.ts`, `url-safety.test.ts`. <br> + Split pages into separate routes (`/ops.html`, `/articles.html`, `/runs.html`, `/failures.html`) instead of using the hash anchor (`#`) mechanism of the old dashboard. <br> + Implement safe navigation logic, ensuring articles only redirect to valid absolute HTTP/HTTPS links via helper `isSafeUrl`. | 29/06/2026 | 29/06/2026 | <https://cloudjourney.awsstudygroup.com/> |
| 6 | + Run the entire frontend test suite and build successfully -> 16/16 tests pass, export static directory `frontend/out/`. <br> + UI Cleanup: Remove write/admin labels like `Admin`, `Open admin`, `Create view`, `New category` to ensure the dashboard is completely read-only. <br> + Security/Build Audit: Use `rg` to scan for `x-api-key`, `DEMO_API_KEY`, CSRF tokens or admin credentials in the static build bundle. <br> + Confirm safe rendering against XSS: Text fields like title, source, summary, and error must render as pure React text, never using `innerHTML` or `dangerouslySetInnerHTML`. <br> + Integrate API base URL via environment variable `NEXT_PUBLIC_CLOUDBRIEF_API_BASE_URL` for actual CloudFront deployment. | 30/06/2026 | 30/06/2026 | <https://cloudjourney.awsstudygroup.com/> |

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

* **Built and Finalized Read-only Dashboard Frontend:**
  * Deployed static Next.js dashboard (static-export) located in the `frontend/` directory, outputting to `frontend/out/`.
  * Designed paginated routing structure: Operations Overview (`/ops.html`), Article List (`/articles.html`), Run History (`/runs.html`), and Failure List (`/failures.html`).
  * Successfully integrated real data from `GET /api/v1/dashboard` and other endpoints via the `use-cloudbrief-dashboard.ts` hook.

* **Wrote and Operated Automated Frontend Test Suites:**
  * Unit tests: `admin-api-client`, `api-client`, `article-display`, `brief-api-client`, `brief-display`, `dashboard-navigation`, `dashboard-store`, `fixtures`, `social-api-client`, `url-safety`.
  * Frontend test suite successfully executed via Bun with **16/16 tests pass**.

* **Ensured Security and Safe Read-only Features:**
  * Completely removed write-permission buttons/labels like `Admin`, `Open admin`, `Create view`, and `New category` on the demo UI.
  * Ensured no API keys (`x-api-key`, `DEMO_API_KEY`), secrets, or CSRF tokens are embedded directly in the client static bundle.
  * Implemented safe rendering against XSS attacks: encoded plain text in React for all article fields (title, summary, error), never using `innerHTML` or `dangerouslySetInnerHTML`.
  * Restricted external links: open in new tab (`target="_blank"` and `rel="noopener noreferrer"`) and only accept secure protocol URLs (HTTP/HTTPS).

