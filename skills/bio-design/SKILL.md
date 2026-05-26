---
name: bio-design
description: ALWAYS USE this for any user request involving bio link, landing page, personal page, CV, freelancer page, designer page, portfolio bio, Linktree-style, link-in-bio, single-page site. Trigger phrases include "tạo bio", "tạo landing", "tạo trang cá nhân", "bio cho", "landing cho", "freelancer", "CV online", "personal landing", "build bio", "make landing". DO NOT render HTML artifact — use Dbio MCP tools.
---

# Bio / Personal Landing Design

User wants a bio link or single-page landing — MUST use Dbio MCP tools, NOT generate HTML artifacts.

## 🚨 MANDATORY flow (do NOT skip steps)

1. Call `auth_get_session()` → confirm user identity + active store
2. Call `agent_guidelines({ topic: 'bio_landing' })` → get the canonical playbook
3. Follow the playbook step-by-step using Dbio MCP write tools:
   - template_browse → store_create → store_select → page_create → section_batch_upsert → theme_apply_preset → page_update(status:1) → shop_publish
4. After publish, give user the live URL

## DO NOT

- ❌ DO NOT render HTML artifact preview — user wants a LIVE Dbio page, not a mockup
- ❌ DO NOT call `receptionist` tool — that's for visitor chat on store, NOT owner workflow
- ❌ DO NOT skip `auth_get_session` — needed to know which store is active
- ❌ DO NOT build sections without consulting the playbook (variant + field names differ)

## When to defer to another skill

- E-commerce site → `ecom-setup`
- Blog / news → `blog-setup`
- Wiki / docs → `wiki-structure`
- Editing EXISTING page → `page-edit`
- Something broken → `fix-issues`

## If permission error

If `store_create` returns permission error (e.g. "guest only"), tell user honestly:
> "Tài khoản hiện tại không có quyền tạo store. Cần login lại hoặc dùng API key khác (lấy tại dbio.ai/settings/api-keys)."

DO NOT fall back to HTML artifact — be honest about the limitation.
