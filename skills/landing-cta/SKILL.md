---
name: landing-cta
description: Improving conversion on a Dbio landing page — clearer CTAs, lead capture, hero refinement.
---

# Landing CTA Optimization

Relevant pieces for tweaking conversion on an existing page:

- `auth_get_session`, `page_list`, `page_get` — find the page + inspect current state
- `section_update` / `section_upsert` — adjust hero / cta sections
- `section_catalog({ section_type: "hero" | "cta" })` — see real available variants + fields
- `components_guide` — find form / contact / addon components you can drop in

Defer to `page-edit` for general section editing, `content-write` for copy generation, `fix-issues` if something is broken.
