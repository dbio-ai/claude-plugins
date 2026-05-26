# dbio plugin for Claude Code

Build websites, bio pages, and online stores on [Dbio](https://dbio.ai) — all from inside Claude Code.

## What it does

This plugin connects Claude Code to your Dbio account so you can:

- Create stores (single-page, multi-page, wiki, e-commerce)
- Design bio pages and landing pages with sections
- Add products with AI-generated images
- Customize themes (colors, typography)
- Publish and connect custom domains

Claude understands Dbio's conventions out of the box — section variants, field name gotchas, template flow, multi-tenant rules — so you get correct results without learning the MCP tool names.

## Install

```bash
claude plugin marketplace add dbio-ai/claude-plugins
claude plugin install dbio
```

## Setup

### 1. Get an API key

- **International** (USD): https://dbio.ai/settings/api-keys
- **Vietnam** (VND, SePay): https://dbio.vn/settings/api-keys

### 2. Set environment variable

```bash
# In your shell profile (~/.bashrc, ~/.zshrc, ~/.profile)
export DBIO_API_KEY="dbio_pk_xxxxxxxxxxxx"
```

For dbio.vn, also set:
```bash
export DBIO_MCP_URL="https://mcp.dbio.vn/mcp"
```

### 3. Restart Claude Code

```bash
# In a new terminal
claude
```

## Try it

```
/dbio:new-store My Coffee Shop
```

Or just talk:

> "Tạo cho tôi 1 trang bio cho quán cafe"  
> "Build me an e-commerce store for selling t-shirts"  
> "Add 5 menu items to my restaurant store"

The plugin's skills auto-activate based on context — no command needed.

## Commands

| Command | Purpose |
|---|---|
| `/dbio:new-store [name]` | Create a new store (interactive) |
| `/dbio:new-bio [name]` | Add a new page to active store |
| `/dbio:add-product [description]` | Create a product with AI image |
| `/dbio:templates [type] [industry]` | Browse templates |
| `/dbio:publish` | Publish active store, show URL |
| `/dbio:whoami` | Show current session, platform, quota |

## Skills (auto-activated)

Claude automatically uses these when relevant — no slash command needed:

| Skill | Activates when |
|---|---|
| `store-create` | User wants to create a new site/store |
| `bio-design` | User wants to design or edit a page |
| `ecommerce-setup` | User is building an online shop |
| `product-create` | User wants to add products |
| `content-write` | User asks for copy / headlines / CTAs |
| `theme-customize` | User wants to change colors / fonts |
| `publish-deploy` | User wants to publish or add a domain |
| `platform-switch` | User wants to change platforms or self-host |

## Configuration

| Env var | Purpose | Default |
|---|---|---|
| `DBIO_API_KEY` | API key (required) | — |
| `DBIO_MCP_URL` | MCP server endpoint | `https://mcp.dbio.ai/mcp` |

## Troubleshooting

**"Unauthorized" errors**: API key invalid or expired. Get a new one at the dashboard.

**Tools not available**: Restart Claude Code after setting env vars. Run `claude --version` to confirm v2.0+.

**Wrong platform**: Check `DBIO_MCP_URL`. Default = dbio.ai (international, USD). Set explicitly for dbio.vn or self-hosted.

**Quota exceeded**: Run `/dbio:whoami` to see usage. Upgrade plan at dashboard.

## Support

- Docs: https://docs.dbio.ai
- Email: support@dbio.ai
- Issues: https://github.com/dbio-ai/claude-plugins/issues

## License

Apache 2.0
