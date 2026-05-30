# MASTER_SPEC — Cross-Cutting Rules

This file defines rules that apply across all modules.

## Authentication

- JWT access tokens (60 min) + refresh tokens (1 day)
- Email/password authentication
- Custom JWT claims: `email`, `is_staff`

## Authorization

- Default DRF permission: `IsAuthenticated`
- Public endpoints explicitly set to `AllowAny`
- RBAC roles: Buyer, Seller, Admin

## API Conventions

- Base path: `/api/v1/<domain>/`
- Input/output serializers are separate classes
- Error format: `{ "detail": "..." }` or `{ "field_errors": { "field": ["msg"] } }`
- Pagination: page + page_size query params, paginated response with count/next/previous/results

## Database

- All models inherit `TimeStampedModel` (created_at, updated_at) from `core`
- Soft deletes are opt-in, not default
- Constraint naming: `app_entity_field_check` for check constraints

## Error Handling

- Domain exceptions in `exceptions.py`, inherit `DomainException`
- Service layer raises exceptions; views catch and map to HTTP status
- Exception → HTTP mapping defined per module in technical spec

## Testing

- pytest + model-bakery for backend
- Vitest + Playwright for frontend
- Each module has happy path + error + edge case tests

## Spec Conventions

- Metadata: version, status, last_updated required in every spec
- Status lifecycle: draft → approved → implemented → deprecated
- Business specs use plain language (readable by non-engineers)
- Technical specs use precise schemas (readable by AI agents)
