---
title: "Pre-Selection Analysis"
layout: default
parent: "Cloud Architecture Design"
nav_order: 2
---

## Pre-Selection Analysis

### Tenancy Models: Single vs. Multi-Tenant

**Single-Tenant:** Each customer gets isolated infrastructure (dedicated database, separate app instance).

- **Use case:** Enterprise SaaS with compliance requirements, resource isolation guarantees.
- **Trade-off:** Higher per-customer cost, complex provisioning automation.

**Multi-Tenant:** All customers share infrastructure with logical isolation (row-level security, schema separation).

- **Use case:** B2C apps, internal tools, cost-sensitive SaaS.
- **Trade-off:** Noisy neighbor problems, security boundaries in application code.

{: .note }
> **For the testbed:** Multi-tenant. A simple web app doesn't need isolated infrastructure per user. Use shared resources with logical separation if needed.

---

### Infrastructure Responsibility: What You Manage vs. What You Delegate

This is the most consequential architectural decision you'll make.

#### Self-Managed Open Source (IaaS)

**What you control:** OS, runtime, application code, database tuning, backups, security patches.

**Examples:** PostgreSQL on EC2, Redis on a VM, self-hosted Kubernetes.

**When to choose:** You need fine-grained control (custom kernel modules, specialized hardware), or vendor costs are prohibitive at scale.

**Operational cost:** You own the pager. Database crashes at 3am? You're SSHing in.

#### Managed Services (PaaS/DBaaS)

**What you control:** Schema design, queries, application code. Provider handles infrastructure.

**Examples:** RDS, Cloud SQL, Heroku Postgres, managed Redis.

**When to choose:** You want reliability without operational burden. Sprint-style deadlines.

**Trade-off:** Higher per-unit cost, less tuning control, potential for vendor-specific quirks.

#### Serverless (FaaS/BaaS)

**What you control:** Application code only. No servers, no scaling config.

**Examples:** Lambda, Cloud Functions.

**When to choose:** Unpredictable traffic, zero operational overhead, pay-per-use economics.

**Trade-off:** Cold starts, execution time limits, debugging complexity.

---

### The Serverless Question

Serverless is not "zero infrastructure." It's "someone else's infrastructure, billed by the millisecond."

**When serverless wins:**

- Traffic is spiky or unpredictable
- You have zero budget for idle resources
- Cold start latency (100-500ms) is acceptable

**When serverless loses:**

- Sustained high throughput (cost > equivalent VM)
- Long-running processes (exceeds execution time limits)
- Tight latency requirements (cold starts kill p99)

{: .warning }
> **For the testbed:** Use serverless functions + managed database. No VM provisioning, no server patching. Deploy via Git push. Your entire infrastructure is code. Focus on proving the concept, not managing servers.

---

[Previous: Thinking Like an Architect](thinking-like-architect){: .btn .float-left }
[Next: Advanced Architectural Patterns](advanced-patterns){: .btn .btn-primary .float-right }
