---
name: blog-setup
description: Set up a blog or news site on Dbio (multi-page with article list, categories, tags, search). Use when user wants to start a blog, news site, content site, or magazine on Dbio.
---

# Blog Setup

Use when user wants a content-driven multi-page site (blog / news / magazine).

## Flow

1. Call `agent_guidelines({ topic: 'blog_setup' })` for the canonical playbook
   (structure / steps / categorization / SEO / gotchas).
2. Follow the playbook's steps in order.
3. After initial setup, trigger `blog-write` to draft first post.

## When to defer to another skill

- Single blog post (no full site) → use section `content` of `bio-design`
- Hierarchical knowledge base → `wiki-structure`
- Editing existing blog → `page-edit`
- Writing the post content → `blog-write`

## Don't

- ❌ Don't add header/footer sections on individual posts (inherit from home)
- ❌ Don't put categories on section.content — they live in page.metadata
- ❌ Don't forget `type: "link"` on menu items
