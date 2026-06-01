# Git Workflow

## Current Reality

Solo/small-team e-commerce project. Development on localhost with Docker Compose. One production `main` branch. Staging/QA environments will be added after first deployment.

## Branch Strategy

| Branch | Environment | Current Status |
|--------|------------|---------------|
| `main` | Production | Active — code deployed here |
| `staging` | Pre-production | Planned — after first deployment |
| `test` | QA | Planned — after staging is set up |

### Flow (Today)
```
feature/* → main (PR, reviewed and merged)
```

### Flow (After Deployment)
```
feature/* → main (PR) → Docker image tagged → deploy
```

### Flow (Future — with staging)
```
feature/* → main → staging (UAT) → main (production)
```

## Branch Naming

| Type | Pattern | Example |
|------|---------|---------|
| Feature | `feature/<ticket-id>-<description>` | `feature/PROJ-123-user-auth` |
| Bugfix | `bugfix/<ticket-id>-<description>` | `bugfix/PROJ-234-ui-fix` |
| Hotfix | `hotfix/<ticket-id>-<description>` | `hotfix/PROJ-345-payment-crash` |

## Commit & PR Workflow

### 1. Create Feature Branch
```bash
git checkout main && git pull origin main
git checkout -b feature/<ticket-id>-<description>
```

### 2. Implement & Commit (after each logical unit)
```
<type>(TICKET-ID): <description>
[optional body]
```

### 3. Push
```bash
git push origin feature/<ticket-id>-<description>
```

### 4. Create PR to main
```bash
gh pr create --base main --head feature/<ticket-id>-<description> \
  --title "<type>(TICKET-ID): <description>" \
  --body "## Description\n\nImplementation of [brief description].\n\n## Changes\n- List key changes\n\n## Testing\n- [ ] Docker compose up — app starts\n- [ ] Tests pass\n\nCloses #TICKET-ID"
```

### 5. Do NOT Merge
I review and merge PRs. Only create and report the URL.

## PR Title Format

```
<type>(TICKET-ID): <description>
```

Types: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `chore`, `ci`
Breaking change: add `!` after type — `feat(PROJ-123)!: change auth flow`

## Commit Message Format

```
<type>(TICKET-ID): <description>

[optional body]

[optional footer]
```

Examples:
- `feat(PROJ-123): add JWT authentication with refresh tokens`
- `fix(PROJ-234): resolve price validation on checkout`
- `refactor(PROJ-345): extract inventory service layer`

## Agent Git Rules
- **DO** create feature branch from main
- **DO** commit with conventional format
- **DO** push to remote
- **DO** create a PR to main
- **DO** use author: nabilnazmul <nabilnazmul868@gmail.com>
- **DO NOT** merge any PR
- **DO NOT** commit directly to main
- **DO NOT** skip the PR step
- **DO NOT** use NKNabil1995 or brainstation-23.com email

## Merge Conflict Resolution

**NEVER** merge target branch into feature branch. Use temp branch from target.

```bash
# 1. Create temp branch from target
git checkout main
git pull origin main
git checkout -b merge-conflict-resolve/main/<feature-name>

# 2. Merge feature into temp branch
git merge feature/<ticket-id>-<description>
# Resolve conflicts
git add . && git commit -m "resolve: merge conflicts for <feature> into main"

# 3. Push and create PR (temp → main)
git push origin merge-conflict-resolve/main/<feature-name>

# 4. Clean up after merge
git branch -d merge-conflict-resolve/main/<feature-name>
git push origin --delete merge-conflict-resolve/main/<feature-name>
```

## Sync Feature Branch with main (Allowed)
```bash
git checkout feature/<ticket-id>-<description>
git merge main && git push origin feature/<ticket-id>-<description>
```

## Hotfix
```bash
# 1. Create from main
git checkout main && git checkout -b hotfix/PROJ-123-description

# 2. Fix → commit → PR to main
git add . && git commit -m "fix(PROJ-123): description"
git push origin hotfix/PROJ-123-description
# PR: hotfix → main
```

## Docker Release Tags

Once deployment starts, use tags to track releases:

```bash
git checkout main
git tag -a prod-v1.0.0 -m "Production release v1.0.0"
git push origin prod-v1.0.0
```

Tags are used by Docker Compose / CI to build and deploy specific versions.
