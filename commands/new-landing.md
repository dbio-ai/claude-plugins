---
description: Create a new landing page (single-page site for promo, event, product launch, lead capture)
argument-hint: "<landing name>"
---

Start a new landing page for: "$ARGUMENTS"

1. Trigger `template-search` skill:
   - `template_browse({ store_type: "single_page", tag: "<landing|event_promo|bio_link|...>", limit: 10 })`
2. If template found → clone
3. Else → `store_create({ store_type: "single_page", ... })` + `store_select`
4. Trigger `bio-design` skill for sections
5. Trigger `landing-cta` skill for conversion optimization
