# Skill: Code Review

## Trigger
Use when asked to review code, check a file, or verify something before committing.

## Instructions

Review the specified file(s) against the following checklist and report findings grouped by severity.

### 🔴 Critical (must fix before merging)
- [ ] Hardcoded secrets, API keys, or credentials
- [ ] SQL/NoSQL injection vulnerabilities
- [ ] Missing authentication on protected routes
- [ ] Unhandled promise rejections or missing try/catch
- [ ] Direct DB operations inside controllers (bypass service layer)

### 🟡 Important (should fix)
- [ ] `any` type used in TypeScript
- [ ] `console.log` left in code
- [ ] Missing input validation
- [ ] N+1 query patterns (fetching in a loop without batching)
- [ ] Functions doing more than one thing
- [ ] Inconsistent error response shape
- [ ] Missing or incorrect TypeScript return types

### 🟢 Minor (nice to fix)
- [ ] Naming doesn't follow project conventions
- [ ] Imports not grouped correctly
- [ ] Unnecessary comments explaining obvious code
- [ ] Magic numbers or strings (should be constants)
- [ ] Unused imports or variables

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
