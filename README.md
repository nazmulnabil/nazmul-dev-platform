# nazmul-dev-platform

Enterprise-grade spec-driven development starter kit. Portable framework for AI-driven teams.

## Structure

```
.ai/specs/                       # Source of truth
  01-product/                    # Vision, strategy, scope, personas
  02-business/                   # Domain logic, workflows, business rules
  03-technical/                  # Architecture, ADRs, contracts, deployment
  04-modules/                    # Feature specs (business + technical per module)
  05-backlog/                    # Epics, stories, tasks
  06-sprints/                    # Sprint plans & reports
  07-development/                # Setup guides, coding standards
  08-design-system/              # UI/UX specs
  09-quality/                    # Test strategy & scenarios
  10-ai-context/                 # AI system, product & coding context
  11-operations/                 # Runbooks, monitoring, DR
  12-change-requests/            # Change management
  13-history/                    # Decision log, archives
  14-assets/                     # Diagrams, images, templates
.claude/                         # AI tool config (skills, agents, commands, hooks)
django-ecommerce-api/            # Backend submodule (Django + DRF)
react-ecommerce/                 # Frontend submodule (React + Vite)
```

## How to Use This Kit

1. **Copy** `.ai/` and `.claude/` to any new project
2. **Fill** `01-product/` with your product context
3. **Let AI** generate specs in `04-modules/` and implement from them
4. **Scale** from 1 to 100+ people by filling more sections as needed

## Repos

| Repo | URL | Branch |
|------|-----|--------|
| Context | `github.com/nazmulnabil/nazmul-dev-platform` | main |
| Backend | `github.com/nazmulnabil/django-ecommerce-api` | main |
| Frontend | `github.com/nazmulnabil/react-ecommerce` | main |

## Principle

Specs are the source of truth. If a decision isn't in `.ai/specs/`, it doesn't exist.
