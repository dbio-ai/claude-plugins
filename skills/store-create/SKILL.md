---
name: store-create
description: Creating a new Dbio store from scratch (single_page, multi_page, wiki, ecomm). Use after template_browse returns no good match, or when the user explicitly opts out of templates.
---

# Create Store

Relevant pieces:

- `auth_get_session` — current platform, locale, currency context
- `template_browse` — try this first; only fall through to store_create when no template fits
- `store_create({ name, store_type, global_code, currency, lang, tags })` — `store_type` is one of `single_page` | `multi_page` | `wiki` | `ecomm`
- `store_select({ store_id })` — REQUIRED before any subsequent write
- `agent_guidelines({ topic: 'create_store_from_scratch' })` for the store_type matrix + when to pick which

After creation defer to the vertical skill: `bio-design` (single_page), `ecom-setup` (ecomm), `blog-setup` (multi_page + blog), `wiki-structure` (wiki).
