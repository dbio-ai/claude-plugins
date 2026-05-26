---
description: Find Dbio templates by use case (semantic search, scoped to your platform)
argument-hint: "<describe what you want to build>"
---

Find Dbio templates matching: "$ARGUMENTS"

Use the `template-search` skill:

1. Compose a semantic query from the user input + any inferred context (industry, store type, language)
2. Call `template_search({ query, ... })`
3. Show top 5 matches with name, thumbnail, industry tags, key features
4. Ask user which to clone
5. If chosen, call `template_clone_store({ source_code, new_name })`
6. After clone, suggest the appropriate vertical skill (ecom-setup / blog-setup / bio-design / wiki-structure)

If no matches found, offer to build from scratch via `store-create`.
