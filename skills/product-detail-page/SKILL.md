---
name: product-detail-page
description: Build a dedicated detail page for ONE product on a Dbio e-commerce store (gallery + variant picker + buy CTA + related products). Use when user wants to customize how a product is shown beyond the default storefront. Triggers - "trang chi tiết sản phẩm", "product detail page", "custom layout cho sản phẩm X".
---

# Product Detail Page

Use when user wants a custom-layout detail page for ONE product.

## Flow

1. Call `agent_guidelines({ topic: 'product_detail_page' })` for the canonical playbook
   (components / structure / steps / wire_up / gotchas).
2. Follow the playbook's steps — uses `<dbio-product-detail>` component to avoid
   reimplementing gallery / variant / buy logic.
3. After publishing, suggest `theme-customize` to tune visual style.

## When to defer

- Multiple products (catalog / shop grid) → playbook `product_listing_page` (via agent_guidelines)
- Adding a NEW product (not building a page for one) → `ecom-product`
- Category landing → playbook `collection_page`
- Default storefront is fine → no need for this skill, products already render at /p/<slug>

## Don't

- ❌ Don't hand-build gallery/price/variant layout — `<dbio-product-detail>` handles it
- ❌ Don't put `product_id` in section.content — it goes in `page.metadata`
- ❌ Don't try this on a single_page store (no /p/ route)
