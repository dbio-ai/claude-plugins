---
description: Find Dbio templates via semantic search. Use FIRST whenever the user wants to create a new site, store, or page — cloning a template is faster and more polished than building from scratch. Templates are auto-scoped to the user's platform.
---

# Template Search

ALWAYS call this skill BEFORE building anything from scratch. Cloning a template gives the user a polished, tested starting point in seconds.

## When to use

✅ User says: "tạo trang nhà hàng", "I want a tech blog", "build a portfolio", "make me an event landing", "open an online shop"
✅ Before triggering `bio-design`, `ecom-setup`, `blog-setup`, etc.
❌ Skip when user explicitly says "build from scratch" or "no template"

## Call pattern

```
template_search({
  query: "<synthesize from user intent>",   // semantic — natural language
  store_type: "single_page|multi_page|ecomm|wiki",  // optional filter
  industry: "food|fashion|tech|event|edu|...",       // optional
  features: ["cart", "menu", "ticket", "rsvp"],      // optional
  limit: 5
})
```

Backend automatically:
- Searches the user's platform's template vector DB (resolved via API key)
- Returns top matches with `code`, `name`, `screenshot_url`, `sections_preview`, `industry`, `features`

Plugin DOES NOT need to specify platform — backend handles routing.

## Compose the query well

Synthesize from user words + inferred context:
- User: "tạo cafe ở Sài Gòn" → query: "Vietnamese cafe restaurant Saigon with menu and ordering"
- User: "tech blog about AI" → query: "modern tech blog AI machine learning developer audience"
- User: "event landing for conference" → query: "professional event conference landing page with speakers agenda tickets"

Better query → better matches. Include industry, language hint, audience, key features.

## Show results to user

For each template:
- Thumbnail (use `screenshot_url`)
- Name + 1-line description
- Industry + features tags
- "Clone this" CTA

Don't show more than 5 — choice overload.

## After user picks

```
template_clone_store({
  source_code: <selected template code>,
  new_name: <user's brand name>,
  global_code: <auto-suggest kebab-case>
})
```

Then `store_select({ store_id: new_id })` and trigger the appropriate vertical skill for customization (ecom-setup / blog-setup / bio-design / etc.).

## If no matches

Backend returns empty list. Tell user honestly:

> "I couldn't find a matching template for your platform. Want to build from scratch, or describe the look you want and I'll generate one?"

Fallback to `store-create` skill for blank build.

## Platform awareness

- dbio.ai user → international templates (USD, English-first)
- dbio.vn user → VN templates (VND, Vietnamese, F&B/retail/service VN style)
- Self-hosted → custom template pool

Skill never needs to detect platform — API key already does.

## Filter tips

- For ecom: always pass `store_type: "ecomm"` + relevant industry
- For blog: `store_type: "multi_page"` + `features: ["blog"]`
- For event: industry "event" + `features: ["ticket", "agenda"]`
- For F&B: industry "food" + `features: ["menu", "reservation"]`
- For wiki/docs: `store_type: "wiki"`

## Don't

- ❌ Don't call template_search 3+ times with slight variations — refine query and try once or twice
- ❌ Don't auto-clone without showing user the options first
- ❌ Don't promise templates exist before searching
