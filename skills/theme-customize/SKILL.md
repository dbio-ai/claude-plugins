---
name: theme-customize
description: Adjusting visual style of a Dbio store — colors, typography, design tokens, presets.
---

# Theme Customization

Relevant pieces:

- `theme_list_presets()` — see available presets (don't assume names)
- `theme_apply_preset({ preset })` — overwrites tokens with preset values
- `theme_get_store()` — see current tokens before adjusting
- `theme_update_tokens({ tokens: { "--key": value } })` — fine-tune individual CSS custom properties

Changes apply instantly (no rebuild). Edge cache ~60s — user may see stale briefly.

The CSS compiler strips some modern CSS from `template_css` (e.g. `flex-wrap`, `grid`, `clamp()`, `max-width`). Use inline `style` attributes or a registry variant rather than custom CSS.
