---
name: blog-setup
description: Setting up a blog, news site, or magazine on Dbio (multi-page with article list + post template + categories). Triggers - "tạo blog", "build blog", "blog cho", "news site", "magazine", "content site", "tạo trang tin tức".
---

# Blog Setup on Dbio

Quick flow (2-page structure: home + post template):

1. `auth_get_session` — confirm context
2. `template_browse({ search: "<niche>", type: "store", industry: "blog" })` — try template first
3. If template fits → `template_clone_store` → `store_select`
4. Else → `store_create({ store_type: "multi_page", tags: ["blog"] })` → `store_select`
5. `page_create({ slug: "home", profile_type: "landing" })` — list page with `items` (article-grid section)
6. `page_create({ slug: "first-post", profile_type: "blog" })` — post template
7. `store_update({ settings: { menu: [...] } })` — nav (items need `type: "link"`)
8. `page_publish` both → `shop_publish`

## Gotchas

- Posts use `profile_type: 'blog'` (not 'landing')
- Don't add header/footer on individual posts — inherited from home
- Categories/tags live in `page.metadata`, not in section.content
- Menu items missing `type: "link"` render blank
- `receptionist` tool is for visitor chat, not owner workflow

## Deeper reference

`agent_guidelines({ topic: 'blog_setup' })` for component catalog, SEO fields, scheduling, newsletter integration.

## Defer

- Single blog post on landing → use `bio-design` instead
- Hierarchical KB → `wiki-structure`
- Writing post content → `blog-write`
- Editing existing blog → `page-edit`
