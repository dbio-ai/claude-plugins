---
description: Create a new wiki or documentation site on Dbio (hierarchical knowledge base, help center)
argument-hint: "<wiki name>"
---

Start a new wiki/docs site for: "$ARGUMENTS"

1. Trigger `template-search`:
   - `template_browse({ search: "<inferred + 'documentation'>", type: "store", industry: "docs", limit: 10 })`
2. Filter results to `store_type: "wiki"`, show top 5
3. If found → clone
4. Else → `store_create({ store_type: "wiki", ... })` + `store_select`
5. Trigger `wiki-structure` skill for hierarchy + content
