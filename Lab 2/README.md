# 📘 COM311 – Week 2 & 3 Manual

## Development Phase

---

## 🎯 Goal

Over Weeks 2 and 3, your team will **implement the system skeleton and complete the core features**. By the end of Week 3, you should have a working mini e-commerce flow:

* Browse products
* Place an order
* Process a simulated payment
* Confirm the order and reduce stock

This is the **development phase** of the project.

---

## 📅 Week 2 – Development Sprint 1 (Skeleton System)

### Objectives

* Build a running system skeleton using **docker-compose**.
* Expose `/healthz` endpoints for all services.
* Implement stubbed endpoints and wire services through the **Gateway**.
* Demonstrate a simple happy-path order returning a `PENDING` status.

### Deliverables

* **Frontend**: Simple page (mocked product list, “Place Order” button).
* **Orders Service**: `POST /orders` returns `{orderId, status: PENDING}`.
* **Inventory Service**: Exposes `/healthz`, stubs for `GET /inventory/{id}`.
* **Payments Service**: Exposes `/healthz`, stub for `POST /payments/charge`.
* **Gateway**: Nginx config routing `/orders/*`, `/inventory/*`, `/payments/*`.
* **docker-compose.yml**: Spins up all services + Postgres.

### Acceptance Criteria

* `docker compose up` runs from a clean clone.
* All services respond `200 OK` on `/healthz` via Gateway.
* `POST /orders` returns a valid JSON response with status `PENDING`.
* Each team member has merged at least 2 reviewed PRs.

---

## 📅 Week 3 – Development Sprint 2 (Feature Complete)

### Objectives

* Implement **real logic** for orders, inventory, and payments.
* Connect Inventory to Postgres (read/write products and stock).
* Make Payments return **realistic results** (success, failed, pending).
* Update Orders to orchestrate calls to Inventory + Payments.
* Frontend connects to Orders API and shows order status.
* Add minimal JSON logging for debugging.

### Deliverables

* **Frontend**: Calls Orders API, displays order result (`CONFIRMED`, `CANCELLED`, etc.).
* **Orders**: Implements full flow:

  * Validate stock (via Inventory)
  * Call Payments
  * Confirm or cancel order
  * Update Inventory if successful
* **Inventory**: Connects to Postgres, decrements stock on confirmed order.
* **Payments**: Returns outcome (rule-based or random simulation).
* **Gateway**: Routes traffic correctly.
* **Logs**: Each service logs structured JSON with `timestamp, level, msg`.

### Acceptance Criteria

* Manual end-to-end test works:

  * User places order in Frontend.
  * Orders Service orchestrates.
  * Payments responds.
  * Inventory decrements stock if payment success.
* OpenAPI docs updated to match implemented APIs.
* `.env.example` present (no secrets in repo).

---

## ✅ Hints for Weeks 2–3

* **Keep it simple**: One happy path first, then handle payment failure.
* **Divide work fairly**: Each person codes their own service + Dockerfile.
* **Think ahead**: Requirements must be verifiable later in testing (Week 4) and deployment (Week 5).
* **Pair up for reviews**: No PR should be merged without review.

---

## 📌 Summary

* **Week 2**: Skeleton system – everything runs in Docker, returns `PENDING`.
* **Week 3**: Feature complete – real flows, persistence, status updates.

By the end of Week 3, your project should be a **working mini e-commerce system** running with `docker compose up`.
