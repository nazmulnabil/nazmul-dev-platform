# Mobile Development

**Stack**: TBD (React Native / Flutter — not yet scaffolded)

## Getting Started

Mobile is not yet implemented. When it begins:

```bash
# Future scaffold command
```

## Conventions (proposed)

| Concern | Convention |
|---------|-----------|
| Screens | One screen per file in `screens/` |
| Navigation | React Navigation (stack + tab) |
| API calls | Axios + interceptors |
| State | React Context + SWR/React Query |
| Offline | AsyncStorage for cache, NetInfo for connectivity |
| Testing | Detox for e2e, Jest for unit |

## API Contract Flow

1. Read `technical/contracts/rest/<domain>-api.yaml` for endpoint specs
2. Create API service in `src/services/<domain>.ts`
3. Call from screens via hooks
4. Handle all states: loading, empty, error, success

## Project Structure (proposed)

```
src/
  screens/      # Screen-level components
  components/   # Shared UI components
  services/     # API client functions
  navigation/   # Navigation config
  hooks/        # Custom hooks
  storage/      # Local storage / caching
  utils/        # Helpers
```

## Related

- Design system tokens: `design-system/`
- Per-module mobile specs: `modules/<domain>/mobile/spec.md`
