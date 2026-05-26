---
description: Add a product to the active store (with AI-generated image)
argument-hint: [product description]
---

Create a product based on this description: "$ARGUMENTS"

Use the `product-create` skill:

1. Parse the description into product fields (name, price, category)
2. If price not given, ask
3. Generate 1 image via `media_generate_image` with food/product photography prompt
4. Call `product_create` with category_names + brand_name (strings, not IDs)
5. Call `product_image` to attach the generated media
6. Confirm with user, ask if they want more images or variants
