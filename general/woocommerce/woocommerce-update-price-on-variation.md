---
title: "How to Update Price on Variation Selection in WooCommerce"
slug: update-price-on-variation
description: "Update the displayed price in real time when a customer selects a new variation in WooCommerce. Target the price element and set conditions with Classic Monks."
last_updated: 2026-08-06
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/update-price-on-variation/
---

# How to Update Price on Variation Selection in WooCommerce

> Update the displayed price in real time when a customer selects a different variation. Point Classic Monks at the price container on your product page, set optional conditions, and the price refreshes on selection.

## Key Takeaways

- Update the product price instantly when a variation is selected
- Target the price element with CSS selectors for your theme
- Optionally restrict behavior to sale products only, or exclude them
- Works on the variable product page with your theme's markup
- Fine-tune the wrapper and price container classes to match your layout

## What Does the Feature Do?

When a customer selects a variation, WooCommerce knows the new price but many themes do not refresh the displayed price smoothly. The **Update Price on Variation Selection** feature makes the price update in real time when a variation is chosen, using your theme's price container markup.

Because themes differ in how they structure the product and price areas, the feature lets you provide the CSS selectors it targets. You specify which element wraps the product and which element holds the price, so the update works regardless of your theme's markup.

## Why You Need It

Real-time price feedback removes a common point of doubt in the purchase flow:

- Customers see the exact price for the variation they chose before adding to cart
- Comparing prices across variations (for example, Small vs Large) is immediate
- No surprise at checkout when the final price differs from the shown one
- The default selectors work on most themes, with overrides available for custom layouts

---

## How to Update Price on Variation Selection in WooCommerce

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Single Product** settings area.
3. Toggle on **Update Price on Variation Selection**. The nested options expand below the toggle.

### Step 2: Set the Target Selectors

- **Product Wrapper Class**: the element that wraps the product. Default `.product`. Example value: `.product-type-variable`.
- **Price Container Class**: the element that holds the price. Default `.single-product__price .price`. Use a selector matched to your theme's price markup.

### Step 3: Set Conditions (Optional)

Use **Conditions** to control when the update applies:

- **None**: update the price for all variable products.
- **Exclude Sale Products**: do not update for products on sale.
- **Only Sale Products**: update only for products on sale.

### Step 4: Save and Test

Click **Save Changes**. Open a variable product, select a different variation, and confirm the displayed price updates to match the selected variation. If it does not, adjust the **Price Container Class** to match your theme's price element.

---

## Configuration Options

| Option | Behavior | Default |
|--------|----------|---------|
| **Update Price on Variation Selection** | Master toggle. | Off |
| **Product Wrapper Class** | CSS selector for the element wrapping the product. | `.product` |
| **Price Container Class** | CSS selector for the element that holds the price. | `.single-product__price .price` |
| **Conditions** | None, Exclude Sale Products, or Only Sale Products. | None |

---

## What Gets Affected

- The displayed price on the variable product page: refreshes when a variation is selected
- The price container identified by **Price Container Class**: this is the element that updates

## What Does NOT Get Affected

- The variation's actual price data: those are set in WooCommerce > Products > Variations
- The variation image and other product elements: only the price container updates
- Simple products: they have no variations to select
- Tax behavior: how prices include tax is controlled by WooCommerce tax settings

---

## Advanced Options (Developers)

The feature registers its hooks in `functions/woocommerce/variation-display.php`, gated on the **Update Price on Variation Selection** toggle:

```php
add_filter( 'woocommerce_variable_price_html', 'cm_modify_variable_price_html', 10, 2 );
add_action( 'wp_enqueue_scripts', 'cm_variation_scripts', 20 );
add_action( 'wp_enqueue_scripts', 'cm_variation_price_scripts' );
add_action( 'wp_enqueue_scripts', 'cm_add_variation_animation_styles' );
add_action( 'wp_enqueue_scripts', 'cm_live_price_update' );
```

- **`woocommerce_variable_price_html`** (`cm_modify_variable_price_html`) adjusts the variable price output.
- The `wp_enqueue_scripts` actions load the scripts and styles that perform the live price refresh, using the **Product Wrapper Class**, **Price Container Class**, and **Conditions** to know which price element to target and when.

---

## Troubleshooting

### The price is not updating

**Cause:** The feature toggle is off, or the **Price Container Class** does not match your theme's price element.
**Fix:** Confirm the toggle is on. Inspect the product page and identify the actual class that wraps the price, then set **Price Container Class** to that selector. Clear caches.

### The price updates for the wrong element

**Cause:** The **Price Container Class** targets a different element on the page.
**Fix:** Make the selector more specific. Use a combined selector such as `.single-product__price .price` that uniquely identifies the price container used in your theme.

### The update does not respect my sale products setting

**Cause:** The **Conditions** setting is not set to the option you intend.
**Fix:** Confirm **Conditions** is set to Exclude Sale Products or Only Sale Products as needed, then save and retest.

### It has no effect on my theme

**Cause:** The theme renders the price with a non-standard structure or an element the default selectors do not match.
**Fix:** Use the **Product Wrapper Class** and **Price Container Class** to point at the exact elements in your theme. If the theme replaces the price area entirely, the feature may need the price container selector that matches its markup.

---

## Frequently Asked Questions

### What does this feature change?

It makes the displayed price update in real time when a variation is selected, using your theme's price container markup.

### Why do I need to set CSS classes?

Themes structure the product and price areas differently. The **Product Wrapper Class** and **Price Container Class** tell the feature which elements to target so the update works with your specific theme.

### Does it change the variation's actual price?

No. Prices are set in WooCommerce's product variations. The feature only refreshes what is displayed when a variation is selected.

### How does the Conditions option work?

None updates every variable product. Exclude Sale Products skips on-sale items, and Only Sale Products updates just those. Use it to avoid unwanted refreshes on sale pricing.

### Does it affect tax-inclusive prices?

No. Tax display is controlled by your WooCommerce tax settings. The feature reflects the price WooCommerce returns for the selected variation.

---

## Related Articles

- [How to Auto-Select the First Variation in WooCommerce](woocommerce-auto-select-first-variation.md)
- [How to Hide the Default Variation Price in WooCommerce](woocommerce-hide-default-variation-price.md)
- [How to Add Variation Swatches to WooCommerce in WordPress](woocommerce-product-swatches.md)
