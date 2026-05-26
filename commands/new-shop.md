---
description: Create a new e-commerce store on Dbio (online shop with cart + checkout)
argument-hint: "<shop name>"
---

Start a new e-commerce store named "$ARGUMENTS".

1. Trigger `template-search` skill first:
   - query: "<inferred from name>" + "online shop"
   - store_type: "ecomm"
   - features: ["cart", "checkout"]
2. If template found → clone via `template_clone_store`
3. If no template → call `store_create({ store_type: "ecomm", ... })`
4. Call `store_select` on new store
5. Trigger `ecom-setup` skill to add products and configure
