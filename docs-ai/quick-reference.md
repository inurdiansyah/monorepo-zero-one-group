# Zero One Monorepo — Quick Reference

Use this sheet when you need fast answers about operating the repo.

## Setup & Bootstrap
- Clone template: `pnpm dlx tiged zero-one-group/monorepo <new-project>`
- Install deps: `pnpm install`
- Copy env: `cp .env.example .env` (per app/package)
- Replace namespace tokens (`myorg`, `example.com`) before shipping.

## Daily Commands
- `pnpm run prepare` — run `moon setup`
- `moon :dev` / `moon <project>:dev` — start dev servers
- `moon :lint`, `moon :check`, `moon :typecheck`, `moon :test`, `moon :build`
- `pnpm run format` — Biome formatter
- `pnpm compose:up` / `pnpm compose:down` — local Postgres + Mailpit (+ optional stacks)

## Template Workflow Recap
1. Build features under `apps/<name>`.
2. `./build-templates.sh` copies to `templates/<name>` and strips artifacts.
3. Builder scripts inject tokens (e.g. `{{ package_name | kebab_case }}`) — do not hardcode values they expect to replace.
4. `.moon/workspace.yml#generator.templates` exposes zipped outputs for `moon generate TEMPLATE_NAME`.

## Managing Dependencies
- Add runtime dep: `pnpm --filter <project_id> add <pkg>`
- Add dev dep: `pnpm --filter <project_id> add -D <pkg>`
- Update workspace deps: `pnpm run update-deps`
- Cleanup install/cache artifacts: `pnpm run cleanup`

## Frequently Used moon Tasks
- Go (`go-clean`, `go-modular`): `moon <project>:dev`, `:test`, `:docker-build`, `:docker-run`
- Frontend (React/Next/Astro): `moon <project>:dev`, `:test`, `:e2e`, `:build`, `:docker-build`
- Strapi: `moon strapi-cms:start`, `:build`, `:docker-run`
- Shared UI: `moon shared-ui:build`, `:storybook`, `:storybook-build`

## Testing Highlights
- Unit & integration: `moon :test` or project-scoped `moon <project>:test`
- Playwright suites: `moon <project>:e2e`, `:e2e-ui`, `:e2e-chrome` etc.
- Type checks: `moon :typecheck`

## Contribution Checklist
- Update project README/docs after generating a new template instance.
- Ensure moon tasks are defined in `moon.yml` when adding helpful commands.
- Run formatter + lint (`pnpm run format`, `moon :lint`) before submitting changes.

## Getting Help
- GitHub issues: `https://github.com/zero-one-group/monorepo`
- Maintainers: General `@riipandi`, `@rubiagatra`; Go `@ameliarahman`, `@mirfmaster`; Python `@mirfmaster`; Infra `@prihuda`

Keep this file tight—expand long answers in the public docs at `docsite/` when needed.

