---
title: "Section 1: Thinking Like an Architect"
layout: default
parent: "Cloud Architecture Design"
nav_order: 1
---

## Section 1: Thinking Like an Architect
{: .section-header }

### The Transition: From Coder to System Designer

You've written code that works on your laptop. You've passed unit tests. You've pushed to GitHub. But when you architect systems, you're no longer optimizing for "does it run?"—you're optimizing for "does it survive?"

{: .callout-box }
> **Key Distinction:** Coding solves a problem once. Architecture solves a problem repeatedly, under variable load, across failure modes, with maintainers who aren't you.

This shift requires thinking across four core concepts:

{: .framework-box }
> ### Software Engineering vs. Architecture Thinking
>
> #### Logic
>
> **Software Thinking:** Business logic—the feature itself. Does my code solve the problem?
>
> **Architecture Thinking:** How logic holistically transforms into services. How do features decompose into distributed components?
>
> #### Orchestration
>
> **Software Thinking:** Tools—the libraries and frameworks I use. Which npm package should I install?
>
> **Architecture Thinking:** Service orchestration and integration. How do systems coordinate, communicate, and handle dependencies?
>
> #### Infrastructure
>
> **Software Thinking:** Code optimization—making my algorithm faster. Can I reduce O(n²) to O(n log n)?
>
> **Architecture Thinking:** Right-sizing resources to demand. What compute and storage models match workload patterns and cost constraints?
>
> #### Operations
>
> **Software Thinking:** Bug fixing—it crashed, let me debug. What line threw the exception?
>
> **Architecture Thinking:** Operational reality—designing for failure modes before they happen. How does this behave when traffic spikes, credentials leak, or dependencies fail?

---

### From Features to Services: Drawing Boundaries

**Traditional thinking:** One application, one codebase, one database, one deployment. You build "features" that all live in the same place.

**The problem:** If any piece fails, everything fails. A memory leak in the reporting module crashes checkout. A database lock from analytics queries blocks user login. Deploying a minor UI fix requires redeploying the entire application—and risking everything.

{: .important }
> **The Service-Oriented Shift:** Stop thinking in features. Start thinking in services.

**Service-oriented architecture:** Decompose the system into independently deployable services:

- Each service owns its domain and data
- Has its own failure boundary so one service crash doesn't take down others
- Scales independently based on its workload
- Deploys on its own cadence—meaning you can fix payments without touching search

Ask these questions to determine if something should be a separate service:

- **Failure independence:** If this fails, can the rest of the system continue?
- **Scaling profile:** Does this component have different resource needs? (CPU-heavy vs. memory-heavy vs. I/O-bound)
- **Deployment frequency:** Does this change more or less often than other components?
- **Team ownership:** Can a single team own this domain end-to-end?

### Monolith vs. Service-Oriented Thinking

| Monolithic Thinking | Service-Oriented Thinking |
|:-------------------|:-------------------------|
| Add a feature to the codebase | Which service owns this domain? |
| Deploy the entire app | Deploy only changed services |
| Scale the whole server | Scale the bottleneck service |
| One database for everything | Each service owns its data store |
| Fix a bug = risk breaking everything | Fix a bug = isolated deployment |

{: .warning }
> **Critical Insight:** "Best practices" are context-dependent. Kubernetes is over-engineering for a 50-user dashboard. PostgreSQL on a VM is under-engineering for a multi-tenant SaaS. Your job is to defend your choices against your constraints, not against a blog post.

---
