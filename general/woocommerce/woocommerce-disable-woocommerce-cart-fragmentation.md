---
title: "How to Disable the WooCommerce Cart Fragments Script"
slug: disable-woocommerce-cart-fragmentation
description: "Disable WooCommerce cart fragments so the cart contents do not refresh over AJAX on every page. Reduce extraneous requests and improve load performance."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-woocommerce-cart-fragmentation/
---

# How to Disable the WooCommerce Cart Fragments Script

> Turn off WooCommerce cart fragments so the cart no longer refreshes its contents over AJAX across the site. This removes a frequent background request and lightens the page load.

## Key Takeaways

- Dequeue the WooCommerce cart-fragments script
- Stop the cart from silently re-fetching contents on every page
- Reduce a common extraneous AJAX request
- One toggle, no nested options
- Ideal when the mini cart is not used or causes extra load

## What Does the Feature Do?

WooCommerce's **cart fragments** feature lets the mini cart and cart count update without a full page reload. It does this by loading the `wc-cart-fragments.js` script and re-fetching the cart contents over AJAX when the page changes. That background request runs site-wide, even on pages where the cart is never shown.

The **Disable WooCommerce Cart Fragmentation** feature dequeues that script, so the cart no longer refreshes asynchronously. The store's cart data is unchanged; only the auto-refresh behavior is removed.

## Why You Need It

Cart fragmentation adds a request to nearly every page:

- It deletes the need for a global background fetch when no mini cart is shown
- It reduces one round-trip per page load
- It avoids the "recalculate cart" churn that fragments can trigger
- It cleans up performance on content-heavy and non-checkout pages

---

## How to Disable WooCommerce Cart Fragmentation

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Optimization** settings area.
3. Toggle on **Disable WooCommerce Cart Fragmentation**.

### Step 2: Save and Test

Click **Save Changes**. Load a page and check that the `wc-cart-fragments` script is no longer enqueued. Note that a mini cart that relied on live AJAX updates will no longer refresh that way.

---

## Configuration Options

| Option | Default |
|--------|---------|
| **Disable WooCommerce Cart Fragmentation** | Off |

There are no nested options. The feature is a single on/off control.

---

## What Gets Affected

- The `wc-cart-fragments` script: no longer enqueued on the front end
- Automatic mini cart and cart count refreshes: no longer happen over AJAX

## What Does NOT Get Affected

- The cart data and contents: these remain stored in the session
- The cart and checkout pages: the main cart functionality works normally
- Page loads on shop and checkout pages: these still work with the refresh gone
- Manually refreshed cart actions: add to cart still works as usual

---

## Advanced Options (Developers)

The feature registers one hook in `functions/woocommerce/woocommerce-functions.php`:

```php
add_action( 'wp_enqueue_scripts', 'cm_disable_woocommerce_cart_fragmentation', 99 );
```

**`wp_enqueue_scripts`** (priority 99) calls `cm_disable_woocommerce_cart_fragmentation()`, which dequeues `wc-cart-fragments` so the script does not load site-wide.

---

## Common Use Cases

**Mini cart not used.** If the theme does not rely on a live mini cart, the fragments script is pure overhead.

**Performance tuning.** Removing a background request is a small, safe win on every page.

**Cache-friendly sites.** Static or cached pages gain from not triggering cart re-fetches.

---

## Troubleshooting

### The mini cart no longer updates live

**Cause:** Cart fragments are what make the mini cart refresh without a reload.
**Fix:** If you need a live mini cart, leave the feature off. If you only avoid extraneous loads, keep it on and update the cart through the cart page.

### The fragments script still loads

**Cause:** The toggle is off, or a theme or plugin enqueues the script directly.
**Fix:** Confirm the toggle is on. If another plugin re-adds `wc-cart-fragments`, that plugin is loading it independently.

### A count badge does not update after adding to cart

**Cause:** The count was refreshed by fragments, which are now disabled.
**Fix:** Keep the feature off if a header cart count must update automatically. Otherwise, the count updates on page load.

---

## Frequently Asked Questions

### What are cart fragments?

They are the WooCommerce mechanism that refreshes the mini cart and cart count without reloading the page, via the `wc-cart-fragments` script and background AJAX.

### Does disabling them break the cart?

No. The cart and checkout still work. Only the automatic background refresh is removed, so a mini cart that relied on it no longer updates live.

### Why is this a performance win?

The fragments script triggers an AJAX request site-wide. Removing it eliminates that request on pages that do not need a live cart.

### Can I re-enable it?

Yes. Turn the toggle off to restore the fragments script and live mini cart updates.

---

## Related Articles

- [How to Disable WooCommerce Scripts and Styles on Non-WooCommerce Pages](woocommerce-disable-woocommerce-scripts.md)
- [How to Disable WooCommerce Admin Features](woocommerce-disable-woocommerce-admin-features.md)
- [How to Disable All WooCommerce Widgets](woocommerce-disable-woocommerce-widgets.md)
