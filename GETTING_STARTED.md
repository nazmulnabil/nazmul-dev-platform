# Getting Started

This kit scales from solo to enterprise. **Start small. Add folders as you grow.**

> Jump to your scale: [Solo](#solo--small-team) · [Team](#team) · [Enterprise](#enterprise)

## Solo / Small Team (< 5 people)

Only need 3 folders — ignore everything else:

```
.ai/specs/
├── product/              ← Vision, scope, personas (1-2 files)
└── modules/<domain>/     ← Your first feature
    ├── business/spec.md
    └── backend/spec.md   (or frontend/ — whichever platforms exist)
```

**Workflow**: Write `product/vision.md` → AI clarifies → write `modules/<domain>/business/spec.md` → AI implements

**Ignore until needed**: `business/`, `backlog/`, `iterations/`, `technical/contracts/`, `quality/`, `design-system/`

## Team (5-10 people)

Add planning and consistency layers:

```
Add: backlog/              ← Track stories and tasks
Add: iterations/           ← Plan feature slices
Add: quality/              ← Write tests
Add: development/          ← Coding standards, CI/CD
Add: technical/contracts/  ← API contracts for frontend/backend alignment
```

**Workflow**: Plan in `backlog/` → Spec in `modules/<domain>/` → Ship via `iterations/`

## Enterprise (10+ people)

Add governance and scale:

```
Add: decisions/           ← ADRs — start early, scales with you
Add: proposals/           ← PRFAQs, architecture proposals
Add: wbs/                 ← Timelines, estimates, dependencies
Add: operations/          ← Runbooks, monitoring (only post-deployment)
```

**Workflow**: PRFAQ → ADR → backlog → iterations → quality → operations

## Quick reference

| Scale | Must-have folders | Nice-to-have |
|-------|-------------------|--------------|
| Solo | `product/`, `modules/` | `technical/`, `ai-context/` |
| Team | + `backlog/`, `iterations/`, `quality/` | `development/`, `design-system/` |
| Enterprise | + `decisions/`, `proposals/`, `wbs/` | `operations/`, `reference/` |
