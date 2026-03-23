# Skill: Create Laravel Migration

## Trigger
Use when asked to create a database migration, add a table, or modify a schema.

## Instructions

1. Ask what the migration does (create table, add column, add index, rename, etc.)
2. Ask for the table name and fields (name, type, nullable, default, indexed)
3. Generate the migration — do NOT run it

**Create table template:**
```php
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    public function up(): void
    {
        Schema::create('[table_name]', function (Blueprint $table) {
            $table->id();
            // fields here
            $table->timestamps();
        });
    }

    public function down(): void
    {
        Schema::dropIfExists('[table_name]');
    }
};
```

4. Show the user the migration content and the command to run it:
```bash
php artisan migrate
```
5. Do NOT run `php artisan migrate` — the user runs it manually

## Field Type Reference
| Type | Blueprint method |
|------|-----------------|
| String (VARCHAR 255) | `$table->string('name')` |
| Long text | `$table->text('body')` |
| Integer | `$table->integer('count')` |
| Big integer (FK) | `$table->unsignedBigInteger('user_id')` |
| Boolean | `$table->boolean('active')->default(true)` |
| Decimal | `$table->decimal('price', 10, 2)` |
| DateTime | `$table->timestamp('published_at')->nullable()` |
| Foreign key | `$table->foreign('user_id')->references('id')->on('users')->cascadeOnDelete()` |

## Rules
- Always include a `down()` method that fully reverses the `up()`
- Use `unsignedBigInteger` for all foreign keys
- Index foreign keys and frequently queried columns explicitly
- Never modify an existing migration — create a new one instead
- Never suggest `migrate:fresh` on a project with real data
