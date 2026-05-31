# nazmul-dev-platform — Non-Negotiables

Spec-first development platform. All features driven by specs in `.ai/specs/`.

## External File Loading

When you encounter `@` file references below, use your Read tool to load them when needed. Do not pre-load everything — lazy-load on need.

- `@.claude/skills/git-workflow.md` — branch strategy, naming, commit/PR format, conflict resolution
- `@.claude/skills/architecture.md` — project overview, repos, backend patterns
- `@.claude/skills/spec-conventions.md` — spec format rules, versioning, templates
- `@.claude/skills/operations.md` — test/lint commands, decision log
- `@.claude/agents/spec-writer.md` — instructions for writing specs
- `@.claude/agents/implementer.md` — instructions for implementing from specs

## Core Rule: Spec is Truth

- Before implementing, read the spec from `.ai/specs/modules/<domain>/`
- If spec doesn't exist → write it first
- If implementation diverges → update spec first
- See `.ai/specs/MASTER_SPEC.md` for cross-cutting rules

## Project Structure

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
django-ecommerce-api/            # Backend submodule
react-ecommerce/                 # Frontend submodule
```

## Mandatory: Always Create a PR

After completing any task (implementation, refactor, spec write, etc.), the agent **must always**:
1. Commit all changes in a single commit with a descriptive message
2. Push the branch
3. Create a PR using the web URL: `https://github.com/nazmulnabil/nazmul-dev-platform/pull/new/<branch-name>`
4. Return the PR link to the user

Do NOT skip PR creation. Do NOT ask to create a PR — just do it.

## Workflow

1. **Context**: Read `.ai/specs/ai-context/` for current project state
2. **Spec-first**: Write business + technical specs in `.ai/specs/modules/<domain>/`
3. **Implement**: Agent reads technical spec → implements → tests
4. **Verify**: Tests validate against spec; update spec if needed
5. **PR**: Commit, push, create PR, and return the link

For Git operations (branch, commit, push, PR), see `@.claude/skills/git-workflow.md`.
