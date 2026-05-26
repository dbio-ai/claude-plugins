---
name: bio-design
description: Helping the user build a single-page bio site, landing page, personal profile, CV, portfolio, or link-in-bio on Dbio.
---

# Bio / Single-Page Design

Dbio has tools for single-page personal sites. Relevant pieces:

- `auth_get_session` — current store + permissions
- `template_browse` — find an existing design before building from scratch
- `store_create` + `store_select` + `page_create` + `section_upsert` / `section_batch_upsert` — build path
- `components_guide` + `agent_guidelines({ topic: 'bio_landing' })` — variants, fields, gotchas

Use the tools that fit the request. For ecommerce, blog, wiki, editing existing pages, or troubleshooting — defer to those skills.
