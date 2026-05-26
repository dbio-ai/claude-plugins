---
description: Publish a Dbio store, set up custom domain, manage subdomains. Use when user wants to make their site live, connect a custom domain, or manage publishing.
---

# Publish & Deploy

Use when user wants to publish their site or connect a custom domain.

## Step 1: Publish the store

```
shop_publish()
```

This makes the store + all published pages live. Default URL:
```
{global_code}.dbio.ai     (international platform)
{global_code}.dbio.vn     (Vietnam platform)
```

Get the live URL:
```
get_urls()
```

## Step 2: Verify pages are published

Each `bio_profile` has its own `status`. Set `status: 1` to publish individual pages:
```
page_update({ bio_id, status: 1 })
// or
page_publish({ bio_id })
```

Pages with `status: 0` show as drafts (not public).

## Step 3: List existing domains

```
domain_list()
```

Returns subdomain + any custom domains attached.

## Step 4: Custom domain (dashboard-only, not via MCP)

Custom domain setup is **dashboard-only** for security reasons. Instruct user:

1. Go to Dashboard → Settings → Domains
2. Add custom domain (e.g. `mycafe.com`)
3. Add CNAME record at registrar:
   ```
   Type: CNAME
   Name: @  (or `www`)
   Value: domains.dbio.ai
   ```
4. Wait 5-30 minutes for DNS propagation
5. Dbio auto-issues SSL via Cloudflare

For VN domain (`.vn`), DNS may take longer (up to 2 hours).

## Step 5: Verify deployment

After publishing, ask user to visit the URL. Common checks:
- All pages load (200, not 404)
- Images render (no broken images)
- Menu links route correctly
- Mobile view looks good
- Forms submit (contact, checkout)

If issues: `cache_clear()` is dashboard-only — instruct user to refresh + try incognito.

## Unpublish

To take site offline:
```
shop_unpublish()
```

Or set individual store `status: 0` via store_update.

## Domain pricing (info only, can't purchase via MCP)

Domain purchase is dashboard-only. Pricing varies by TLD:
- `.com`, `.net`: standard market rate
- `.vn`: VN registrar pricing
- `.ai`: premium TLD

## Don't

- ❌ Don't try to call `domain_add`, `domain_purchase`, `cache_clear` — those are dashboard-only tools, not exposed via public MCP.
- ❌ Don't promise instant DNS propagation — always say "up to 30 minutes".
- ❌ Don't claim SSL is auto if user uses non-Cloudflare DNS — they may need manual cert.
