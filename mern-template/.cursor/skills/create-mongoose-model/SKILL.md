# Skill: Create Mongoose Model

## Trigger
Use when asked to create a new database model or schema.

## Instructions

1. Ask for the model name (singular PascalCase, e.g. `User`, `BusListing`) if not provided
2. Ask what fields are needed — name, type, required, default, indexed
3. Create the file at `src/models/[ModelName].ts`:

```ts
import { Schema, model, Document } from 'mongoose'

export interface I[ModelName] extends Document {
  // field definitions matching schema
  createdAt: Date
  updatedAt: Date
}

const [ModelName]Schema = new Schema<I[ModelName]>(
  {
    // fields here
  },
  {
    timestamps: true,
    versionKey: false,
  }
)

// Add indexes for frequently queried fields
[ModelName]Schema.index({ fieldName: 1 })

export default model<I[ModelName]>('[ModelName]', [ModelName]Schema)
```

4. Show the user the model and ask for confirmation before saving

## Rules
- Always use `timestamps: true` and `versionKey: false`
- Always define a TypeScript interface extending `Document`
- Index any field used in search or sort operations
- Use `required: true` explicitly — do not rely on schema defaults for required fields
- Enum fields should use a TypeScript enum or `as const` object
