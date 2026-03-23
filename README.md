# Cursor Project Structure Templates

[![GitHub Stars](https://img.shields.io/github/stars/astabile/cursor-structure?style=flat&logo=github)](https://github.com/astabile/cursor-structure/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/astabile/cursor-structure?style=flat&logo=github)](https://github.com/astabile/cursor-structure/network/members)
[![Last Commit](https://img.shields.io/github/last-commit/astabile/cursor-structure?style=flat)](https://github.com/astabile/cursor-structure/commits/main)
[![Issues](https://img.shields.io/github/issues/astabile/cursor-structure?style=flat)](https://github.com/astabile/cursor-structure/issues)
[![License MIT](https://img.shields.io/badge/license-MIT-green?style=flat)](./LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-blue?style=flat)](#)
[![Templates](https://img.shields.io/badge/templates-2-orange?style=flat)](#templates)
[![Token Savings](https://img.shields.io/badge/TOKEN_SAVINGS-30%25+-brightgreen?style=flat)](#)

Two production-ready Cursor agent setup templates — one per stack. Copy the relevant one into your project root and follow the setup checklist inside.

## Templates

| Template | Stack | README |
|----------|-------|--------|
| `mern-template/` | MongoDB, Express, React, Node.js + TypeScript | [Setup guide](./mern-template/README.md) |
| `php-laravel-template/` | PHP 8.1+, Laravel, MySQL/PostgreSQL | [Setup guide](./php-laravel-template/README.md) |

## What's Inside Each Template

```
.cursor/
├── settings.json     ← Agent permissions + blocked commands
├── mcp.json          ← MCP servers (GitHub, filesystem, DB)
├── rules/            ← Always-on agent rules (core, git, conventions, architecture)
├── skills/           ← Stack-specific scaffolding skills + code review
└── plugins/
    └── manifest.json ← Skill and rule index

conductor/
├── product.md        ← What the product is
├── tech-stack.md     ← Exact versions and infra
├── workflow.md       ← Dev flow and deployment
└── decisions.md      ← Architectural decisions log
```

## Claude Code → Cursor Mapping

| Claude Code | Cursor Equivalent | Status |
|---|---|---|
| `CLAUDE.md` | `.cursor/rules/*.mdc` | ✅ |
| `.claude/settings.json` | `.cursor/settings.json` | ✅ |
| `commands/*.md` + `skills/` | `.cursor/skills/` | ✅ |
| `plugins/manifest.json` | `.cursor/plugins/manifest.json` | ✅ |
| `.mcp.json` | `.cursor/mcp.json` | ✅ |
| Hooks | `core.mdc` always-apply rules | ⚠️ Partial |
