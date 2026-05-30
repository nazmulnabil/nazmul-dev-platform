# ADR-005: Service/Selector Layer Pattern

**Status**: Accepted
**Date**: 2026-05-30

## Context
Django projects commonly mix business logic in views or models, leading to fat models, untestable views, and unclear responsibility boundaries.

## Decision
Adopt a strict three-layer pattern per app:

| Layer | File | Responsibility |
|-------|------|----------------|
| **Service** | `services.py` | Business logic, mutations, domain operations |
| **Selector** | `selectors.py` | Read logic, queries, projections |
| **View** | `views.py` | HTTP handling, serialization, delegation |

Domain exceptions live in `exceptions.py`, inheriting from `core.exceptions.DomainException`.

## Consequences
- Positive: Business logic is testable without HTTP, views are thin and predictable, selectors cacheable, clear separation of concerns
- Neutral: More files per feature — each endpoint typically needs a service function and a selector query
- Negative: Over-engineering for trivial CRUD (e.g., simple list endpoints) — but consistency across the codebase justifies it

## Alternatives
- **Fat models with managers**: Django convention but leads to model files with hundreds of lines mixing query logic, business rules, and validation
- **Logic in views**: Simplest but impossible to unit test without HTTP client
- **Use cases (Clean Architecture)**: Too ceremonial for Django — service layer achieves same goal with less boilerplate
