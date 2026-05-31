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
| `product/` | Vision, strategy, objectives, scope, personas | PM, stakeholders |
| `business/` | Domain logic, workflows, business rules, compliance | Domain experts |
| `technical/` | Architecture, ADRs, system design, contracts, deployment | Engineers |
| `modules/` | Feature specs (business + technical per module) | AI agents |
| `backlog/` | Epics, stories, tasks, bugs | PM, team |
| `sprints/` | Sprint plans, completion reports, feedback | PM, team |
| `development/` | Setup guides, coding standards, CI/CD, release process | Developers |
| `design-system/` | UI tokens, components, patterns | Designers, frontend |
| `quality/` | Test strategy, e2e scenarios, performance, security | QA, engineers |
| `ai-context/` | AI system context, product context, known issues | AI agents |
| `operations/` | Runbooks, monitoring, incidents, DR | Ops, SRE |
| `change-requests/` | Change management, CR tracking | PM, team |
| `history/` | Archived specs, completed sprints, decision log | Everyone |
| `assets/` | Diagrams, images, templates, mockups | Everyone |

## How to Use

1. **New project**: Copy `.ai/` folder. Fill `product/` and `business/` first.
2. **New feature**: Create spec pair in `modules/<domain>/business/spec.md` + `technical/spec.md`.
3. **Architecture decision**: Write ADR in `technical/architecture/decisions/ADR-NNN-title.md`.
4. **Track work**: Update `CURRENT_SPRINT.md`, add stories to `backlog/`.
5. **Ship**: Agent reads `modules/<domain>/technical/spec.md`, implements, runs tests.

## Principle

Specs are the source of truth. If a decision isn't in `.ai/specs/`, it doesn't exist.
