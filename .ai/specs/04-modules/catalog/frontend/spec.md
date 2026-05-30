# Catalog — Frontend Implementation

**Contracts**: `03-technical/contracts/rest/catalog/`

## Pages / Routes

| Route | Page | Auth | Description |
|-------|------|------|-------------|
| `/categories` | CategoryListPage | Public | Browse product categories |
| `/categories/:slug` | CategoryDetailPage | Public | Products in category |
| `/products/:slug` | ProductDetailPage | Public | Product details + variants |

## Components

### CategoryListPage
- `CategoryCard` — name, image, product count
- `CategoryTree` — nested subcategory navigation
- States: loading → list → empty → error

### CategoryDetailPage
- `ProductGrid` — paginated product cards
- `FilterBar` — price range, brand, sort
- `SearchInput` — text search
- States: loading → grid → no results → error

### ProductDetailPage
- `ProductImages` — gallery with primary image
- `VariantSelector` — size, color, etc.
- `PriceDisplay` — current price, original price if on sale
- `AddToCartButton` — disabled if out of stock
- States: loading → detail → error

## API Dependencies

| Endpoint | Contract File |
|----------|---------------|
| Category list / detail | `catalog/categories-api.yaml` |
| Product list with filters | `catalog/products-api.yaml` |
| Product detail | `catalog/products-api.yaml` |
| Inventory / stock check | `catalog/inventory-api.yaml` |

## Error Handling

| Scenario | UI |
|----------|----|
| Category load fails | Retry button with error message |
| Product not found | "Product not found" page |
| Out of stock | "Out of stock" badge, disabled Add to Cart |
