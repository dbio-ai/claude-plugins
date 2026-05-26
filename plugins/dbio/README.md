# dbio plugin for Claude Code

Build websites, bio pages, and online stores on [Dbio](https://dbio.ai) — all from inside Claude Code.

## What it does

This plugin connects Claude Code to your Dbio account so you can:

- **Bio link / landing pages** — single-page personal sites, link-in-bio, CV
- **E-commerce stores** — products, cart, checkout, coupons
- **Blogs & news** — multi-page content sites with categories
- **Wikis & docs** — hierarchical knowledge bases
- **Multi-page sites** — portfolios, catalogs, corporate sites
- **Verticals** (via templates) — restaurants, events, courses, services, and more

Claude understands Dbio's conventions out of the box — section variants, field name gotchas, template flow, vertical patterns — so you get correct results without learning the MCP tool names.

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
> "Add 5 menu items to my restaurant store"

The plugin's skills auto-activate based on context — no command needed.

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

Claude automatically uses these based on context:

### Cross-cutting

| Skill | Activates when |
|---|---|
| `template-search` | User wants to create anything new (tries templates first) |
| `store-create` | Build from scratch (no template) |
| `content-write` | Writing copy, headlines, descriptions |
| `theme-customize` | Change colors, fonts, design tokens |
| `publish-deploy` | Publish or set up custom domain |
| `platform-switch` | Change platform endpoint or self-host |

### Vertical-specific

| Skill | Activates when |
|---|---|
| `bio-design` | Personal bio link / single-page landing |
| `landing-cta` | Optimize landing page conversions |
| `ecom-setup` | Set up e-commerce store |
| `ecom-product` | Add products to ecom store |
| `ecom-checkout` | Configure coupons, payments, orders |
| `blog-setup` | Set up blog/news site structure |
| `blog-write` | Draft SEO-optimized blog posts |
| `wiki-structure` | Structure knowledge base / docs |

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
