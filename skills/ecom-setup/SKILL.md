---
name: ecom-setup
description: Setting up a Dbio e-commerce store end-to-end — products, landing, checkout flow on the storefront.
---

# E-commerce Setup

Relevant pieces:

- `auth_get_session`, `template_browse` — try a shop template first
- `store_create` (`store_type: "ecomm"`) + `store_select`
- `product_create` — see `ecom-product` skill for the product authoring flow
- Default storefront already serves `/products`, `/product/<slug>`, `/cart`, `/checkout` — no need to build those pages
- `page_create` for custom system pages (`profile_type: "about" | "contact" | "faq"`)
- `agent_guidelines({ topic: 'cart_checkout_setup' })` for checkout config + payment notes

Coupons, payment-gateway config, order management, and tax are dashboard-only — they don't have MCP tools.
