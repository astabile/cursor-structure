# Skill: Create Laravel Controller

## Trigger
Use when asked to create a new controller, endpoint, or resource in a Laravel project.

## Instructions

1. Ask for the resource name (singular PascalCase, e.g. `User`, `Listing`) if not provided
2. Ask which methods are needed: index, show, store, update, destroy
3. Create three files:

**Controller** → `app/Http/Controllers/[Resource]Controller.php`
```php
<?php

declare(strict_types=1);

namespace App\Http\Controllers;

use App\Http\Requests\Store[Resource]Request;
use App\Http\Requests\Update[Resource]Request;
use App\Http\Resources\[Resource]Resource;
use App\Services\[Resource]Service;
use Illuminate\Http\JsonResponse;

class [Resource]Controller extends Controller
{
    public function __construct(private readonly [Resource]Service $service) {}

    public function index(): JsonResponse
    {
        return response()->json([
            'success' => true,
            'data'    => [Resource]Resource::collection($this->service->getAll()),
        ]);
    }

    public function store(Store[Resource]Request $request): JsonResponse
    {
        $resource = $this->service->create($request->validated());

        return response()->json([
            'success' => true,
            'data'    => new [Resource]Resource($resource),
            'message' => '[Resource] created successfully',
        ], 201);
    }
}
```

**Service** → `app/Services/[Resource]Service.php`
```php
<?php

declare(strict_types=1);

namespace App\Services;

use App\Models\[Resource];

class [Resource]Service
{
    public function getAll(): \Illuminate\Database\Eloquent\Collection
    {
        return [Resource]::all();
    }

    public function create(array $data): [Resource]
    {
        return [Resource]::create($data);
    }
}
```

**Form Request** → `app/Http/Requests/Store[Resource]Request.php`
```php
<?php

declare(strict_types=1);

namespace App\Http\Requests;

use Illuminate\Foundation\Http\FormRequest;

class Store[Resource]Request extends FormRequest
{
    public function authorize(): bool
    {
        return true;
    }

    public function rules(): array
    {
        return [
            // define validation rules
        ];
    }
}
```

4. Show the route line to add in `routes/api.php` — do NOT edit the file automatically

## Rules
- Controllers are thin — no business logic, no DB queries
- Always use constructor injection for the service
- Always use Form Requests — never `$request->input()` directly in controllers
- Return consistent JSON response shapes
