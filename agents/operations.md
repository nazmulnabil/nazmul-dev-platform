# Operations — Commands & Decisions

## Key Commands

| Action | Command (run in `django-ecommerce-api/`) |
|--------|-----------------------------------------|
| Run tests | `pytest` |
| Run linter | `ruff check .` |
| Generate OpenAPI schema | `python manage.py spectacular --file schema.yaml` |

## Decisions Log

| Date | Decision | Rationale |
|------|----------|-----------|
| 2026-05-27 | Spec-first development | AI agents implement from structured specs |
| 2026-05-27 | Dual format (MD + YAML) | MD for human readability, YAML for agent parsing |
| 2026-05-27 | Domain-based spec directories | Groups API + UI specs for same feature together |
| 2026-05-27 | Backfill existing features as `implemented` status | Document what exists before building new features |
