# AGENTS.md — Project Memory & Conventions

## Project Overview

- **Purpose**: Central context repository for e-commerce platform development
- **Backend**: `django-ecommerce-api/` — Django + DRF, JWT auth, PostgreSQL
- **Frontend**: `react-ecommerce/` — React (Vite), coming soon
- **Approach**: Spec-first development. Specs are the source of truth.

## Repos

| Repo | Type | URL | Branch |
|------|------|-----|--------|
| `django-ecommerce-api` | Backend submodule | `github.com/nazmulnabil/django-ecommerce-api` | main |
| `react-ecommerce` | Frontend submodule | `github.com/nazmulnabil/react-ecommerce` | main |

## Backend Architecture Patterns

- **Service Layer**: Business logic in `services.py` as pure functions
- **Selector Layer**: Read/query logic in `selectors.py`
- **Domain Exceptions**: Custom exceptions in `exceptions.py`, inheriting `DomainException`
- **Serializers**: Separate input and output serializers (`*InputSerializer`, `*OutputSerializer`)
- **Views**: DRF `APIView` with `@extend_schema` for OpenAPI docs
- **URLs**: Versioned under `/api/v1/<domain>/`
- **Testing**: pytest + model-bakery. Tests in `tests/` per app.

## Spec Writing Conventions

- Each feature has a `README.md` (human) and `.spec.yaml` (agent)
- YAML specs follow `spec-template-api.yaml` or `spec-template-ui.yaml`
- Versions use semver: `1.0.0`
- Status values: `draft` → `approved` → `implemented` → `deprecated`
- For implemented features, status is `implemented` and the spec documents what exists

## Decisions Log

| Date | Decision | Rationale |
|------|----------|-----------|
| 2026-05-27 | Spec-first development | AI agents implement from structured specs |
| 2026-05-27 | Dual format (MD + YAML) | MD for human readability, YAML for agent parsing |
| 2026-05-27 | Domain-based spec directories | Groups API + UI specs for same feature together |
| 2026-05-27 | Backfill existing features as `implemented` status | Document what exists before building new features |

## Git Workflow — Operational Commands

### Merge Conflict Resolution
**IMPORTANT**: Never merge target branch into feature branch. Use temp branch from target.
Only left-to-right sync allowed: main → staging → test → dev → feature.

```bash
# 1. Create temp branch from target
git checkout <target-branch>      # e.g. dev, test, staging
git pull origin <target-branch>
git checkout -b merge-conflict-resolve/<target>/<feature-name>

# 2. Merge feature into temp branch
git merge feature/<ticket-id>-<description>
# Resolve conflicts in IDE
git add .
git commit -m "resolve: merge conflicts for <feature-name> into <target>"

# 3. Push and create PR
git push origin merge-conflict-resolve/<target>/<feature-name>
# PR: temp-branch → target-branch

# 4. Clean up after merge
git branch -d merge-conflict-resolve/<target>/<feature-name>
git push origin --delete merge-conflict-resolve/<target>/<feature-name>
```

### Left-to-Right Sync (Allowed)
```bash
# Sync main → feature branch
git checkout feature/<ticket-id>-<description>
git merge main
git push origin feature/<ticket-id>-<description>

# Sync main → staging (via PR)
git checkout staging
git pull origin staging
git checkout -b merge-conflict-resolve/staging/main-sync
git merge main
# resolve → push → PR to staging
```

### Hotfix Deployment
```bash
# 1. Create from main
git checkout main
git checkout -b hotfix/PROJ-123-description

# 2. Fix → commit → PR to main
git add .
git commit -m "fix(PROJ-123): description"
git push origin hotfix/PROJ-123-description
# PR: hotfix → main

# 3. After merge, cherry-pick to other branches
git checkout staging && git cherry-pick <hash> && git push
git checkout test && git cherry-pick <hash> && git push
git checkout dev && git cherry-pick <hash> && git push
```

## Key Commands

- **Run backend tests**: `pytest` in `django-ecommerce-api/`
- **Run linter**: `ruff check .` in `django-ecommerce-api/`
- **Generate OpenAPI schema**: `python manage.py spectacular --file schema.yaml` in `django-ecommerce-api/`
