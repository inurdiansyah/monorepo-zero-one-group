# Zero One Monorepo — AI Guide

Give the answer from this file before opening anything else. Link to source paths when extra detail is required.

## TL;DR
- Tooling: moonrepo (≥1.41), pnpm 10.18, Biome formatter, Docker Compose for Postgres + Mailpit.
- Stacks: React (SPA + SSR), Next.js, Astro, Go backends (`go-clean`, `go-modular`), FastAPI (`fastapi-ai`), Strapi CMS.
- Templates: develop in `apps/`, run `build-templates.sh`, builder scripts inject placeholders, distributed via `.moon/workspace.yml#generator`.
- Shared UI: `packages/shared-ui/` is large; inspect `src/components/index.ts` or Storybook docs first.
- Prefer moon tasks (`moon :dev`, `moon :lint`, `moon :test`, `moon :build`) over raw scripts.

## Essential Commands
- Install deps → `pnpm install`
- Moon setup → `pnpm run prepare`
- Start services (optional) → `pnpm compose:up`
- Formatting → `pnpm run format`
- Inspect graph → `moon project-graph`

## Key Paths
- `apps/` — active sources. Frontends use Vite + Tailwind (`app/` or `src/app`). Go apps expose CLI via `cmd/` and modules under `internal/` or `modules/`. FastAPI layers: `router/` → `services/` → `repository/`.
- `packages/shared-ui/` — React component kit (tsx/css.ts/mdx per component).
- `templates/` — cleaned copies of apps with template variables.
- `builder/` — post-process scripts (keep tokens like `{{ package_name | kebab_case }}` intact).
- `docker/` + `compose.yaml` — local infra stacks.
- `docsite/` — Hugo docs for human-friendly guidance.

## Testing & Quality Gates
- Unit/type checks via moon tasks (`:test`, `:typecheck`).
- Playwright E2E: `moon <frontend-project>:e2e` or `:e2e-ui`.
- Docker helpers per project (`docker-build`, `docker-run`, `docker-shell`).

## Agent Tips
- Answer high-level questions with TL;DR + Key Paths; avoid crawling entire repos unless a specific file is requested.
- When summarizing shared UI, point to export files instead of enumerating every component.
- If modifying templates, verify the matching builder script preserves variable placeholders.

