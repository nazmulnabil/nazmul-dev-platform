# nazmul-dev-platform — Agent Instructions

This is a spec-first development platform. All features are driven by specs in `specs/`.

## External File Loading

When you encounter `@` file references below, use your Read tool to load them when the task requires that information. Do not pre-load everything — lazy-load on need.

Key reference files:
- `@agents/AGENTS.md` — project memory, detailed git commands, architecture patterns
- `@agents/spec-writer.md` — instructions for writing specs
- `@agents/implementer.md` — instructions for implementing from specs

## Core Rule: Spec is Truth

- **Before implementing anything**, read the relevant spec from `specs/<domain>/`
- The spec defines: API contracts, data models, business rules, error handling
- If the spec doesn't exist for an unimplemented feature → write it first
- If implementation diverges from spec → update the spec first, then fix code

## Project Structure

```
specs/                        # Source of truth
  <domain>/
    README.md                 # Human-readable spec (Markdown)
    <feature>.spec.yaml       # Agent-parsable spec (YAML)
    <feature>-api.spec.yaml   # Backend API spec
    <feature>-ui.spec.yaml    # Frontend UI spec
agents/                       # Agent configurations
  AGENTS.md                   # Project memory, conventions
  spec-writer.md              # Agent: write specs
  implementer.md              # Agent: implement from specs
django-ecommerce-api/         # Backend submodule
react-ecommerce/              # Frontend submodule
```

## Workflow

1. **Spec-first**: For new features → write `spec.yaml` + `README.md` in `specs/<domain>/`
2. **Implement**: Agent reads spec → implements code → runs tests
3. **Verify**: Tests validate against spec; update spec if behavior changes

## Git Workflow — Commit, Push & PR Workflow

When implementing a feature or fix from a spec, follow this exact sequence:

### 1. Create Feature Branch
```bash
git checkout main
git pull origin main
git checkout -b feature/<ticket-id>-<description>
```
Always branch from `main`, never from another feature branch.

### 2. Implement & Commit
- Commit after each logical unit of work (not everything in one commit)
- Follow the commit format strictly:

```
<type>(TICKET-ID): <description>

[optional body]
```

### 3. Push
```bash
git push origin feature/<ticket-id>-<description>
```

### 4. Create PR to Target Branch
After pushing, create a PR. The target depends on where you're deploying:

**Dev environment (default):**
```bash
gh pr create --base dev --head feature/<ticket-id>-<description> \
  --title "<type>(TICKET-ID): <description>" \
  --body "## Description\n\nImplementation of [brief description].\n\n## Changes\n- List key changes\n\n## Testing\n- [ ] Tests pass\n\nCloses #TICKET-ID"
```

**Test environment (QA):**
```bash
gh pr create --base test --head feature/<ticket-id>-<description> \
  --title "<type>(TICKET-ID): <description>" \
  --body "..."
```

### 5. Do NOT Merge
**I review and merge PRs.** Never merge a PR yourself. Only create it and report the URL.

### Summary — Agent Git Rules
- **DO** create feature branch from main
- **DO** commit with conventional format
- **DO** push to remote
- **DO** create a PR to the target branch
- **DO NOT** merge any PR
- **DO NOT** commit directly to main/dev/test/staging
- **DO NOT** skip the PR step

## Git Workflow — Branch Strategy

4 protected branches (hierarchy: MAIN ← STAGING ← TEST ← DEV):

| Branch | Environment | Protection | Deployment |
|--------|------------|------------|------------|
| `main` | Production | Protected, 1 reviewer | App Store/Play Store |
| `staging` | Staging/UAT | Protected, 1 reviewer | Staging flavor |
| `test` | QA Testing | Protected, 1 reviewer | Test flavor |
| `dev` | Dev Integration | Unprotected | Dev flavor |

### Branch Flow Rules

- **Feature/Bugfix branches** always created from `main`
- Feature → `dev`: PR or local merge
- Feature → `test`: individual PR (QA testing)
- Feature → `staging`: individual PR, selective (only QA-approved)
- `staging` → `main`: PR after UAT approval
- Sync allowed: MAIN → STAGING → TEST → DEV → feature branches (left-to-right only)

### Branch Naming

| Type | Pattern | Example |
|------|---------|---------|
| Feature | `feature/<ticket-id>-<description>` | `feature/PROJ-123-user-auth` |
| Bugfix | `bugfix/<ticket-id>-<description>` | `bugfix/PROJ-234-ui-fix` |
| Hotfix | `hotfix/<ticket-id>-<description>` | `hotfix/PROJ-345-payment-crash` |

### PR Title Format

```
<type>(TICKET-ID): <description>
```

Types: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `chore`, `ci`

Breaking change: add `!` after type — `feat(PROJ-123)!: change auth flow`

### Commit Message Format

```
<type>(TICKET-ID): <description>

[optional body]

[optional footer]
```

Examples:
- `feat(PROJ-123): add JWT authentication with refresh tokens`
- `fix(PROJ-234): resolve price validation on checkout`
- `refactor(PROJ-345): extract inventory service layer`

### Merge Conflict Resolution

- **NEVER** merge target branch into feature branch to resolve conflicts
- Use temp branch from target: `merge-conflict-resolve/<target>/<feature>`
- Only left-to-right sync allowed (main → staging → test → dev → feature)
- See `@agents/AGENTS.md` for full conflict resolution commands

## Conventions

- Every spec has a semver version in its YAML
- `specs/spec-template-api.yaml` and `specs/spec-template-ui.yaml` are the authoring templates
- See `@agents/AGENTS.md` for project memory, detailed conventions, and operational commands
