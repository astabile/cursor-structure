# Skill: Create React Component

## Trigger
Use when asked to create a new React component.

## Instructions

1. Ask for the component name if not provided
2. Ask what type: `ui` (pure display), `feature` (has logic/state), or `page` (route-level)
3. Determine the correct folder:
   - `ui` → `src/components/`
   - `feature` → `src/components/[feature-name]/`
   - `page` → `src/pages/`
4. Create the component file following this structure:

```tsx
import { FC } from 'react'

interface [ComponentName]Props {
  // define props here
}

const [ComponentName]: FC<[ComponentName]Props> = ({ }) => {
  return (
    <div>
      {/* component content */}
    </div>
  )
}

export default [ComponentName]
```

5. If the component needs a hook, create it in `src/hooks/use[ComponentName].ts`
6. Do NOT create an index barrel file unless explicitly asked

## Rules
- TypeScript only — no `.jsx` files
- Props interface defined above the component, not inline
- Named export from the file, default export at bottom
- No inline styles — use CSS modules or Tailwind classes
- Do not add placeholder lorem ipsum content
