---
description: Create a new blog or news site on Dbio (multi-page with article list, categories)
argument-hint: "<blog name>"
---

Start a new blog/news site for: "$ARGUMENTS"

1. Trigger `template-search`:
   - `template_browse({ search: "<inferred + 'blog'>", type: "store", industry: "blog", limit: 10 })`
2. Filter results to `store_type: "multi_page"`, show top 5
3. If found → clone via `template_clone_store`
4. Else → `store_create({ store_type: "multi_page", tags: ["blog"], ... })` + `store_select`
5. Trigger `blog-setup` skill for structure
6. Suggest `blog-write` to draft first post
