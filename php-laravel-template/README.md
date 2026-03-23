# PHP / Laravel — Cursor Project Template

Cursor agent setup for **PHP 8.1+ + Laravel + MySQL/PostgreSQL** projects.

---

## Project Setup Checklist

Do this once when starting a new project:

- [ ] Fill in `conductor/product.md` — what is this product and who uses it?
- [ ] Fill in `conductor/tech-stack.md` — exact versions, infra, env var keys
- [ ] Fill in `.cursor/rules/architecture.mdc` — folder structure, key decisions, off-limits areas
- [ ] Set MCP env vars in `.cursor/mcp.json` (`GITHUB_TOKEN`, `DB_*` vars, `PROJECT_ROOT`)
- [ ] Log your first decisions in `conductor/decisions.md`

---

## Structure

```
.cursor/
├── settings.json          ← Agent permissions + blocked commands (git commit, push, migrate:fresh...)
├── mcp.json               ← MCP servers: GitHub, filesystem, MySQL
├── rules/
│   ├── core.mdc           ← Non-negotiable agent rules (always applied)
│   ├── git.mdc            ← Branch strategy + what agent can/cannot do with git
│   ├── conventions.mdc    ← PHP/Laravel naming, folder structure, PSR-12, strict types
│   └── architecture.mdc   ← Fill in: stack versions, environments, off-limits areas
├── skills/
│   ├── create-controller/     ← Scaffold Controller + Service + FormRequest
│   ├── create-migration/      ← Generate migration with reversible down() method
│   ├── create-api-resource/   ← Scaffold API Resource JSON transformer
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
| Run migrations | Only with explicit approval |
| Install packages (Composer) | Always asks first |
| Large changes (3+ files) | Summarizes plan and waits for approval |
| Ambiguous tasks | Asks one clarifying question before starting |

---

## Available Skills

| Skill | Trigger phrase |
|-------|----------------|
| Create Laravel controller | "create controller", "new endpoint", "scaffold resource" |
| Create migration | "create migration", "new table", "add column" |
| Create API resource | "create resource", "JSON transformer", "response formatter" |
| Code review | "review this", "code review" |

---

## MCP Servers Configured

| Server | Purpose | Requires |
|--------|---------|---------|
| `github` | PR/issue/repo access | `GITHUB_TOKEN` |
| `filesystem` | Scoped file access | `PROJECT_ROOT` |
| `mysql` | Direct DB queries | `DB_HOST`, `DB_USERNAME`, `DB_PASSWORD`, `DB_DATABASE` |

---

## Keeping It Updated

| File | Update when |
|------|-------------|
| `conductor/decisions.md` | After any significant architectural decision |
| `conductor/tech-stack.md` | When adding or changing dependencies/infra |
| `.cursor/rules/architecture.mdc` | When project structure or patterns evolve |
| `.cursor/skills/` | When repeating the same scaffolding instructions |
