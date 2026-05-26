---
name: template-search
description: Finding a Dbio template that matches the user's intent before building from scratch. Vector semantic search, supports any language.
---

# Template Search

Relevant pieces:

- `template_browse({ search, type, industry, limit })` — vector search (any language) + filters
  - `type: "store" | "bio" | "product" | "all"` — pick `"store"` for site templates
  - `industry` is a loose tag filter (e.g. `food`, `fashion`, `service`, `blog`, `docs`); omit if unsure
- `template_clone_store({ source_code, new_name, global_code })` — clone after user picks
- `store_select` after clone — REQUIRED before further writes

Show top 5 results max (name, url, score, store_type). Defer to the vertical skill for customization after the clone.
