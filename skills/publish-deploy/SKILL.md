---
name: publish-deploy
description: Publishing a Dbio store, setting up a custom domain, managing subdomains, verifying DNS.
---

# Publish & Deploy

Relevant pieces:

- `shop_publish` / `shop_unpublish` — store-level go-live / pause
- `page_publish` / `page_update({ status })` — per-page draft ↔ published
- `page_list({ status: 0 })` — find drafts
- `get_urls` — live URL after publish
- `domain_list` — see attached domains
- `domain_add_custom({ store_id, domain })` — returns DNS TXT verification token; user adds TXT record at `_dbio-verify.<domain>` + CNAME at `@` or `www` → `domains.dbio.ai`
- `domain_verify({ store_id, domain })` — runs the DNS check; SSL auto-issues once verified
- `domain_set_primary({ store_id, domain })` — canonical domain when multiple
- `agent_guidelines({ topic: 'publish_with_custom_domain' })` for full DNS walk-through + propagation expectations

Domain removal + purchase + search are dashboard-only (no MCP tools).
