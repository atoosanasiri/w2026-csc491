---
title: Product Development Framework
layout: default
parent: Course Material
nav_order: 1
---

# Product Development Framework: Sprint Architecture & Validation Gates
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## REASONING OUTLINE

1. **Expert Selection**: Drew from product engineering (Marty Cagan, Teresa Torres), technical architecture (Chris Richardson), and startup methodology (Steve Blank, Eric Ries) — all have published rigorous frameworks on iterative product development and evidence-based validation.

2. **Framework Prioritization**: Focused on (a) continuous discovery frameworks that align CUJ evolution with feature sequencing, (b) multi-tier architectural thinking vs. modular decomposition, and (c) evidence-driven sprint gating (proof-of-concept → proof-of-value → beta).

3. **Source Constraints**: Cited published books, research papers from IEEE/ACM, and vendor-neutral architecture documentation. Avoided blog-level content.

4. **Gap Identification**: Your A2/A3 assignments are **tactically sound** but lack explicit **validation gates** and **architectural maturity progression** across sprints. The 10-week cycle demands **incremental complexity scaling** — each demo must add one architectural dimension (e.g., state management → observability → horizontal scaling).

5. **Pedagogical Alignment**: Maintained your no-filler, evidence-first tone. Applied your rubric structure (functionality, operational logic, audit trail, narrative defense) to each new assignment.

---

## TARGETED QUESTIONS

1. **Validation Rigor**: Do you want students to define **quantitative success metrics** (e.g., latency <200ms, task completion time reduction) for each sprint, or is qualitative CUJ friction analysis sufficient?

2. **Architectural Scaffolding**: Should A4 enforce a **specific architectural pattern** (e.g., event-driven, CQRS, microservices-lite) as a forcing function, or do students choose based on their CSC454 product constraints?

3. **Deployment Maturity**: By A9 (Beta Release), do you expect **production-grade observability** (logging, monitoring, alerting) or just functional deployment + CI/CD?

---

## EXPERT FRAMEWORKS

### 1. Teresa Torres — Continuous Discovery Framework

**Claim**: Product decisions must be anchored in **weekly evidence collection** (user interviews, instrumentation data, friction analysis). Discovery is not a phase; it's a parallel cadence.

**Evidence**: *Continuous Discovery Habits* (2021) — documents how teams at Amazon, Netflix, and Spotify use weekly "opportunity solution trees" to map user pain points to feature experiments. CUJ evolution becomes the forcing function for prioritization.

{: .warning }
> **Critique**: **Overkill for MVPs**. Weekly discovery cadence assumes mature product-market fit. For proof-of-concept sprints, discovery can lag implementation (you build first, then validate friction).

{: .note }
> **When It Applies**: **A5–A9**. Once students have a surface product (A4), continuous CUJ refinement prevents feature bloat and keeps them honest about "does this solve the validated pain point?"

### 2. Chris Richardson — Microservices Patterns (Multi-Tier Evolution)

**Claim**: **Start monolithic, decompose incrementally**. Premature microservices create distributed debugging hell. Use **logical boundaries** (API contracts, bounded contexts) even in a monolith to enable future decomposition.

**Evidence**: *Microservices Patterns* (2018) — Richardson's "Strangler Fig" pattern shows how to evolve from monolith → service-oriented → event-driven without rewriting. Logical decoupling ≠ physical decoupling on Day 1.

{: .warning }
> **Critique**: **Students over-optimize architecture**. They'll read "multi-tier" and immediately build 5 Docker containers. The framework doesn't say *when* to decompose — only *how*.

{: .note }
> **When It Applies**: **A4–A6** enforce logical boundaries (e.g., frontend calls backend via REST API, even if both run in one process). **A7–A8** introduce decomposition (e.g., separate auth service, async job queue). **A9** should be production-ready but not necessarily microservices.

### 3. Eric Ries — Validated Learning & Build-Measure-Learn

**Claim**: **Each sprint must answer one risky assumption**. If you're building features without a hypothesis (e.g., "users will abandon the flow if auth takes >3 clicks"), you're guessing.

**Evidence**: *The Lean Startup* (2011) — Ries formalized the feedback loop used at IMVU, Dropbox, and Zappos. Every sprint should have a **learning goal** (not just a feature goal).

{: .warning }
> **Critique**: **Assumes users exist**. For student projects in CSC454, "validation" often means "we built it and it didn't crash" — not real user testing. Framework breaks if you fake the data.

