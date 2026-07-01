---
title: "How to Update Price on Variation Selection in WordPress | CM"
slug: woocommerce/update-price-on-variation
description: "Update the displayed price in real-time when customers select a different variation in Classic Monks. Provides immediate price feedback during the variation selection process."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/woocommerce/update-price-on-variation/
---

# How to Update Price on Variation Selection in WordPress

> Update Price on Variation Selection dynamically updates the displayed price when customers select a different variation. Provides immediate price feedback during the variation selection process.

## Key Takeaways

- Single toggle, no nested options
- Price updates immediately when variation is selected
- Improves transparency (customer sees the price before adding to cart)
- Works with all variation types (size, color, etc.)
- Standard WooCommerce behavior; this feature ensures it's enabled

## What Is the Update Price on Variation Selection feature?

By default, WooCommerce updates the price when a variation is selected. The Update Price on Variation Selection feature ensures this behavior is active and can be customized.

When a customer selects a different variation (e.g., changes from "Medium" to "Large"), the displayed price updates immediately to reflect the new variation's price. This is standard WooCommerce behavior, but some themes or plugins may disable it. The feature ensures it works.

## Why You Need It

The price update on variation selection is critical for:

- **Price transparency**: Customers see the price before adding to cart (no surprises at checkout)
- **Decision-making**: Customers can compare prices across variations (Small vs Large)
- **Conversion rate**: When the price updates immediately, customers are more confident in the purchase

For most stores, this is the expected behavior. If a theme or plugin is preventing it, this feature restores the standard behavior.

---

## How to Update Price on Variation Selection in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Single Product** subtab.

### Step 3: Enable Update Price on Variation Selection

Scroll to **Update Price on Variation Selection** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit a variable product on the front-end. Select a different variation. The price should update immediately.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Update Price on Variation Selection** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- Variable product pages: the price updates when a variation is selected
- Product loops (with the option enabled): the price updates as variations are selected
- AJAX variation selection: the price update is part of the AJAX response

## What Does NOT Get Affected

- The variation's actual price (set in WooCommerce > Products > Variations)
- The price display on non-variable products (simple products don't have variations)
- The product image (separate feature, not handled by this toggle)
- The cart and checkout pages (price is final at that point)

---

## Advanced Options (Developers)

This feature registers 2 WordPress hooks in `variation-display.php`:

**Actions:**

- `wp_enqueue_scripts` calls `cm_live_price_update()` (Enqueues live price update JS)
- `wp_enqueue_scripts` calls `cm_variation_price_scripts()` (Enqueues variation price scripts)

```php
// Hooked in variation-display.php
add_action( 'wp_enqueue_scripts', 'cm_live_price_update' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The price is not updating when I select a variation

**Cause:** A theme or plugin is preventing the variation JavaScript from running.
**Fix:** Check the browser console for errors. Verify the variation form is being submitted (look for the `variation_id` form field). Disable other variation-related plugins to find the conflict.

### The price updates but the image doesn't

**Cause:** This feature only controls the price. The image update is a separate feature (handled by WooCommerce's default behavior).
**Fix:** Verify the product has variation images set (Variations tab > set image for each variation). If the issue persists, check for plugin conflicts.

### The price is wrong (showing the wrong amount)

**Cause:** The variation's price is not set correctly, or the sale price logic is incorrect.
**Fix:** Verify the variation's prices in WooCommerce > Products > edit variation. Verify sale prices are correct. The displayed price is the variation's sale price if on sale, otherwise the regular price.

### The price updates but doesn't include tax

**Cause:** WooCommerce's tax settings determine whether prices include tax. The price update doesn't change tax behavior.
**Fix:** Verify the tax settings in WooCommerce > Settings > General > Tax options. Prices can be displayed with or without tax depending on the settings.

---

## Related Articles

- [How to Hide Default Variation Price in WordPress](woocommerce-hide-default-variation-price.md)
- [How to Auto-select First Variation in WordPress](woocommerce-auto-select-first-variation.md)
- [How to Use Product Swatches in WordPress](woocommerce-product-swatches.md)
