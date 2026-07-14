---
title: "Event 5"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.5. </b> "
---

# REPORT “FIRST CLOUD AI JOURNEY - AWS SLA, SECURITY & EXAM ROADMAPS”

### Event Purpose

- Strategically guide and build a roadmap to conquer the AWS Certified Cloud Practitioner (CLF-C02) certification for beginners.
- Analyze the importance of monitoring based on end-user experience rather than solely relying on technical infrastructure.
- Introduce automated information security solutions using AI to optimize costs and performance compared to manual methods.
- Equip participants with a system risk management mindset and apply standard AWS models in practice.

### Speaker List

- **Nguyen Huynh Son** - Member of AWS Student Builder Group HUFLIT, Ex Infrastructure Reliability Engineer at SPS; shared on the topic of SLA and monitoring systems.
- **Ngo Le Tan Huy** - Speaker providing strategic roadmap guidance and tips for the AWS Cloud Practitioner exam.
- **Thinh Nguyen** - DevOps/DevSecOps/Cloud Engineer at Styl Solutions; shared about automated security solutions with AWS Security Agent.

### Key Highlights

1. Monitoring System and Service Level Agreement (SLA)

   - **The Nature of SLA**: It is a formal agreement on the level of service between the provider and the customer. AWS is responsible for warranting their services, but the actual user experience is the responsibility of the system builders.
   - **Infrastructure Monitoring Gaps**: Infrastructure reporting a "green" status (normal CPU, RAM) does not equate to a good user experience. For example: An endpoint checking system health (`/health`) operates normally, but the actual login flow (`/login`) might fail due to database connection errors.
   - **The Monitoring Pyramid Model**:
     - **Bottom Layer (Cloud Infrastructure/Service)**: CPU, Memory, EC2, RDS for root cause diagnostics.
     - **Top Layer (User Experience/Business)**: Successful login rate, revenue, and orders help determine the actual impact level.
   - **Risk Management Cycle**: Risk identification $\rightarrow$ Signal monitoring (metrics, logs, alarms) $\rightarrow$ Automated response via SNS/Slack $\rightarrow$ System improvement.

2. Strategy to Conquer AWS Cloud Practitioner Certification (CLF-C02)

   - **Exam Structure**: Consists of 65 multiple-choice questions (single or multiple answers), 90 minutes of exam time (non-native English speakers get an extra 30 minutes), passing score is 700/1000. The certification is valid for 3 years.
   - **Focus on 4 Knowledge Domains**:
     - **Cloud Concepts (24%)**: Focuses on digital transformation mindset, 6 benefits of the Cloud, Well-Architected Framework, and CAF.
     - **Security and Compliance (30%)**: Shared responsibility model (Security OF vs IN the cloud), IAM, security groups (Security Groups/NACLs), AWS Artifact.
     - **Cloud Technology and Services (34%)**: Understanding use cases through service names (Compute, Storage, Database, Networking).
     - **Billing, Pricing, and Support (12%)**: EC2 pricing models, cost management tools (Cost Explorer, Budgets), and support plans.
   - **Effective Study Methods**:
     - **Keyword Mapping Mindset**: Associate each service with 1-2 core keywords (e.g., "Decouple" means SQS).
     - **Mistake Analysis**: When doing practice tests, clarify why other options are wrong to avoid exam traps.
     - **Free Tier Practice**: Directly interact with fundamental services for easy visualization.

3. Optimizing Web Application Security with AWS Security Agent

   - **Bottlenecks of Traditional Pentest**: Manual testing often takes weeks, is expensive ($5k - $20k), and results are inconsistent depending on the expert's skills.
   - **Automated AI Solution (Frontier Agent)**: Powered by Amazon Bedrock, capable of autonomously planning and verifying vulnerabilities by conducting actual exploitation tests instead of just providing theoretical alerts.
   - **Comprehensive Coverage**:
     - **Design Review**: Inspecting Markdown documents or Terraform code right from the design phase according to PCI DSS, NIST CSF standards.
     - **Code Review**: Automatically integrated into Pull Requests on GitHub/GitLab to scan for malware, leaked secrets, and suggest direct patch fixes.
     - **Automated Pentesting**: Performing multi-step attack chains (IDOR $\rightarrow$ XSS) like a real user.
   - **Core Limitations**: Blocked by complex authentication systems (MFA, Biometrics, mTLS) and faces difficulty detecting business logic fraud.

### Lessons Learned

#### Design & Management Mindset

- Stable infrastructure services are only a necessary condition; the sufficient condition to evaluate a good system is customer satisfaction and a seamless end-user experience.
- Information security needs to be integrated early (Shift-left security) right from the architectural design phase via automated scanning tools to minimize subsequent remediation costs.

#### Techniques & Tools

- Learned how to set up Custom metrics combined with CloudWatch Alarms and SNS to receive early warnings before customers even report issues.
- Mastered techniques for taking AWS multiple-choice exams, such as the elimination method for fake options and paying attention to crucial keywords (Not, Least cost, Most scalable).
- Deeply understood the pricing model based on task execution hours (Task-Hour) of security AI agents to balance costs compared to hiring personnel.

### Application to Work

- **Rebuilding the Monitoring Dashboard System** for current projects: Adding metrics to measure the application layer and business experience (Login rate, successful checkout rate) instead of just looking at CPU/RAM charts.
- **Planning to study for the AWS Certified Cloud Practitioner** according to the 4-domain roadmap, utilizing free resources from AWS Skill Builder and practicing on a Free Tier account.
- **Experimenting with integrating automated source code scanning tools** into the team's CI/CD pipeline to automatically check security every time a Pull Request is created.

<div style="display: flex; gap: 10px; justify-content: center; flex-wrap: wrap; margin-top: 20px;">
  <img src="/images/4-EventParticipated/sk5_1.jpg" alt="sk5_1" style="width: 30%; min-width: 250px; height: auto;" />
  <img src="/images/4-EventParticipated/sk5_2.jpg" alt="sk5_2" style="width: 30%; min-width: 250px; height: auto;" />
  <img src="/images/4-EventParticipated/sk5_3.jpg" alt="sk5_3" style="width: 30%; min-width: 250px; height: auto;" />
</div>
