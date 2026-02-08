---
title: "Section 6: The MVP Architect's Dilemma"
layout: default
parent: "Cloud Architecture Design"
nav_order: 6
---

## Section 6: The MVP Architect's Dilemma

### Tactical Execution: Deploy Fast Without Technical Debt Traps

**Technical Debt vs. Architectural Compromise:**

- **Acceptable compromise** means using serverless instead of Kubernetes—you can migrate later without rewriting application logic
- **Technical debt** means skipping authentication to ship faster—now every endpoint is public and retrofitting auth requires touching every route

---

### Defer Optimization, Not Foundations

**The Principle:** You can defer performance tuning. You cannot defer foundational architecture decisions.

**Deferrable (optimize later):**

- Performance tuning (database indexes, query optimization, caching strategies)
- Observability dashboards (custom Grafana panels, advanced alerting rules)
- Multi-region deployment (start single-region, expand when traffic justifies it)
- Advanced CI/CD (canary releases, staged rollouts, automated rollback logic)

**Non-deferrable (build it now):**

- Authentication/Authorization (every endpoint must verify identity from Day One)
- Encrypted connections HTTPS (non-negotiable, free via Let's Encrypt or managed platforms)
- Secret management (database credentials in GitHub Secrets, never in code)
- Basic CI/CD (automated deployment pipeline where `git push` → production)

---

### Minimum Viable Architecture for the Testbed

You're building a simple web app under sprint-style constraints with decoupled frontend/backend. Here's what you need:

#### Frontend, Backend, and Database

**Non-negotiable:** Static hosting with HTTPS for frontend, serverless or containerized compute for backend, managed database service with automatic backups. Git-based deployment with auto-scaling capability.

**Defer:** Custom domains, rate limiting, API versioning, read replicas, multi-region replication.

#### Authentication

**Optional for MVP testbed, but non-negotiable for your next project.**

If implementing: Use a managed authentication service with OAuth/JWT token support.

**Defer:** Role-based permissions, audit logs (start with simple "logged in" vs. "not logged in").

#### CI/CD

**Non-negotiable:** Automated deployment pipeline. `git push` → tests → deploy.

**Defer:** Staging environments, integration tests, security scans.

#### Observability

**Optional for MVP:** Can skip custom dashboards and metrics. Use provider-native logging if needed for debugging.

**Defer:** Distributed tracing, custom metrics, alerting.

---

### The Trap of Premature Optimization

Netflix has 1,000 engineers and 200 million users.

You have 2 engineers and an MVP to validate.

**Build for the problem you HAVE, not the problem you IMAGINE.**

Kubernetes is magnificent for 10,000 microservices. For a sprint-constrained web app, it's a distraction that prevents shipping.

**Document Your Assumptions:**

In your `README.md`, write:

"This architecture assumes <500 users, single-region deployment, no PII storage. When these assumptions break, revisit the following decisions: database choice, caching strategy, multi-region deployment."

When assumptions break, you know exactly what to revisit.

---

### Architectural Integrity Under Constraint

The best architecture:

- **Ships on deadline** (not theoretically perfect, but actually deployed)
- **Survives first contact with users** (doesn't crash when 10 people use it simultaneously)
- **Can evolve when requirements change** (adding a feature doesn't require a rewrite)
- **Doesn't require heroic engineering to keep running** (no 3am SSH sessions to restart services)

{: .important }
> **The Final Principle:** Perfect is the enemy of shipped. But shipped without foundations is the enemy of sustainable growth. Find the line.

You're not building for Netflix scale. You're building to prove the concept works. But you're also not building a house of cards that collapses the moment someone wants to add a feature.

The architect's job: maximize learning velocity while minimizing rework cost. Ship fast. Ship solid. Ship something you can build on.

---