{: .note }
> **When It Applies**: **A4** = proof-of-concept (Does the core interaction work?). **A5** = proof-of-value (Do users complete the CUJ?). **A6–A8** = specific hypotheses (e.g., "adding real-time sync reduces friction by 40%"). **A9** = beta validation with external users.

---

## ACTIONABLE RECOMMENDATIONS

### 1. Define Explicit Validation Gates

Each assignment must have a **go/no-go decision criterion**:

- **A4**: Does the surface product prove the technical concept is feasible? (Gate: working prototype + CUJ baseline)
- **A5**: Does the core feature prove users can complete the primary task? (Gate: <2 severe friction points in CUJ)
- **A6**: Does the architecture support the next layer of complexity? (Gate: diagram shows data/control plane decoupling)
- **A8**: Can the system handle realistic load? (Gate: observability or stress test results)
- **A9**: Is the beta release publicly demoable? (Gate: zero hardcoded secrets, CI/CD functional, live URL)

**Rationale**: Without gates, students will add features without validating prior assumptions (per Ries). This forces **forward fixing** over **premature optimization**.

### 2. Architectural Deep-Dive Rotation

Each demo **magnifies one architectural dimension**:

- **A4**: API contract design (REST or GraphQL schema documentation)
- **A5**: State management (database schema, caching strategy)
- **A6**: Async workflows (background jobs, event queues)
- **A7**: Security & secrets (auth flows, secret rotation)
- **A8**: Observability (structured logging, error tracking)
- **A9**: Horizontal scaling readiness (stateless design, load balancer topology)

**Rationale**: Per Richardson, students must **think like architects** by adding **one layer of complexity per sprint** — not bolting everything on at the end.

### 3. CUJ Evolution Tracker

Mandate a **cumulative CUJ document** (Markdown table) that grows each sprint:

- **A4**: Baseline CUJ (user persona, goal, initial friction count)
- **A5**: Updated CUJ (friction reduction delta, new context switches)
- **A6–A8**: Friction severity trends (are you fixing or adding complexity?)
- **A9**: Final CUJ (target: <1 severe friction point, total time <50% of A4 baseline)

**Rationale**: Per Torres, **continuous discovery** means CUJ is a living artifact. If students don't track friction progression, they'll confuse "more features" with "better product."

---

## ASSUMPTIONS & LIMITS

1. **Assumes students have functional CSC454 product ideas**. If their business concept is vague, they'll build random features to hit deadlines.
2. **Assumes GitHub Actions literacy from A3**. If they struggled with CI/CD in A3, scaling it to A9 will be brutal.
3. **Assumes access to real users for validation**. If students fake CUJ data, the framework collapses into theater.
4. **No guidance on pivot triggers**. If proof-of-concept fails at A4, do they switch ideas or double down?

---

## DISAGREEMENT / FAILURE MODES

### Where This Breaks

1. **A6–A8 Scope Creep**: Without tight gates, students will add "cool" features instead of architectural maturity (e.g., adding social login instead of instrumenting latency).
2. **CUJ Fabrication**: If students don't test with real users, CUJ becomes creative writing. Torres' framework assumes honest friction measurement.
3. **Architectural Over-Engineering**: Richardson's patterns are for **scaling** problems. Students will prematurely decompose into microservices, creating distributed system chaos they can't debug.

### When to Reject This Approach

- If CSC454 projects are **research prototypes** (not user-facing products), continuous discovery is overkill. Switch to **technical feasibility proofs** instead of CUJ.
- If students lack **deployment infrastructure** (e.g., no cloud credits), A9 beta release becomes impossible. You'd need to downgrade to "deployment-ready architecture diagram."

---

## SOURCES

1. Torres, T. (2021). *Continuous Discovery Habits*. Product Talk LLC. [Framework for weekly evidence-based product decisions]
2. Richardson, C. (2018). *Microservices Patterns*. Manning Publications. [Strangler Fig pattern, logical vs. physical decomposition]
3. Ries, E. (2011). *The Lean Startup*. Crown Business. [Build-Measure-Learn loop, validated learning gates]
4. Cagan, M. (2017). *Inspired: How to Create Tech Products Customers Love*. Wiley. [Product discovery vs. delivery cadence]
5. Blank, S. (2013). *The Four Steps to the Epiphany*. K&S Ranch. [Customer development framework for startups]

---

{: .highlight }
**NEXT**: Confirm validation gate criteria (quantitative vs. qualitative) and architectural scaffolding constraints before I draft the five assignment specifications.
