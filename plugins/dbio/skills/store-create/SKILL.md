---
description: Create a new Dbio store (single_page, multi_page, wiki, or ecomm). Use when user wants to start a new website, bio page, online shop, or knowledge base on Dbio.
---

# Create a Dbio Store

Use this skill when the user wants to start a new site, store, or bio page.

## Store types (pick one)

| Type | Use for |
|---|---|
| `single_page` | Bio link, landing page, CV, event promo, business card |
| `multi_page` | Multi-page site with menu: blog, news, portfolio, catalog |
| `wiki` | Docs, knowledge base, help center, manual |
| `ecomm` | Full online shop with cart + checkout: shop, food, service, travel, course |

If unsure, ask. Default for "bio link" or "landing" = `single_page`. Default for "shop" or "online store" = `ecomm`.

## Flow

1. **Gather inputs** — ask for missing pieces:
   - `name` — store display name (e.g. "Cafe Mekong")
   - `store_type` — from table above
   - `global_code` — subdomain (auto-suggest from name, kebab-case)
   - `currency` — default from user's platform (USD for dbio.ai, VND for dbio.vn). Override if user specifies.
   - `lang` — default from user's locale (en/vi)
   - `tags` — optional. E.g. `["food"]`, `["fashion"]`, `["docs"]`. First tag = primary subtype.

2. **Create store**:
   ```
   store_create({
     name, store_type, global_code, currency, lang,
     tags: ["food"]  // optional
   })
   ```

3. **Activate the new store** — REQUIRED before next steps:
   ```
   store_select({ store_id: <new_id> })
   ```

4. **Suggest next step** based on type:
   - `single_page` → trigger `bio-design` skill
   - `multi_page` → trigger `bio-design` for landing, then add more pages
   - `wiki` → create hierarchical pages
   - `ecomm` → trigger `ecommerce-setup` skill

## Naming rules

- `global_code` must be kebab-case, 3-30 chars, alphanumeric + hyphens.
- Use `template_browse({ store_type, tag })` first to suggest a clonable template — faster than building from scratch.
- Template codes starting with `tpl-` are official templates.

## Common pitfalls

- ❌ Don't use legacy types (`bio`, `bio_store`, `shop`). Use the 4 canonical types above.
- ❌ Don't forget `store_select` — subsequent tool calls will fail without active store context.
- ❌ Don't hardcode currency or domain — read from user/platform context.
