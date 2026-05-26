---
description: Create a new landing page (single-page site for promo, event, product launch, lead capture)
argument-hint: "<landing name>"
---

Start a new landing page for: "$ARGUMENTS"

1. Trigger `template-search` skill:
   - `template_browse({ search: "<inferred + 'landing'>", type: "store", industry: "<personal|event|service|...>", limit: 10 })`
2. Filter results to `store_type: "single_page"`, show top 5
3. If template found → clone
4. Else → `store_create({ store_type: "single_page", ... })` + `store_select`
5. Trigger `bio-design` skill for sections
6. Trigger `landing-cta` skill for conversion optimization
