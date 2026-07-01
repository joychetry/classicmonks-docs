---
title: "How to Show Price Savings in WordPress | CM"
slug: show-price-savings
description: "Display the amount or percentage saved on sale products in Classic Monks. Customizable prefix and suffix text, with optional display in product loops."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/show-price-savings/
---

# How to Show Price Savings in WordPress

> Show Price Savings displays the amount or percentage saved on sale products. Use the [price_savings] shortcode, customize the prefix and suffix text, and optionally show savings in product loops.

## Key Takeaways

- Display the dollar amount saved on sale products
- Display the percentage discount (e.g., "20% off")
- Customize the prefix and suffix text
- Optionally show savings in product loops (shop, category pages)
- Works with the standard WooCommerce sale price system

## What Is the Show Price Savings feature?

The Show Price Savings feature adds the `[price_savings]` shortcode for displaying the amount or percentage saved on sale products. It works alongside WooCommerce's standard sale price mechanism.

Two related toggles:

- **Show Price Savings**: Display the dollar amount saved (e.g., "You save $20!")
- **Show Percentage Off**: Display the percentage discount (e.g., "20% off")

Each has customizable prefix and suffix text.

## Why You Need It

WooCommerce's default sale display shows the original price crossed out and the sale price, but doesn't show "You save $20!". For most e-commerce sites, displaying the savings is a key conversion driver:

- Increases urgency ("You save $50 if you buy today")
- Highlights value perception
- Creates a clear call-to-action

The shortcode-based approach gives you flexibility: place the savings display wherever you want (product pages, loops, custom templates).

---

## How to Use Show Price Savings in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Single Product** subtab.

### Step 3: Enable Show Price Savings

Scroll to **Show Price Savings** and toggle on.

### Step 4: Configure Display Options

The sub-options include:

- **Prefix Text**: Text before the savings amount (e.g., "You save")
- **Suffix Text**: Text after the savings amount (e.g., "now" or "off")
- **Show in Product Loops**: Display the savings on archive pages (optional)

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Add the Shortcode to Your Theme

For single product pages, add the shortcode to your theme's product page template:

```php
<?php echo do_shortcode('[price_savings]'); ?>
```

For product loops, enable the "Show in Product Loops" option and add the shortcode to your theme's loop template.

### Step 7: Use the Shortcode

The `[price_savings]` shortcode accepts attributes:

- `[price_savings]`: Default display
- `[price_savings prefix="Save: " suffix=" today"]`: Custom prefix/suffix

For the percentage version, the shortcode is `[percentage_off]` (used when "Show Percentage Off" is enabled).

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Show Price Savings** | Master toggle. | Off |
| **Prefix Text** | Text before the savings amount. | "You save" |
| **Suffix Text** | Text after the savings amount. | "" (empty) |
| **Show in Product Loops** | Display in archive pages. | Off |
| **Show Percentage Off** | Master toggle for percentage display. | Off |
| **Prefix Text (Percentage Off)** | Text before the percentage. | "" (empty) |
| **Suffix Text (Percentage Off)** | Text after the percentage. | "off" |

---

## What Gets Affected

- Single product pages: the savings display appears (where the shortcode is rendered)
- Product loops (with the option enabled): savings display on shop, category, archive pages
- Variable products: shows savings based on the lowest variation price (or the active variation)
- Sale products only: non-sale products don't show the savings display

## What Does NOT Get Affected

- The sale price itself: WooCommerce's standard sale mechanism handles this
- The original price (crossed out): WooCommerce's default behavior
- Cart or checkout pages: the savings display is product-page only
- The product's HTML structure: the shortcode is added where you place it

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Actions:**

- `init` calls `cm_init_product_display_features()` (Registers price_savings shortcode)

```php
// Hooked in woocommerce-functions.php
add_action( 'init', 'cm_init_product_display_features' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The savings display is not showing

**Cause:** The toggle is off, the product is not on sale, or the shortcode is not in the theme.
**Fix:** Verify the toggle is on. Verify the product is on sale (regular price > sale price). Verify the shortcode is in the theme template where you want the display.

### The percentage shows wrong

**Cause:** The percentage is calculated from the regular price and sale price. If your store uses taxes or complex pricing rules, the calculation may be off.
**Fix:** Verify the regular and sale prices are set correctly. The percentage is `((regular - sale) / regular) * 100`. If using taxes, the calculation may include or exclude them depending on the WooCommerce tax settings.

### The savings display is duplicating

**Cause:** The shortcode is in the theme template AND the product meta. Both render the display.
**Fix:** Remove the shortcode from one location. Use the toggle alone (which adds the display automatically) or the shortcode alone (which requires manual placement), but not both.

### The display is showing the wrong currency

**Cause:** The currency formatting follows the WooCommerce currency settings. If the currency is set incorrectly, the savings display will use the wrong currency symbol.
**Fix:** Verify the WooCommerce currency settings (WooCommerce > Settings > General > Currency options). Clear the cache.

---

## Related Articles

- [How to Customize the Add to Cart Button in WordPress](woocommerce-customize-add-to-cart-button.md)
- [How to Use Product Swatches in WordPress](woocommerce-product-swatches.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
