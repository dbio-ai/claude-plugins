---
description: Diagnose and fix common Dbio site issues (page not visible, broken images, CSS issues, menu 404, products not showing, domain not working)
argument-hint: "<describe the issue>"
---

User reports issue: "$ARGUMENTS"

Trigger the `fix-issues` skill:

1. Gather diagnostic info:
   - `auth_get_session()` for store context
   - `get_urls()` for live URL
   - Ask user for: which page, screenshot, expected vs actual
2. Run the relevant decision tree from fix-issues skill based on issue type
3. Apply fix via appropriate tools (section_update, page_update, store_update, domain_verify, etc.)
4. Confirm fix worked — ask user to refresh and verify

If issue is a known bug (e.g. Mustache R2 cache), acknowledge it and provide workaround.

If beyond MCP capability → direct user to dashboard or `report_issue`.
