---
title: "How to Disable Out of Stock Variations in WooCommerce"
slug: disable-out-of-stock-variations
description: "Prevent customers from selecting out of stock variations in WooCommerce. Mark an out of stock variation as inactive so it is not offered in dropdowns."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-out-of-stock-variations/
---

# How to Disable Out of Stock Variations in WooCommerce

> Disable out of stock variations in WooCommerce so they are not offered as pickable options. When enabled, an out of stock variation is treated as inactive in variation dropdowns, guiding customers toward available choices.

## Key Takeaways

- Mark out of stock variations as inactive in dropdowns
- Uses WooCommerce's variation activity check so unavailable options are not selectable
- Works with your existing variation dropdowns and product data
- Simple on/off toggle, no nested options
- Prevents checkout surprises from out of stock selections

## What Does the Feature Do?

WooCommerce lets customers select any variation shown in a dropdown, even one that is out of stock. A customer can pick an unavailable size or color, add it to cart, and only learn it is unavailable later.

The **Disable Out of Stock Variations** feature filters variation activity so out of stock variations are no longer valid pickable options. It hooks into WooCommerce's `woocommerce_variation_is_active` check, so a variation that is out of stock is treated as inactive and does not appear as an available choice.

## Why You Need It

Disabling unavailable options prevents a common source of friction:

- Customers cannot add an out of stock variation and later discover it is gone
- The dropdown only offers what can actually be purchased
- Customers are guided toward available options instead of hitting dead ends
- Checkout and cart avoid the "no longer in stock" error state

---

## How to Disable Out of Stock Variations in WooCommerce

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Single Product** settings area.
3. Toggle on **Disable Out of Stock Variations**.

### Step 2: Save and Test

Click **Save Changes**. On a variable product, set one variation to out of stock (Inventory > Stock status). Visit the product and confirm that variation is no longer offered as a selectable option, while in stock variations remain available.

---

## Configuration Options

| Option | Default |
|--------|---------|
| **Disable Out of Stock Variations** | Off |

There are no nested options. The feature is a single on/off control.

---

## What Gets Affected

- Variable product dropdowns: out of stock variations are no longer active pickable options
- The variation selection flow: WooCommerce will not validate an out of stock variation as a valid choice

## What Does NOT Get Affected

- The variation's data and price: these stay in place
- The product's stock management: inventory still works as normal in WooCommerce
- In stock variations: these remain available as before
- The variation attributes themselves: only the active/available state changes

---

## Advanced Options (Developers)

The feature registers one hook in `functions/woocommerce/variation-display.php`:

```php
add_filter( 'woocommerce_variation_is_active', 'cm_disable_out_of_stock_variations', 10, 2 );
```

**`woocommerce_variation_is_active`** calls `cm_disable_out_of_stock_variations()` when the feature is enabled, so out of stock variations are reported as inactive. This is the standard WooCommerce hook that determines whether a variation can be selected.

---

## Troubleshooting

### An out of stock variation is still selectable

**Cause:** The feature toggle is off, or the variation is not actually marked as out of stock in WooCommerce.
**Fix:** Confirm **Disable Out of Stock Variations** is on. Open the product's Variations tab and verify the variation's Stock status is set to "Out of stock" (or its stock quantity is zero).

### The variation is disabled in the dropdown but still shown elsewhere

**Cause:** Dropdowns use the variation activity check, while other display areas may render the attribute differently.
**Fix:** The feature targets variation activity. If a swatch or other custom element still shows the option, check that it respects WooCommerce's active-variation state or is theme-specific.

### In stock variations are also affected

**Cause:** A theme or another plugin may apply its own variation filtering on top of this feature.
**Fix:** Confirm the affected variation is actually out of stock. If an in stock variation is being hidden, review other variation plugins that also filter active variations.

---

## Frequently Asked Questions

### How does WooCommerce decide a variation is available?

This feature uses WooCommerce's `woocommerce_variation_is_active` filter. When the feature is on, an out of stock variation returns as inactive and is not offered as a pickable option.

### Does this remove the variation from the product?

No. The variation, its data, and its price remain on the product. Only its active/available state changes so customers cannot select an out of stock option.

### Will it affect my inventory tracking?

No. Stock management is unchanged. The feature only changes which variations are presented as available in the dropdown.

### Does it work with swatches?

If your swatches respect WooCommerce's active-variation state, they will reflect the disabled variations. The feature itself targets the variation dropdown activity check via WooCommerce's standard filter.

---

## Related Articles

- [How to Customize the Out of Stock Button in WooCommerce](woocommerce-customize-out-of-stock-button.md)
- [How to Auto-Select the First Variation in WooCommerce](woocommerce-auto-select-first-variation.md)
- [How to Add Variation Swatches to WooCommerce in WordPress](woocommerce-product-swatches.md)
