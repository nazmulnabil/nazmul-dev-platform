# nazmul-dev-platform

Enterprise-grade spec-driven development starter kit. Portable framework for AI-driven teams.

## Structure

```
.ai/specs/                       # Source of truth
  product/                       # Vision, strategy, scope, personas
  business/                      # Domain logic, workflows, business rules
  technical/                     # Architecture, ADRs, contracts, deployment
  modules/                       # Feature specs (business + technical per module)
  backlog/                       # Epics, stories, tasks
  sprints/                       # Sprint plans & reports
  development/                   # Setup guides, coding standards
  design-system/                 # UI/UX specs
  quality/                       # Test strategy & scenarios
  ai-context/                    # AI system, product & coding context
  operations/                    # Runbooks, monitoring, DR
  change-requests/               # Change management
  history/                       # Decision log, archives
  assets/                        # Diagrams, images, templates
  decisions/                     # ADRs (architecture decision records)
  iterations/                    # Feature-slice iteration plans
.claude/                         # AI tool config (skills, agents, commands, hooks)
django-ecommerce-api/            # Backend submodule (Django + DRF)
react-ecommerce/                 # Frontend submodule (React + Vite)
```

## How to Use This Kit

1. **Copy** `.ai/` and `.claude/` to any new project
2. **Fill** `product/` with your product context
3. **Let AI** generate specs in `modules/` and implement from them
4. **Scale** from 1 to 100+ people by filling more sections as needed

## Repos

| Repo | URL | Branch |
|------|-----|--------|
| Context | `github.com/nazmulnabil/nazmul-dev-platform` | main |
| Backend | `github.com/nazmulnabil/django-ecommerce-api` | main |
| Frontend | `github.com/nazmulnabil/react-ecommerce` | main |

## Principle

Specs are the source of truth. If a decision isn't in `.ai/specs/`, it doesn't exist.
