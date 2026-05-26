---
description: Configure checkout, coupons, payment options, and order flow for a Dbio e-commerce store. Use when user wants to set up coupons, configure payment methods, customize cart/checkout, or manage orders.
---

# E-commerce Checkout Setup

Use when user wants to configure checkout-related features on an active ecomm store.

## Prerequisites

- Active store with `store_type: ecomm`
- `store_select` already called
- Has at least 1 product (else suggest `ecom-product` first)

## Common tasks

### 1. Create a coupon

```
coupon_create({
  code: "WELCOME10",                 // user-facing code, uppercase
  discount_type: "percentage",       // percentage | fixed
  discount_value: 10,                // 10% or fixed amount in store currency
  min_order_amount: 100000,          // optional, in store currency
  max_uses: 100,                     // optional total cap
  max_uses_per_user: 1,              // optional per-user cap
  starts_at: "2026-06-01 00:00:00",  // optional, ISO datetime
  expires_at: "2026-12-31 23:59:59", // optional
  applicable_to: "all",              // all | products | categories
  status: 1
})
```

Best practices:
- First-time discount: 10-15% off
- Cart minimum: 5x discount value (avoid abuse)
- Time-bound: 7-30 days for urgency
- Don't stack coupons (max_uses_per_user: 1)

### 2. Free shipping threshold

Configure in store settings (dashboard) — not exposed via MCP for security.

Instruct user:
> "Set free shipping threshold at Dashboard → Settings → Shipping. Common value: 2-3x average order value."

### 3. Payment methods

Configured per-platform automatically:
- dbio.ai → Stripe (cards, Apple Pay, Google Pay) — user enables in Dashboard → Payments
- dbio.vn → SePay (VietQR bank transfer) + Stripe — user adds bank account in Dashboard

Cannot be configured via MCP. Tell user where to go.

### 4. Order management

List recent orders:
```
order_list({ status: "pending", limit: 20 })
```

Update order status:
```
order_update({ order_id, status: "shipped", tracking_number: "..." })
```

Order lifecycle: `pending → paid → shipped → delivered` (or `cancelled`/`refunded`).

### 5. Customer accounts (optional)

If user wants customer login + order history:
```
store_update({
  settings: { features: { customer_accounts: true } }
})
```

This enables `/auth/login` page on the storefront.

### 6. Tax & invoice

VN market:
- Show tax-included pricing (default in Dbio for VND stores)
- VAT invoice flow: dashboard-only, user inputs MST + uploads receipt template

International (USD):
- Tax handled by Stripe Tax (auto-calculate per region) — user enables in Dashboard

### 7. Abandoned cart recovery

Dashboard-only feature (uses notification queue). Tell user:
> "Enable abandoned cart emails at Dashboard → Marketing → Recovery. Default sends at 1h, 24h, 72h."

## Don't

- ❌ Don't try to call `wallet_deposit`, `wallet_purchase`, `domain_purchase` — dashboard-only
- ❌ Don't hardcode payment method — depends on platform
- ❌ Don't expose coupon codes in URLs or social posts (suggest unique per channel)
