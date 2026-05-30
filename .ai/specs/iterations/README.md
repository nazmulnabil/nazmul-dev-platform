# iterations/ — Feature Slices

An iteration is a **self-contained feature slice** that delivers independent value. It is NOT a time-boxed sprint and NOT a PR batch.

## Anatomy of an iteration

```
iterations/
├── README.md
├── iteration-001-user-auth/
│   ├── README.md              # What this iteration ships + completion report
│   ├── plan.md                # AI-generated plan → human approved
│   ├── stories.md             # Stories included in this iteration
│   └── tasks.md               # Platform-specific task breakdown
└── iteration-002-catalog-api/
```

## What determines a single iteration

An iteration is a **vertical feature slice** that:

- Spans all layers that exist for this feature (business logic → API → UI → mobile)
- Can be demoed to a stakeholder
- Has a clear "done" boundary
- Fits in hours or days, not weeks

| Right Size | Too Large |
|------------|-----------|
| "User registration with email/password" | "Build the entire auth system" |
| "Product listing page with pagination" | "Build the entire catalog" |
| "Add item to cart API" | "Build the entire checkout flow" |

## When to create a new iteration

| Situation | Action |
|-----------|--------|
| Shipping a new feature | Create `iteration-NNN-name/` |
| Extending a shipped feature | Create a new iteration for the extension |
| Fixing a set of related bugs | Create `iteration-NNN-bugfix-description/` |
| Iteration is taking >5 days | Break it into smaller iterations |

## When to extend an existing iteration

| Situation | Action |
|-----------|--------|
| Feature is still in progress and not shipped | Extend the existing iteration |
| Feedback from review requires small changes | Extend the existing iteration |

## Bad signs

- An iteration with 50+ tasks → too large. Split it.
- An iteration taking 2+ weeks → smells like a sprint. Break it down.
- An iteration with no completion report → never finished. Close it or ship it.

## Minimal example entry

```markdown
# iteration-001: User Authentication

## Ships
Email/password registration and login with JWT tokens.

## Plan
1. Domain model: User entity
2. Backend API: register, login, token refresh
3. Frontend: login page, registration form
4. Tests: backend pytest, frontend Vitest

## Completed
- User model with email as USERNAME_FIELD
- POST /api/v1/auth/register/
- POST /api/v1/auth/login/
- Login page with form validation
- Backend tests: 8/8 passing

## Not Done (deferred)
- Mobile auth screens → iteration-007
- Social login → iteration-009
```
