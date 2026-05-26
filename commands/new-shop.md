---
description: Create a new e-commerce store on Dbio (online shop with cart + checkout)
argument-hint: "<shop name>"
---

Start a new e-commerce store named "$ARGUMENTS".

1. Trigger `template-search` skill:
   - `template_browse({ store_type: "ecomm", tag: "<food|fashion|shop|service|...>", limit: 10 })`
2. If template found → clone via `template_clone_store({ source_code, new_name })`
3. If no template → `store_create({ store_type: "ecomm", name, global_code, currency, lang, tags: ["shop"] })`
4. `store_select({ store_id })` on new store
5. Trigger `ecom-setup` skill to add products and configure
