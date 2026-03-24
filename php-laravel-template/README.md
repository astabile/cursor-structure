# PHP / Laravel — Cursor Project Template

Cursor agent setup for **PHP 8.1+ + Laravel + MySQL/PostgreSQL** projects.

---

## Project Setup Checklist

Do this once when starting a new project:

- [ ] Run `laravel new project-name` to scaffold the Laravel app
- [ ] Copy `.cursor/` and `conductor/` folders into the project root
- [ ] Copy `.env.example` values into Laravel's `.env` and run `php artisan key:generate`
- [ ] Run `composer install && npm install`
- [ ] Fill in `conductor/product.md` — what is this product and who uses it?
- [ ] Fill in `conductor/tech-stack.md` — exact versions, infra, env var keys
- [ ] Fill in `.cursor/rules/architecture.mdc` — folder structure, key decisions, off-limits areas
- [ ] Set MCP env vars in `.cursor/mcp.json` (`GITHUB_TOKEN`, `DB_*` vars, `PROJECT_ROOT`)
- [ ] Log your first decisions in `conductor/decisions.md`
- [ ] Run `php artisan serve` — http://localhost:8000

---

## Project Structure

Laravel scaffolds its own structure via `laravel new`. This template adds the following on top:

```
your-laravel-project/
├── app/
│   ├── Http/
│   │   ├── Controllers/       ← Thin — delegate to Services
│   │   ├── Middleware/
│   │   ├── Requests/          ← Form Request validation classes
│   │   └── Resources/         ← API Resource JSON transformers
│   ├── Models/                ← Eloquent models
│   ├── Services/              ← ✅ Added — business logic layer
│   ├── Repositories/          ← ✅ Added — DB query abstraction (optional)
│   ├── Enums/                 ← ✅ Added — PHP 8.1 enums
│   ├── Jobs/
│   ├── Events/
│   └── Listeners/
│
├── database/
│   ├── migrations/
│   ├── seeders/
│   └── factories/
│
├── routes/
│   ├── api.php
│   └── web.php
│
├── resources/views/           ← Blade templates
│
├── .cursor/                   ← Cursor agent setup
│   ├── settings.json          ← Agent permissions + blocked commands
│   ├── mcp.json               ← MCP servers: GitHub, filesystem, MySQL
│   ├── rules/                 ← Always-on agent rules
│   ├── skills/                ← Scaffolding skills + code review
│   └── plugins/manifest.json  ← Skill and rule index
│
├── conductor/                 ← Project context for the agent
│   ├── product.md
│   ├── tech-stack.md
│   ├── workflow.md
│   └── decisions.md
│
└── .env.example               ← Reference for required env vars
```

---

## Getting Started

```bash
# 1. Create a new Laravel project
laravel new project-name
cd project-name

# 2. Copy template files into the project
cp -r /path/to/php-laravel-template/.cursor .
cp -r /path/to/php-laravel-template/conductor .

# 3. Install dependencies
composer install
npm install

# 4. Set up environment
cp .env.example .env
php artisan key:generate

# 5. Run migrations
php artisan migrate

# 6. Start dev server
php artisan serve
```

| Command | What it does |
|---------|-------------|
| `php artisan serve` | Start dev server — http://localhost:8000 |
| `php artisan make:model Name -m` | Create model + migration |
| `php artisan migrate` | Run pending migrations |
| `php artisan test` | Run test suite |
| `php artisan route:list` | List all registered routes |

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
