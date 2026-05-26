---
description: Show current Dbio session info (which platform, active store, plan, quota)
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
3. Show plugin endpoint from `$DBIO_MCP_URL` (or default `https://mcp.dbio.ai/mcp`)
4. If no active store, suggest `/dbio:new-store`

If user wants to **switch platform** (e.g. dbio.vn → dbio.ai), tell them:

```bash
# Edit shell profile (~/.zshrc, ~/.bashrc)
export DBIO_API_KEY="<new platform's key>"
export DBIO_MCP_URL="https://mcp.dbio.vn/mcp"   # or omit for dbio.ai default

# Restart Claude Code
```

Keys are at https://dbio.ai/settings/api-keys or https://dbio.vn/settings/api-keys.
