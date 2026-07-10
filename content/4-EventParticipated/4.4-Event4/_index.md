---
title: "Event 4"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.4. </b> "
---


# Report on “FCAJ Community Day - June 2026”

### Event Purpose

- **Share Corporate Experience**: The FCAJ Community Day is a monthly event organized to create a space for speakers from various businesses to share their most realistic experiences, trials, and perspectives from corporate working environments.

### Speaker List

- **Mr. Steve Tran**: Career journey and AI applications in supporting cloud infrastructure operations.
- **Mr. Hieu Nghi, Mr. Kiet, and Mr. Trung**: Co-presenters on Building a Voice AI system for Vietnamese.
- **Ms. Bao and Mr. Nguyen Nguyen**: Automating error investigation and system recovery with DevOps Agent.
- **Mr. Truong and Ms. Minh Anh**: AI and enterprise human resources - Applying Amazon Q to optimize HR processes.
- **Mr. Toan Nguyen**: Establishing private security/VPC connections for AI (Amazon Q) and MCP Server systems.

### Key Highlights

The event included multiple presentations surrounding the development of Cloud and AI technologies in various fields:

#### Career Journey and AI in Cloud Operations

- **SRE & Cloud Evolution**: Mr. Steve Tran shared his career journey from managing physical servers manually to becoming a Solutions Architect at AWS, and the reasons for founding Cloud Thinker.
- **AI in Recruitment**: He emphasized that AI is changing the way companies recruit, prioritizing individuals who are exceptionally good at coding or outstanding at utilizing AI tools.
- **Agent Architecture**: He compared Multi-agent and Single-agent AI architectures in managing complex cloud infrastructures.

#### Building Voice AI for Vietnamese

- **Voice AI Architecture**: The speakers presented the architecture of Voice AI, highlighting the specific challenges of Vietnamese lacking data for direct Speech-to-Speech models.
- **Conversion Solutions**: The solution involves converting voice to text (STT), passing it to LLMs for processing, and then converting it back to voice (TTS).
- **Context Optimization**: AI is also trained to understand context, interrupt naturally, recognize gender (addressing as anh/chị), and handle regional dialects in banking applications.

#### Automation with DevOps Agent

- **DevOps Agent**: Introduced an AI DevOps Agent that automates investigating, classifying system errors, and proposing remediation solutions.
- **Key Features**: The strengths of this Agent include Context learning, connecting tools via MCP, and billing based on execution runtime rather than static infrastructure.
- **DoS Attack Demo**: A live demo showed the DevOps Agent analyzing logs and finding that the application slowness was caused by a DoS attack in a short amount of time.

#### Applying Amazon Q in Human Resources (HR)

- **The Problem**: Manual CV screening easily leads to missing talents and relies heavily on subjective judgment.
- **Recruitment Support**: Amazon Q was introduced as an AI Assistant that can automatically read CVs, grade candidates based on Job Descriptions (JD), and output visual reports without leaking data thanks to built-in security features.

#### Secure Network Connection for AI using Private MCP

- **Security Concerns**: Instead of connecting AI to public internet MCP servers (vulnerable to DoS or data leaks), systems need secure transmission solutions.
- **Internal Connections**: The system utilizes VPC Connections, ALB, and Route 53 Resolvers to create a completely internal and secure transmission path on the AWS Cloud.



### Lessons Learned

#### Career Guidance & Entrepreneurship

- **Early Experience**: Students or fresh graduates should look for early opportunities in corporate environments to gain practical experience.
- **The Role of AI**: Although AI is growing rapidly and companies tend to reduce bulk hiring, AI will not completely replace humans in critical infrastructure systems; rather, it acts to support and amplify skills.
- **Startup Spirit**: Don't spend too much time thinking; execute immediately. Find "champion" clients (large organizations with existing real-world problems) to apply ideas and solve actual enterprise pain points.

#### System Design & Operations

- **Agent Choice**: In AI Agent design, Multi-agent structures help control access and distribute work well, but sometimes a well-designed Single-agent can handle 95% of complex tasks.
- **Human in the Loop**: AI solutions should not automatically execute changes on production environments; they should only provide recommendations, with the final approval decisions belonging to humans. Total reliance on automated systems brings significant risks.
- **Observability**: For AI to investigate errors accurately, the underlying system must have good observability with complete logs.
