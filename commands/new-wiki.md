---
description: Create a new wiki or documentation site on Dbio (hierarchical knowledge base, help center)
argument-hint: "<wiki name>"
---

Start a new wiki/docs site for: "$ARGUMENTS"

1. Trigger `template-search`:
   - `template_browse({ store_type: "wiki", tag: "docs", limit: 10 })`
2. If found → clone
3. Else → `store_create({ store_type: "wiki", ... })` + `store_select`
4. Trigger `wiki-structure` skill for hierarchy + content
