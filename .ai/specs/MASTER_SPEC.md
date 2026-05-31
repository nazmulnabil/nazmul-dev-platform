# MASTER_SPEC — Cross-Cutting Rules

This file defines rules that apply across all modules.

## Authentication

- JWT access tokens (60 min) + refresh tokens (1 day) — see ADR-004
- Email/password authentication
- Custom JWT claims: `email`, `is_staff`

## Authorization

- Default DRF permission: `IsAuthenticated`
- Public endpoints explicitly set to `AllowAny`
- RBAC roles: Buyer, Seller, Admin

## API Conventions

- Base path: `/api/v1/<domain>/`
- Input/output serializers are separate classes (see ADR-005)
- Error format: `{ "detail": "..." }` or `{ "field_errors": { "field": ["msg"] } }`
- Pagination: page + page_size query params, paginated response with count/next/previous/results

## Database

- PostgreSQL (see ADR-002)
- All models inherit `TimeStampedModel` (created_at, updated_at) from `core`
- Soft deletes are opt-in, not default
- Constraint naming: `app_entity_field_check` for check constraints

## Architecture

- Modular monolith for Phase 1 (see ADR-003)
- Service/Selector layer pattern per app (see ADR-005)
- Domain exceptions in `exceptions.py`, inherit `core.exceptions.DomainException`

## Testing

- pytest + model-bakery for backend
- Vitest + Playwright for frontend (planned)
- Each module has happy path + error + edge case tests

## Spec Conventions

- Metadata: version, status, last_updated required in every spec
- Status lifecycle: draft → approved → implemented → deprecated
- Business specs use plain language (readable by non-engineers)
- Technical specs use precise schemas (readable by AI agents)
- Module specs are presence-based — only create files for platforms that exist

## Multi-Platform Structure

- API contracts are the single source of truth (`technical/contracts/rest/`)
- Backend implements contracts (`modules/<domain>/backend/`)
- Frontend and Mobile consume contracts (`modules/<domain>/frontend/`, `mobile/`)
- Module specs are presence-based — only create platform folders that exist
- All platforms reference the same contract file — no drift
