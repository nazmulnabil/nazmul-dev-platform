# Users — Mobile Implementation

**Contract**: `03-technical/contracts/rest/users-api.yaml`

## Screens

| Screen | Access | Description |
|--------|--------|-------------|
| `ProfileScreen` | Authenticated | View + edit profile |
| `AddressListScreen` | Authenticated | List + swipe delete |
| `AddressFormScreen` | Authenticated | Add / edit address |

## Components

### ProfileScreen
- Avatar, name, email, phone
- Tap-to-edit with save button
- States: loading → display → editing → saving

### AddressListScreen
- Swipeable address cards
- "Set as default" toggle
- FAB to add, pull-to-refresh
- Empty state illustration

### AddressFormScreen
- Form: label, street, city, country, postal code
- "Set as default" toggle
- States: idle → validating → submitting → error

## API Dependencies (from contract)
Same endpoints as frontend spec. All from `users-api.yaml`.

## Platform-Specific
- Pull-to-refresh on list
- Swipe-to-delete gesture on cards
- Native selection for country field

## Offline Behavior
- Cache last-loaded profile and addresses
- View cached data when offline
- Queue saves for retry (future)
