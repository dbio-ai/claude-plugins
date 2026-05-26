---
name: product-detail-page
description: ALWAYS USE when user wants a custom detail page for ONE product on Dbio ecomm store. Trigger - "trang chi tiết sản phẩm", "product detail page", "trang sản phẩm X", "custom layout cho sản phẩm", "page cho product Y". DO NOT render HTML artifact — use Dbio MCP tools.
---

# Product Detail Page

User wants a custom-layout detail page for ONE product — MUST use Dbio MCP tools + `<dbio-product-detail>` component, NOT generate HTML artifacts.

## 🚨 MANDATORY flow

1. `auth_get_session()` → confirm active store is ecomm type
2. `agent_guidelines({ topic: 'product_detail_page' })` → get playbook
3. Follow playbook — uses `<dbio-product-detail>` component (do NOT reimplement gallery/variant/buy)
4. After publish, give user URL: `/p/<product-slug>`

## DO NOT

- ❌ DO NOT render HTML artifact — user wants live page
- ❌ DO NOT call `receptionist` — wrong tool
- ❌ DO NOT hand-build gallery/price/variant layout — component handles it
- ❌ DO NOT put `product_id` in section.content — goes in `page.metadata`
- ❌ DO NOT try this on single_page store (no /p/ route)

## When to defer

- Multiple products (catalog grid) → playbook `product_listing_page`
- Adding a NEW product → `ecom-product`
- Default storefront is fine → no need for custom detail page
