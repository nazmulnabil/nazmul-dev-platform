# Implementer Agent

Your job is to implement features from specs. Always follow these rules:

## Core Rule

**The spec is the source of truth.** Do not deviate from it. If you believe the spec is wrong or incomplete, pause and ask to update the spec first.

## Process

### 1. Read the Spec

Read `specs/<domain>/README.md` and `specs/<domain>/<feature>.spec.yaml` completely.

### 2. Map Spec to Code

| Spec Section | Implementation Target |
|-------------|----------------------|
| `entities` | Django models in `<app>/models.py` |
| `endpoints` | DRF views in `<app>/views.py`, URLs in `<app>/urls.py` |
| `endpoints.request/response` | Serializers in `<app>/serializers.py` |
| `business_rules` | Service functions in `<app>/services.py` |
| `exceptions` | Exception classes in `<app>/exceptions.py` |
| `testing` | Test files in `<app>/tests/` |

### 3. Follow Project Patterns

- **Service layer**: Business logic in `services.py`, not in views
- **Selector layer**: Read logic in `selectors.py`
- **Domain exceptions**: Inherit `core.exceptions.DomainException`
- **Separate serializers**: Input and Output are separate classes
- **Views**: Use `APIView` with `@extend_schema` for OpenAPI
- **URLs**: Prefix with `/api/v1/<domain>/`
- **Tests**: pytest + model-bakery

### 4. Verify

- **All endpoints** from the spec are callable and return correct status codes
- **All business rules** are enforced (not just documented)
- **All exceptions** are raised with correct HTTP status
- **Tests pass**: Run `pytest` and confirm all pass
- **Spec is still accurate**: If behavior changed, update the spec first, then code

### 5. Frontend Implementation

For UI specs (`type: ui`):

| Spec Section | Implementation Target |
|-------------|----------------------|
| `page.route` | React Router route in `src/routes/` |
| `components` | React components in `src/components/` |
| `states` | Loading/error/success state handling |
| `api_dependencies` | API client calls (axios) matching the referenced `.spec.yaml` |
| `error_handling` | Error boundaries, toast notifications |
| `testing` | Vitest unit tests, Playwright e2e tests |
