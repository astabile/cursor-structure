# Workflow

## Development Flow
1. Pull latest from `dev`
2. Create feature branch: `feature/description`
3. Develop + test locally (`php artisan serve`)
4. Run tests before considering done: `php artisan test`
5. Self-review before asking agent for review
6. Merge to `dev` when ready
7. Deploy to staging from `dev` for QA
8. Merge to `main` for production only after QA sign-off

## Agent Collaboration Rules
- Agent NEVER commits or pushes — that's always manual
- Agent NEVER runs migrations without asking first
- Agent NEVER runs `composer require` without approval
- Agent asks before making changes across more than 3 files
- If context seems lost, re-read `conductor/` files before continuing

## Task Breakdown
- Break work into small, focused tasks — one concern at a time
- Finish and verify one task before starting the next
- When stuck, stop and ask rather than guessing

## Code Review Checklist (before merging)
- [ ] No hardcoded secrets or credentials
- [ ] No `dd()`, `dump()`, or `var_dump()` left in code
- [ ] All inputs validated via Form Requests
- [ ] Migrations are reversible (has `down()` method)
- [ ] New routes are protected by appropriate middleware
- [ ] Follows naming and folder conventions
- [ ] No N+1 queries (use `with()` eager loading)

## Deployment
- Dev → local only (`php artisan serve`)
- Staging → deployed from `staging` branch (Forge / Envoyer / manual)
- Production → manual deploy from `main` after approval
