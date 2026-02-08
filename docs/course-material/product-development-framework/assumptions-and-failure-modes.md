---
title: "Assumptions & Failure Modes"
layout: default
parent: "Product Development Framework"
grand_parent: "Course Material"
nav_order: 4
---

## Assumptions & Failure Modes
{: .section-header }

### Assumptions & Limits

{: .callout-box }
> **Every framework has preconditions.** If these assumptions don't hold, the framework collapses.

1. **Assumes students have functional CSC454 product ideas**. If their business concept is vague, they'll build random features to hit deadlines.
2. **Assumes GitHub Actions literacy from A3**. If they struggled with CI/CD in A3, scaling it to A9 will be brutal.
3. **Assumes access to real users for validation**. If students fake CUJ data, the framework collapses into theater.
4. **No guidance on pivot triggers**. If proof-of-concept fails at A4, do they switch ideas or double down?

---

### Where This Breaks

{: .framework-box }
> #### Failure Modes
>
> - **A6–A8 Scope Creep**: Without tight gates, students will add "cool" features instead of architectural maturity (e.g., adding social login instead of instrumenting latency).
> - **CUJ Fabrication**: If students don't test with real users, CUJ becomes creative writing. Torres' framework assumes honest friction measurement.
> - **Architectural Over-Engineering**: Richardson's patterns are for **scaling** problems. Students will prematurely decompose into microservices, creating distributed system chaos they can't debug.

---

### When to Reject This Approach

{: .warning }
> If CSC454 projects are **research prototypes** (not user-facing products), continuous discovery is overkill. Switch to **technical feasibility proofs** instead of CUJ.

{: .warning }
> If students lack **deployment infrastructure** (e.g., no cloud credits), A9 beta release becomes impossible. You'd need to downgrade to "deployment-ready architecture diagram."

---

[Previous: Actionable Recommendations](actionable-recommendations){: .btn .float-left }
[Next: Sources & Bibliography](sources){: .btn .btn-primary .float-right }
