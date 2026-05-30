# Coding Context

## Backend (Django + DRF)

- Models: `django.db.models`, inherit `core.models.TimeStampedModel`
- Views: `rest_framework.views.APIView` with `@extend_schema`
- Serializers: Separate `*InputSerializer` and `*OutputSerializer`
- Services: Business logic in `<app>/services.py` (pure functions)
- Selectors: Read logic in `<app>/selectors.py`
- Exceptions: Custom in `<app>/exceptions.py`, inherit `core.exceptions.DomainException`
- URLs: `/api/v1/<domain>/`
- Tests: pytest + model-bakery; tests in `tests/` per app

## Frontend (React + Vite)

- Placeholder — not yet implemented.
