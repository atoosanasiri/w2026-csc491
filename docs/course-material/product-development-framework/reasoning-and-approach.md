---
title: "Reasoning & Approach"
layout: default
parent: "Product Development Framework"
grand_parent: "Course Material"
nav_order: 1
---

## Reasoning & Approach
{: .section-header }

### Reasoning Outline

{: .framework-box }
> #### Expert Selection
>
> Drew from product engineering (Marty Cagan, Teresa Torres), technical architecture (Chris Richardson), and startup methodology (Steve Blank, Eric Ries) — all have published rigorous frameworks on iterative product development and evidence-based validation.
>
> #### Framework Prioritization
>
> Focused on (a) continuous discovery frameworks that align CUJ evolution with feature sequencing, (b) multi-tier architectural thinking vs. modular decomposition, and (c) evidence-driven sprint gating (proof-of-concept → proof-of-value → beta).
>
> #### Source Constraints
>
> Cited published books, research papers from IEEE/ACM, and vendor-neutral architecture documentation. Avoided blog-level content.
>
> #### Gap Identification
>
> The A2/A3 assignments are **tactically sound** but lack explicit **validation gates** and **architectural maturity progression** across sprints. The 10-week cycle demands **incremental complexity scaling** — each demo must add one architectural dimension (e.g., state management → observability → horizontal scaling).
>
> #### Pedagogical Alignment
>
> Maintained a no-filler, evidence-first tone. Applied the rubric structure (functionality, operational logic, audit trail, narrative defense) to each new assignment.

---

### Targeted Questions

{: .callout-box }
> **These design questions must be resolved before drafting assignment specifications.**

1. **Validation Rigor**: Do you want students to define **quantitative success metrics** (e.g., latency <200ms, task completion time reduction) for each sprint, or is qualitative CUJ friction analysis sufficient?

2. **Architectural Scaffolding**: Should A4 enforce a **specific architectural pattern** (e.g., event-driven, CQRS, microservices-lite) as a forcing function, or do students choose based on their CSC454 product constraints?

3. **Deployment Maturity**: By A9 (Beta Release), do you expect **production-grade observability** (logging, monitoring, alerting) or just functional deployment + CI/CD?

---

[Next: Expert Frameworks](expert-frameworks){: .btn .btn-primary .float-right }
