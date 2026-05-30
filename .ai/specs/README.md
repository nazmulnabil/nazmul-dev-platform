# .ai/specs — Spec-Driven Development Kit

Enterprise-grade, AI-native spec framework. Portable across any project.

## Navigation

| File | Purpose |
|------|---------|
| `INDEX.md` | AI navigation map to every spec file |
| `MASTER_SPEC.md` | Cross-cutting rules (auth, RBAC, audit, NFRs) |
| `CURRENT_SPRINT.md` | Active sprint context (what AI is working on) |
| `ROADMAP.md` | Project roadmap and milestones |
| `CHANGELOG.md` | Project-level changelog |
| `GLOSSARY.md` | Domain terminology |

## Sections

| Folder | Content | Audience |
|--------|---------|----------|
| `01-product/` | Vision, strategy, objectives, scope, personas | PM, stakeholders |
| `02-business/` | Domain logic, workflows, business rules, compliance | Domain experts |
| `03-technical/` | Architecture, ADRs, system design, contracts, deployment | Engineers |
| `04-modules/` | Feature specs (business + technical per module) | AI agents |
| `05-backlog/` | Epics, stories, tasks, bugs | PM, team |
| `06-sprints/` | Sprint plans, completion reports, feedback | PM, team |
| `07-development/` | Setup guides, coding standards, CI/CD, release process | Developers |
| `08-design-system/` | UI tokens, components, patterns | Designers, frontend |
| `09-quality/` | Test strategy, e2e scenarios, performance, security | QA, engineers |
| `10-ai-context/` | AI system context, product context, known issues | AI agents |
| `11-operations/` | Runbooks, monitoring, incidents, DR | Ops, SRE |
| `12-change-requests/` | Change management, CR tracking | PM, team |
| `13-history/` | Archived specs, completed sprints, decision log | Everyone |
| `14-assets/` | Diagrams, images, templates, mockups | Everyone |

## How to Use

1. **New project**: Copy `.ai/` folder. Fill `01-product/` and `02-business/` first.
2. **New feature**: Create spec pair in `04-modules/<domain>/business/spec.md` + `technical/spec.md`.
3. **Architecture decision**: Write ADR in `03-technical/architecture/decisions/ADR-NNN-title.md`.
4. **Track work**: Update `CURRENT_SPRINT.md`, add stories to `05-backlog/`.
5. **Ship**: Agent reads `04-modules/<domain>/technical/spec.md`, implements, runs tests.

## Principle

Specs are the source of truth. If a decision isn't in `.ai/specs/`, it doesn't exist.
