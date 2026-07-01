---
title: "How to Hide Default Variation Price in WordPress | CM"
slug: hide-default-variation-price
description: "Hide the default price display for variable WooCommerce products in Classic Monks. Shows price only when a specific variation is selected, reducing customer confusion."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/hide-default-variation-price/
---

# How to Hide Default Variation Price in WordPress

> Hide Default Variation Price hides the default price range display for variable WooCommerce products. Shows the price only after a specific variation is selected, reducing customer confusion from the "from $X to $Y" range.

## Key Takeaways

- Single toggle, no nested options
- Hides the default "From $X" price range
- Price appears after a variation is selected
- Works with the Auto-select First Variation feature (price shows immediately)
- Reduces confusion for products with many variations and wide price ranges

## What Is the Hide Default Variation Price feature?

By default, WooCommerce shows a price range for variable products: "From $X" or "$X - $Y" (depending on the variation prices). The Hide Default Variation Price feature hides this default display, so the price is only shown when a specific variation is selected.

## Why You Need It

The default price range display can be confusing:

- "From $10" suggests the cheapest variation is $10, but the variation the customer wants might be $50
- The range display doesn't help with purchase decisions (the customer can't tell which variation is at which price)
- Some products have wide ranges ($10 to $200) that make the product feel unpredictable

Hiding the default price and showing it only after selection:

- Eliminates the "From $X" confusion
- Shows the exact price for the selected variation
- Forces the customer to engage with the variation selection

For most stores, this is a UX improvement. For stores where the price range is a key selling point (e.g., "From $5, our most affordable plan starts at..."), keep the default display.

---

## How to Hide Default Variation Price in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Single Product** subtab.

### Step 3: Enable Hide Default Variation Price

Scroll to **Hide Default Variation Price** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit a variable product on the front-end. Before selecting a variation, no price should appear. After selecting a variation, the price should appear.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Hide Default Variation Price** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- Variable product pages: the default "From $X" price range is hidden
- The variation price: shown when a variation is selected (via AJAX)
- Product loops: the price is hidden until variation is selected (if the loop shows variation dropdowns)

## What Does NOT Get Affected

- The variation's actual price (set in WooCommerce > Products > Variations)
- The price on non-variable products
- The price on variable products that have a single variation (no price range to hide)
- The cart and checkout pages (price is final at that point)

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `variation-display.php`:

**Actions:**

- `wp_head` calls `anonymous()` (Hides default variation price display via CSS)

```php
// Hooked in variation-display.php
add_action( 'wp_head', 'anonymous' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The price is not showing at all (even after selecting a variation)

**Cause:** A theme or plugin is preventing the AJAX variation response from rendering the price.
**Fix:** Check the browser console for errors. Verify the variation form is being submitted. Disable other variation-related plugins to find the conflict.

### The "From $X" text is still showing

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the toggle is on. Clear all caching layers.

### The price shows after selection but not before

**Cause:** This is the expected behavior when the toggle is on. If the price doesn't show after selection, see the troubleshooting above.

### I want to show a "From $X" hint but not the full price range

**Cause:** The toggle is binary (show or hide). It doesn't support partial display.
**Fix:** Configure in the plugin settings to show a custom message (e.g., "From $X" or "Select option for price"). This gives a hint without showing the full price.

---

## Related Articles

- [How to Update Price on Variation Selection in WordPress](woocommerce-update-price-on-variation.md)
- [How to Show Price Savings in WordPress](woocommerce-show-price-savings.md)
- [How to Use Product Swatches in WordPress](woocommerce-product-swatches.md)
