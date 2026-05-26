---
name: blog-setup
description: ALWAYS USE for any user request to build a blog, news site, magazine, content site, articles platform. Trigger phrases - "tạo blog", "build blog", "blog cho", "news site", "magazine", "content site", "tạo trang tin tức". DO NOT render HTML artifact — use Dbio MCP tools.
---

# Blog Setup

User wants a blog/news site — MUST use Dbio MCP tools, NOT generate HTML artifacts.

## 🚨 MANDATORY flow

1. `auth_get_session()` → confirm context
2. `agent_guidelines({ topic: 'blog_setup' })` → get playbook
3. Follow playbook step-by-step with Dbio MCP write tools
4. Give user live URL after publish

## DO NOT

- ❌ DO NOT render HTML artifact — user wants live Dbio site
- ❌ DO NOT call `receptionist` — wrong tool for this workflow
- ❌ DO NOT skip playbook — blog has specific 2-page structure (home + post template)
- ❌ DO NOT add header/footer on individual posts (inherit from home)

## When to defer

- Single blog post on landing → use `bio-design` instead
- Wiki/docs → `wiki-structure`
- Writing the post content (after setup) → `blog-write`
- Editing existing blog → `page-edit`
