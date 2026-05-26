---
description: Browse Dbio templates by store type and industry
argument-hint: [store_type] [industry]
---

Browse available Dbio templates for "$ARGUMENTS".

1. Parse arguments — store_type (single_page/multi_page/wiki/ecomm), optional industry tag (food/fashion/service/...)
2. Call `template_browse({ store_type, tag })`
3. Show top 10 results with: code, name, store_type, thumbnail URL, brief description
4. Ask user which to clone
5. If chosen, ask for new store name and call `template_clone_store({ source_code, new_name })`
