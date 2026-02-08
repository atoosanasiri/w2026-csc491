---
title: "Advanced Architectural Patterns"
layout: default
parent: "Cloud Architecture Design"
nav_order: 3
---

## Advanced Architectural Patterns

### Decoupled Foundations: API Gateway Pattern

**API Gateway as System Boundary:** A single entry point that handles:

- **Authentication/authorization** — token validation before requests hit backend
- **Rate limiting** — prevent abuse without touching application code
- **Request routing** — `/api/users` → User Service, `/api/reports` → Analytics Service
- **Protocol translation** — HTTP → gRPC, REST → GraphQL

**Why this matters:** Your backend doesn't handle auth logic, your frontend doesn't know service topology—the gateway is the contract.

---

### Static vs. Dynamic Separation: CDN/Edge Delivery

Your HTML, CSS, JavaScript, and images should never be served from your application server.

**The pattern:**

- **Static assets:** S3 + CloudFront, or Netlify → Globally distributed, cached at edge
- **Dynamic API:** Lambda/Cloud Run behind API Gateway → Handles business logic, database queries

**Why separate?** Static content scales infinitely at near-zero cost. Dynamic content is expensive and stateful. Don't pay compute costs to serve a logo.

{: .note }
> **For the testbed:** Choose infrastructure that matches your web app's requirements—static hosting for frontend, serverless or containerized compute for backend, and managed database for persistence. Prioritize services with free tiers, automatic scaling, and minimal operational overhead to focus on building features rather than managing infrastructure.

---

### Beyond Request-Response: Event-Driven Architecture

**The Problem with Synchronous Everything:**

User uploads CSV → API validates → processes 10,000 rows → writes to database → returns response.

If processing takes 30 seconds, the HTTP request times out. User sees an error. Data may or may not have been saved.

**Event-Driven Solution:**

User uploads CSV → API returns "Processing started, job ID: 12345" immediately → Background worker processes file → Sends notification when complete.

#### Message Queues as Decoupling Layer

**Pattern:** API publishes message to queue (SQS, Pub/Sub, RabbitMQ). Worker subscribes to queue, processes asynchronously.

**Benefits:**

- API stays responsive (returns instantly)
- Workers scale independently of API
- Failed jobs retry automatically
- No lost work if API crashes mid-processing

**When to use:** Long-running tasks (report generation, data imports, email sends), batch processing, integration with third-party APIs with unreliable uptime.

---

### Edge Computing: Bring Logic Closer to Users (Advanced)

**Traditional:** User in Tokyo → request crosses Pacific → hits US data center → returns.

**Edge:** User in Tokyo → request hits Tokyo edge node → logic executes locally → returns (10ms vs. 200ms).

**What runs at the edge:**

- Authentication checks
- A/B test routing
- Geo-based content serving
- Simple transformations (resize images, filter responses)

**What doesn't:** Stateful operations, complex business logic, database writes.

{: .warning }
> **For the testbed:** Edge is overkill for a simple web app with localized users. Prioritize it only if you expect globally distributed traffic or need ultra-low latency.

---

[Previous: Pre-Selection Analysis](pre-selection-analysis){: .btn .float-left }
[Next: Operational Excellence](operational-excellence){: .btn .btn-primary .float-right }
