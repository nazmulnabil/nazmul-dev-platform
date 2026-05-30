# ADR-003: Modular Monolith for Phase 1 (not Microservices)

**Status**: Accepted
**Date**: 2026-05-30

## Context
E-commerce platform with multiple domains (auth, users, catalog, cart, orders). Need to move fast in Phase 1 without the operational overhead of distributed systems.

## Decision
Build Phase 1 as a modular monolith — separate Django apps per domain with clear service boundaries, but deployed as a single process. Microservices only if needed later.

## Consequences
- Positive: No inter-service complexity (no message brokers, no distributed transactions), fast development velocity, single deployment unit
- Neutral: Domain boundaries enforced through code convention (services/selectors pattern), not through network boundaries — requires discipline
- Negative: Will need to split if any domain needs independent scaling

## Alternatives
- **Full microservices**: Premature. Would add 3x operational complexity for zero benefit at current scale
- **Serverless (Lambda + API Gateway)**: Would work but adds cold start latency, vendor lock-in, testing complexity
