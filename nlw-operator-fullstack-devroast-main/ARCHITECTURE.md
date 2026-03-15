# Project Architecture

## 📁 Project Structure

```text
devroast/
├── src/
│   ├── app/                       # Next.js App Router pages, layouts, route handlers
│   │   ├── api/trpc/[trpc]/route.ts  # tRPC HTTP entrypoint
│   │   ├── leaderboard/           # Leaderboard route segment
│   │   └── roast/[id]/            # Roast details and OG image route
│   ├── components/                # Shared UI and feature components
│   │   ├── ui/                    # Reusable design-system-like primitives
│   │   └── og/                    # Open Graph image components
│   ├── trpc/                      # API layer (routers, client/server integration)
│   │   └── routers/               # Domain routers (_app, roast)
│   ├── db/                        # Database schema, connection, seed
│   ├── hooks/                     # Reusable React hooks
│   └── lib/                       # Shared services/utilities (AI, language metadata)
├── drizzle/                       # Generated SQL migrations + metadata
├── docs/plans/                    # Product/feature planning notes
├── specs/                         # Technical implementation specs
├── docker-compose.yml             # Local PostgreSQL service for development
├── drizzle.config.ts              # Drizzle migration configuration
├── next.config.ts                 # Next.js runtime/build configuration
├── biome.json                     # Lint + formatter rules
├── postcss.config.mjs             # CSS/PostCSS build config
├── tsconfig.json                  # TypeScript compiler settings
└── package.json                   # Scripts and dependencies
```

Current status by category:
- Public assets (`public/images`, `public/fonts`, `public/js`): **not present yet**. Add `public/` when static assets are needed.
- Source code: centralized under `src/`, split by runtime concerns (`app`, `trpc`, `db`, `components`, `hooks`, `lib`).
- Tests (`unit`, `integration`, `e2e`): **not present yet** (no `tests/` folder, no test scripts).
- Build/deployment files: `next.config.ts`, `postcss.config.mjs`, `docker-compose.yml`, npm scripts (`build`, `start`, DB scripts).

## 🎯 Architecture Principles

- Separation of responsibilities:
  - `src/app` handles rendering and route composition.
  - `src/trpc` owns API contracts and orchestration.
  - `src/db` owns persistence model and DB access.
  - `src/components`, `src/hooks`, and `src/lib` keep UI and reusable behavior decoupled from route files.
- Scalability:
  - Feature growth should happen by expanding `src/trpc/routers` and route segments under `src/app`.
  - Shared logic must move to `hooks`/`lib` instead of duplicating in pages/components.
- Reusability:
  - UI primitives live in `src/components/ui`.
  - Cross-page behavior should be extracted into hooks and services.
- Maintainability:
  - Enforce formatting/linting with Biome.
  - Keep modules focused and small.
  - Use migration-first schema evolution via Drizzle (`drizzle/` as source of migration history).

## 📝 Conventions

- Naming:
  - Files/folders: `kebab-case` (for route/component files and directories).
  - Functions/variables: `camelCase`.
  - Types/components/classes: `PascalCase`.
- Module structure:
  - Prefer one clear responsibility per file.
  - Keep feature entrypoints close to their route/router boundary.
  - Avoid circular dependencies between `app`, `trpc`, `db`, and `components`.
- Coding style:
  - Use TypeScript across the codebase.
  - Biome is the formatter/linter source of truth (`pnpm lint`, `pnpm format`).
- Engineering practices:
  - Follow Clean Code + SOLID + DRY + KISS + YAGNI.
  - Favor composition over inheritance.
  - Avoid introducing new frameworks/libraries when existing stack already solves the problem.

## 🛠️ Maintenance and Expansion

### Maintenance

- Dependency updates:
  - Run updates in small batches and validate with lint/build before merging.
  - Prioritize security and runtime-critical packages (`next`, `react`, `trpc`, `drizzle`, `pg`).
- Bug fixing and quality:
  - Reproduce each bug with a test first (once test setup is available), then implement a minimal fix.
  - Keep fixes scoped to the impacted module and avoid unrelated refactors in the same PR.
- Clean and documented code:
  - Keep `README.md`, `specs/`, and this architecture file aligned with structural changes.
  - Add concise comments only where intent is not obvious.

### Adding New Features

1. Create a new route segment and/or feature component in `src/app` or `src/components`.
2. Add required support files in `src/hooks`, `src/lib`, `src/trpc/routers`, and `src/db` (if persistence is needed).
3. Update project configuration only when strictly necessary (`next.config.ts`, Biome, TS, PostCSS).
4. Add tests for the feature:
   - Unit: pure logic/hooks/components.
   - Integration: tRPC router + DB boundaries (with controlled test database).
   - E2E: critical user flows.

Suggested baseline test layout to introduce:

```text
tests/
├── unit/
├── integration/
└── e2e/
```

And add scripts in `package.json`:
- `test`
- `test:watch`
- `test:e2e`

---

**Last update**: 2026-03-13  
**Project version**: 0.1.0  
**Maintainer**: Felipe Moreira

