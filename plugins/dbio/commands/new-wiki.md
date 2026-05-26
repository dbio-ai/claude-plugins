---
description: Create a new wiki or documentation site on Dbio (hierarchical knowledge base, help center)
argument-hint: "<wiki name>"
---

Start a new wiki/docs site for: "$ARGUMENTS"

1. Trigger `template-search`:
   - query: "<inferred>" + "documentation knowledge base"
   - store_type: "wiki"
   - features: ["search", "sidebar"]
2. If found → clone
3. Else → `store_create({ store_type: "wiki" })` + `store_select`
4. Trigger `wiki-structure` skill for hierarchy + content
