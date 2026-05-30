# 04-Modules — Feature Specifications

Each module has two spec files:
- **business/spec.md** — Plain language. Readable by non-engineers.
- **technical/spec.md** — Engineering detail. Readable by AI agents.

## Current Modules

| Module | Business | Technical | Status |
|--------|----------|-----------|--------|
| auth | [View](auth/business/spec.md) | [View](auth/technical/spec.md) | ✅ Implemented |
| users | [View](users/business/spec.md) | [View](users/technical/spec.md) | ✅ Implemented |
| catalog | [View](catalog/business/spec.md) | [View](catalog/technical/) | ✅ Implemented |

## Creating a New Module

1. Create `04-modules/<domain>/` directory
2. Write `business/spec.md` — what the feature does, in plain language
3. Write `technical/spec.md` — entities, endpoints, rules, exceptions
4. Reference `MASTER_SPEC.md` for cross-cutting conventions
