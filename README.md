# AI QA Engineer

Development foundation for the controlled QA platform in [the implementation plan](docs/reference/implementation-plan.md). This is a runnable scaffold, not the completed product.

## Quick start

```sh
nvm use
npm ci
cp .env.example .env
npm run doctor
npm run infra:up
npm run dev
```

Open http://127.0.0.1:3000. API health: http://127.0.0.1:3001/health. Fixture: http://127.0.0.1:3002. Worker scaffold health: http://127.0.0.1:3003. Services currently run without the database or queue, so `npm run dev` also works before infrastructure is started. `.env` is consumed by Compose; future application configuration must explicitly load and validate it. Current service ports use defaults or shell environment variables.

```sh
npm run check       # lint, typecheck, contract tests, production builds
npm run infra:stop  # stop infrastructure while retaining local data
```

## Layout

- `apps/web`: development landing page
- `apps/api`: NestJS health endpoint
- `apps/worker`: inactive execution service with health endpoint
- `apps/fixture`: local fixture placeholder
- `packages/contracts`: strict initial DSL and rejection tests
- `packages/runner`, `packages/security`, `packages/ai`: explicit capability boundaries
- `infra`: loopback-only PostgreSQL and Redis services
- `docs`: architecture, reference plan and ordered build backlog

## Next implementation milestone

Follow [the build backlog](docs/BUILD_BACKLOG.md) to implement a static, approved fixture test with tenant-scoped persisted results and sanitized evidence. No database migrations, authentication, real checkout, browser execution, evidence upload or AI generation exist yet. No external orders are placed. See [architecture decisions](docs/ARCHITECTURE.md).
