---
description: Create a new bio / landing page on the active store
argument-hint: [name]
---

Create a new bio page named "$ARGUMENTS" on the currently active store.

1. Verify a store is active via `auth_get_session`. If not, prompt user to run `/dbio:new-store` first.
2. Suggest a slug (kebab-case from name, or "home" if first page)
3. Pick profile_type: landing | blog | about | contact | faq | collection
4. Call `bio_create({ name, slug, profile_type, status: 0 })`
5. Trigger the `bio-design` skill to start adding sections
