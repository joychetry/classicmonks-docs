---
title: "How to Auto-select First Variation in WordPress | CM"
slug: auto-select-first-variation
description: "Automatically select the first available product variation in Classic Monks when customers visit variable product pages. Speeds up the purchase decision."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/auto-select-first-variation/
---

# How to Auto-select First Variation in WordPress

> Auto-select First Variation automatically selects the first available product variation when customers visit variable product pages. Removes the need to manually choose a variation before adding to cart.

## Key Takeaways

- Single toggle, no nested options
- First available variation is auto-selected on page load
- Works for variable products with multiple variations
- Speeds up the purchase decision (one less click)
- Can be confusing for customers who want to see all options first

## What Is the Auto-select First Variation feature?

By default, when a customer visits a variable product page, no variation is pre-selected. The customer must click a variation (size, color, etc.) before the "Add to Cart" button becomes active.

The Auto-select First Variation feature pre-selects the first available variation, so the customer can immediately add to cart without first selecting a variation.

## Why You Need It

For stores with many variations, the default behavior forces customers to make a choice before they can purchase:

- For fashion: "Small, Medium, or Large?" before they can add to cart
- For electronics: "Black, Silver, or Gold?" before they can add to cart
- For services: "Basic, Pro, or Enterprise?" before they can add to cart

This adds friction. Auto-selecting the first variation:

- Reduces friction (one less click)
- Speeds up the purchase decision
- Defaults to the most common option (if the first variation is the most popular)
- Can be confusing if the customer wants to see all options first

For most e-commerce stores, the trade-off favors auto-selection.

---

## How to Use Auto-select First Variation in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Single Product** subtab.

### Step 3: Enable Auto-select First Variation

Scroll to **Auto-select First Variation** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit a variable product on the front-end. The first variation should be pre-selected, and the price/image should reflect that variation.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Auto-select First Variation** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- Variable product pages: the first variation is pre-selected on page load
- The variation price: shown immediately (instead of showing a price range)
- The variation image: shown immediately (instead of showing the default product image)
- The Add to Cart button: enabled immediately (instead of being disabled until a selection is made)

## What Does NOT Get Affected

- The variation selection area (dropdowns, swatches): still shows all options for the customer to change
- The variation data: still loaded for all variations, just one is pre-selected
- The cart: still requires a variation selection (just pre-selected now)
- The single product pages of non-variable products: not affected (the feature only applies to variable products)

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `variation-display.php`:

**Filters:**

- `woocommerce_dropdown_variation_attribute_options_args` calls `auto-select()` (Auto-selects first available variation option)

```php
// Hooked in variation-display.php
add_filter( 'woocommerce_dropdown_variation_attribute_options_args', 'auto-select' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The first variation is not pre-selected

**Cause:** The toggle is off, or the product is not a variable product.
**Fix:** Verify the toggle is on. Verify the product is set as "Variable product" in the product data panel.

### The pre-selected variation is out of stock

**Cause:** The default behavior pre-selects the first variation in the product data order, regardless of stock.
**Fix:** Configure in the plugin settings to pre-select an in-stock variation instead (see Advanced Options).

### The variation image is wrong

**Cause:** The first variation's image is being shown, but the customer expected a different image.
**Fix:** Reorder the variations in the product data (Variations tab in the product edit screen). The first variation in the data order is the one pre-selected.

### The Add to Cart button is still disabled

**Cause:** A theme or plugin conflict is preventing the variation auto-select from enabling the Add to Cart button.
**Fix:** Check the browser console for errors. Verify the variation was actually selected (the price/image should reflect it). Some themes need the variation form to be submitted before the Add to Cart is enabled.

---

## Related Articles

- [How to Remove the Clear Variation Link in WordPress](woocommerce-remove-clear-variation-link.md)
- [How to Update Price on Variation Selection in WordPress](woocommerce-update-price-on-variation.md)
- [How to Use Product Swatches in WordPress](woocommerce-product-swatches.md)
