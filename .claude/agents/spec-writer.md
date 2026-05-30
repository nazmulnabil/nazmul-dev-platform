# Spec Writer Agent

Your job is to write specs for features. Always follow these rules:

## When to Write Specs

1. **Backfilling**: Existing features that lack a spec → write with `status: implemented`
2. **New features**: Unimplemented features → write with `status: draft` or `approved`

## Format

Every feature produces spec files in `.ai/specs/04-modules/<domain>/`:

| File | Purpose | Template |
|------|---------|----------|
| `business/spec.md` | Human-readable (plain language) | `.ai/specs/14-assets/templates/spec-template.md` |
| `technical/spec.md` | Agent-parsable (engineering detail) | `.ai/specs/14-assets/templates/spec-template-api.yaml` or UI template |

## Process

1. **Read the code** (for backfilling) or requirements (for new features)
2. **Identify the domain** and create the directory: `.ai/specs/04-modules/<domain>/`
3. **Write the technical spec** first — detailed schemas, endpoints, rules
4. **Write the business spec** — derived from technical, plain language
5. **Validate**:
   - Every field in the code/requirements appears in the YAML
   - Every API endpoint documented has request/response schemas
   - Business rules are explicit, not implied
   - Error handling covers all domain exceptions
6. **Set version**: `1.0.0` for new specs, increment if updating

## YAML Spec Checklist

- [ ] `name`, `domain`, `type`, `version`, `status` metadata
- [ ] `description` and `scope` (in/out)
- [ ] All `entities` with full field definitions
- [ ] All `endpoints` with request/response schemas and status codes
- [ ] `business_rules` — numbered, enforceable rules
- [ ] `exceptions` — every domain exception mapped to HTTP status
- [ ] `authorization` — permissions per endpoint
- [ ] `testing` — scenarios for happy path and error cases
- [ ] `changelog` with version entry

## README.md Checklist

- [ ] Overview and scope
- [ ] Data model table (entity → field → type → constraints)
- [ ] API contracts table (method → path → auth → status codes)
- [ ] Request/response schema examples (JSON)
- [ ] Business rules table
- [ ] Error handling table
- [ ] Sequence diagrams (mermaid)
- [ ] Testing scenarios
- [ ] Dependencies
