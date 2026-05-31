# INDEX — Spec Navigation Map

Root files: `README.md` · `MASTER_SPEC.md` · `CURRENT_SPRINT.md` · `ROADMAP.md` · `CHANGELOG.md` · `GLOSSARY.md`

## Product (INCEPTION)
- [vision.md](product/vision.md) — Product vision statement
- [strategy.md](product/strategy.md) — Market, competition, growth
- [objectives.md](product/objectives.md) — Business objectives & KPIs
- [scope.md](product/scope.md) — In/out scope per phase
- [personas.md](product/personas.md) — Buyer, Seller, Admin personas

## Business (INCEPTION)
- [README.md](business/README.md) — Domain overview

## Decisions (CONSTRUCTION)
- [ADR-001](decisions/ADR-001-django-drf.md) — Django + DRF
- [ADR-002](decisions/ADR-002-postgresql.md) — PostgreSQL
- [ADR-003](decisions/ADR-003-modular-monolith.md) — Modular monolith
- [ADR-004](decisions/ADR-004-jwt-auth.md) — JWT authentication
- [ADR-005](decisions/ADR-005-service-selector-pattern.md) — Service/Selector pattern

## Technical / Contracts (CONSTRUCTION)
- [Technology stack](technical/architecture/technology-stack.md)
- [Auth API](technical/contracts/rest/auth-api.yaml) — register, login, token refresh
- [Users API](technical/contracts/rest/users-api.yaml) — profile, addresses
- [Catalog APIs](technical/contracts/rest/catalog/) — categories, products, inventory

## Modules (CONSTRUCTION)
| Module | Business | Backend | Frontend | Mobile | Status |
|--------|----------|---------|----------|--------|--------|
| **Auth** | [spec.md](modules/auth/business/spec.md) | [spec.yaml](modules/auth/backend/spec.yaml) | [spec.md](modules/auth/frontend/spec.md) | [spec.md](modules/auth/mobile/spec.md) | ✅ |
| **Users** | [spec.md](modules/users/business/spec.md) | [spec.yaml](modules/users/backend/spec.yaml) | [spec.md](modules/users/frontend/spec.md) | [spec.md](modules/users/mobile/spec.md) | ✅ |
| **Catalog** | [spec.md](modules/catalog/business/spec.md) | [backend/](modules/catalog/backend/) | [spec.md](modules/catalog/frontend/spec.md) | [spec.md](modules/catalog/mobile/spec.md) | ✅ |

## Iterations (CONSTRUCTION)
- [iteration-001](iterations/iteration-001-starter-kit-setup/README.md) — Starter kit setup

## Development Guides (CONSTRUCTION)
- [Frontend](development/frontend/README.md) — React setup, conventions, API flow
- [Mobile](development/mobile/README.md) — Mobile setup (scaffold pending)

## AI Context (CROSS-CUTTING)
- [system-context.md](ai-context/system-context.md) — System overview for AI
- [coding-context.md](ai-context/coding-context.md) — Coding conventions & commands

## Templates
- [Mobile spec](assets/templates/spec-template-mobile.md) — Mobile implementation template
- [API contract](assets/templates/spec-template-contract.yaml) — Shared contract template
