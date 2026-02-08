---
title: "Cloud Architecture Design"
parent: "Course Material"
has_children: true
has_toc: false
nav_order: 2
---

Cloud Architecture Design: From Localhost to Production
{: .lecture-title }

CSC491 - Capstone Project Design
{: .lecture-meta }

---

{: .lecture-info }
> ### Lecture Overview
>
> **Objective:** Teach architectural thinking for cloud-native systems—how to design infrastructure that survives first contact with production.
>
> **Reference Scenario:** The Rapid MVP (The Testbed) - A simple web app built under sprint-style constraints with decoupled frontend/backend architecture. This testbed mimics real-world engineering where local development must respect eventual production deployment constraints.
>
> **Core Question:** How do you architect a system that ships fast today but doesn't collapse when requirements change tomorrow?

---


This lecture is organized into the following sections:

1. [Thinking Like an Architect](thinking-like-architect) - Learn the transition from coding to system design, understanding the shift from building features to architecting services.

2. [Pre-Selection Analysis](pre-selection-analysis) - Explore tenancy models, infrastructure responsibility, and the critical decision between managed services and self-hosted solutions.

3. [Advanced Architectural Patterns](advanced-patterns) - Master API Gateway patterns, static/dynamic separation, event-driven architecture, and edge computing.

4. [Operational Excellence in the Cloud](operational-excellence) - Understand reliability, self-healing systems, security, scalability, and observability.

5. [Automation is Not Optional](automation) - Discover why automation is foundational, covering CI/CD, Infrastructure as Code, secret management, and deployment strategies.

6. [The MVP Architect's Dilemma](mvp-dilemma) - Navigate the balance between tactical execution and architectural foundations, learning what to defer and what to build now.

7. [Suggested Reading & Bibliography](reading-bibliography) - Access curated resources, essential texts, and references for deeper exploration of cloud architecture topics.
