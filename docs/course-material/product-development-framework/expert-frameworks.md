---
title: "Expert Frameworks"
layout: default
parent: "Product Development Framework"
grand_parent: "Course Material"
nav_order: 2
---

## Expert Frameworks
{: .section-header }

### Teresa Torres — Continuous Discovery Framework

**Claim**: Product decisions must be anchored in **weekly evidence collection** (user interviews, instrumentation data, friction analysis). Discovery is not a phase; it's a parallel cadence.

**Evidence**: *Continuous Discovery Habits* (2021) — documents how teams at Amazon, Netflix, and Spotify use weekly "opportunity solution trees" to map user pain points to feature experiments. CUJ evolution becomes the forcing function for prioritization.

{: .warning }
> **Critique**: **Overkill for MVPs**. Weekly discovery cadence assumes mature product-market fit. For proof-of-concept sprints, discovery can lag implementation (you build first, then validate friction).

{: .note }
> **When It Applies**: **A5–A9**. Once students have a surface product (A4), continuous CUJ refinement prevents feature bloat and keeps them honest about "does this solve the validated pain point?"

---

### Chris Richardson — Microservices Patterns (Multi-Tier Evolution)

{: .callout-box }
> **Key Principle:** Start monolithic, decompose incrementally. Premature microservices create distributed debugging hell.

**Claim**: Use **logical boundaries** (API contracts, bounded contexts) even in a monolith to enable future decomposition.

**Evidence**: *Microservices Patterns* (2018) — Richardson's "Strangler Fig" pattern shows how to evolve from monolith → service-oriented → event-driven without rewriting. Logical decoupling ≠ physical decoupling on Day 1.

{: .warning }
> **Critique**: **Students over-optimize architecture**. They'll read "multi-tier" and immediately build 5 Docker containers. The framework doesn't say *when* to decompose — only *how*.

{: .note }
> **When It Applies**: **A4–A6** enforce logical boundaries (e.g., frontend calls backend via REST API, even if both run in one process). **A7–A8** introduce decomposition (e.g., separate auth service, async job queue). **A9** should be production-ready but not necessarily microservices.

---

### Eric Ries — Validated Learning & Build-Measure-Learn

{: .callout-box }
> **Key Principle:** Each sprint must answer one risky assumption. If you're building features without a hypothesis, you're guessing.

**Evidence**: *The Lean Startup* (2011) — Ries formalized the feedback loop used at IMVU, Dropbox, and Zappos. Every sprint should have a **learning goal** (not just a feature goal).

{: .warning }
> **Critique**: **Assumes users exist**. For student projects in CSC454, "validation" often means "we built it and it didn't crash" — not real user testing. Framework breaks if you fake the data.

{: .note }
> **When It Applies**: **A4** = proof-of-concept (Does the core interaction work?). **A5** = proof-of-value (Do users complete the CUJ?). **A6–A8** = specific hypotheses (e.g., "adding real-time sync reduces friction by 40%"). **A9** = beta validation with external users.

---

[Previous: Reasoning & Approach](reasoning-and-approach){: .btn .float-left }
[Next: Actionable Recommendations](actionable-recommendations){: .btn .btn-primary .float-right }
