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

- Before implementing, read the spec from `.ai/specs/04-modules/<domain>/`
- If spec doesn't exist → write it first
- If implementation diverges → update spec first
- See `.ai/specs/MASTER_SPEC.md` for cross-cutting rules

## Project Structure

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
django-ecommerce-api/            # Backend submodule
react-ecommerce/                 # Frontend submodule
```

## Workflow

1. **Context**: Read `.ai/specs/10-ai-context/` for current project state
2. **Spec-first**: Write business + technical specs in `.ai/specs/04-modules/<domain>/`
3. **Implement**: Agent reads technical spec → implements → tests
4. **Verify**: Tests validate against spec; update spec if needed

For Git operations (branch, commit, push, PR), see `@.claude/skills/git-workflow.md`.
