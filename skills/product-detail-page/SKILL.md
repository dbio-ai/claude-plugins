---
name: product-detail-page
description: Helping the user build a custom detail page for one product on a Dbio e-commerce store.
---

# Product Detail Page

Dbio provides a `<dbio-product-detail>` web component that wires gallery / price / variant / buy from a `product_id`. Relevant pieces:

- `auth_get_session`, `product_get`
- `page_create` with `metadata.product_id` set
- `section_upsert` (custom variant) embedding `<dbio-product-detail>` and related components
- `components_guide({ topic: 'product' })` + `agent_guidelines({ topic: 'product_detail_page' })` for full attributes

Default storefront already renders `/p/<slug>` — custom page is only needed when the user wants a non-default layout.
