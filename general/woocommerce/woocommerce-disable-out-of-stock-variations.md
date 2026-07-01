---
title: "How to Disable Out of Stock Variations in WordPress | CM"
slug: woocommerce/disable-out-of-stock-variations
description: "Visually disable or hide out-of-stock product variations in Classic Monks. Choose between blur with cross, blur only, or completely hidden behavior."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/woocommerce/disable-out-of-stock-variations/
---

# How to Disable Out of Stock Variations in WordPress

> Disable Out of Stock Variations visually disables or hides product variations that are out of stock. Choose between blur with cross, blur only, or completely hidden behavior.

## Key Takeways

- Single toggle, no nested options
- Three behavior options: blur with cross, blur only, or hidden
- Applies to all variation types (size, color, etc.)
- Works with swatches and dropdowns
- Prevents customer frustration with unavailable options

## What Is the Disable Out of Stock Variations feature?

By default, WooCommerce shows out-of-stock variations in the same way as in-stock variations. Customers can select an out-of-stock variation, add it to cart, and only discover it's unavailable at checkout.

The Disable Out of Stock Variations feature changes this by either:

- **Blur with cross**: Show the variation but blur it and add a red X overlay
- **Blur only**: Show the variation but blur it (no overlay)
- **Hidden**: Completely remove the variation from the display

The choice between "blur with cross" and "blur only" affects how clearly customers understand the variation is unavailable.

## Why You Need It

The default behavior creates a bad user experience:

- Customer selects "Medium" (out of stock)
- Adds to cart
- Goes to checkout
- Discovers Medium is unavailable
- Has to re-select a different size
- Likely abandons the purchase

Pre-disabling out-of-stock variations:

- Prevents wasted checkout steps
- Sets clear expectations (customer knows Medium is out before they add to cart)
- Guides customers toward available options

For most e-commerce stores, this is a high-ROI optimization.

---

## How to Disable Out of Stock Variations in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Single Product** subtab.

### Step 3: Enable Disable Out of Stock Variations

Scroll to **Disable Out of Stock Variations** and toggle on.

### Step 4: Configure the Behavior

Set the **Disabled Swatch Behavior** dropdown (this is a related toggle for Product Swatches):

- **Blur with Cross**: Blur the variation and add a red X overlay
- **Blur**: Blur the variation only (no overlay)
- **Hide**: Completely remove the variation from display

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Test

Set a variation to out of stock (Inventory > Stock status). Visit the product. The variation should appear blurred or hidden based on your configuration.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable Out of Stock Variations** | Master toggle. | Off |
| **Disabled Swatch Behavior** | Blur with Cross, Blur, or Hide. | Blur |

The "Disabled Swatch Behavior" is a related toggle in the Product Swatches subtab. The Disable Out of Stock Variations toggle is in the Single Product subtab.

---

## What Gets Affected

- Variable product pages: out-of-stock variations are visually disabled or hidden
- Product loops: if the variation is in the loop, it's disabled/hidden there too
- AJAX variation selection: works normally with disabled variations
- The cart: disabled variations cannot be added (the Add to Cart button won't enable for them)

## What Does NOT Get Affected

- The product's stock status (managed in WooCommerce > Inventory)
- The variation's data (it's still in the database, just not shown)
- The variation's price (still displayed for in-stock variations)
- The product's image (still shown, even if the selected variation is out of stock)

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `variation-display.php`:

**Filters:**

- `woocommerce_variation_is_active` calls `cm_disable_out_of_stock_variations()` (Removes out of stock variations from dropdown (priority 10))

```php
// Hooked in variation-display.php
add_filter( 'woocommerce_variation_is_active', 'cm_disable_out_of_stock_variations' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### Disabled variations are still showing as enabled

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the toggle is on. Clear all caching layers. The disabled state is rendered server-side, so caching is the most common cause.

### The blur effect is not working visually

**Cause:** The CSS for the blur effect is not loading, or a theme is overriding the styles.
**Fix:** Check that the Classic Monks framework CSS is loading (View Source). If a custom theme has high-specificity CSS for variation dropdowns, it may override the blur.

### The Hide behavior is hiding the variation but customers want to see it as out of stock

**Cause:** The Hide behavior is intentional (it completely removes the variation).
**Fix:** Switch to Blur or Blur with Cross to keep the variation visible but disabled. This shows the customer that the variation exists but is out of stock.

### The variation is enabled when it should be disabled

**Cause:** The variation's stock status is not set to "Out of stock" in the product data.
**Fix:** Edit the product > Variations tab. For each variation, set Stock Status to "Out of stock" (or set the Stock quantity to 0). The Disable Out of Stock Variations feature only affects variations that are already marked as out of stock.

---

## Related Articles

- [How to Customize the Out of Stock Button in WordPress](woocommerce-customize-out-of-stock-button.md)
- [How to Use Product Swatches in WordPress](woocommerce-product-swatches.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
