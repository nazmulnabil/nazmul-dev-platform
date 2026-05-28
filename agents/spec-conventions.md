# Spec Writing Conventions

## Format
- Each feature has a `README.md` (human) and `.spec.yaml` (agent)
- YAML specs follow `spec-template-api.yaml` or `spec-template-ui.yaml`
- For implemented features, status is `implemented` — spec documents what exists
- For new features, status is `draft` until approved

## Versioning
- Every spec has a semver version in its YAML: `1.0.0`
- Status lifecycle: `draft` → `approved` → `implemented` → `deprecated`

## Template Files
- `specs/spec-template.md` — human-readable Markdown template
- `specs/spec-template-api.yaml` — backend API spec template
- `specs/spec-template-ui.yaml` — frontend UI spec template

## Per-Endpoint Detail
Each endpoint in the YAML spec must include:
- Full path and HTTP method
- Auth requirement and permission class
- Complete request schema with all fields, types, constraints
- Complete response schema with all fields
- All possible status codes and their exception mappings
