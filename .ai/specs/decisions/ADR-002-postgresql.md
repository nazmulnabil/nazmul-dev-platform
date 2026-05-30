# ADR-002: PostgreSQL over MySQL or SQLite

**Status**: Accepted
**Date**: 2026-05-30

## Context
E-commerce platform needs a relational database with JSON support for flexible product attributes, transactional integrity for orders/payments, and full-text search for catalog queries.

## Decision
Use PostgreSQL. Chosen over MySQL for superior JSON indexing, full-text search capabilities, and concurrent write performance.

## Consequences
- Positive: JSONField for flexible product attributes, built-in full-text search (no Elasticsearch needed early on), strong transactional guarantees with serializable isolation
- Neutral: PostgreSQL-specific migration patterns (array fields, JSONB operators)
- Operational: Requires managed PostgreSQL on cloud (RDS, Cloud SQL) — not an issue for deployment

## Alternatives
- **MySQL/MariaDB**: Comparable feature set but weaker JSON indexing, no native full-text search at PostgreSQL's quality
- **SQLite**: Excellent for dev/testing but production writes would bottleneck under multi-user e-commerce load
