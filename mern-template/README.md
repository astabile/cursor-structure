# MERN Stack — Cursor Project Template

Cursor agent setup for **MongoDB + Express + React + Node.js + TypeScript** projects.

---

## Project Setup Checklist

Do this once when starting a new project:

- [ ] Fill in `conductor/product.md` — what is this product and who uses it?
- [ ] Fill in `conductor/tech-stack.md` — exact versions, infra, env var keys
- [ ] Fill in `.cursor/rules/architecture.mdc` — folder structure, key decisions, off-limits areas
- [ ] Set MCP env vars in `.cursor/mcp.json` (`GITHUB_TOKEN`, `MONGO_URI`, `PROJECT_ROOT`)
- [ ] Log your first decisions in `conductor/decisions.md`

---

## Structure

```
.cursor/
├── settings.json          ← Agent permissions + blocked commands (git commit, push, rm -rf...)
├── mcp.json               ← MCP servers: GitHub, filesystem, MongoDB
├── rules/
│   ├── core.mdc           ← Non-negotiable agent rules (always applied)
│   ├── git.mdc            ← Branch strategy + what agent can/cannot do with git
│   ├── conventions.mdc    ← TypeScript, React, Express naming + folder conventions
│   └── architecture.mdc   ← Fill in: stack versions, environments, off-limits areas
├── skills/
│   ├── create-component/      ← Scaffold React component (ui / feature / page)
│   ├── create-api-route/      ← Scaffold Express route + controller + service
│   ├── create-mongoose-model/ ← Scaffold Mongoose schema + TypeScript interface
│   └── code-review/           ← Review files against project conventions
└── plugins/
    └── manifest.json          ← Index of all skills and rules

conductor/
├── product.md       ← What the product does, target users, goals
├── tech-stack.md    ← Exact versions, infrastructure, env var keys
├── workflow.md      ← Dev flow, branch strategy, deployment, review checklist
└── decisions.md     ← Architectural decisions log (prevents re-debating)
```

---

## Agent Rules Summary

| Rule | Behavior |
|------|----------|
| Git commits | Never — you commit manually |
| Git push | Never — you push manually |
| Delete files | Only with explicit confirmation |
| Install packages | Always asks first |
| Large changes (3+ files) | Summarizes plan and waits for approval |
| Ambiguous tasks | Asks one clarifying question before starting |

---

## Available Skills

| Skill | Trigger phrase |
|-------|----------------|
| Create React component | "create component", "new component" |
| Create API route | "create route", "new endpoint" |
| Create Mongoose model | "create model", "new schema" |
| Code review | "review this", "code review" |

---

## MCP Servers Configured

| Server | Purpose | Requires |
|--------|---------|---------|
| `github` | PR/issue/repo access | `GITHUB_TOKEN` |
| `filesystem` | Scoped file access | `PROJECT_ROOT` |
| `mongodb` | Direct DB queries | `MONGO_URI` |

---

## Keeping It Updated

| File | Update when |
|------|-------------|
| `conductor/decisions.md` | After any significant architectural decision |
| `conductor/tech-stack.md` | When adding or changing dependencies/infra |
| `.cursor/rules/architecture.mdc` | When project structure or patterns evolve |
| `.cursor/skills/` | When repeating the same scaffolding instructions |
