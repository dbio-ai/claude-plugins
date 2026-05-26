---
name: blog-setup
description: Helping the user set up a blog, news site, magazine, or content site on Dbio.
---

# Blog / Content Site Setup

Dbio supports multi-page sites with an article list + post template. Relevant pieces:

- `auth_get_session`, `template_browse`
- `store_create` (`store_type: "multi_page"`) + `store_select`
- `page_create` for the home (list) page and individual posts
- `section_upsert` / `section_batch_upsert` for the page content
- `agent_guidelines({ topic: 'blog_setup' })` for the structure + fields + gotchas

For wiki/docs use `wiki-structure`. For editing existing posts use `page-edit`. For writing post content use `blog-write`.
