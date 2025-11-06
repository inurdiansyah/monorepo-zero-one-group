# Business Context Guide

Use this note to align SDD (Spec-Driven Development) and emerging VDD (Vertical-Driven Development) workflows with the Zero One monorepo.

## Purpose
- Provide a shared vocabulary for business stakeholders, product teams, and AI agents.
- Map business requirements to the templates/apps available in this repository.
- Supply the background needed to draft PRDs and technical plans quickly.

## Core Verticals
- **Digital Commerce** – storefronts, headless commerce, and order management. Typical stack: `nextjs-app`, `react-app`, `go-clean` (checkout APIs).
- **Internal Operations** – dashboards, admin portals, workflow tooling. Templates: `react-ssr`, `astro-web`, `go-modular` for complex backoffice flows.
- **AI/Automation Services** – assistant backends, data processing, ML integrations. Templates: `fastapi-ai`, `shared-ui` for admin panels.
- **Content & Community** – marketing sites, blogs, CMS-powered experiences. Templates: `astro-web`, `strapi-cms`.
- **Infrastructure & Platform** – reusable stacks (GitLab CI/CD, load balancer, monitoring, terragrunt) for deployment alignment.

## Business Outcomes & Metrics
- **Acquisition** – conversion rate, qualified leads captured, SEO performance.
- **Engagement** – active users, session duration, journey completion.
- **Operational Efficiency** – SLA compliance, automation coverage, time-to-resolution.
- **Retention & Revenue** – repeat usage, NPS, subscription/transaction volume.

## Aligning SDD and VDD
1. **VDD Discovery (Business First)**
   - Capture the vertical, target personas, and desired outcomes.
   - Document current vs. future journey and critical business rules.
2. **SDD Specification (Product & UX)**
   - Convert vertical insights into PRD sections: problem statement, success metrics, journey steps, edge cases.
   - Identify which templates or packages best fit the workload.
3. **SDD Planning (Technical)**
   - Produce architecture and tasks referencing moon tasks, templates, and shared UI components.
4. **Execution & Continuous Alignment**
   - Keep PRD/tech guides alongside code (see `docs-ai/prd-template.md`, `docs-ai/technical-guide.md`).
   - Update documentation when business rules or vertical assumptions change.

## Artifacts
- **PRD** – use `docs-ai/prd-template.md` to capture product perspective.
- **Technical Implementation Guide** – follow `docs-ai/technical-guide.md` to map requirements into code.
- **Feature Briefs / Specs** – store SDD outputs under `specs/` (if using the spec-kit workflow).

Keep this guide concise; expand vertical-specific playbooks in separate files only when necessary.

