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
- For product/business alignment consult `docs-ai/business-context.md`, `docs-ai/prd-template.md`, and `docs-ai/technical-guide.md`.
- **SDD Integration**: This monorepo uses Spec-Driven Development - see `docs-ai/sdd-workflow.md` for commands. Use `/brief` for 80% of features (30-min planning), full SDD 2.0 for complex ones. Check `.sdd/guidelines.md` for monorepo-specific SDD rules.
- **VDD Integration**: Vertical Driven Development guides architecture - organize by business features (vertical slices), not technical layers. See `.cursor/rules/vdd-core-principles.mdc` for VDD philosophy. Use `/vdd-build` or `/vdd-all-in-one` for complete apps with vertical slices.
- Avoid expanding `packages/shared-ui` unless necessary; consult `src/components/index.ts` first.
- When answering developer questions, cite specific paths and moon tasks. Keep responses token-efficient.

## SDD Workflow Quick Reference
- **Lightweight (80%)**: `/brief feature-name` → Start coding → `/evolve` to update
- **Complex (20%)**: PRD → `/research` → `/specify` → `/plan` → `/tasks` → `/implement`
- **Full Projects**: `/sdd-full-plan` for epic-level roadmaps
- **VDD Commands**: `/vdd-build` or `/vdd-all-in-one` for complete apps with vertical slices
- **System Rules**: `.cursor/rules/sdd-system.mdc` contains SDD system overview, `.cursor/rules/vdd-*.mdc` for VDD principles

