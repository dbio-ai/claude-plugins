---
name: page-edit
description: Modifying existing pages and sections on a Dbio site — change text, swap images, reorder, delete, restore from backup.
---

# Page / Section Editing

Relevant pieces:

- `auth_get_session`, `page_list`, `page_get` — find the page + inspect current state
  - Pass `sections_only: true` + `section_types: [...]` to keep response small (full page payloads can be 50K+ chars)
  - Pass `store_id` explicitly when editing pages of a different store than the active one
- `section_update` — change one section; **merge with existing `content`** to avoid wiping other fields
- `section_catalog({ section_type })` — see real variants + fields before changing variant
- `section_reorder` — change order
- `section_delete` — remove
- `section_upsert` / `section_batch_upsert` — insert into existing page
- `page_backup_list` + `page_backup_restore` — undo
- `page_update` for metadata (name, status, seo, metadata); changing slug breaks URLs

Defer to `fix-issues` if something is broken, `content-write` if rewriting copy.
