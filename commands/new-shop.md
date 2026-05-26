---
description: Create a new e-commerce store on Dbio (online shop with cart + checkout)
argument-hint: "<shop name>"
---

Start a new e-commerce store named "$ARGUMENTS".

1. Trigger `template-search` skill:
   - `template_browse({ search: "<inferred from name + 'online shop'>", type: "store", industry: "shop", limit: 10 })`
2. Filter results to `store_type: "ecomm"`, show top 5
3. If template found → clone via `template_clone_store({ source_code, new_name })`
4. If no template → `store_create({ store_type: "ecomm", name, global_code, currency, lang, tags: ["shop"] })`
5. `store_select({ store_id })` on new store
6. Trigger `ecom-setup` skill to add products and configure
