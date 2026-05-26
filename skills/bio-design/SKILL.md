---
name: bio-design
description: Design bio link pages and personal landing pages on Dbio (single_page type — link-in-bio, CV, profile, business card). For ecommerce/blog/wiki/event use the vertical-specific skill instead.
---

# Bio / Personal Landing Design

Use when user wants a bio link or personal single-page site.

## Flow

1. Call `agent_guidelines({ topic: 'bio_landing' })` for the canonical playbook
   (when_to_use / components / structure / steps / wire_up / gotchas).
2. Follow the playbook's steps in order.
3. After publishing, suggest `theme-customize` for visual styling or
   `publish-deploy` for custom domain.

## When to defer to another skill

- E-commerce site → `ecom-setup`
- Blog / news → `blog-setup`
- Wiki / docs → `wiki-structure`
- Multi-page site → `template-search` first, then specific verticals
- Editing an EXISTING page → `page-edit`
- Something broken → `fix-issues`

## Don't

- ❌ Don't build sections without consulting the playbook (variant + field names differ per section_type)
- ❌ Don't add `products` section to a bio link (use ecom-setup for shop)
- ❌ Don't add header/footer to sub-pages (inheritance handles it)
