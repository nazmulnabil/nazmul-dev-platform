# nazmul-dev-platform — Agent Instructions

Spec-first development platform. All features driven by specs in `specs/`.

## External File Loading

When you encounter `@` file references below, use your Read tool to load them when needed. Do not pre-load everything — lazy-load on need.

- `@agents/git-workflow.md` — branch strategy, naming, commit/PR format, conflict resolution
- `@agents/architecture.md` — project overview, repos, backend patterns
- `@agents/spec-conventions.md` — spec format rules, versioning, templates
- `@agents/operations.md` — test/lint commands, decision log
- `@agents/spec-writer.md` — instructions for writing specs
- `@agents/implementer.md` — instructions for implementing from specs

## Core Rule: Spec is Truth

- Before implementing, read the spec from `specs/<domain>/`
- If spec doesn't exist → write it first
- If implementation diverges → update spec first

## Project Structure

```
specs/                        # Source of truth
  <domain>/
    README.md                 # Human-readable spec
    <feature>[-api|-ui].spec.yaml  # Agent-parsable spec
agents/                       # Agent configurations
django-ecommerce-api/         # Backend submodule
react-ecommerce/              # Frontend submodule
```

## Workflow

1. **Spec-first**: Write `spec.yaml` + `README.md` in `specs/<domain>/`
2. **Implement**: Agent reads spec → implements → tests
3. **Verify**: Tests validate against spec; update spec if needed

For Git operations (branch, commit, push, PR), see `@agents/git-workflow.md`.
