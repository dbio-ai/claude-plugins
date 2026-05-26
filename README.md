# Dbio plugin for Claude Code

Build websites, bio pages, and online stores on [Dbio](https://dbio.ai) — all from inside Claude Code.

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

Slash commands:
```
/dbio:new-shop My Coffee Shop
/dbio:new-blog Tech Insights
/dbio:new-landing Product Launch
/dbio:new-wiki Product Docs
/dbio:find-template restaurant with menu and reservation
```

Or just talk to Claude:

> "Tạo cho tôi 1 trang bán hàng cho quán cafe"  
> "Build me a tech blog with categories"  
> "I want a docs site for my API"

Skills auto-activate based on context — no command needed.

## What it builds

- **Bio link / landing pages** — single-page personal sites, link-in-bio, CV
- **E-commerce stores** — products, cart, checkout, coupons
- **Blogs & news** — multi-page content sites with categories
- **Wikis & docs** — hierarchical knowledge bases
- **Multi-page sites** — portfolios, catalogs, corporate sites
- **Verticals** (via templates) — restaurants, events, courses, services

## Commands

| Command | Purpose |
|---|---|
| `/dbio:find-template <description>` | Find a template by use case (semantic) |
| `/dbio:new-store [name]` | Create blank store (interactive) |
| `/dbio:new-shop [name]` | Create ecommerce store |
| `/dbio:new-landing [name]` | Create landing page |
| `/dbio:new-blog [name]` | Create blog/news site |
| `/dbio:new-wiki [name]` | Create wiki/docs site |
| `/dbio:new-bio [name]` | Add a page to active store |
| `/dbio:ecom-add-product <desc>` | Create a product with AI image |
| `/dbio:publish` | Publish active store, show URL |
| `/dbio:whoami` | Show session, platform, quota |

## Skills (auto-activated)

### Cross-cutting
- `template-search` — try templates first whenever building anything
- `store-create` — build from scratch when no template fits
- `content-write` — context-aware copy (industry, locale)
- `theme-customize` — colors, typography, design tokens
- `publish-deploy` — publish + custom domain + DNS verify

### Vertical-specific
- `bio-design` — bio link / personal landing
- `landing-cta` — landing page conversion optimization
- `ecom-setup` — full e-commerce setup
- `ecom-product` — add products with images/variants
- `ecom-checkout` — coupons, payment, order management
- `blog-setup` — blog/news site structure
- `blog-write` — SEO-optimized post drafting
- `wiki-structure` — hierarchical docs/KB

## Configuration

| Env var | Purpose | Default |
|---|---|---|
| `DBIO_API_KEY` | API key (required) | — |
| `DBIO_MCP_URL` | MCP server endpoint | `https://mcp.dbio.ai/mcp` |

## Troubleshooting

- **Unauthorized errors** — API key invalid/expired. Get a new one at the dashboard.
- **Tools not available** — restart Claude Code after setting env vars. Need v2.0+.
- **Wrong platform** — check `DBIO_MCP_URL`. Set explicitly for dbio.vn or self-hosted.
- **Quota exceeded** — run `/dbio:whoami` to see usage. Upgrade plan at dashboard.

## Links

- Website: https://dbio.ai · https://dbio.vn
- Docs: https://docs.dbio.ai
- Support: support@dbio.ai
- Issues: https://github.com/dbio-ai/claude-plugins/issues

## License

Apache 2.0
