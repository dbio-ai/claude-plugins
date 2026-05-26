---
description: Show current Dbio session info (which platform, active store, plan)
---

Show the current Dbio session:

1. Call `auth_get_session()` and display:
   - Platform (dbio.ai / dbio.vn / self-hosted)
   - User email / account
   - Active store name + ID + URL
   - Plan (free / pro / business / enterprise)
   - Currency
2. Call `quota_check()` and show usage:
   - Stores: used / limit
   - Products: used / limit
   - Storage: used / limit
3. Show plugin endpoint from `$DBIO_MCP_URL` (or default)
4. If no active store, suggest `/dbio:new-store`
