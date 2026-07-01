---
title: "How to Disable WooCommerce Gutenberg Blocks Styles in WordPress | CM"
slug: disable-woocommerce-blocks-styles
description: "Prevent WooCommerce Gutenberg blocks CSS from loading when blocks aren't used. Improves frontend performance on sites that don't use WooCommerce blocks."
last_updated: 2026-06-24
author: Joy
reading_time: 2 min
canonical: https://classicmonks.com/docs/disable-woocommerce-blocks-styles/
---

# How to Disable WooCommerce Gutenberg Blocks Styles in WordPress

> Disable WooCommerce Gutenberg blocks styles to improve frontend performance on sites that don't use the WooCommerce block editor.

## Key Takeaways

- Single toggle, no nested options
- Reduced unused CSS on pages without WooCommerce blocks
- Faster page load times on classic-editor pages
- Better PageSpeed and Core Web Vitals scores

## What Is the Disable WooCommerce Gutenberg blocks styles feature?

WooCommerce registers Gutenberg blocks for products, cart, checkout, etc. When these blocks are used on a page, WooCommerce loads its blocks CSS. This feature prevents the CSS from loading when the blocks are not used on the page, reducing unused CSS.

## Why You Need It

WooCommerce's blocks CSS is a small but unnecessary load for pages that don't use WooCommerce blocks. For most stores using the classic editor or third-party page builders, the blocks CSS is dead weight. Disabling it improves frontend performance without affecting pages that do use the blocks.

---

## How to Disable WooCommerce Gutenberg Blocks Styles in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Optimization** subtab.

### Step 3: Enable the Feature

Toggle on **Disable WooCommerce Gutenberg blocks styles**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

View a page that uses the classic editor (not Gutenberg blocks). The WooCommerce blocks CSS should not be loaded.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable WooCommerce Gutenberg blocks styles** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- WooCommerce blocks CSS is not loaded on pages without blocks
- Pages that do use WooCommerce blocks still load the CSS
- Reduced overall CSS size on most pages

## What Does NOT Get Affected

- Pages that use WooCommerce Gutenberg blocks (the CSS still loads for them)
- The WooCommerce blocks themselves (they're still available in the block editor)
- The customer-facing shop functionality

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Actions:**

- `wp_enqueue_scripts` calls `cm_disable_woocommerce_scripts()` (Dequeues WooCommerce blocks styles (priority 99))

```php
// Hooked in woocommerce-functions.php
add_action( 'wp_enqueue_scripts', 'cm_disable_woocommerce_scripts' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Common Use Cases

### PageSpeed Insights and Core Web Vitals

The WooCommerce blocks CSS adds approximately 30-50KB of unused CSS to pages that don't use blocks. For stores targeting the green score on PageSpeed Insights, removing this CSS contributes to better LCP and CLS scores. The fix is especially valuable for blog posts and content pages that don't have any WC content.

### Custom product templates

Stores that have their own product page templates via Elementor Pro or Bricks don't need the WC blocks CSS. Disabling it removes the dead weight from those pages.

### PageSpeed optimization

PageSpeed Insights flags unused CSS as a warning. Removing the WC blocks CSS improves the score on pages without blocks.

### Themed product pages

If your theme handles product page layouts via templates, the WC blocks CSS is unused. Disabling it removes the dead weight.

### Classic editor stores

Stores that use the classic editor for all pages and posts don't need WooCommerce blocks CSS.

### Third-party page builder stores

Stores using Elementor, Bricks, or Oxygen for all product pages don't need WooCommerce blocks.

### Performance-focused stores

Every kilobyte of CSS counts for PageSpeed scores. Removing unused WooCommerce blocks CSS is a quick win.

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
