# Spec Writing Conventions

## Format
- Each feature has `business/spec.md` (human) and `technical/spec.md` (agent)
- Templates live in `.ai/specs/assets/templates/`
- For implemented features, status is `implemented` — spec documents what exists
- For new features, status is `draft` until approved

## Versioning
- Every spec has a semver version: `1.0.0`
- Status lifecycle: `draft` → `approved` → `implemented` → `deprecated`

## Template Files
- `.ai/specs/assets/templates/spec-template.md` — human-readable Markdown template
- `.ai/specs/assets/templates/spec-template-api.yaml` — backend API spec template
- `.ai/specs/assets/templates/spec-template-ui.yaml` — frontend UI spec template

## Per-Endpoint Detail
Each endpoint in the technical spec must include:
- Full path and HTTP method
- Auth requirement and permission class
- Complete request schema with all fields, types, constraints
- Complete response schema with all fields
- All possible status codes and their exception mappings
