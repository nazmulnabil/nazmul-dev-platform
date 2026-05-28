# Git Workflow — All Rules

## Branch Strategy

4 protected branches (hierarchy: MAIN ← STAGING ← TEST ← DEV):

| Branch | Environment | Protection | Deployment |
|--------|------------|------------|------------|
| `main` | Production | Protected, 1 reviewer | App Store/Play Store |
| `staging` | Staging/UAT | Protected, 1 reviewer | Staging flavor |
| `test` | QA Testing | Protected, 1 reviewer | Test flavor |
| `dev` | Dev Integration | Unprotected | Dev flavor |

### Flow Rules
- Feature/Bugfix branches always created from **main**
- Feature → `dev`: PR or local merge
- Feature → `test`: individual PR (QA testing)
- Feature → `staging`: individual PR, selective (only QA-approved)
- `staging` → `main`: PR after UAT approval
- Sync allowed: MAIN → STAGING → TEST → DEV → feature (left-to-right only)

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

### 4. Create PR
**Dev (default):**
```bash
gh pr create --base dev --head feature/<ticket-id>-<description> \
  --title "<type>(TICKET-ID): <description>" \
  --body "## Description\n\nImplementation of [brief description].\n\n## Changes\n- List key changes\n\n## Testing\n- [ ] Tests pass\n\nCloses #TICKET-ID"
```

**Test (QA):**
```bash
gh pr create --base test --head feature/<ticket-id>-<description> \
  --title "<type>(TICKET-ID): <description>" --body "..."
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

## Agent Git Rules Summary
- **DO** create feature branch from main
- **DO** commit with conventional format
- **DO** push to remote
- **DO** create a PR to the target branch
- **DO NOT** merge any PR
- **DO NOT** commit directly to main/dev/test/staging
- **DO NOT** skip the PR step

## Merge Conflict Resolution

**NEVER** merge target branch into feature branch. Use temp branch from target.
Only left-to-right sync allowed: main → staging → test → dev → feature.

```bash
# 1. Create temp branch from target
git checkout <target-branch>
git pull origin <target-branch>
git checkout -b merge-conflict-resolve/<target>/<feature-name>

# 2. Merge feature into temp branch
git merge feature/<ticket-id>-<description>
# Resolve conflicts
git add . && git commit -m "resolve: merge conflicts for <feature> into <target>"

# 3. Push and create PR (temp → target)
git push origin merge-conflict-resolve/<target>/<feature-name>

# 4. Clean up after merge
git branch -d merge-conflict-resolve/<target>/<feature-name>
git push origin --delete merge-conflict-resolve/<target>/<feature-name>
```

## Left-to-Right Sync (Allowed)

```bash
# Sync main → feature branch
git checkout feature/<ticket-id>-<description>
git merge main && git push origin feature/<ticket-id>-<description>

# Sync main → staging (via temp branch + PR)
git checkout staging && git pull origin staging
git checkout -b merge-conflict-resolve/staging/main-sync
git merge main
# resolve → push → PR to staging
```

## Hotfix Deployment

```bash
# 1. Create from main
git checkout main && git checkout -b hotfix/PROJ-123-description

# 2. Fix → commit → PR to main
git add . && git commit -m "fix(PROJ-123): description"
git push origin hotfix/PROJ-123-description
# PR: hotfix → main

# 3. After merge, cherry-pick to other branches
git checkout staging && git cherry-pick <hash> && git push
git checkout test && git cherry-pick <hash> && git push
git checkout dev && git cherry-pick <hash> && git push
```
