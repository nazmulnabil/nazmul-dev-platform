# Frontend Development

**Stack**: React + Vite + TypeScript (scaffolded in `react-ecommerce/`)

## Getting Started

```bash
cd react-ecommerce/
npm install
npm run dev
```

## Conventions

| Concern | Convention |
|---------|-----------|
| Components | `src/components/`, one file per component |
| Pages | `src/pages/`, one page per route |
| API calls | Axios instance with interceptors for auth header + 401 refresh |
| State | React Context for global auth/cart, local state for forms |
| Styling | CSS Modules or Tailwind (TBD) |
| Testing | Vitest for unit, Playwright for e2e |

## API Contract Flow

1. Read `technical/contracts/rest/<domain>-api.yaml` for endpoint specs
2. Create API client function in `src/api/<domain>.ts`
3. Call from components via hooks or directly
4. Handle all states: loading, empty, error, success

## Project Structure

```
src/
  api/          # API client functions (one per domain)
  components/   # Shared UI components
  pages/        # Route-level components
  hooks/        # Custom React hooks
  contexts/     # React Context providers
  types/        # TypeScript types
  utils/        # Helpers
```

## Related

- Design system tokens: `design-system/`
- Per-module frontend specs: `modules/<domain>/frontend/spec.md`
