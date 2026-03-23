# Architecture Decisions Log

> This file prevents re-debating decisions already made.
> Before proposing a change to any of these, read this file first.

---

## Template — copy this format for each decision

### [YYYY-MM-DD] Decision Title
**Decision:** What was decided  
**Reason:** Why this was chosen over alternatives  
**Alternatives considered:** What else was evaluated  
**Status:** Active / Superseded  

---

## Decisions

### [YYYY-MM-DD] Example: Service Layer
**Decision:** All business logic lives in Service classes — controllers are thin  
**Reason:** Keeps controllers testable and single-purpose, business logic reusable across jobs/commands  
**Alternatives considered:** Fat controllers (rejected — not scalable), Repository pattern (too heavy for this scope)  
**Status:** Active

---
<!-- Add new decisions above this line -->
