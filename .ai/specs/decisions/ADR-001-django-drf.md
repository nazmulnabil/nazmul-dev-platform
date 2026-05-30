# ADR-001: Django + DRF over FastAPI or Node.js

**Status**: Accepted
**Date**: 2026-05-30

## Context
Need a backend framework for an e-commerce platform with complex relational models (products, variants, inventory, orders), admin interfaces, and rapid iteration. The team is small and values mature ecosystem over raw performance.

## Decision
Use Django 5 + Django REST Framework. Python ecosystem, mature ORM, built-in admin, extensive package ecosystem (simplejwt, drf-spectacular, model-bakery).

## Consequences
- Positive: Mature ORM for complex relational queries, built-in admin panel, excellent testing tooling (pytest + model-bakery), drf-spectacular generates OpenAPI schema automatically
- Neutral: Monolithic by default — requires deliberate effort to split later
- Negative: Heavier than FastAPI for simple services, not async-native

## Alternatives
- **FastAPI**: Better performance, async-native, but fewer Django-style batteries (no ORM, no admin)
- **Node.js/Express**: Larger hiring pool but weaker relational modeling. Not chosen because domain complexity favors Django's ORM
