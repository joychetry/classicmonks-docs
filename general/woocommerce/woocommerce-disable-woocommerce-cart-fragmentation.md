---
title: "How to Disable WooCommerce Cart Fragmentation in WordPress | CM"
slug: woocommerce/disable-woocommerce-cart-fragmentation
description: "Prevent WooCommerce from fragmenting the cart for caching. Improves compatibility with caching plugins and enhances site performance."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/woocommerce/disable-woocommerce-cart-fragmentation/
---

# How to Disable WooCommerce Cart Fragmentation in WordPress

> Disable WooCommerce cart fragmentation to improve caching compatibility and avoid performance issues with cached pages.

## Key Takeaways

- Single toggle, no nested options
- Full-page caching works correctly (cart widget is cached)
- Faster page load times for cached pages
- Reduced server load (fewer AJAX requests)

## What Is the Disable WooCommerce cart fragmentation feature?

WooCommerce uses AJAX endpoints (called 'cart fragments') to update the cart widget and other dynamic content on every page load. While this provides real-time cart updates, it can interfere with caching plugins (since each AJAX request is uncached). This feature disables the cart fragment script, allowing the cart widget to be cached.

## Why You Need It

Cart fragmentation prevents effective caching of pages that show the cart widget. For most stores, the cart widget is acceptable to show with a slight delay (when the user adds an item and refreshes, or when the page is re-cached). Disabling cart fragmentation allows full-page caching, which is a major performance win.

---

## How to Disable WooCommerce Cart Fragmentation in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Optimization** subtab.

### Step 3: Enable the Feature

Toggle on **Disable WooCommerce cart fragmentation**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

View the cart widget on a non-cart page. The cart should still show the correct item count (after a refresh or page reload).

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable WooCommerce cart fragmentation** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- Cart fragment AJAX requests are disabled on non-cart pages
- The cart widget is cached (no AJAX updates)
- Caching plugins can fully cache pages with the cart widget

## What Does NOT Get Affected

- The cart widget still shows the correct count (when the page is reloaded)
- Add to cart functionality (the cart updates on page reload, not via AJAX)
- Cart and checkout functionality

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Actions:**

- `wp_enqueue_scripts` calls `cm_disable_woocommerce_cart_fragmentation()` (Disables cart fragmentation AJAX for performance (priority 99))

```php
// Hooked in woocommerce-functions.php
add_action( 'wp_enqueue_scripts', 'cm_disable_woocommerce_cart_fragmentation' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Common Use Cases

### Redis or Memcached Object Cache

Stores using a high-performance object cache (Redis, Memcached) can disable cart fragmentation to reduce cache misses. The cart fragment AJAX request was designed for sites without object cache, where the cart count needs to be fresh on every page load. With object cache, the cart count can be cached briefly (5-10 seconds) without a noticeable difference in UX.

### WooCommerce hosting

On managed WooCommerce hosting (Kinsta, Pressable), caching is already handled at the server level. Disabling cart fragmentation reduces unnecessary AJAX traffic.

### Server resource constraints

AJAX cart fragment requests can add up on busy sites. Disabling them reduces server load.

### Static-site cache plugins

Static-site cache plugins (WP Static Cache, Simply Static) work better when there's no dynamic AJAX to invalidate the cache.

### Cache-heavy stores

Stores with aggressive caching benefit from disabling cart fragmentation. The cart widget is fully cached instead of updating via AJAX on every page load.

### Low-traffic stores

For stores with low traffic, the AJAX overhead of cart fragmentation is unnecessary. Disabling it saves server resources.

### Mobile-optimized stores

Cart fragment AJAX requests can be expensive on mobile networks. Disabling them improves mobile performance.

## Troubleshooting

### The feature is not taking effect

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the toggle is on. Clear all caching layers (page cache, object cache, CDN).

### I want the feature to apply only to specific pages

**Cause:** The toggle is global.
**Fix:** Use a small custom plugin that checks the current page and conditionally enables the feature (e.g., via the filter above).

### A third-party plugin is breaking after enabling

**Cause:** Some plugins depend on the disabled feature.
**Fix:** Disable the toggle and find an alternative (e.g., conditional loading via a performance plugin).

### The change is not visible to customers

**Cause:** The feature is admin-only or affects specific page types that the customer doesn't visit.
**Fix:** Verify the feature is working in the appropriate context (e.g., admin pages, non-WooCommerce pages, etc.).

---

## Related Articles

- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
- [How to Use Logs in WordPress](../core/core-logs.md)
