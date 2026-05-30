# decisions/ — Architecture Decision Records (ADRs)

Permanent, timestamped records of architectural choices that shape this system.

## What belongs here

Numbered ADRs that document significant, long-lived architectural decisions:

```
decisions/
├── README.md
├── ADR-001-use-postgresql.md
├── ADR-002-use-jwt-auth.md
└── ADR-NNN-title-of-decision.md
```

Each ADR follows this structure:

| Section | Content |
|---------|---------|
| **Context** | What problem or constraint drove this decision |
| **Decision** | What was chosen |
| **Consequences** | Positive and negative effects of this choice |
| **Alternatives** | What else was considered and why it was rejected |

## What does NOT belong here

- **Session-specific agent notes** like "we agreed to use Ruff for linting" → goes to `ai-context/decisions/`
- **Temporary workarounds or in-progress state** → goes to `ai-context/state/`
- **Operational runbooks** → goes to `operations/runbooks/`

**Rule of thumb**: If the decision should still make sense in 6 months, it belongs in `decisions/`. If it's relevant for the current session only, it belongs in `ai-context/`.

## Minimal example

```markdown
# ADR-001: Use PostgreSQL as Primary Database

**Status**: Accepted
**Date**: 2026-05-29

## Context
E-commerce platform needs a relational database with JSON support for flexible product attributes, transactional integrity for orders/payments, and full-text search for catalog queries.

## Decision
Use PostgreSQL. Chosen over MySQL for superior JSON indexing, full-text search capabilities, and concurrent write performance.

## Consequences
- Positive: JSONField for flexible product attributes, built-in full-text search, strong transactional guarantees
- Neutral: Requires PostgreSQL-specific migration patterns
- Operational: Managed PostgreSQL on AWS RDS

## Alternatives
- **MySQL**: Comparable but weaker JSON indexing and full-text search
- **MongoDB**: NoSQL — doesn't suit transactional order/inventory domain
```

## When to write an ADR

Write an ADR when you make a decision that:
- Has lasting impact on the system architecture
- Involves a trade-off between alternatives
- A future team member would benefit from understanding the rationale
