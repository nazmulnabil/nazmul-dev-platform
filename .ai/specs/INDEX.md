# INDEX — Spec Navigation Map

Root files: `README.md` · `MASTER_SPEC.md` · `CURRENT_SPRINT.md` · `ROADMAP.md` · `CHANGELOG.md` · `GLOSSARY.md`

## Product (INCEPTION)
- [vision.md](01-product/vision.md) — Product vision statement
- [strategy.md](01-product/strategy.md) — Market, competition, growth
- [objectives.md](01-product/objectives.md) — Business objectives & KPIs
- [scope.md](01-product/scope.md) — In/out scope per phase
- [personas.md](01-product/personas.md) — Buyer, Seller, Admin personas

## Business (INCEPTION)
- [README.md](02-business/README.md) — Domain overview

## Decisions (CONSTRUCTION)
- [ADR-001](decisions/ADR-001-django-drf.md) — Django + DRF
- [ADR-002](decisions/ADR-002-postgresql.md) — PostgreSQL
- [ADR-003](decisions/ADR-003-modular-monolith.md) — Modular monolith
- [ADR-004](decisions/ADR-004-jwt-auth.md) — JWT authentication
- [ADR-005](decisions/ADR-005-service-selector-pattern.md) — Service/Selector pattern

## Technical / Contracts (CONSTRUCTION)
- [Technology stack](03-technical/architecture/technology-stack.md)
- [Auth API](03-technical/contracts/rest/auth-api.yaml) — register, login, token refresh
- [Users API](03-technical/contracts/rest/users-api.yaml) — profile, addresses
- [Catalog APIs](03-technical/contracts/rest/catalog/) — categories, products, inventory

## Modules (CONSTRUCTION)
| Module | Business | Backend | Frontend | Mobile | Status |
|--------|----------|---------|----------|--------|--------|
| **Auth** | [spec.md](04-modules/auth/business/spec.md) | [spec.yaml](04-modules/auth/backend/spec.yaml) | [spec.md](04-modules/auth/frontend/spec.md) | [spec.md](04-modules/auth/mobile/spec.md) | ✅ |
| **Users** | [spec.md](04-modules/users/business/spec.md) | [spec.yaml](04-modules/users/backend/spec.yaml) | [spec.md](04-modules/users/frontend/spec.md) | [spec.md](04-modules/users/mobile/spec.md) | ✅ |
| **Catalog** | [spec.md](04-modules/catalog/business/spec.md) | [backend/](04-modules/catalog/backend/) | [spec.md](04-modules/catalog/frontend/spec.md) | [spec.md](04-modules/catalog/mobile/spec.md) | ✅ |

## Iterations (CONSTRUCTION)
- [iteration-001](iterations/iteration-001-starter-kit-setup/README.md) — Starter kit setup

## Development Guides (CONSTRUCTION)
- [Frontend](07-development/frontend/README.md) — React setup, conventions, API flow
- [Mobile](07-development/mobile/README.md) — Mobile setup (scaffold pending)

## AI Context (CROSS-CUTTING)
- [system-context.md](10-ai-context/system-context.md) — System overview for AI
- [coding-context.md](10-ai-context/coding-context.md) — Coding conventions & commands

## Templates
- [Mobile spec](14-assets/templates/spec-template-mobile.md) — Mobile implementation template
- [API contract](14-assets/templates/spec-template-contract.yaml) — Shared contract template
