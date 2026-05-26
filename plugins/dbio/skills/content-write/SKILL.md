---
description: Write copy, headlines, descriptions, and CTAs for Dbio sites. Use when user asks for help writing content for hero sections, product descriptions, about pages, or any text on their site.
---

# Content Writing for Dbio Sites

Use when user needs help writing copy for their site — headlines, descriptions, CTAs, product copy, about pages.

## Detect language

- User writes in Vietnamese → respond in Vietnamese, write copy in Vietnamese
- User writes in English → respond in English, write copy in English
- Mixed → ask which language for the copy

## Detect industry / tone

Look at:
- Store name and `tags` (food, fashion, service, tech...)
- Existing content already on the site (read via `page_get`)
- User's brief

Tone matrix:
| Industry | Tone | Examples |
|---|---|---|
| F&B / restaurant | Warm, sensory | "Hương vị truyền thống, công thức gia đình 3 đời" |
| Fashion | Aspirational, confident | "Designed for the bold. Made for every day." |
| SaaS / B2B | Clear, benefit-led | "Ship faster. Sleep better." |
| Service / consulting | Trust + expertise | "20+ năm đồng hành cùng doanh nghiệp Việt" |
| Personal bio | Authentic, personable | "Writer. Maker. Coffee enthusiast." |

## Hero copy formula

Headline (5-9 words) + Subhead (10-20 words) + CTA (1-3 words)

```
{title}     — main hook, benefit-first
{subtitle}  — qualifier, target audience
{cta_text}  — verb-led action
```

Examples:
- F&B: `"Cafe Sài Gòn xưa, hương vị nay" / "Pha thủ công mỗi ngày, không hương liệu" / "Đặt bàn"`
- Bio: `"Build sites with AI in minutes" / "From bio link to full storefront, one tool" / "Get started"`

## Product description structure

```
short_description: 1-2 sentence hook (used in product cards)
description: HTML, 3-5 paragraphs:
  - Para 1: What it is + key benefit
  - Para 2: Who it's for / when to use
  - Para 3: Specs / ingredients / materials
  - Para 4: Trust signals (origin, awards, reviews)
  - Para 5: CTA / FAQ snippet
```

## About / Story page

5-paragraph template:
1. Origin — when, why we started
2. Mission — what we believe
3. Approach — how we work
4. People — who's behind it (optional)
5. Invite — what we want with you

Field name: `story` (NOT `description`).

## CTA writing

- ✅ Action verbs: "Get started", "Order now", "Book a table", "Learn more"
- ❌ Generic: "Click here", "Submit", "Read more"
- VN: "Đặt ngay", "Xem thêm", "Liên hệ"

## SEO basics

When writing for SEO-sensitive sections:
- Title tag: 50-60 chars, brand at end
- Meta description: 140-160 chars, include primary keyword + CTA
- H1 = hero title (only 1 per page)
- Alt text on images (descriptive, not keyword-stuffed)

Use `page_update({ seo: { title, description, og_image } })` to set SEO fields.

## Don't

- Don't use buzzword salad ("synergize", "leverage", "disrupt")
- Don't write in 3rd person for solo creators
- Don't translate VN→EN literally — rewrite for English audience
- Don't fill placeholder text — ask user for real info
