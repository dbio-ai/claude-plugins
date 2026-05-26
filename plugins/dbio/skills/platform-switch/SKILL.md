---
description: Switch between Dbio platforms (dbio.ai international, dbio.vn Vietnam) or use a self-hosted Dbio instance. Use when user wants to change which Dbio account/platform their plugin connects to.
---

# Switch Dbio Platform

Use when user wants to switch which Dbio platform their plugin talks to, or set up self-hosted endpoint.

## How it works

The plugin reads two environment variables:

| Variable | Purpose | Default |
|---|---|---|
| `DBIO_MCP_URL` | Which Dbio MCP server to talk to | `https://mcp.dbio.ai/mcp` |
| `DBIO_API_KEY` | Authentication for that platform | (required) |

To switch, user sets new env vars + restarts Claude Code.

## Common scenarios

### Switch to dbio.vn (Vietnam, VND)

```bash
export DBIO_MCP_URL="https://mcp.dbio.vn/mcp"
export DBIO_API_KEY="<key from dbio.vn dashboard>"
```

### Switch to dbio.ai (international, USD)

```bash
export DBIO_MCP_URL="https://mcp.dbio.ai/mcp"
export DBIO_API_KEY="<key from dbio.ai dashboard>"
```

(Or unset `DBIO_MCP_URL` to use default.)

### Self-hosted / enterprise

```bash
export DBIO_MCP_URL="https://mcp.your-company.com/mcp"
export DBIO_API_KEY="<enterprise key>"
```

## After switching

User must:
1. Save env vars (add to `~/.bashrc`, `~/.zshrc`, or shell profile to persist)
2. Restart Claude Code (or open new terminal)
3. Verify with `auth_get_session()` — should return new platform info

## Tell user where to get keys

- dbio.ai key: https://dbio.ai/settings/api-keys
- dbio.vn key: https://dbio.vn/settings/api-keys
- Enterprise: contact account manager

## Differences between platforms (info, not config)

| | dbio.ai | dbio.vn |
|---|---|---|
| Currency default | USD | VND |
| Payment | Stripe | SePay + Stripe |
| UI language | English | Vietnamese |
| Templates | International | VN-focused (food, retail, service) |
| Support hours | Global | VN business hours |

Pricing is the same across platforms — different payment gateway only.

## Don't

- Don't try to switch via MCP tool — there's no such tool. Env vars only.
- Don't store API key in code or git — always env var.
- Don't share keys between machines without permission.
