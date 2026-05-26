---
name: blog-write
description: Drafting blog posts and articles for a Dbio blog — SEO structure, hero meta, body content.
---

# Blog Post Writing

Relevant pieces:

- `auth_get_session`, `page_list({ profile_type: "blog" })` — match the existing voice
- `media_generate_image` — cover image (1200x630 for OG)
- `page_create` (`profile_type: "blog"`) — see `page_schema` for available metadata / seo / cover fields
- `section_upsert` — body content; check `section_catalog({ section_type: "content" })` for real variants
- `agent_guidelines({ topic: 'blog_post_create' })` for structure + SEO + scheduling specifics

General copy guidance lives in `content-write`. For setting up a blog site from scratch use `blog-setup`.
