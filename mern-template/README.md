# MERN Stack — Cursor Project Template

Cursor agent setup for **MongoDB + Express + React + Node.js + TypeScript** projects.

---

## Project Setup Checklist

Do this once when starting a new project:

- [ ] Copy this template into your project root
- [ ] Run `cp .env.example .env` and fill in real values
- [ ] Run `npm run install:all` to install all dependencies
- [ ] Fill in `conductor/product.md` — what is this product and who uses it?
- [ ] Fill in `conductor/tech-stack.md` — exact versions, infra, env var keys
- [ ] Fill in `.cursor/rules/architecture.mdc` — folder structure, key decisions, off-limits areas
- [ ] Set MCP env vars in `.cursor/mcp.json` (`GITHUB_TOKEN`, `MONGO_URI`, `PROJECT_ROOT`)
- [ ] Log your first decisions in `conductor/decisions.md`
- [ ] Run `npm run dev` — starts client + server concurrently

---

## Project Structure

```
mern-template/
├── client/                        ← React + Vite + TypeScript
│   └── src/
│       ├── assets/                ← Images, fonts, static files
│       ├── components/            ← Reusable UI components
│       ├── hooks/                 ← Custom React hooks
│       ├── pages/                 ← Route-level components
│       ├── services/              ← API call wrappers (axios)
│       ├── store/                 ← Global state (Context / Zustand)
│       ├── types/                 ← Frontend TypeScript types
│       └── utils/                 ← Pure helper functions
│
├── server/                        ← Express + Node.js + TypeScript
│   └── src/
│       ├── config/                ← DB connection, env config, constants
│       ├── controllers/           ← Request/response handlers (thin)
│       ├── middleware/            ← Auth, error handler, logger
│       ├── models/                ← Mongoose schemas + interfaces
│       ├── routes/                ← Route definitions
│       ├── services/              ← Business logic
│       └── utils/                 ← Pure helper functions
│
├── shared/                        ← Types shared between client + server
│   └── types/
│
├── .cursor/                       ← Cursor agent setup
│   ├── settings.json              ← Agent permissions + blocked commands
│   ├── mcp.json                   ← MCP servers: GitHub, filesystem, MongoDB
│   ├── rules/                     ← Always-on agent rules
│   ├── skills/                    ← Scaffolding skills + code review
│   └── plugins/manifest.json      ← Skill and rule index
│
├── conductor/                     ← Project context for the agent
│   ├── product.md
│   ├── tech-stack.md
│   ├── workflow.md
│   └── decisions.md
│
├── .env.example                   ← Copy to .env and fill in values
├── .gitignore
└── package.json                   ← Root scripts (dev, build, install:all)
```

---

## Getting Started

```bash
# 1. Install all dependencies (root + client + server)
npm run install:all

# 2. Set up environment
cp .env.example .env

# 3. Start dev servers (client + server concurrently)
npm run dev
```

| Command | What it does |
|---------|-------------|
| `npm run dev` | Starts client (Vite) + server (nodemon) concurrently |
| `npm run dev:client` | Client only — http://localhost:5173 |
| `npm run dev:server` | Server only — http://localhost:5000 |
| `npm run build` | Builds client + server for production |

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
