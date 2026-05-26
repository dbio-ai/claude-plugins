---
description: Edit an existing page or section on the active store
argument-hint: "<what to edit, e.g. 'home page hero title'>"
---

User wants to edit: "$ARGUMENTS"

Trigger the `page-edit` skill:

1. `page_list()` → find the page user mentioned (by name or slug)
2. `page_get({ page_id })` → fetch current sections
3. Identify what user wants to change (section, field)
4. Show current value, propose new value
5. After user confirms, call `section_update` (merge with existing content) or `page_update`
6. Confirm change saved, mention edge cache 60s
