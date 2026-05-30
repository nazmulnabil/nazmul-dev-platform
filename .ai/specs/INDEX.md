# INDEX — Spec Navigation Map

## Product
- [vision.md](01-product/vision.md) — Product vision
- [strategy.md](01-product/strategy.md) — Go-to-market strategy
- [objectives.md](01-product/objectives.md) — Business objectives & KPIs
- [scope.md](01-product/scope.md) — In/out scope
- [personas.md](01-product/personas.md) — User personas
- [stakeholders.md](01-product/stakeholders.md) — Stakeholder map
- [constraints.md](01-product/constraints.md) — Business & technical constraints
- [assumptions.md](01-product/assumptions.md) — Key assumptions
- [risks.md](01-product/risks.md) — Risk register
- [success-criteria.md](01-product/success-criteria.md) — Success criteria

## Business
- `02-business/domains/<domain>/` — Domain-specific business rules & workflows
- `02-business/workflows/` — Cross-domain workflow definitions
- `02-business/operations/` — Operational procedures
- `02-business/approvals/` — Approval chains
- `02-business/reporting/` — Reporting requirements
- `02-business/integrations/` — Business integration requirements
- `02-business/compliance/` — Regulatory compliance

## Technical
- `03-technical/architecture/overview.md` — Architecture overview
- `03-technical/architecture/principles.md` — Design principles
- `03-technical/architecture/technology-stack.md` — Technology decisions
- `03-technical/architecture/decisions/ADR-*.md` — Architecture Decision Records
- `03-technical/system-design/` — C4 diagrams, module boundaries
- `03-technical/contracts/rest/` — OpenAPI specs per domain
- `03-technical/contracts/schemas/` — Shared data schemas
- `03-technical/contracts/events/` — Event contracts
- `03-technical/deployment/` — Deployment architecture
- `03-technical/security/` — Security model
- `03-technical/observability/` — Monitoring & logging

## Modules (Feature Specs)
| Module | Business | Technical |
|--------|----------|-----------|
| auth | [business/spec.md](04-modules/auth/business/spec.md) | [technical/spec.md](04-modules/auth/technical/spec.md) |
| users | [business/spec.md](04-modules/users/business/spec.md) | [technical/spec.md](04-modules/users/technical/spec.md) |
| catalog | [business/spec.md](04-modules/catalog/business/spec.md) | [technical/](04-modules/catalog/technical/) |

## Delivery
- `05-backlog/epics.md` — Epic breakdown
- `05-backlog/stories/` — User stories
- `05-backlog/tasks/` — Task breakdown
- `05-backlog/bugs/` — Bug tracker
- `05-backlog/technical-debt.md` — Tech debt log
- `06-sprints/sprint-N/` — Per-sprint plans & reports

## Development
- `07-development/setup.md` — Dev environment setup
- `07-development/coding-standards.md` — Code style & conventions
- `07-development/testing-guide.md` — How to test
- `07-development/ci-cd.md` — CI/CD pipeline
- `07-development/release-process.md` — Release workflow

## Quality
- `09-quality/testing-strategy.md` — Overall test strategy
- `09-quality/e2e/` — End-to-end test scenarios
- `09-quality/integration/` — Integration test scenarios
- `09-quality/security/` — Security test scenarios
- `09-quality/performance/` — Performance benchmarks

## AI Context
- `10-ai-context/system-context.md` — System overview for AI
- `10-ai-context/product-context.md` — Product context for AI
- `10-ai-context/architecture-context.md` — Architecture context for AI
- `10-ai-context/coding-context.md` — Coding rules for AI
- `10-ai-context/sprint-context.md` — Current sprint for AI
- `10-ai-context/known-issues.md` — Known issues & gotchas

## Governance
- `12-change-requests/CR-*.md` — Change requests
- `13-history/decisions/` — Decision log
- `13-history/archived-specs/` — Deprecated specs
- `13-history/completed-sprints/` — Sprint completion reports
