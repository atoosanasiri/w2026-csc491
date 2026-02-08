---
title: "Actionable Recommendations"
layout: default
parent: "Product Development Framework"
grand_parent: "Course Material"
nav_order: 3
---

## Actionable Recommendations
{: .section-header }

### Validation Gates

{: .callout-box }
> **The Rule:** Each assignment must have a go/no-go decision criterion. Without gates, students add features without validating prior assumptions.

{: .framework-box }
> #### Sprint Validation Gates
>
> - **A4**: Does the surface product prove the technical concept is feasible? (Gate: working prototype + CUJ baseline)
> - **A5**: Does the core feature prove users can complete the primary task? (Gate: <2 severe friction points in CUJ)
> - **A6**: Does the architecture support the next layer of complexity? (Gate: diagram shows data/control plane decoupling)
> - **A8**: Can the system handle realistic load? (Gate: observability or stress test results)
> - **A9**: Is the beta release publicly demoable? (Gate: zero hardcoded secrets, CI/CD functional, live URL)

**Rationale**: Without gates, students will add features without validating prior assumptions (per Ries). This forces **forward fixing** over **premature optimization**.

---

### Architectural Deep-Dive Rotation

{: .callout-box }
> **The Rule:** Each demo magnifies one architectural dimension. One layer of complexity per sprint — not everything bolted on at the end.

{: .framework-box }
> #### Sprint Architecture Focus
>
> - **A4**: API contract design (REST or GraphQL schema documentation)
> - **A5**: State management (database schema, caching strategy)
> - **A6**: Async workflows (background jobs, event queues)
> - **A7**: Security & secrets (auth flows, secret rotation)
> - **A8**: Observability (structured logging, error tracking)
> - **A9**: Horizontal scaling readiness (stateless design, load balancer topology)

**Rationale**: Per Richardson, students must **think like architects** by adding **one layer of complexity per sprint** — not bolting everything on at the end.

---

### CUJ Evolution Tracker

{: .callout-box }
> **The Rule:** Mandate a cumulative CUJ document (Markdown table) that grows each sprint. If students don't track friction progression, they'll confuse "more features" with "better product."

{: .framework-box }
> #### Sprint CUJ Milestones
>
> - **A4**: Baseline CUJ (user persona, goal, initial friction count)
> - **A5**: Updated CUJ (friction reduction delta, new context switches)
> - **A6–A8**: Friction severity trends (are you fixing or adding complexity?)
> - **A9**: Final CUJ (target: <1 severe friction point, total time <50% of A4 baseline)

**Rationale**: Per Torres, **continuous discovery** means CUJ is a living artifact. If students don't track friction progression, they'll confuse "more features" with "better product."

---

[Previous: Expert Frameworks](expert-frameworks){: .btn .float-left }
[Next: Assumptions & Failure Modes](assumptions-and-failure-modes){: .btn .btn-primary .float-right }
