# Skill: Create API Route

## Trigger
Use when asked to create a new API endpoint or route.

## Instructions

1. Ask for the resource name (e.g. `user`, `listing`, `order`) if not provided
2. Ask which HTTP methods are needed (GET, POST, PUT, DELETE)
3. Create three files:

**Route file** → `src/routes/[resource].routes.ts`
```ts
import { Router } from 'express'
import { getAll, getById, create, update, remove } from '../controllers/[resource].controller'
import { authenticate } from '../middleware/auth'

const router = Router()

router.get('/', authenticate, getAll)
router.get('/:id', authenticate, getById)
router.post('/', authenticate, create)
router.put('/:id', authenticate, update)
router.delete('/:id', authenticate, remove)

export default router
```

**Controller file** → `src/controllers/[resource].controller.ts`
```ts
import { Request, Response } from 'express'
import { [Resource]Service } from '../services/[resource].service'

export const getAll = async (req: Request, res: Response) => {
  try {
    const data = await [Resource]Service.getAll()
    res.json({ success: true, data })
  } catch (error) {
    res.status(500).json({ success: false, error: 'Internal server error' })
  }
}
// ... repeat pattern for each method
```

**Service file** → `src/services/[resource].service.ts`
```ts
import [Resource] from '../models/[Resource]'

export const [Resource]Service = {
  getAll: async () => {
    return [Resource].find().lean()
  },
  // ... other methods
}
```

4. Register the route in the main router file — show the user the line to add, do not edit it automatically

## Rules
- Controllers only handle request/response — no DB queries inside them
- All business logic goes in the service
- Always wrap in try/catch with consistent error response shape
- Authenticate middleware applied by default — ask if a route should be public
