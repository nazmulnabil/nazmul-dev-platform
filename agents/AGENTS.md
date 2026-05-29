# AGENTS.md — Project Memory

## Overview
- **Purpose**: Central context repo for e-commerce platform
- **Backend**: `django-ecommerce-api/` — Django + DRF, JWT, PostgreSQL
- **Frontend**: `react-ecommerce/` — React (Vite), coming soon
- **Approach**: Spec-first development

## Repos
| Repo | Type | URL | Branch |
|------|------|-----|--------|
| `django-ecommerce-api` | Backend | `github.com/nazmulnabil/django-ecommerce-api` | main |
| `react-ecommerce` | Frontend | `github.com/nazmulnabil/react-ecommerce` | main |

## Reference Files
- `@agents/git-workflow.md` — all git rules
- `@agents/architecture.md` — backend patterns
- `@agents/spec-conventions.md` — spec rules
- `@agents/operations.md` — commands & decisions
- `@agents/spec-writer.md` — writing specs
- `@agents/implementer.md` — implementing specs

## Decisions Log
| Date | Decision | Rationale |
|------|----------|-----------|
| 2026-05-27 | Spec-first development | AI agents implement from structured specs |
| 2026-05-27 | Dual format (MD + YAML) | MD for human, YAML for agent parsing |
| 2026-05-27 | Domain-based spec directories | Groups API + UI specs together |
| 2026-05-27 | Backfill existing as `implemented` | Document what exists before building new |
