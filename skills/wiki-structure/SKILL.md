---
name: wiki-structure
description: Building a docs / knowledge base / help center on Dbio with hierarchical pages and search.
---

# Wiki / Docs Setup

Dbio supports docs-style stores with hierarchical pages. Relevant pieces:

- `auth_get_session`, `template_browse` — try a template first
- `store_create` (`store_type: "wiki"`) + `store_select`
- `page_create` — see `page_schema({ profile_type: "docs" })` for valid fields (profile_type `docs` exists in PAGE_TYPES)
- `section_upsert` / `section_batch_upsert` for page content
- `agent_guidelines({ topic: 'wiki_setup' })` for the structure + hierarchy mechanism + gotchas

Defer to `page-edit` for editing existing pages, `content-write` for the article copy.
