# Auth — Mobile Implementation

**Contract**: `03-technical/contracts/rest/auth-api.yaml`

## Screens

| Screen | Access | Description |
|--------|--------|-------------|
| `LoginScreen` | Public | Email + password login |
| `RegisterScreen` | Public | Registration |

## Components

### LoginScreen
- Email field, password field, "Sign In" button
- Link to RegisterScreen
- States: idle → submitting → error → success (navigate to Home)

### RegisterScreen
- Email, username, password, phone fields, "Create Account"
- Link to LoginScreen
- States: idle → submitting → error → success (navigate to Home)

## API Dependencies (from contract)

| Endpoint | Mobile Behavior |
|----------|----------------|
| `POST /api/v1/auth/register/` | 201 → store tokens in secure storage; 409 → inline error |
| `POST /api/v1/auth/login/` | 200 → store tokens in secure storage; 401 → inline error |
| `POST /api/v1/auth/token/refresh/` | Silently refresh; 401 → clear storage, navigate to Login |

## Platform-Specific
- Token storage: iOS Keychain / Android EncryptedSharedPreferences
- Deep link support (future)

## Offline Behavior
- Cannot register or login offline
- Show cached user info when offline

## Error Handling
- Network: snackbar "No internet connection"
- Validation: inline field errors
- Session expired: modal → navigate to LoginScreen
