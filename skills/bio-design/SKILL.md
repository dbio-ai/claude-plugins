---
name: bio-design
description: Designing bio link pages, personal landing pages, CV, freelancer/designer pages, portfolio bios, Linktree-style single-page sites on Dbio. Common Vietnamese triggers - "tạo bio", "tạo landing", "trang cá nhân", "bio cho", "landing cho", "freelancer", "CV online".
---

# Bio / Personal Landing Design

The user wants a bio link or single-page landing. Dbio MCP can create a real published page; prefer that over rendering an HTML preview when the tools are available.

## Recommended flow

1. `auth_get_session()` — see active store + permissions
2. `agent_guidelines({ topic: 'bio_landing' })` — get the canonical playbook (structure, components, steps, gotchas)
3. Follow the playbook using Dbio write tools (template_browse → store_create → store_select → page_create → section_batch_upsert → publish)

## When to defer

- E-commerce store → `ecom-setup`
- Blog / news → `blog-setup`
- Wiki / docs → `wiki-structure`
- Editing EXISTING page → `page-edit`
- Something broken → `fix-issues`

## When HTML artifact fits better

If `auth_get_session` returns guest / read-only / no write permission, the user probably wants a preview mockup — render an HTML artifact and be explicit it's a preview, not a live page. Otherwise the live-page path is what they're paying for.

## Common gotchas (the playbook has more)

- Avatar/image URLs must be Dbio CDN (call `media_import_url` for external)
- `testimonials` field: `content` (not "quote"), `author_name` (not "name")
- `hero` variants `restaurant`/`destination`/`tour`/`centered` use `background_image` (not `image`)
- `receptionist` tool is for visitor-facing chat on a published store, not for owner workflows
