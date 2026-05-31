# System Context

## What This Is

**nazmul-dev-platform**: Enterprise-grade spec-first development starter kit with an e-commerce reference implementation.

- **Backend**: Django 5 + DRF, JWT auth, PostgreSQL — 3 apps: `authentication`, `profiles`, `catalog`
- **Frontend**: React + Vite (scaffolded, not yet built)
- **Approach**: Spec-first — `.ai/specs/` is the source of truth. AI-DLC rituals drive the process.

## Repo Structure

```
.ai/specs/                    # Source of truth
.claude/                      # AI tool configuration (rituals, agents, skills)
django-ecommerce-api/         # Backend submodule — 3 Django apps
react-ecommerce/              # Frontend submodule — Vite + React scaffold
AGENTS.md                     # Loaded every session
CLAUDE.md                     # Non-negotiables
GETTING_STARTED.md            # Usage scale guide
```

## Backend Apps

| Django App | Domain | Key Models | Status |
|------------|--------|------------|--------|
| `authentication` | Auth | User (custom, email-based) | ✅ Implemented |
| `profiles` | Users | Address | ✅ Implemented |
| `catalog` | Catalog | Category, Seller, Product, ProductImage, ProductVariant, VariantAttribute, AttributeKey, Warehouse, Inventory, InventoryReservation | ✅ Implemented |

## Key Decisions (see `decisions/` for ADRs)

- Modular monolith for Phase 1 (ADR-003)
- JWT auth with short-lived access tokens (ADR-004)
- Service/Selector layer pattern per app (ADR-005)

## Key Links

- Backend: `github.com/nazmulnabil/django-ecommerce-api`
- Frontend: `github.com/nazmulnabil/react-ecommerce`
