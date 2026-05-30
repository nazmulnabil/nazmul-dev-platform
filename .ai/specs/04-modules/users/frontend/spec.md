# Users — Frontend Implementation

**Contract**: `03-technical/contracts/rest/users-api.yaml`

## Pages / Routes

| Route | Page | Auth | Description |
|-------|------|------|-------------|
| `/profile` | ProfilePage | Yes | View + edit profile |
| `/profile/addresses` | AddressListPage | Yes | List, add, edit, delete addresses |

## Components

### ProfilePage
- `ProfileCard` — email, username, phone display
- `ProfileEditForm` — inline edit
- States: loading → display → editing → saving

### AddressListPage
- `AddressCard` per address with default badge
- `AddressForm` (modal) — label, street, city, country, postal code, is_default
- `EmptyState` — "No addresses yet"
- `DeleteConfirm` dialog

## API Dependencies (from contract)

| Endpoint | UI Behavior |
|----------|-------------|
| `GET /api/v1/auth/users/me/` | Page load → populate profile |
| `PATCH /api/v1/auth/users/me/` | Save → update displayed data |
| `GET /api/v1/auth/users/me/addresses/` | Page load → render cards or empty state |
| `POST /api/v1/auth/users/me/addresses/` | Save → add to list |
| `PATCH /api/v1/auth/users/me/addresses/{id}/` | Set default → uncheck others |
| `DELETE /api/v1/auth/users/me/addresses/{id}/` | Confirm → remove from list |

## State Management
- Profile: `{ user, isLoading, isSaving }`
- Addresses: `{ items[], isLoading, editingId }`
- Delete: optimistic removal → rollback on error
