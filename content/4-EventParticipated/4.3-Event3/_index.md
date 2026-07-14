---
title: "Event 3"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.3. </b> "
---


# Report on “First Cloud Journey Meetup - June 2026”


### Event Purpose

- Share knowledge on Container and Docker technologies for beginners.
- Introduce advanced solutions such as GraphRAG on AWS Bedrock and Neptune.
- Guide building a network intrusion detection system (NIDS) using Machine Learning.
- Share practical experience on career development paths from IT Helpdesk to Senior Sysadmin/Cloud Engineer.
- Explore Multiplayer game connectivity architectures using AWS WebSockets and Godot.
- Highlight golden rules and tools for effective teamwork.

### Speaker List

- **Bao Huynh** - Junior Cloud Native Developer at Endava Vietnam & Founder of ITea Lab.
- **Viet Phat** - AI Major at Swinburne University of Technology.
- **Le Hoang Gia Dai** - Final year student at HUTECH, Team AWS G3.
- **Tran Trung Vinh** - System Administrator at Central Retail Group.
- **Nguyen Quoc Bao** - Speaker on Multiplayer Cloud Networking.
- **Truong Huy Phuoc** - Speaker on The Art of Effective Teamwork.

### Key Highlights

#### Docker - Containerization Technology

- Concept: Packaging applications and dependencies into a single package to run consistently anywhere.
- Benefits: High portability, consistency, resource efficiency, and fast deployment.
- Key Components: Docker Images (read-only templates), Dockerfiles (build instructions), and Docker Containers (running application instances).

#### GraphRAG with Amazon Bedrock & Neptune

- The Problem: Traditional RAG is limited in answering queries that require multi-hop reasoning.
- The Solution: Use graphs to store explicit relationships between entities, helping LLMs understand deeper contexts.
- Tools: Amazon Bedrock (entity processing/embedding) and Amazon Neptune (graph storage and querying).

#### IT Infrastructure Career Path

- Core Skills: Start from troubleshooting skills, communication, and learning mindsets at Helpdesk.
- The Shift: Learn Linux, Networking, and build home labs to understand how systems are built.
- Cloud/DevOps Mindset: Shift from managing physical servers to Infrastructure as Code (IaC - Terraform) and automation culture (CI/CD, Docker).

#### Connecting Games with AWS WebSockets

- Architecture: Use API Gateway WebSockets to maintain full-duplex two-way connections.
- State Management: Combine Lambda (logic processing) and DynamoDB (connection ID and game state storage).
- Godot Integration: Use the WebSocketPeer class to handle network events in the game loop.



### Lessons Learned

#### Design Mindset

- **Cloud-Native Mindset**: Understand elastic scaling and pay-for-use models.
- **Security-First**: Security is not just about using rigid rules but requires the flexibility of AI/ML to adapt to new threats.
- **Teamwork Core**: Understand that clear common goals and individual accountability are the keys to work efficiency.

#### Technical Architecture

- **Containerization vs. Virtualization**: Clearly understand why Containers are lighter and more optimal than traditional VMs by sharing the OS.
- **Real-time Communication**: Distinguish when to use WebSockets (for turn-based games, chat) and when to use GameLift for games requiring high update frequencies.
- **Data Engineering for AI**: Importance of data cleaning and handling class imbalance in training ML models.

### Development Strategy

- **Hands-on Experience**: Practicing through real-world projects and building portfolios is more important than just having certificates.
- **Automation**: Automate repetitive tasks to free up time for system design and improvement.

### Applying to Work

- Deploy Docker: Package current applications to optimize CI/CD processes and reduce infrastructure costs.
- Upgrade Security: Research integrating ML NIDS into existing AWS systems to enhance attack detection.
- Improve Teamwork: Use tools like Trello, Slack, or Discord to manage projects and communicate effectively according to golden rules.
- Develop WebSocket Applications: Test building real-time interactive features using AWS Lambda and DynamoDB.

### Event Experience

Participating in the Meetup on June 06, 2026 was a multi-dimensional learning journey from infrastructure, security to application programming. Some outstanding impressions:

#### Learning from Practice
- Stories about mistakes during Sysadmin work and the lesson "never test in production environments" provided high practical value.
- Live demo sessions connecting the Godot game and monitoring DynamoDB data in real-time helped clarify abstract concepts.

#### Updating Pioneering Technologies
- Gained access to GraphRAG - a new trend that helps solve complex problems that traditional RAG cannot.
- Understood how to combine Cloud-native power with Machine Learning to protect systems against modern attacks.

#### Community Networking
- The event created space for students, fresh graduates, and experts to discuss development paths "from scratch".
- Better understood the importance of digital tools in promoting smooth coordination among team members.

#### Lessons Learned
- Technology is just a tool; the right design mindset and persistence in practice are the deciding factors of success.
- Modernizing applications through Docker and Serverless helps businesses speed up product launches and minimize operational risks.

<div style="display: flex; gap: 10px; justify-content: center; flex-wrap: wrap; margin-top: 20px;">
  <img src="/images/4-EventParticipated/sk3_1.jpg" alt="sk3_1" style="width: 30%; min-width: 250px; height: auto;" />
  <img src="/images/4-EventParticipated/sk3_2.jpg" alt="sk3_2" style="width: 30%; min-width: 250px; height: auto;" />
  <img src="/images/4-EventParticipated/sk3_3.jpg" alt="sk3_3" style="width: 30%; min-width: 250px; height: auto;" />
</div>
<div style="display: flex; gap: 10px; justify-content: center; flex-wrap: wrap; margin-top: 10px;">
  <img src="/images/4-EventParticipated/sk3_4.jpg" alt="sk3_4" style="width: 30%; min-width: 250px; height: auto;" />
  <img src="/images/4-EventParticipated/sk3_5.jpg" alt="sk3_5" style="width: 30%; min-width: 250px; height: auto;" />
</div>
