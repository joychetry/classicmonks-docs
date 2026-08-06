---
title: "How to Disable WooCommerce Block Styles You Do Not Use"
slug: disable-woocommerce-blocks-styles
description: "Remove the WooCommerce Gutenberg block styles when your store does not use block layouts. Trim unused block CSS and requests with a single Classic Monks toggle."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-woocommerce-blocks-styles/
---

# How to Disable WooCommerce Block Styles You Do Not Use

> Remove the WooCommerce Gutenberg block styles from your pages when you do not use the block-based layouts. Classic Monks dequeues the block CSS you do not need.

## Key Takeaways

- Dequeue WooCommerce block editor styles
- Remove the registered `wc-blocks-*` style handles
- Trim unused block CSS from the front end
- Uses WooCommerce's registered block style handles
- Keeps the store functional while removing unused block styles

## What Does the Feature Do?

WooCommerce registers a set of block styles (the `wc-blocks-*` style handles) for its Gutenberg block layouts. The **Disable WooCommerce Blocks Styles** feature dequeues those registered styles from the front end when you are not using the block-based WooCommerce layouts.

Removing them trims unnecessary CSS without affecting the core shop, which uses its own product and checkout templates.

## Why You Need It

Block styles add CSS that may not be used:

- A classic-theme store does not render WooCommerce block layouts
- Dropping the registered block styles reduces CSS weight and requests
- It cleans up the front end for non-block store designs
- It applies to the specific handles WooCommerce registers for its blocks

---

## How to Disable WooCommerce Gutenberg Blocks Styles

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Optimization** settings area.
3. Toggle on **Disable WooCommerce Blocks Styles**.

### Step 2: Save and Test

Click **Save Changes**. Load a WooCommerce page and confirm the block styles are no longer enqueued. The shop and checkout still work normally.

---

## Configuration Options

| Option | Default |
|--------|---------|
| **Disable WooCommerce Blocks Styles** | Off |

There are no nested options. The feature is a single on/off control.

---

## What Gets Affected

- The front end: WooCommerce block styles are dequeued
- Page CSS: the registered `wc-blocks-*` style handles no longer load

## What Does NOT Get Affected

- The core shop, product, and checkout templates: these keep their own styles
- WooCommerce functionality: products, cart, checkout work normally
- Block layouts you actively use: if you rely on block layouts, leave the feature off

---

## Advanced Options (Developers)

The feature registers its logic in `functions/woocommerce/woocommerce-functions.php`:

```php
add_action( 'wp_enqueue_scripts', 'cm_disable_gutenberg_blocks_styles' );
```

**`wp_enqueue_scripts`** calls `cm_disable_gutenberg_blocks_styles()`. When enabled, it dequeues the registered WooCommerce block style handles, which include the `wc-blocks-*` styles for the various product and checkout blocks.

---

## Common Use Cases

**Classic themes.** Stores on classic product and checkout templates do not render block layouts, so the block styles are unused CSS.

**Performance tuning.** Removing unused block CSS reduces page weight on WooCommerce pages.

**Lightweight stores.** Any store that wants a leaner front end without block layout CSS benefits from this toggle.

---

## Troubleshooting

### The block styles are still loading

**Cause:** The toggle is off, or a block layout is actively enqueuing its styles.
**Fix:** Confirm the toggle is on. If a page uses a WooCommerce block, it may enqueue the needed style independently of this toggle.

### A block layout does not look right

**Cause:** The block styles were removed, so a block layout renders without its intended styling.
**Fix:** If you use block layouts, keep the feature off so the registered block styles load.

### The shop still works

**Cause:** This is expected. The feature removes block layout styles, not the core shop templates.
**Fix:** No action needed.

---

## Frequently Asked Questions

### What styles get removed?

The registered WooCommerce block styles, identified by the `wc-blocks-*` handles. These style the WooCommerce Gutenberg block layouts.

### Does it affect the shop and checkout?

The core shop and checkout keep their own styles and work normally. Only the block layout styles are dequeued.

### Should I use this with block themes?

If your store relies on WooCommerce block layouts, keep the feature off. It is intended for stores that do not use the block-based layouts.

---

## Keeping It Set Up

Set the toggle once and it stays active across the site. To change behavior, return to the WooCommerce settings, adjust the option, and save again. The store continues to run normally throughout, and you can turn the feature off at any time to restore the previous default behavior. For teams managing multiple environments, confirm the setting on staging first, then apply it to production and verify a real page load before treating it as live.

---

## Related Articles

- [How to Disable WooCommerce Scripts and Styles on Non-WooCommerce Pages](woocommerce-disable-woocommerce-scripts.md)
- [How to Disable All WooCommerce Widgets](woocommerce-disable-woocommerce-widgets.md)
- [How to Disable WooCommerce Admin Features](woocommerce-disable-woocommerce-admin-features.md)
