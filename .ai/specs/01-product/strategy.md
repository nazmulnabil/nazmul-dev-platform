# Product Strategy

## Target Market

- **Primary**: Small-to-medium e-commerce businesses seeking a customizable, API-first marketplace
- **Secondary**: Developers and teams who want a spec-first, AI-native reference platform to learn from
- **Geographic**: Global, English-first with i18n-ready architecture

## Competitive Landscape

| Competitor | Weakness | Our Advantage |
|------------|----------|---------------|
| Shopify | Proprietary, limited customization, high transaction fees | Open source, fully customizable, spec-transparent |
| WooCommerce | Plugin hell, PHP legacy, security surface | Modern Django + DRF, clean API, type-safe |
| Medusa.js | Headless-only, requires separate frontend hosting | Monolithic option for Phase 1, modular split later |

## Go-to-Market

- **Phase 1**: Open-source reference implementation — developer audience
- **Phase 2**: Self-hosted marketplace package with Docker Compose
- **Phase 3**: Managed cloud offering (optional)

## Growth Strategy

- Phase 1: Foundation — auth, users, catalog (current)
- Phase 2: Transactions — cart, checkout, orders, payments
- Phase 3: Scale — multi-vendor, marketplace mechanics, analytics
