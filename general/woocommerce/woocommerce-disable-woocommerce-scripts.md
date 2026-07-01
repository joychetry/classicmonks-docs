---
title: "How to Disable WooCommerce Scripts and Styles on Non-WooCommerce Pages in WordPress | CM"
slug: disable-woocommerce-scripts
description: "Prevent WooCommerce CSS and JavaScript files from loading on pages that don't need WooCommerce functionality. Improves site performance by reducing unnecessary asset loading."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-woocommerce-scripts/
---

# How to Disable WooCommerce Scripts and Styles on Non-WooCommerce Pages in WordPress

> Disable WooCommerce scripts and styles on non-WooCommerce pages to improve site performance by reducing unnecessary asset loading.

## Key Takeaways

- Single toggle, no nested options
- Faster page load times on non-WooCommerce pages (blog, regular pages)
- Reduced bandwidth usage and fewer HTTP requests
- Improved Core Web Vitals (LCP, CLS) on non-shop pages

## What Is the Disable WooCommerce scripts and styles on non-WooCommerce pages feature?

By default, WooCommerce loads its CSS and JavaScript files on every page of the site, including pages that don't need them (e.g., blog posts, regular pages). This feature prevents the WooCommerce assets from loading on non-WooCommerce pages, reducing page load time and improving performance.

## Why You Need It

WooCommerce's default behavior loads its full CSS and JavaScript on every page, even pages that don't display any WooCommerce content. For content-heavy sites, this can be a significant performance hit. By preventing the WooCommerce assets from loading on non-WooCommerce pages, you reduce page load time, decrease bandwidth usage, and improve the user experience on your blog and other non-shop pages.

---

## How to Disable WooCommerce Scripts and Styles on Non-WooCommerce Pages in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Optimization** subtab.

### Step 3: Enable the Feature

Toggle on **Disable WooCommerce scripts and styles on non-WooCommerce pages**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

View source on a non-WooCommerce page (e.g., a blog post). The WooCommerce CSS and JS files should not be loaded.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable WooCommerce scripts and styles on non-WooCommerce pages** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- Non-WooCommerce pages: WooCommerce assets are not loaded
- WooCommerce pages (shop, cart, checkout, account): assets still load normally
- The total number of HTTP requests on non-WooCommerce pages is reduced

## What Does NOT Get Affected

- WooCommerce pages still load all necessary assets
- The cart functionality (the cart widget may still load on non-WooCommerce pages)
- WooCommerce data and settings (orders, products, etc.)

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Actions:**

- `wp_enqueue_scripts` calls `cm_disable_woocommerce_scripts()` (Dequeues WooCommerce scripts on specific pages (priority 99))

```php
// Hooked in woocommerce-functions.php
add_action( 'wp_enqueue_scripts', 'cm_disable_woocommerce_scripts' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Common Use Cases

### Multi-page checkout flows

If you use a multi-page checkout (vs. the default one-page), the WC assets on non-checkout pages are unused. Disabling them improves landing page performance.

### Headless frontend with WP backend

Stores that use WordPress as a backend for a custom React/Vue frontend don't need WC assets on WordPress pages.

### Content-heavy blogs

Stores that have a large blog or content section benefit from not loading WooCommerce assets on blog posts and pages.

### Portfolio sites with a small shop

Sites where the shop is a minor feature don't need WooCommerce assets on every page.

### Landing page stores

Custom landing pages (sales pages, opt-in pages) don't need WooCommerce assets. Disabling them improves landing page performance.

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
