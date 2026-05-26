# Dbio Plugins for Claude Code

Official [Claude Code](https://code.claude.com) plugins for [Dbio](https://dbio.ai) — build websites, bio pages, and online stores with AI.

## What's in this marketplace

| Plugin | Description |
|---|---|
| **dbio** | Build single-page sites, landing pages, multi-page sites, wikis, and full e-commerce stores on Dbio. |

More plugins coming: `devent` (event/ticketing), `dgame` (game hosting), `dedu` (courses), and more.

## Install

```bash
# Add this marketplace
claude plugin marketplace add dbio-ai/claude-plugins

# Install the dbio plugin
claude plugin install dbio
```

## Quick start

1. Get your Dbio API key:
   - International: https://dbio.ai/settings/api-keys
   - Vietnam: https://dbio.vn/settings/api-keys

2. Set environment variable:
   ```bash
   export DBIO_API_KEY="dbio_pk_..."
   ```

3. Restart Claude Code. Try:
   ```
   /dbio:new-store My Cafe
   ```

See [plugins/dbio/README.md](./plugins/dbio/README.md) for full plugin docs.

## Switching platforms

Override the MCP endpoint to switch between dbio.ai and dbio.vn:

```bash
# Default — dbio.ai (USD, international)
export DBIO_API_KEY="..."

# Vietnam — dbio.vn (VND, SePay)
export DBIO_MCP_URL="https://mcp.dbio.vn/mcp"
export DBIO_API_KEY="..."

# Self-hosted / enterprise
export DBIO_MCP_URL="https://mcp.your-company.com/mcp"
export DBIO_API_KEY="..."
```

## License

Apache 2.0 — see [LICENSE](./LICENSE).

## Links

- Website: https://dbio.ai · https://dbio.vn
- Docs: https://docs.dbio.ai
- Support: support@dbio.ai
- Issues: https://github.com/dbio-ai/claude-plugins/issues
