---
name: product-detail-page
description: Building a custom detail page for ONE product on a Dbio ecomm store (gallery + variant picker + buy CTA + related products). Triggers - "trang chi tiết sản phẩm", "product detail page", "trang sản phẩm X", "custom layout cho sản phẩm", "page riêng cho product".
---

# Product Detail Page

The user wants a custom-layout detail page for ONE product. Dbio provides a `<dbio-product-detail>` web component so you don't reimplement gallery/variant/buy logic.

## Recommended flow

1. `auth_get_session()` — confirm active store is ecomm
2. `agent_guidelines({ topic: 'product_detail_page' })` — canonical playbook (component usage, wire-up, gotchas)
3. Follow the playbook (product_get → page_create with metadata.product_id → section_upsert with `<dbio-product-detail>` → publish)

## When to defer

- Multiple products grid → playbook `product_listing_page`
- Adding a NEW product (not building its page) → `ecom-product`
- Default storefront /p/<slug> is already fine → no custom page needed

## Common gotchas

- `product_id` lives in `page.metadata`, not in section.content
- `<dbio-product-detail>` handles gallery/price/variant — don't rebuild that layout
- Only works on `multi_page` or `ecomm` stores (single_page has no /p/ route)
