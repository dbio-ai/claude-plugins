---
description: Publish the active store and show the live URL
---

Publish the currently active Dbio store.

1. Verify a store is active via `auth_get_session`. If not, prompt user.
2. List unpublished pages via `page_list({ status: 0 })` — ask user if they want to publish those too.
3. Call `shop_publish()`
4. Call `get_urls()` and show the live URL
5. Suggest the `publish-deploy` skill if user wants to add a custom domain
