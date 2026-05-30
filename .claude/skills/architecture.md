# Architecture — Project Overview & Backend Patterns

## Project Overview
- **Purpose**: Central context repository for e-commerce platform development
- **Backend**: `django-ecommerce-api/` — Django + DRF, JWT auth, PostgreSQL
- **Frontend**: `react-ecommerce/` — React (Vite), coming soon
- **Approach**: Spec-first development. Specs are the source of truth.

## Repos

| Repo | Type | URL | Branch |
|------|------|-----|--------|
| `django-ecommerce-api` | Backend submodule | `github.com/nazmulnabil/django-ecommerce-api` | main |
| `react-ecommerce` | Frontend submodule | `github.com/nazmulnabil/react-ecommerce` | main |

## Backend Architecture Patterns

- **Service Layer**: Business logic in `services.py` as pure functions
- **Selector Layer**: Read/query logic in `selectors.py`
- **Domain Exceptions**: Custom exceptions in `exceptions.py`, inheriting `DomainException`
- **Serializers**: Separate input and output serializers (`*InputSerializer`, `*OutputSerializer`)
- **Views**: DRF `APIView` with `@extend_schema` for OpenAPI docs
- **URLs**: Versioned under `/api/v1/<domain>/`
- **Testing**: pytest + model-bakery. Tests in `tests/` per app.

## Project Structure

```
.ai/specs/                        # Source of truth
  <domain>/
    business/spec.md              # Human-readable spec (Markdown)
    technical/spec.md             # Agent-parsable spec (YAML/MD)
  <domain>-api.spec.yaml          # Backend API spec
  <domain>-ui.spec.yaml           # Frontend UI spec
.claude/                          # AI tool config
django-ecommerce-api/             # Backend submodule
react-ecommerce/                  # Frontend submodule
```
