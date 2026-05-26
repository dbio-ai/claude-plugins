---
name: product-detail-page
description: Building a custom detail page for ONE product on a Dbio ecomm store (gallery + variant picker + buy CTA + related products). Triggers - "trang chi tiết sản phẩm", "product detail page", "trang sản phẩm X", "custom layout cho sản phẩm", "page riêng cho product".
---

# Product Detail Page on Dbio

Dbio has a `<dbio-product-detail>` web component — drop it in `template_html` and the backend wires title/price/gallery/variant/buy. Don't reimplement.

Quick flow:

1. `auth_get_session` — confirm active store is `ecomm` or `multi_page`
2. `product_get({ id: X })` — verify product + grab category_slug
3. `page_create({ profile_type: "product", global_code: product.slug, metadata: { product_id: X } })`
4. `section_upsert({ section_type: "content", variant: "custom", content: { template_html: "<dbio-product-detail product_id=\"{{product_id}}\" /> ..." } })`
5. `page_publish`

URL becomes `{{platform}}/p/{{product.slug}}`.

## Gotchas

- `product_id` lives in `page.metadata`, NOT in section.content
- `<dbio-product-detail>` is monolithic — heavy custom layout needs `product_listing_page` pattern instead
- Won't work on `single_page` stores (no `/p/` route)

## Deeper reference

`agent_guidelines({ topic: 'product_detail_page' })` for full component attributes, related-products patterns, and edge cases.

## Defer

- Multi-product grid (catalog) → `agent_guidelines({ topic: 'product_listing_page' })`
- Adding a NEW product → `ecom-product`
- Default storefront /p/<slug> is already fine → no custom page needed
