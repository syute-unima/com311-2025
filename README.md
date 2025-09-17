# 📘 COM311 – Software Engineering Lab Series  
## Welcome & Introduction

---

## 👋 Welcome
Dear Students,  

Welcome to **COM311 – Software Engineering**. Over the next 6 weeks, you will work together in small teams to design, build, test, and deploy a **mini e-commerce checkout system** using modern software engineering tools and practices.  

This is not a traditional exam-based course. Instead, you will **learn by doing**. You will design requirements, write code, collaborate in teams, manage pull requests, set up automated tests, build CI pipelines, containerize applications, and finally deploy everything to a Kubernetes cluster.  

By the end of this journey, you will have built and deployed a small but **complete software system** that mirrors the workflows used by modern software teams around the world.  

---

## 🏗️ What We’re Building
You will develop a **Mini E-Commerce System** where a user can:
1. Browse a list of products.  
2. Place an order.  
3. Make a (simulated) payment.  
4. Receive confirmation of the order.  

To make this work, the project is split into **five components**:
1. **Frontend** – A simple web interface for browsing and ordering.  
2. **Orders Service** – Orchestrates order creation and status.  
3. **Inventory Service** – Manages products and stock (with a Postgres database).  
4. **Payments Service** – Simulates a payment gateway (success, failed, pending).  
5. **Gateway** – A router (Nginx) that directs traffic to the correct service.  

Each team will have **five members**. Each member will take responsibility for one of the components. If there are six people in a team, the sixth will act as **QA/Testing lead**, supporting everyone with integration and test automation.  

---

## 🎯 What You Will Learn
Throughout this lab series, you will gain practical skills in:
- **Requirements engineering** – Writing clear, testable requirements.  
- **Team collaboration** – Using GitHub Issues, Pull Requests, and review workflows.  
- **API design** – Documenting APIs using OpenAPI and building services that interact.  
- **Testing** – Writing unit, integration, and contract tests; running them in CI.  
- **Continuous Integration (CI)** – Building pipelines with GitHub Actions.  
- **Containerization** – Packaging your applications into Docker images.  
- **Deployment** – Running your system in Kubernetes with health checks and configs.  

---

## 📅 The 6-Week Journey

### **Week 1 – Requirements & Architecture**
- Write **functional and non-functional requirements**.  
- Draft a simple **architecture document** with diagrams, API stubs, and data models.  
- Set up your GitHub repository with roles, issues, and PR policies.  
- No coding yet—just planning and design.  

### **Week 2 – Development Sprint 1 (Skeleton System)**
- Implement health check endpoints for each service.  
- Connect everything with **docker-compose**.  
- Demonstrate a basic “happy path” where an order returns a pending status.  

### **Week 3 – Development Sprint 2 (Feature Complete)**
- Implement real logic in Orders, Inventory, and Payments.  
- Persist product stock in Postgres.  
- Frontend connects to backend APIs and shows order status.  
- End-to-end ordering works.  

### **Week 4 – Testing & CI**
- Write unit, integration, and API contract tests.  
- Set up GitHub Actions CI to run tests automatically on Pull Requests.  
- Add a coverage badge and enforce passing tests before merges.  

### **Week 5 – Deployment**
- Package each service in Docker (multi-stage builds).  
- Deploy services to Kubernetes using manifests and Ingress.  
- Demonstrate health checks and end-to-end flow in the cluster.  

### **Week 6 – Demo & Reflection**
- Perform resilience tests (restart a service and see recovery).  
- Run performance smoke tests.  
- Write a short **postmortem report**: what worked, what failed, what you learned.  
- Final presentation & demo to the class.  

---

## ✅ Expectations
- **Teamwork**: Everyone must contribute; no one should be idle.  
- **Pull Requests**: All code changes go through PRs and require review.  
- **Documentation**: Keep requirements, architecture, and PR policies up to date.  
- **Simplicity**: Do not over-engineer—keep APIs, schemas, and services small.  
- **Quality over quantity**: A working simple system is better than a broken complex one.  

---

## 📌 Important Notes
- You do not need advanced cloud accounts—everything runs **locally** with Docker and a lightweight Kubernetes (k3d or kind).  
- We will provide **starter templates** (compose files, API stubs, docs) to help you begin.  
- Weekly deliverables will be graded; missing a week makes it hard to catch up.  
- Ask questions early—this is about learning, not just delivering.  

---

## 🙌 Closing Remark
This lab is a chance to **practice the craft of software engineering in teams**. You will see how planning, testing, automation, and deployment all come together in real projects. The skills you learn here will be valuable not just for exams, but for your careers in software engineering.  

We are excited to see what you build. Let’s get started! 🚀  

