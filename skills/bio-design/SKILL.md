---
name: bio-design
description: Designing bio link pages, personal landing pages, CV, freelancer/designer pages, portfolio bios, Linktree-style single-page sites on Dbio. Common Vietnamese triggers - "tạo bio", "tạo landing", "trang cá nhân", "bio cho", "landing cho", "freelancer", "CV online".
---

# Bio / Personal Landing on Dbio

Quick flow:

1. `auth_get_session` — check active store + permissions
2. `template_browse({ search: "<niche>", type: "store", limit: 5 })` — try template first
3. If template fits → `template_clone_store` → `store_select`
4. Else → `store_create({ store_type: "single_page", tags: ["bio_link"] })` → `store_select`
5. `page_create({ slug: "home", profile_type: "landing" })`
6. `section_batch_upsert` with hero + items + content + footer
7. `page_update({ status: 1 })` → `shop_publish`

## Gotchas (most common mistakes)

- `testimonials` field: `content` (not "quote"), `author_name` (not "name")
- `hero` variants `restaurant`/`destination`/`tour`/`centered`: use `background_image` (not `image`)
- Avatar / images must be on Dbio CDN — call `media_import_url` for external URLs
- `receptionist` tool is for visitor chat on a published store, NOT for owner workflows
- `single_page` has no nav between pages — for multi-page nav, use `multi_page` instead

## Deeper reference (call if needed)

For component catalog, edge cases, or full structured playbook:
`agent_guidelines({ topic: 'bio_landing' })`

## Defer to another skill

- E-commerce → `ecom-setup`
- Blog / news → `blog-setup`
- Wiki → `wiki-structure`
- Editing EXISTING page → `page-edit`
- Bug / fix → `fix-issues`
