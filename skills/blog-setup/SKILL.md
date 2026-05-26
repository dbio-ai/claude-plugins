---
name: blog-setup
description: Setting up a blog, news site, or magazine on Dbio (multi-page with article list + post template + categories). Triggers - "tạo blog", "build blog", "blog cho", "news site", "magazine", "content site", "tạo trang tin tức".
---

# Blog Setup

The user wants a blog/news site. Dbio MCP creates real multi-page sites with article structure.

## Recommended flow

1. `auth_get_session()` — confirm context
2. `agent_guidelines({ topic: 'blog_setup' })` — canonical 2-page playbook (home with article list + post template)
3. Follow the playbook with Dbio write tools

## When to defer

- Single blog post on a landing → use `bio-design` (content section)
- Hierarchical KB → `wiki-structure`
- Writing the post content after setup → `blog-write`
- Editing existing blog → `page-edit`

## Common gotchas

- Posts use `profile_type: 'blog'` (not 'landing')
- Don't add header/footer on individual posts — they inherit from the home page
- Categories/tags live in `page.metadata`, not in section.content
- Menu items need `type: 'link'` or they render blank
- `receptionist` tool is for visitor chat, not owner workflow
