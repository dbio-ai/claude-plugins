---
name: template-search
description: Find Dbio templates via semantic search + filters. Use FIRST whenever the user wants to create a new site, store, or page — cloning a template is faster than building from scratch. Vector search supports any language (Vietnamese, English, etc). Templates are auto-scoped to the user's platform via API key.
---

# Template Search

ALWAYS call this skill BEFORE building anything from scratch. Cloning a template gives the user a polished starting point in seconds.

## When to use

✅ User says: "tạo trang nhà hàng", "I want a tech blog", "build a portfolio", "make me an event landing", "open an online shop"
✅ Before triggering `bio-design`, `ecom-setup`, `blog-setup`, `wiki-structure`
❌ Skip when user explicitly says "build from scratch" or "no template"

## Call pattern

```
template_browse({
  search: "<natural language describing what user wants>",  // semantic vector search (any language)
  type: "store",                // store | bio | product | all (default: all)
  industry: "shop|food|fashion|service|...",  // optional filter
  limit: 10
})
```

**Important**:
- `search` accepts any language — Vietnamese, English, mixed. Vector embedding finds semantic matches.
- `type: "store"` filters to STORE templates only (otherwise returns mix of stores/bios/products).
- `industry` is a loose tag filter — combine with `search` for best matches.

Returns top results with `id`, `name`, `store_id`, `image`, `url`, `store_type`, `score`.

Backend auto-scopes templates to the user's platform — plugin doesn't pass platform.

## Pick the right params

| User intent | search | type | industry |
|---|---|---|---|
| Bio link / personal landing | "personal bio link" | `store` | `personal` |
| Restaurant / cafe / food | "Vietnamese cafe with menu" | `store` | `food` |
| Online shop | "modern online shop fashion" | `store` | `shop` (or specific) |
| Tech blog | "tech blog with articles" | `store` | `blog` |
| Documentation site | "documentation knowledge base" | `store` | `docs` |
| Event landing | "event conference landing" | `store` | `event` |
| Portfolio | "creative portfolio designer" | `store` | `portfolio` |
| Service / consulting | "service business consulting" | `store` | `service` |
| Travel / tour | "travel agency tour packages" | `store` | `travel` |

If unsure of industry, omit it — semantic search handles ranking.

## Show results to user

For each template (top 5):
- Name + score (or just rank)
- `url` (preview link if available)
- `image` (thumbnail if available)
- `store_type` (so user knows what they're cloning)

Don't show more than 5 — choice overload.

## After user picks

```
template_clone_store({
  source_code: "<template_id or code>",  // use the id from results
  new_name: "<user's brand name>",
  global_code: "<auto-suggest kebab-case from name>"
})
```

Then `store_select({ store_id: <new_id> })` and trigger the matching vertical skill:
- ecomm template → `ecom-setup` for customization
- multi_page blog template → `blog-setup`
- wiki template → `wiki-structure`
- single_page template → `bio-design`

## If no good matches

Top results have low score (<0.05) or generic results:

> "Templates không khớp lắm với mong muốn của bạn. Mình có thể build từ đầu — bạn thấy ổn không?"

Fall back to `store-create` skill for blank build.

## Don't

- ❌ Don't use `store_type:` — not a valid param. Use `type: "store"` to filter to stores.
- ❌ Don't use `tag:` — param is named `industry`.
- ❌ Don't use `features:` — not supported.
- ❌ Don't call `template_browse` 5 times with slight variations — pick a good filter and run once.
- ❌ Don't auto-clone without showing options first.
- ❌ Don't promise templates exist before browsing.
