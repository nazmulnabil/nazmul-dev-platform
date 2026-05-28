# nazmul-dev-platform

**Spec-first e-commerce platform.** Backend API built with Django + DRF, frontend in React. All features start as specs — the single source of truth that both agents and humans read, implement against, and validate.

---

## Why This Repo Exists

This is not just another codebase. It's an **AI-augmented development platform** organized so that:

- **AI agents** understand the full context before writing a single line of code
- **Humans** review specs before implementation begins, catching design issues early
- **Specs stay fresh** — when code changes, the spec must change first
- **New contributors** (human or AI) get up to speed by reading specs, not digging through code

---

## The Flow

```
Requirement → Spec (MD + YAML) → Agent reads spec → Agent implements → Tests validate → PR reviewed → Merged
                ↑                                                                         │
                └───────────────────── Update spec if behavior changes ←──────────────────┘
```

---

## What's Implemented (backfilled as specs)

| Domain | Status | Spec | Backend | Frontend |
|--------|--------|------|---------|----------|
| Auth (register, login, JWT) | ✅ Built | `specs/auth/` | `users/` app | — |
| User profiles & addresses | ✅ Built | `specs/users/` | `users/` app | — |
| Catalog (categories, products, variants) | ✅ Service layer | `specs/catalog/` | `catalog/` app | — |
| Inventory (warehouse, reservations) | ✅ Service layer | `specs/catalog/` | `catalog/` app | — |

---

## Repository Structure

```
├── AGENTS.md                         # Entry point for opencode (auto-loaded)
├── CLAUDE.md                         # Entry point for Claude Code (auto-loaded)
├── specs/                            # 🎯 Source of truth — every feature starts here
│   ├── spec-template.md              #     Human-readable Markdown template
│   ├── spec-template-api.yaml        #     Backend API YAML template (agent-parsable)
│   ├── spec-template-ui.yaml         #     Frontend UI YAML template (agent-parsable)
│   ├── auth/                         #     Auth domain: register, login, JWT
│   ├── users/                        #     Users domain: profiles, addresses
│   └── catalog/                      #     Catalog domain: products, inventory
│
├── agents/                           # 🧠 Agent instruction files
│   ├── AGENTS.md                     #     Project memory & decision log
│   ├── git-workflow.md               #     Branch strategy, commits, PRs, conflicts
│   ├── architecture.md               #     Backend patterns & conventions
│   ├── spec-conventions.md           #     Spec format rules & versioning
│   ├── operations.md                 #     Test/lint commands & decisions log
│   ├── spec-writer.md                #     Agent: how to write a spec
│   └── implementer.md                #     Agent: how to implement from a spec
│
├── django-ecommerce-api/             # 📦 Backend (git submodule)
├── react-ecommerce/                  # 📦 Frontend (git submodule, scaffolding)
└── docs/                             # Architecture decisions (ADRs), conventions
```

---

## How Specs Work

Each feature gets a pair of files in `specs/<domain>/`:

| File | Purpose | Audience |
|------|---------|----------|
| `README.md` | Full human-readable spec | Developers, reviewers, stakeholders |
| `<name>.spec.yaml` | Structured, machine-parsable contract | AI agents |

### Writing a new feature spec

```bash
# 1. Write the spec
#    specs/<domain>/README.md
#    specs/<domain>/<name>[-api|-ui].spec.yaml

# 2. Agent reads spec, implements, tests
# 3. Reviewer validates spec matches implementation
```

### Status lifecycle

```
draft → approved → implemented → deprecated
```

---

## Git Workflow (4-branch)

| Branch | Environment | Protection |
|--------|------------|------------|
| `main` | Production | Protected, 1 reviewer |
| `staging` | Staging / UAT | Protected, 1 reviewer |
| `test` | QA Testing | Protected, 1 reviewer |
| `dev` | Developer integration | Unprotected |

Feature branches are created from `main`, then promoted: `feature → dev → test → staging → main`.

See `@agents/git-workflow.md` for full branch naming, commit format, PR conventions, and conflict resolution.

---

## Quick Start

```bash
git clone https://github.com/nazmulnabil/nazmul-dev-platform.git
cd nazmul-dev-platform
git submodule update --init --recursive

# Backend
cd django-ecommerce-api
cp .env.example .env              # configure DATABASE_URL
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver

# Tests
pytest
```

---

## Key References

| What | Where |
|------|-------|
| Agent instructions (opencode) | `AGENTS.md` |
| Agent instructions (Claude) | `CLAUDE.md` |
| Git rules | `@agents/git-workflow.md` |
| Backend architecture | `@agents/architecture.md` |
| Spec conventions | `@agents/spec-conventions.md` |
| Test & lint commands | `@agents/operations.md` |

---

## Design Principles

1. **Spec is truth.** No spec = no implementation. Code changes = spec changes first.
2. **Lazy-load instructions.** Agents read what they need, when they need it — not everything on every turn.
3. **Dual format.** Humans get Markdown. Agents get YAML. Same content, different surfaces.
4. **Backend-first, domain-driven.** Features are grouped by business domain (auth, catalog, cart, orders), not by layer.
