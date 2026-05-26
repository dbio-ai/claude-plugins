---
description: Design and edit bio pages, landing pages, and content pages on Dbio. Use when user wants to build a bio link, single-page site, landing page, or edit any page sections.
---

# Bio Page Design

Use this skill when designing or editing any page on a Dbio store. Works for single_page, multi_page, and ecomm landing pages.

## Prerequisites

User must have a store active (`store_select` already called). If not, trigger `store-create` skill first.

## Step 1: Pick template or start fresh

```
template_browse({ store_type, tag: "food" })  // industry tag optional
```

If a relevant template exists → suggest `template_clone_bio({ source_code, slug: "home" })`.

Else create blank:
```
bio_create({ name, slug: "home", profile_type: "landing", status: 1 })
```

## Step 2: Plan sections

9 section types available — see `section_catalog()` for variants per type.

Standard order for a typical landing:
1. `header` (logo + nav, optional on single_page)
2. `hero` (title + tagline + CTA + image)
3. `items` (services / link grid / menu items)
4. `products` (when store has products)
5. `content` (about / story)
6. `gallery` (images)
7. `cta` (signup / contact form)
8. `footer`

For F&B (`tag: food`): use `hero` variant `restaurant` (has open_hours, rating, location).
For tour: `hero` variant `tour`.
For shop: `hero` variant `product`.

## Step 3: Add sections with `section_upsert`

ALWAYS use `section_upsert` (idempotent), never `section_add`. Each section has `template_html` from registry variant — DO NOT write custom HTML unless explicitly asked.

```
section_upsert({
  bio_id, position: 1, section_type: "hero", variant: "split",
  content: { title, subtitle, image_url, cta_text, cta_link }
})
```

Or batch many at once:
```
section_batch_upsert({ bio_id, sections: [...] })
```

## Step 4: Mustache variables — required pattern

All section content uses Mustache. NEVER hardcode text directly in template_html. Pass data via `content` field:
- Backend auto-resolves `product_ids`, `category_ids`, `media_id`, `media_ids` into Mustache vars.
- Frontend renders Mustache at runtime.

## Step 5: Field name gotchas

Common WRONG → CORRECT:
- testimonials: `quote` → `content`, `name` → `author_name`, `role` → `author_title`, `avatar` → `author_avatar`
- about: `description` → `story`
- footer: `brand` → `logo_text`, columns `items[].text` → `links[].label`, `items[].link` → `links[].url`
- hero (restaurant/destination/tour): use `background_image`, NOT `image`

## Step 6: Header/footer inheritance

For sub-page bios (blog post, product detail, etc.), DO NOT add `header` or `footer` sections — they inherit from the store's landing bio.

## Step 7: Publish

```
page_publish({ bio_id })  // or page_update({ status: 1 })
```

## After designing

- Confirm with user, ask for changes.
- Trigger `theme-customize` if user wants to adjust colors/typography.
- Trigger `publish-deploy` for custom domain setup.
