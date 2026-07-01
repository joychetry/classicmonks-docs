---
title: "How to Remove the Clear Variation Link in WordPress | CM"
slug: remove-clear-variation-link
description: "Remove the Clear link that lets customers deselect chosen product variations in Classic Monks. Streamlines the variation selection process."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/remove-clear-variation-link/
---

# How to Remove the Clear Variation Link in WordPress

> Remove Clear Variation Link removes the "Clear" link that allows customers to deselect chosen product variations. Streamlines the variation selection process and prevents accidental deselection.

## Key Takeaways

- Single toggle, no nested options
- Removes the "Clear" link from the variation selection area
- Customers can still change their selection (just can't clear to "no selection")
- Prevents accidental clearing during multi-attribute selection
- Useful for stores with many variations where clearing is a common user error

## What Is the Remove Clear Variation Link feature?

When a customer selects product variations (e.g., "Size: Medium, Color: Blue"), WooCommerce shows a "Clear" link that allows them to deselect all variations and return to the unselected state. The Remove Clear Variation Link feature removes this "Clear" link.

After disabling, customers can change their selection (clicking a different size or color) but cannot clear to "no selection". This is a minor UI change that affects user flow.

## Why You Need It

The "Clear" link is a small UI element that can cause issues:

- **Accidental deselection**: Users may click Clear by accident, then have to re-select all variations
- **Mobile UX**: On small screens, the Clear link is easy to tap accidentally
- **Variation abandonment**: Some users clear variations when they shouldn't, then abandon the purchase

For most stores, the Clear link is harmless. For stores with many variations or mobile-heavy traffic, removing it can improve UX.

---

## How to Remove the Clear Variation Link in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Single Product** subtab.

### Step 3: Enable Remove Clear Variation Link

Scroll to **Remove Clear Variation Link** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit a variable product on the front-end. Select a variation. The "Clear" link should not appear.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Remove Clear Variation Link** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- Variable product pages: the "Clear" link is removed
- The variation selection area still functions (clicking a different size or color changes the selection)
- The variation price and image still update correctly

## What Does NOT Get Affected

- The variation dropdowns or swatches themselves
- The "Add to Cart" button (except when no variation is selected, in which case the button may be hidden or disabled by WooCommerce's default behavior)
- AJAX variation changes
- Cart and checkout pages

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `variation-display.php`:

**Filters:**

- `woocommerce_reset_variations_link` calls `__return_empty_string()` (Hides the reset variations link)

```php
// Hooked in variation-display.php
add_filter( 'woocommerce_reset_variations_link', '__return_empty_string' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The Clear link is still showing

**Cause:** The toggle is off, or a caching plugin is serving an old page.
**Fix:** Verify the toggle is on. Clear all caching layers (page cache, object cache, CDN).

### The Add to Cart button is hidden when no variation is selected

**Cause:** WooCommerce's default behavior hides the Add to Cart button when no variation is selected. Without the Clear link, customers can't deselect to "no selection", but they can still change their selection.
**Fix:** This is WooCommerce's default behavior. The Remove Clear Variation Link feature doesn't change this. If you want the Add to Cart to always show, customize the WooCommerce template or use a plugin.

### I want the Clear link to show in some places but not others

**Cause:** The toggle is global.
**Fix:** The feature is global. If you need per-product control, use the plugin settings and check the product ID or product type before deciding to remove the link.

### The variation selection area is broken after enabling

**Cause:** A theme or plugin conflict is preventing the variation JavaScript from loading.
**Fix:** Check the browser console for errors. Disable other variation-related plugins to find the conflict. Verify the variation swatches/dropdowns are still visible (the Clear link is just one element of the variation area).

---

## Related Articles

- [How to Auto-select First Variation in WordPress](woocommerce-auto-select-first-variation.md)
- [How to Update Price on Variation Selection in WordPress](woocommerce-update-price-on-variation.md)
- [How to Use Product Swatches in WordPress](woocommerce-product-swatches.md)
