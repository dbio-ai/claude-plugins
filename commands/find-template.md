---
description: Browse Dbio templates by store type and industry tag (scoped to your platform)
argument-hint: "<describe what you want to build>"
---

Find Dbio templates matching: "$ARGUMENTS"

Use the `template-search` skill:

1. Infer `store_type` and `tag` from user input (see template-search skill for mapping table)
2. Call `template_browse({ store_type, tag, limit: 10 })`
3. Show top 5 matches with name, screenshot URL, store_type, tags
4. Ask user which to clone
5. If chosen, call `template_clone_store({ source_code, new_name })` then `store_select({ store_id })`
6. Suggest the appropriate vertical skill (ecom-setup / blog-setup / bio-design / wiki-structure)

If no matches found, offer to build from scratch via `store-create`.
