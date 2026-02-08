---
title: Course Material Styling Guide
layout: default
parent: Course Material
nav_exclude: true
---

# Course Material Styling Guide
{: .no_toc }

Quick reference for custom styling classes used in course materials.

---

## Available Custom Styles

### 1. Lecture Title Header
Use for main page titles with special emphasis. Use `|` for line breaks within the title.

```markdown
# Cloud Architecture Design: From Localhost to Production
{: .lecture-title }
```

Or with line breaks:

```markdown
# Cloud Architecture Design: | From Localhost to Production
{: .lecture-title }
```

### 2. Lecture Meta/Tagline
Use for course info, dates, instructor name. Use `|` for line breaks.

```markdown
**CSC491 - Capstone Project Design** | **Winter 2026** | Atoosa Nasiri
{: .lecture-meta }
```

### 3. Lecture Info Box
Use for important overview sections, key information blocks.

```markdown
{: .lecture-info }
> ### Lecture Overview
>
> **Objective:** Teach architectural thinking for cloud-native systems.
>
> **Core Question:** How do you architect a system that ships fast today but doesn't collapse when requirements change tomorrow?
```

### 4. Section Headers
Use for major section dividers with accent bar.

```markdown
## Section 1: Thinking Like an Architect
{: .section-header }
```

### 5. Callout Boxes
Use for key insights, important distinctions, emphasized statements.

```markdown
{: .callout-box }
> **The Service-Oriented Shift:** Stop thinking in features. Start thinking in services.
```

OR

```markdown
{: .callout-box }
> **Key Distinction:** Coding solves a problem once. Architecture solves a problem repeatedly, under variable load, across failure modes, with maintainers who aren't you.
```

### 6. Framework Boxes
Use for structured content sections with headers. Great for comparison tables, multi-part concepts, or organized content blocks.

```markdown
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
> **Software Thinking:** Tools—the libraries and frameworks I use.
>
> **Architecture Thinking:** Service orchestration and integration.
```

---

## Combined Example

```markdown
---
title: Cloud Architecture Design
layout: default
parent: Course Material
nav_order: 2
---

# Cloud Architecture Design: From Localhost to Production
{: .lecture-title }

**CSC491 - Capstone Project Design**
**Winter 2026**
Atoosa Nasiri
{: .lecture-meta }

{: .lecture-info }
> ### Lecture Overview
>
> **Objective:** Teach architectural thinking for cloud-native systems.

## Section 1: Thinking Like an Architect
{: .section-header }

You've written code that works on your laptop. But when you architect systems, you're optimizing for "does it survive?"

{: .callout-box }
> **Key Distinction:** Coding solves a problem once. Architecture solves a problem repeatedly.
```

---

## Notes

- All styles use Just the Docs color variables, so they automatically adapt to dark mode
- Monospace font fallbacks ensure compatibility across systems
- IAL syntax `{: .classname }` must appear **immediately after** the element (no blank lines)
- Use `>` blockquote syntax with callout boxes, lecture-info, and framework boxes for proper rendering
- Use `|` for line breaks in `.lecture-title` and `.lecture-meta` instead of multiple text lines
- Table of contents is limited to h1 and h2 headings site-wide (configured in _config.yml)
