# Dbio plugin for AI coding agents

Build websites, bio pages, and online stores on [Dbio](https://dbio.ai) — from inside Claude Code, OpenAI Codex CLI, Cursor, and any MCP-compatible AI tool.

This repo provides:
- **MCP server config** for connecting to `mcp.dbio.ai` (works with all MCP clients)
- **15 skills** with Dbio domain knowledge (auto-fire by intent)
- **12 slash commands** (Claude Code) for common workflows
- **Install scripts** for Claude Code marketplace + Codex CLI

## Quick install

### Claude Code
```bash
claude plugin marketplace add dbio-ai/claude-plugins
claude plugin install dbio
```

### OpenAI Codex CLI
```bash
# macOS / Linux
curl -sSL https://raw.githubusercontent.com/dbio-ai/claude-plugins/main/install-codex.sh | bash

# Windows (PowerShell)
irm https://raw.githubusercontent.com/dbio-ai/claude-plugins/main/install-codex.ps1 | iex
```

### Cursor IDE
Edit `~/.cursor/mcp.json` (or `.cursor/mcp.json` per-project):
```json
{
  "mcpServers": {
    "dbio": {
      "url": "https://mcp.dbio.ai/mcp",
      "headers": { "Authorization": "Bearer ${env:DBIO_API_KEY}" }
    }
  }
}
```

### Other MCP clients (Continue.dev, Aider, etc.)
Point your MCP config at `https://mcp.dbio.ai/mcp` with `Authorization: Bearer $DBIO_API_KEY` header. See [Other AI tools](#other-ai-tools) section below.

## Get an API key

- **International** (USD, Stripe): https://dbio.ai/settings/api-keys
- **Vietnam** (VND, SePay): https://dbio.vn/settings/api-keys

Set the env var, persist in your shell profile:
```bash
export DBIO_API_KEY="dbio_pk_xxxxxxxxxxxx"
```

For dbio.vn:
```bash
export DBIO_MCP_URL="https://mcp.dbio.vn/mcp"   # only for Claude / Cursor / Continue
```

For Codex, set in `~/.codex/config.toml` (see Codex section below).

## Try it

Slash commands (Claude):
```
/dbio:new-shop My Coffee Shop
/dbio:new-blog Tech Insights
/dbio:find-template restaurant with menu
/dbio:edit-page change hero title
/dbio:fix broken images on home page
```

Or just talk to your AI:
> "Tạo cho tôi 1 trang bán hàng cho quán cafe"  
> "Build me a tech blog with categories"  
> "Sửa lại hero của trang home, đổi title"

Skills auto-fire by intent — no command needed.

## What it builds

- **Bio link / landing** — single-page personal sites, link-in-bio, CV
- **E-commerce stores** — products, cart, checkout, coupons
- **Blogs & news** — multi-page with categories
- **Wikis & docs** — hierarchical knowledge bases
- **Multi-page sites** — portfolios, catalogs, corporate
- **Verticals via templates** — restaurants, events, courses, services

## Commands (Claude Code only)

### Create
| Command | Purpose |
|---|---|
| `/dbio:find-template <description>` | Find a template by use case |
| `/dbio:new-store [name]` | Create blank store (interactive) |
| `/dbio:new-shop [name]` | Create ecommerce store |
| `/dbio:new-landing [name]` | Create landing page |
| `/dbio:new-blog [name]` | Create blog/news site |
| `/dbio:new-wiki [name]` | Create wiki/docs site |
| `/dbio:new-bio [name]` | Add a page to active store |
| `/dbio:ecom-add-product <desc>` | Create a product with AI image |

### Edit & Fix
| Command | Purpose |
|---|---|
| `/dbio:edit-page <description>` | Edit page (change text, swap image, reorder) |
| `/dbio:fix <issue>` | Diagnose & fix issues |

### Manage
| Command | Purpose |
|---|---|
| `/dbio:publish` | Publish active store, show URL |
| `/dbio:whoami` | Show session, platform, quota |

## Skills (auto-activated)

### Cross-cutting (7)
- `template-search` — try templates first whenever building anything
- `store-create` — build from scratch when no template fits
- `content-write` — context-aware copy (industry, locale)
- `theme-customize` — colors, typography, design tokens
- `publish-deploy` — publish + custom domain + DNS verify
- `page-edit` — modify existing pages/sections
- `fix-issues` — diagnose & fix common problems

### Vertical-specific (8)
- `bio-design` — bio link / personal landing
- `landing-cta` — landing conversion optimization
- `ecom-setup` — full e-commerce setup
- `ecom-product` — add products with images/variants
- `ecom-checkout` — coupons, payment, order info (mostly dashboard)
- `blog-setup` — blog/news structure
- `blog-write` — SEO-optimized post drafting
- `wiki-structure` — hierarchical docs/KB

## Configuration

| Env var | Purpose | Default |
|---|---|---|
| `DBIO_API_KEY` | API key (required) | — |
| `DBIO_MCP_URL` | MCP server endpoint | `https://mcp.dbio.ai/mcp` |

---

## Other AI tools

### OpenAI Codex CLI (manual)

If you skip the installer, configure manually:

**MCP** — add to `~/.codex/config.toml`:
```toml
[mcp_servers.dbio]
url = "https://mcp.dbio.ai/mcp"
bearer_token_env_var = "DBIO_API_KEY"
```

**Skills** — symlink (or copy) into `~/.agents/skills/`:
```bash
git clone https://github.com/dbio-ai/claude-plugins ~/.dbio/plugins
mkdir -p ~/.agents/skills
ln -s ~/.dbio/plugins/skills/* ~/.agents/skills/
```

See [`config.toml.example`](./config.toml.example) for more options.

### Cursor IDE

Cursor supports MCP but has no skill format. Just MCP config (see Quick install).

Cursor will surface all Dbio MCP tools to its agent automatically. Tool descriptions are detailed enough to be useful without skills.

### Continue.dev

Add to `~/.continue/config.json`:
```json
{
  "experimental": {
    "modelContextProtocolServers": [
      {
        "transport": {
          "type": "streamable-http",
          "url": "https://mcp.dbio.ai/mcp",
          "headers": { "Authorization": "Bearer ${env:DBIO_API_KEY}" }
        }
      }
    ]
  }
}
```

### Other MCP-compatible clients

Point at:
- **Endpoint**: `https://mcp.dbio.ai/mcp` (or `https://mcp.dbio.vn/mcp` for Vietnam)
- **Auth**: `Authorization: Bearer <DBIO_API_KEY>` header
- **Transport**: HTTP (streamable)

Works with Aider, Gemini CLI, and any client implementing the MCP spec.

### Standalone (no plugin / no skills)

Just the MCP server. Tool descriptions are written to be self-sufficient:
- `agent_guidelines({ topic: "..." })` — in-depth flow docs
- `components_guide()` — section variant catalog
- Each tool's `description` includes warnings + examples

You lose the workflow orchestration that skills provide, but core functionality works.

---

## Troubleshooting

- **Unauthorized** — API key invalid/expired. Get new at dashboard.
- **Tools not showing** — restart your AI tool after setting env vars.
- **Wrong platform** — check `DBIO_MCP_URL` (default = dbio.ai).
- **Quota exceeded** — run `/dbio:whoami` (Claude) or `auth_get_session()` to see usage. Upgrade at dashboard.

## Links

- Website: https://dbio.ai · https://dbio.vn
- Docs: https://docs.dbio.ai
- Support: support@dbio.ai
- Issues: https://github.com/dbio-ai/claude-plugins/issues

## License

Apache 2.0
