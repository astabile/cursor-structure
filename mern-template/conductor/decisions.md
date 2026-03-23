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

### [YYYY-MM-DD] Example: State Management
**Decision:** React Query for server state, React Context for UI state — no Redux  
**Reason:** Reduces boilerplate, React Query handles caching/loading/error states natively  
**Alternatives considered:** Redux Toolkit (too heavy for this scope), Zustand (considered for v2)  
**Status:** Active

---
<!-- Add new decisions above this line -->
