# Auth — Frontend Implementation

**Contract**: `03-technical/contracts/rest/auth-api.yaml`

## Pages / Routes

| Route | Page | Auth | Description |
|-------|------|------|-------------|
| `/login` | LoginPage | Public | Email + password login form |
| `/register` | RegisterPage | Public | Registration form |

## Components

### LoginPage
- `LoginForm` — email input, password input, submit button
- States: idle → validating → submitting → error → success (redirect)

### RegisterPage
- `RegisterForm` — email, username, password, phone (optional), submit button
- States: idle → validating → submitting → error → success (redirect)

## API Dependencies (from contract)

| Endpoint | When | UI Behavior |
|----------|------|-------------|
| `POST /api/v1/auth/register/` | Form submit | 201 → store tokens, redirect to /; 409 → "email taken" inline error |
| `POST /api/v1/auth/login/` | Form submit | 200 → store tokens, redirect to /; 401 → "wrong credentials" inline error |
| `POST /api/v1/auth/token/refresh/` | Access token expired | Silently refresh; 401 → redirect to /login |

## State Management

- Auth state: `{ user, accessToken, refreshToken }`
- On app init: check localStorage for tokens
- On 401: attempt refresh, if fails → clear auth → redirect /login

## Error Handling

| Scenario | UI |
|----------|----|
| Network failure | Toast: "Connection failed" |
| Validation error | Inline field errors |
| Session expired | Redirect to /login with message |
