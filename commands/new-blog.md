---
description: Create a new blog or news site on Dbio (multi-page with article list, categories)
argument-hint: "<blog name>"
---

Start a new blog/news site for: "$ARGUMENTS"

1. Trigger `template-search`:
   - `template_browse({ store_type: "multi_page", tag: "blog", limit: 10 })`
2. If found → clone via `template_clone_store`
3. Else → `store_create({ store_type: "multi_page", tags: ["blog"], ... })` + `store_select`
4. Trigger `blog-setup` skill for structure
5. Suggest `blog-write` to draft first post
