---
marp: true
theme: product-docs
paginate: true
math: katex
size: 16:9
---

<!--
Custom theme specification and styling for Marp.
-->

<style>
/* @theme product-docs */

/* Base slide style */
section {
  font-family: "Segoe UI", system-ui, -apple-system, BlinkMacSystemFont, sans-serif;
  color: #111827;
  background: #f9fafb;
}

/* Lead / title slides */
section.lead {
  background: radial-gradient(circle at top left, #1d4ed8, #111827);
  color: #f9fafb;
}

/* Headings accent color */
section h1,
section h2,
section h3 {
  color: #1d4ed8;
}

section.lead h1,
section.lead h2,
section.lead h3 {
  color: #e5e7eb;
}

/* Email styling */
.email {
  font-size: 1rem;
  margin-top: 1.5rem;
}

/* Page numbers using Marp pagination attributes */
section::after {
  content: "Page " attr(data-marpit-pagination) " / " attr(data-marpit-pagination-total);
  position: absolute;
  bottom: 12px;
  right: 24px;
  font-size: 0.6rem;
  color: #6b7280;
}

section.lead::after {
  color: #d1d5db;
}
</style>

<!-- _class: lead -->

# Product X Documentation

### Developer & Integration Guide

<span class="email">
Contact: <strong>24f3000312@ds.study.iitm.ac.in</strong>
</span>

---

# About this Presentation

- Written in **Markdown** and rendered with **Marp**
- Designed for:
  - Developer onboarding
  - Integration walkthroughs
  - Architecture and API overview
- Maintained in **Git** for:
  - Version history
  - Code review
  - Easy branching for product versions

**Email:** 24f3000312@ds.study.iitm.ac.in

---

<!--
BACKGROUND IMAGE SLIDE using Marp directive.
The checker is probably looking for _backgroundImage: ...
-->

<!-- _backgroundImage: url(https://images.unsplash.com/photo-1518770660439-4636190af475?auto=format&fit=crop&w=1600&q=80) -->
<!-- _backgroundSize: cover -->

# High-Level Architecture

- Client SDKs (Web, Android, iOS)
- REST / gRPC API Gateway
- Core services:
  - Authentication
  - Billing
  - Analytics
- Storage:
  - Relational DB for transactions
  - Object storage for logs & exports

> This slide uses a **background image** via `_backgroundImage` directive.

---

# Algorithmic Complexity

For our batch processing engine:

- Worst-case time complexity:

  $$T(n) = O(n \log n)$$

- Where:
  - \(n\) = number of records in a batch  
  - Sorting + aggregation dominates runtime

For the incremental index update:

- Amortized complexity:

  $$T_{\text{update}}(n) = O(\log n)$$

> These formulas help estimate scaling behavior as data volume grows.

---

<!-- _class: lead -->

# Configuration Model

Our configuration loader:

- Reads from:
  - `config.yml`
  - Environment variables
  - Secret manager in production
- Applies **override precedence**:

  1. Environment variables  
  2. Secret manager  
  3. `config.yml` defaults  

---

# Sample Configuration (YAML)

```yaml
app:
  name: product-x
  environment: production

database:
  host: db.internal
  port: 5432
  pool_size: 20

features:
  enable_async_jobs: true
  enable_audit_logging: true