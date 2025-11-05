# Zero One Monorepo – Agent Briefing

Use this file first. Detailed summaries live in `docs-ai/README.md`; load that single file instead of scanning the entire repository. For command cheat sheets, see `docs-ai/quick-reference.md`.

## Setup
- Install dependencies: `pnpm install`
- Initialize moon toolkit: `pnpm run prepare`
- Bring up local services (optional): `pnpm compose:up`

## Core Commands
- `moon :dev` / `moon <project>:dev` – start development servers.
- `moon :lint`, `moon :check`, `moon :typecheck`, `moon :test`, `moon :build` – repo-wide tasks.
- `pnpm run format` – format with Biome.
- `moon project-graph` – inspect project dependencies.

## Project Map (read-only)
- `apps/` – active apps (React, Next.js, Astro, Go, FastAPI, Strapi).
- `packages/shared-ui/` – shared React component library.
- `templates/` – distributable scaffolds generated from `apps/`.
- `builder/` – scripts that convert app copies into template-ready packages.
- `docker/` & `compose.yaml` – local infrastructure stacks.
- `docsite/` – public documentation (Hugo).
- ➡️ See `docs-ai/README.md` for concise per-app notes and workflow details.

## Template Workflow
1. Modify code in `apps/<name>`.
2. Run `./build-templates.sh` to sync into `templates/`.
3. Builder scripts (e.g., `builder/react-app.sh`) inject templating variables. Keep placeholders such as `{{ package_name | kebab_case }}` intact.

## Testing & QA
- Prefer moon tasks—they encapsulate dependencies and environment files.
- E2E tests via Playwright: `moon <frontend-project>:e2e` / `:e2e-ui`.
- Docker image build/run helpers live as moon tasks (`docker-build`, `docker-run`, `docker-shell`).

## Agent Guidelines
- Load `docs-ai/README.md` for additional context instead of trawling directories.
- Grab ready-to-run commands from `docs-ai/quick-reference.md` when you need task reminders.
- Avoid expanding `packages/shared-ui` unless necessary; consult `src/components/index.ts` first.
- When answering developer questions, cite specific paths and moon tasks. Keep responses token-efficient.

