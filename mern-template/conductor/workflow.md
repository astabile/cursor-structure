# Workflow

## Development Flow
1. Pull latest from `dev`
2. Create feature branch: `feature/description`
3. Develop + test locally
4. Self-review before asking agent for review
5. Merge to `dev` when ready
6. Deploy to staging from `dev` for QA
7. Merge to `main` for production only after QA sign-off

## Agent Collaboration Rules
- Agent NEVER commits or pushes — that's always manual
- Agent NEVER installs packages without asking first
- Agent asks before making changes across more than 3 files
- If context seems lost, re-read `conductor/` files before continuing

## Task Breakdown
- Break work into small, focused tasks — one concern at a time
- Finish and verify one task before starting the next
- When stuck, stop and ask rather than guessing

## Code Review Checklist (before merging)
- [ ] No hardcoded secrets or credentials
- [ ] No `console.log` left in production code
- [ ] All new functions have proper TypeScript types
- [ ] Error handling is explicit
- [ ] No unused imports or variables
- [ ] Follows folder/naming conventions

## Deployment
- Dev → local only
- Staging → deployed automatically from `dev` (or manually)
- Production → manual deploy from `main` after approval
