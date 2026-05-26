---
description: Add a product to the active ecommerce store (with AI-generated image)
argument-hint: "<product description>"
---

Create a product based on: "$ARGUMENTS"

Use the `ecom-product` skill:

1. Verify active store is `ecomm` via `auth_get_session`. If not, prompt user.
2. Parse description into product fields (name, price, category)
3. If price not given, ask
4. Generate 1 image via `media_generate_image` with food/product photography prompt
5. Call `product_create` with `category_names` + `brand_name` (strings, not IDs)
6. Call `product_image` to attach the generated media
7. Confirm with user, offer to add more images or variants (size/color/material)
