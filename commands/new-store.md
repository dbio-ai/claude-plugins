---
description: Create a new Dbio store (interactive)
argument-hint: [name]
---

Start the new-store flow for "$ARGUMENTS".

Use the `store-create` skill:

1. If no name given, ask for it
2. Ask user which type: single_page / multi_page / wiki / ecomm
3. Suggest global_code (kebab-case from name)
4. Confirm with user
5. Call `store_create` then `store_select`
6. Suggest the next skill based on store type (bio-design or ecommerce-setup)
