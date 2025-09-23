# 📘 COM311 – Week 1 Manual

## Requirements & Architecture

---

## 🎯 Goal

By the end of this week, your team will produce a **short requirements & architecture package** and prepare your GitHub repo for development.

This week is about **planning, not coding**. You will:

* Write clear **Functional** and **Non-Functional Requirements**.
* Draft a **simple architecture overview** (diagram, APIs, data model).
* Agree on **team workflow** (branching, PR policy, issues board).

> ⚠️ **Important Note:**
> Your requirements should be **testable**, because in **Week 4 (Testing)** and **Week 5 (Deployment)** you will be asked to **verify** that they are met.
>
> * Good FR: *“System shall allow creating an order with multiple products”* → Can be tested with an integration test.
> * Good NFR: *“Checkout flow completes in <2 seconds locally”* → Can be measured with a stopwatch or script.
> * Avoid vague statements like *“System should be fast”* or *“System should be user-friendly.”*

---

## 📂 Deliverables (Week 1)

Submit one GitHub repository containing:

1. **Requirements (`docs/REQS.md`)**

   * **5–7 Functional Requirements (FRs)**
   * **3–5 Non-Functional Requirements (NFRs)**

2. **Architecture (`docs/ARCHITECTURE.md`)**

   * One simple **diagram** (can be ASCII, draw\.io, or screenshot).
   * **1–2 sentences per component** describing responsibilities.
   * **API stubs**: list endpoints + sample requests/responses.
   * **Data model sketch**: products, orders, order\_items tables.

3. **Team Workflow (`docs/PR_POLICY.md`)**

   * Branch naming convention.
   * Review rules (2 reviewers).
   * Short “Definition of Done” checklist.

4. **GitHub Project Board**

   * At least **6–8 issues** with clear owners and deadlines.

---

## ✍️ Writing Requirements

### Functional Requirements (FRs)

* Focus on *what the system should do*.
* Be specific, measurable, and testable.

**Example FRs:**

* FR-1: The system shall allow a user to view a list of products with `id, name, price, available_qty`.
* FR-2: The system shall allow a user to place an order with one or more products.
* FR-3: The Orders Service shall check stock in the Inventory Service before confirming.
* FR-4: The Payments Service shall return one of `success | failed | pending`.
* FR-5: The Frontend shall display the final order status to the user.

### Non-Functional Requirements (NFRs)

* Describe *how the system should behave*.
* Keep them concrete and verifiable.

**Example NFRs:**

* NFR-1: Each service must expose `GET /healthz` that returns 200 within 300 ms.
* NFR-2: The happy-path checkout flow must complete in <2 seconds locally.
* NFR-3: The system must run with a single command: `docker compose up`.
* NFR-4: All logs must include `timestamp, level, msg` in JSON.

---

## 🏗️ Drafting the Architecture

### 1. Context Diagram

A simple diagram showing how the pieces connect:

```
[ User Browser ]
       ↓
   [ Frontend ]
       ↓
   [ Gateway ]
  ↙     ↓     ↘
[Orders] [Inventory] [Payments]
             ↓
         [ Postgres ]
```

### 2. Component Responsibilities

* **Frontend** – UI for browsing products and order status.
* **Orders** – Orchestrates order creation, checks stock, calls Payments.
* **Inventory** – Manages product catalog and stock (with Postgres).
* **Payments** – Simulates payment success/failure/pending.
* **Gateway** – Routes requests, no business logic.

### 3. API Stubs

Keep them short — just list the endpoints.

* **Orders**:

  * `POST /orders` → `{orderId, status}`
  * `GET /orders/{id}` → `{orderId, status}`

* **Inventory**:

  * `GET /inventory/{id}` → product details
  * `POST /inventory/reserve` → `{ok: true}`

* **Payments**:

  * `POST /payments/charge` → `{paymentId, status}`

### 4. Data Model

Minimal tables:

* `products(id, name, price, available_qty)`
* `orders(id, created_at, status)`
* `order_items(order_id, product_id, qty, price_at_order)`

---

## 🔄 Team Workflow

Create a file `docs/PR_POLICY.md` with:

```markdown
# Pull Request Policy

- Branch names: feat/<ticket>, fix/<ticket>, chore/<ticket>
- All PRs require at least 2 reviewers
- Definition of Done:
  - Code builds locally
  - /healthz endpoint works
  - Documentation updated
```

Also:

* Use GitHub Issues for tasks (6–8 issues this week).
* Use a GitHub Project Board to track progress.

---

## 📅 Suggested Timeline (Week 1)

* **Day 1–2:** Draft Functional + Non-Functional Requirements.
* **Day 3:** Draw context diagram, assign roles.
* **Day 4:** Define APIs + data model.
* **Day 5:** Finalize documents, create project board, submit repo link.

---

## ✅ Acceptance Criteria

* REQS.md includes 5–7 FRs and 3–5 NFRs (all testable).
* ARCHITECTURE.md includes diagram, components, API stubs, and data model.
* PR\_POLICY.md exists with rules and checklist.
* GitHub Project Board has 6–8 issues with owners.

---

## 📌 Hints

* **Keep it small**: focus on the happy path (browse → order → pay → confirm).
* **Don’t over-engineer**: no discounts, shipping, or auth in Week 1.
* **Think ahead**: every requirement should be verifiable in Week 4 (tests) or Week 5 (deployment).
* **Everyone contributes**: docs, diagram, PRs, and issues.
