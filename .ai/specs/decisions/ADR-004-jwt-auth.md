# ADR-004: JWT Authentication over Session-Based Auth

**Status**: Accepted
**Date**: 2026-05-30

## Context
E-commerce with plans for mobile apps, API consumers, and potential microservices split. Need a stateless authentication mechanism.

## Decision
Use JWT (JSON Web Tokens) via `rest_framework_simplejwt`. Access tokens (60 min) + refresh tokens (1 day). Custom claims include `email` and `is_staff`.

## Consequences
- Positive: Stateless — no server-side session storage, works across services without shared session store, mobile-friendly, standard library support
- Neutral: Token revocation requires a blocklist or short expiry — we use short access tokens (60 min) with refresh flow
- Negative: Larger payload than session cookies, cannot invalidate individual tokens server-side without blocklist

## Alternatives
- **Session-based (Django default)**: Works well for server-rendered apps but awkward for mobile/API consumers
- **OAuth2 (auth code flow)**: Too heavy for Phase 1 — adds authorization server complexity
