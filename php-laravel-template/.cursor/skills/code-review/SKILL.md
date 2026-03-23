# Skill: Code Review

## Trigger
Use when asked to review code, check a file, or verify something before committing.

## Instructions

Review the specified file(s) against the following checklist and report findings grouped by severity.

### 🔴 Critical (must fix before merging)
- [ ] Hardcoded secrets, credentials, or API keys
- [ ] SQL injection via raw queries without bindings
- [ ] Missing authentication/authorization on protected routes
- [ ] Business logic inside controllers (should be in Services)
- [ ] Direct `$request->input()` without Form Request validation
- [ ] Missing `declare(strict_types=1)`

### 🟡 Important (should fix)
- [ ] N+1 queries — missing `with()` eager loading
- [ ] `dd()`, `dump()`, or `var_dump()` left in code
- [ ] Migration missing `down()` method
- [ ] Model missing `$fillable` or `$guarded`
- [ ] Raw `DB::` queries where Eloquent would be cleaner and safer
- [ ] Missing return types on methods
- [ ] Exception not caught or logged

### 🟢 Minor (nice to fix)
- [ ] Naming doesn't follow project conventions
- [ ] Unused `use` imports
- [ ] Magic strings/numbers that should be constants or enums
- [ ] Comments explaining obvious code
- [ ] Inconsistent spacing or formatting (run Pint instead)

## Output Format

```
## Code Review: [filename]

### 🔴 Critical
- Line X: [issue description]

### 🟡 Important
- Line X: [issue description]

### 🟢 Minor
- Line X: [issue description]

### Summary
[1-2 sentence overall assessment]
```

## Rules
- Be specific — reference line numbers
- Do not rewrite the entire file unless asked
- Suggest fixes, don't just point out problems
- If the file looks good, say so clearly
