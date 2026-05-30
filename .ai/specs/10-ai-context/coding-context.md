# Coding Context

## Backend (Django + DRF)

| Concern | Convention |
|---------|-----------|
| **Models** | `django.db.models`, inherit `core.models.TimeStampedModel` for created_at/updated_at |
| **Views** | `rest_framework.views.APIView` with `@extend_schema` for OpenAPI |
| **Serializers** | Separate `*InputSerializer` and `*OutputSerializer` per operation |
| **Services** | Business logic in `<app>/services.py` — pure functions, raise domain exceptions |
| **Selectors** | Read/query logic in `<app>/selectors.py` — never mutate |
| **Exceptions** | Custom in `<app>/exceptions.py`, inherit `core.exceptions.DomainException` |
| **URLs** | Prefix `/api/v1/<domain>/` |
| **Tests** | pytest + model-bakery. Tests live in `tests/` per app, organized by domain |
| **Linting** | `ruff check .` |

## Frontend (React + Vite)

- Placeholder — not yet implemented. Scaffold: Vite + React + TypeScript.

## Project Root Commands

| Action | Command (in `django-ecommerce-api/`) |
|--------|--------------------------------------|
| Run tests | `pytest` |
| Lint | `ruff check .` |
| Generate OpenAPI schema | `python manage.py spectacular --file schema.yaml` |
