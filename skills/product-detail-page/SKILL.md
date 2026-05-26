---
name: product-detail-page
description: Helping the user build a custom detail page for one product on a Dbio e-commerce store, when the default storefront layout isn't enough.
---

# Product Detail Page

Dbio renders products at the default `/product/<slug>` route automatically — custom page only needed when the user wants a non-default layout.

Relevant pieces:

- `auth_get_session`, `product_get` — verify product + store
- `page_create` with `profile_type: "product_detail"` + `entity_id: <product_id>` — bind page to product
- `section_upsert` (custom variant) embedding the real `<dbio-pd-*>` sub-components (gallery, info, options, trust, description, related, sticky)
- `product_update({ bio_profile_id })` — link product → custom page (else default still wins)
- `components_guide({ topic: 'product' })` + `agent_guidelines({ topic: 'product_detail_page' })` for exact tags, attributes, layout
