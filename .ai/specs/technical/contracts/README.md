# Contracts — Shared API Contracts

Single source of truth for all API contracts. Backend implements, Frontend + Mobile consume.

## Structure

```
contracts/
  rest/
    auth-api.yaml           ← Auth endpoints (register, login, token refresh)
    users-api.yaml          ← Users endpoints (profile, addresses)
    catalog/                ← Catalog endpoints (categories, products, inventory)
      categories-api.yaml
      products-api.yaml
      inventory-api.yaml
```

## Contract-First Flow

```
contracts/rest/auth-api.yaml
    │
    ├── modules/auth/backend/spec.yaml         ← "Implement these endpoints"
    ├── modules/auth/frontend/spec.md           ← "Call these endpoints"
    └── modules/auth/mobile/spec.md             ← "Call these endpoints"
```

## Contract Format

Each contract is an OpenAPI 3.0 YAML with:
- Paths + methods + request/response schemas
- Status codes per endpoint
- Common schemas in `components/schemas/`

Backend specs in `modules/<domain>/backend/` contain additional implementation details (entities, services, exceptions) that are NOT in the contract.
