# Catalog: Product & Inventory Management

**Version**: 1.0.0
**Status**: Implemented
**Last Updated**: 2026-05-28

---

## 1. Overview

Core catalog domain managing categories, sellers, products with variants, and multi-warehouse inventory with reservation system.

**Scope**:
- Category tree (hierarchical, self-referencing)
- Seller profiles linked to user accounts
- Products with category + seller assignment
- Product variants with SKU and attribute-based deduplication
- Multi-warehouse inventory tracking
- Inventory reservation lifecycle (active → released/confirmed)
- Read-only query layer with filtering, search, and pagination

**Note**: Only the service/selector layer is implemented. API views for catalog endpoints are not yet built.

---

## 2. Entity Overview

| Entity | Purpose | Key Fields |
|--------|---------|-----------|
| `Category` | Hierarchical product categories | `parent` (self-FK), `name`, `slug`, `is_active` |
| `Seller` | Seller profiles | `user` (O2O User), `store_name`, `is_verified` |
| `Product` | Products under seller + category | `name`, `slug`, `brand`, `is_active` |
| `ProductImage` | Product images | `image`, `is_primary`, `order` |
| `ProductVariant` | SKU-level product variations | `sku`, `price`, `attribute_hash` |
| `VariantAttribute` | Key-value variant attributes | `key` (FK AttributeKey), `value` |
| `AttributeKey` | Normalized attribute names | `name` (unique case-insensitive) |
| `Warehouse` | Physical storage locations | `name`, `city`, `country`, `is_active` |
| `Inventory` | Stock per variant per warehouse | `quantity`, `reserved`, `available` (property) |
| `InventoryReservation` | Stock reservation lifecycle | `idempotency_key`, `quantity`, `status` |

### Relationships

```
Category ──parent── Category (self)
User ──── Seller
Seller ───N Product ──N ProductVariant ──N VariantAttribute ──N AttributeKey
                │                           │
                N ProductImage         N Inventory ──N InventoryReservation
                                                 N Warehouse
```

---

## 3. Spec Files

| File | Coverage |
|------|----------|
| `categories.spec.yaml` | Category CRUD, active list, slug lookup |
| `products.spec.yaml` | Seller, Product, ProductImage, Variant, VariantAttribute, AttributeKey |
| `inventory.spec.yaml` | Warehouse, Inventory, InventoryReservation lifecycle |

---

## 4. Key Design Decisions

- **Attribute hash deduplication**: Variants with same attribute set get same SHA-256 hash → prevents duplicate variants per product
- **Slug collision retry**: Product slugs are generated from name with up to 5 retries using UUID suffix on collision
- **Idempotent reservations**: `InventoryReservation.idempotency_key` ensures same reservation can't be created twice
- **Pessimistic locking**: Inventory operations use `select_for_update` to prevent race conditions
- **Available inventory**: Computed as `quantity - reserved`; constraint ensures `quantity >= reserved`

---

## 5. Changelog

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0.0 | 2026-05-28 | — | Initial spec (backfilled from implementation) |
