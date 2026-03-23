# Tech Stack

> ⚠️ Keep this updated when packages or infrastructure changes.

## Languages
- PHP X.X (strict types)
- JavaScript / TypeScript (frontend)

## Backend
- Laravel X.X
- REST API / Inertia.js (if SPA hybrid)

## Frontend
- Blade templates
- Alpine.js / Vue.js / React (via Inertia)
- Tailwind CSS / Bootstrap / SASS

## Database
- MySQL X.X / PostgreSQL X.X
- ORM: Eloquent

## Cache & Queue
- Cache driver: Redis / File
- Queue driver: Redis / Database / SQS
- Horizon (if Redis queues)

## Infrastructure
- Hosting: Laravel Forge / AWS / DigitalOcean
- Storage: AWS S3 / local disk
- CI/CD: GitLab / GitHub Actions / Envoyer

## Dev Tools
- Package manager: Composer + npm/yarn
- Linter: PHP CS Fixer / Pint
- Testing: PHPUnit / Pest
- Static analysis: PHPStan / Larastan

## Environment Variables
<!-- List keys (not values) used in the project -->
- `APP_KEY`
- `DB_CONNECTION`, `DB_HOST`, `DB_DATABASE`, `DB_USERNAME`, `DB_PASSWORD`
- `REDIS_HOST`
- `MAIL_MAILER`, `MAIL_HOST`
- `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, `AWS_BUCKET`
- (add more as needed)
