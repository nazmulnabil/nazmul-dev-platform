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

## Technical (CONSTRUCTION)
- [Technology stack](03-technical/architecture/technology-stack.md) — Django, DRF, PostgreSQL, React
- [Contracts](03-technical/contracts/) — API specs, data schemas

## Modules (CONSTRUCTION)
| Module | Business | Technical | Status |
|--------|----------|-----------|--------|
| **Auth** | [business/spec.md](04-modules/auth/business/spec.md) | [technical/spec.yaml](04-modules/auth/technical/spec.yaml) | ✅ Implemented |
| **Users** | [business/spec.md](04-modules/users/business/spec.md) | [technical/spec.yaml](04-modules/users/technical/spec.yaml) | ✅ Implemented |
| **Catalog** | [business/spec.md](04-modules/catalog/business/spec.md) | [technical/](04-modules/catalog/technical/) | ✅ Implemented |

## Iterations (CONSTRUCTION)
- [iteration-001](iterations/iteration-001-starter-kit-setup/README.md) — Starter kit setup

## AI Context (CROSS-CUTTING)
- [system-context.md](10-ai-context/system-context.md) — System overview for AI
- [coding-context.md](10-ai-context/coding-context.md) — Coding conventions & commands
