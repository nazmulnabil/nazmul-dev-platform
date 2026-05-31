# Business — Domain Context

E-commerce marketplace domains.

## Domains

| Domain | Description | Spec Location |
|--------|-------------|---------------|
| **Auth** | Registration, login, JWT token management | `modules/auth/` |
| **Users** | User profiles, address management | `modules/users/` |
| **Catalog** | Categories, products, variants, inventory | `modules/catalog/` |
| **Cart** | Shopping cart (planned Phase 2) | Not yet created |
| **Orders** | Order lifecycle (planned Phase 2) | Not yet created |

## Cross-Domain Workflows

| Workflow | Domains Involved | Status |
|----------|-----------------|--------|
| User registration → profile creation | Auth → Users | ✅ Implemented |
| Product listing → inventory tracking | Catalog (products + inventory) | ✅ Implemented |
| Browse → add to cart → checkout | Catalog → Cart → Orders | 🔜 Planned |

## Business Rules

Business rules per domain are documented in each module's `business/spec.md`. Cross-cutting rules in `MASTER_SPEC.md`.
