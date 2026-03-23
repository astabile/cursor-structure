# Skill: Create Laravel API Resource

## Trigger
Use when asked to create an API resource, JSON transformer, or response formatter.

## Instructions

1. Ask for the model name the resource transforms (e.g. `User`, `Listing`)
2. Ask which fields should be exposed in the API response
3. Create the resource at `app/Http/Resources/[Model]Resource.php`:

```php
<?php

declare(strict_types=1);

namespace App\Http\Resources;

use Illuminate\Http\Request;
use Illuminate\Http\Resources\Json\JsonResource;

class [Model]Resource extends JsonResource
{
    public function toArray(Request $request): array
    {
        return [
            'id'         => $this->id,
            // map fields here — be explicit, never use $this->resource->toArray()
            'created_at' => $this->created_at?->toISOString(),
            'updated_at' => $this->updated_at?->toISOString(),
        ];
    }
}
```

4. If a collection resource is needed, create `[Model]Collection.php`:

```php
<?php

declare(strict_types=1);

namespace App\Http\Resources;

use Illuminate\Http\Resources\Json\ResourceCollection;

class [Model]Collection extends ResourceCollection
{
    public $collects = [Model]Resource::class;
}
```

## Rules
- Never expose sensitive fields (password, remember_token, internal IDs you don't want public)
- Always be explicit about which fields are returned — no wildcard `toArray()`
- Use `$this->whenLoaded('relation')` for conditional relationship inclusion
- Format dates as ISO 8601 strings
- Nest related resources using their own Resource class
