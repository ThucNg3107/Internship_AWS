---
title: "Event 5"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.5. </b> "
---

# REPORT ON “FIRST CLOUD AI JOURNEY - AWS SLA, SECURITY & EXAM ROADMAPS”

### Event Purpose

- Establish an effective study methodology and the shortest roadmap to achieve AWS Certified Cloud Practitioner (CLF-C02) certification.
- Internalize the user-centric application monitoring philosophy measured by end-user experience rather than hardware metrics alone.
- Explore AI-powered automated security scanning tools to enhance source code quality and optimize enterprise budgets.
- Shape infrastructure risk governance mindsets and flexibly apply AWS standardized architectural frameworks to production projects.

### Speaker List

- **Nguyen Huynh Son** - Member of AWS Student Builder Group HUFLIT, Ex Infrastructure Reliability Engineer at SPS; speaker on SLAs and Monitoring systems.
- **Ngo Le Tan Huy** - Speaker guiding strategic preparation roadmaps and exam tips for AWS Cloud Practitioner certification.
- **Thinh Nguyen** - DevOps/DevSecOps/Cloud Engineer at Styl Solutions; speaker introducing automated security solutions with AWS Security Agent.

### Key Highlights

1. Monitoring Systems & Service Level Agreements (SLA)

   - **The Essence of SLAs**: Formal service quality commitments between infrastructure providers and consuming clients. AWS guarantees availability for underlying cloud services, but end-to-end production application experience remains the responsibility of developers.
   - **Infrastructure Monitoring Blindspots**: "Green" infrastructure indicators (healthy CPU/RAM) do not guarantee flawless application user experience. Example: A health check endpoint (`/health`) returns 200 OK, but actual login workflows (`/login`) fail due to database connection bottlenecks.
   - **The Monitoring Pyramid**:
     - **Bottom Tier (Infrastructure/Cloud Services)**: Metrics covering CPU, RAM, EC2, RDS used for root cause diagnosis.
     - **Top Tier (User Experience/Business Outcomes)**: Metrics covering login success rates, checkout volume, and revenue to evaluate actual business impact.
   - **Risk Management Loop**: Threat Identification $\rightarrow$ Signal Telemetry (metrics, logs, alarms) $\rightarrow$ Automated Alerts via SNS/Slack $\rightarrow$ Infrastructure Remediation.

2. Strategy for Conquering AWS Cloud Practitioner (CLF-C02) Certification

   - **Exam Structure**: Consists of 65 multiple-choice/multiple-response questions, 90-minute duration (30-minute extension for non-native English speakers), passing score 700/1000, valid for 3 years.
   - **Core Focus Across 4 Domains**:
     - **Cloud Concepts (24%)**: Focus on digital transformation mindsets, 6 core cloud benefits, Well-Architected Framework, and CAF.
     - **Security and Compliance (30%)**: Grasp Shared Responsibility Model (Security OF vs IN the cloud), IAM, Security Groups/NACLs, and AWS Artifact.
     - **Cloud Technology and Services (34%)**: Map service use cases by domain categories (Compute, Storage, Database, Networking).
     - **Billing, Pricing, and Support (12%)**: EC2 pricing models, cost management tools (Cost Explorer, Budgets), and support tiers.
   - **Effective Preparation Strategies**:
     - **Keyword Mapping Mindset**: Associate each service with 1-2 core keywords (e.g., "Decouple" maps directly to SQS).
     - **Mistake Analysis**: When practicing sample exams, thoroughly analyze why incorrect options are wrong to avoid exam traps.
     - **Hands-on via Free Tier**: Directly operate core services on live cloud accounts to solidify conceptual memory.

3. Web Application Security Optimization via AWS Security Agent

   - **Bottlenecks of Traditional Pentesting**: Manual penetration testing takes weeks, incurs high costs ($5k - $20k), and report quality varies based on individual auditor skills.
   - **Autonomous AI Solution (Frontier Agent)**: Powered by Amazon Bedrock, capable of autonomously planning and executing real-world exploit tests rather than delivering theoretical alerts.
   - **Comprehensive Coverage**:
     - **Design Review**: Inspect Markdown architecture docs or Terraform code during design phases against PCI DSS and NIST CSF standards.
     - **Code Review**: Automatically integrate into GitHub/GitLab Pull Requests to scan for vulnerabilities, exposed secrets, and suggest inline fixes.
     - **Automated Pentesting**: Execute multi-stage attack chains (IDOR $\rightarrow$ XSS) mimicking authentic adversary behavior.
   - **Core Limitations**: Impaired when encountering advanced authentication mechanisms (MFA, Biometrics, mTLS) and complex business logic fraud.

### Lessons Learned

#### Design & Management Mindset

- Stable infrastructure is merely a necessary condition; smooth user experience and end-user satisfaction are the ultimate measures of system success.
- Information security must be shifted left (Shift-left security) - auditing security at the design stage to optimize remediation costs down the line.

#### Technical & Tools

- Learn to configure custom metrics combined with CloudWatch Alarms and SNS to detect incidents proactively before users report issues.
- Master AWS multiple-choice exam strategies, including elimination methods and key decisive terms (Not, Least cost, Most scalable).
- Evaluate Task-Hour execution cost models of AI security agents to make informed decisions comparing AI versus human staffing costs.

### Applying to Work

- **Redesign Monitoring Dashboards** for active projects: Incorporate application-level and business metrics (login success rates, checkout completion rates) alongside CPU/RAM charts.
- **Plan AWS Certified Cloud Practitioner Exam Preparation** following the 4-domain roadmap, utilizing free AWS Skill Builder resources and Free Tier hands-on practice.
- **Integrate Automated Code Scanning Tools** into team CI/CD pipelines to perform automated security checks on every Pull Request.

<div style="display: flex; gap: 10px; justify-content: center; flex-wrap: wrap; margin-top: 20px;">
  <img src="/images/4-EventParticipated/sk5_1.jpg" alt="sk5_1" style="width: 30%; min-width: 250px; height: auto;" />
  <img src="/images/4-EventParticipated/sk5_2.jpg" alt="sk5_2" style="width: 30%; min-width: 250px; height: auto;" />
  <img src="/images/4-EventParticipated/sk5_3.jpg" alt="sk5_3" style="width: 30%; min-width: 250px; height: auto;" />
</div>
