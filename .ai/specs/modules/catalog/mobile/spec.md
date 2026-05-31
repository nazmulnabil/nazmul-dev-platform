# Catalog — Mobile Implementation

**Contracts**: `technical/contracts/rest/catalog/`

## Screens

| Screen | Access | Description |
|--------|--------|-------------|
| `CategoryListScreen` | Public | Browse categories (grid) |
| `ProductListScreen` | Public | Products in category with filters |
| `ProductDetailScreen` | Public | Product details, variants, add to cart |

## Components

### CategoryListScreen
- Category grid (2 columns) with images
- Pull-to-refresh
- Infinite scroll for subcategories (expandable)

### ProductListScreen
- Product cards in list/grid toggle
- Filter bottom sheet (price, brand, sort)
- Search bar in header
- Pull-to-refresh + pagination on scroll

### ProductDetailScreen
- Image gallery (swipeable)
- Variant selector (horizontal scrollable chips)
- Price + stock indicator
- Add to Cart button (sticky bottom)
- States: loading → detail → error

## API Dependencies
Same as frontend. All from `catalog/` contracts.

## Platform-Specific
- Filter bottom sheet (iOS: native sheet, Android: modal)
- Swipeable image gallery
- Haptic feedback on Add to Cart
- Share product via native share sheet

## Offline Behavior
- Cache product images and category tree
- Show cached catalog when offline
- Mark items that may be out of stock (stale data warning)
