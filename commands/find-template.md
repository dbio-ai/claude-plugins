---
description: Browse Dbio templates by semantic search + filters (scoped to your platform)
argument-hint: "<describe what you want to build>"
---

Find Dbio templates matching: "$ARGUMENTS"

Use the `template-search` skill:

1. Compose a semantic search query from user input
2. Call `template_browse({ search: "<query>", type: "store", industry: "<optional>", limit: 10 })`
3. Show top 5 matches with name, score, store_type, url, image
4. Ask user which to clone
5. If chosen, call `template_clone_store({ source_code: <id>, new_name: "<brand>" })` then `store_select({ store_id })`
6. Suggest the appropriate vertical skill (ecom-setup / blog-setup / bio-design / wiki-structure)

If no good matches (score < 0.05 or generic), offer to build from scratch via `store-create`.

Note: `template_browse` uses vector semantic search — supports Vietnamese, English, mixed.
