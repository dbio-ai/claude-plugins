---
name: ecom-product
description: Creating products on a Dbio e-commerce store — single product, bulk, with AI-generated images, with variants.
---

# Product Authoring

Relevant pieces:

- `product_create` — main entry; accepts `category_names` / `brand_name` (strings, NOT ids), `attribute_specs` for variants
- `media_generate_image` — AI images (returns media_id)
- `media_upload` — user-supplied image
- `product_image({ product_id, media_id, position })` — attach to product
- `product_variant_image` — per-variant image
- `product_update` — change price / status / metadata after creation
- `product_get`, `product_list` — verify
- `agent_guidelines({ topic: 'product_create_with_variants' })` for the full schema, variant flow, gotchas

Field gotcha: pass `category_names: ["..."]` not `category_ids`; pass `brand_name: "..."` not `brand_id`. Agents shouldn't know shard IDs.
