---
title: "How to Show Percentage Off in WordPress | CM"
slug: show-percentage-off
description: "Display the percentage discount on sale products in Classic Monks. Customizable prefix and suffix text, with optional display in product loops."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/show-percentage-off/
---

# How to Show Percentage Off in WordPress

> Show Percentage Off displays the percentage discount (e.g., "20% off") on sale WooCommerce products. Customize the prefix and suffix text, and optionally show the percentage in product loops.

## Key Takeaways

- Display the percentage discount on sale products
- Customizable prefix and suffix text
- Optionally show in product loops (shop, category pages)
- Works with the standard WooCommerce sale price system
- Complements the "Show Price Savings" feature (dollar amount)

## What Is the Show Percentage Off feature?

The Show Percentage Off feature adds the `[percentage_off]` shortcode for displaying the percentage discount on sale products. It works alongside WooCommerce's standard sale price mechanism.

This is a separate feature from "Show Price Savings" (which shows the dollar amount). You can enable either or both:

- **Show Price Savings**: Display "You save $20!"
- **Show Percentage Off**: Display "20% off"

Each has customizable prefix and suffix text.

## Why You Need It

Showing the percentage discount is a proven conversion driver:

- Creates urgency ("Save 20% if you buy today")
- Highlights value perception
- Provides instant context (no math required to figure out the discount)

The shortcode-based approach gives you flexibility: place the percentage display wherever you want.

---

## How to Use Show Percentage Off in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Single Product** subtab.

### Step 3: Enable Show Percentage Off

Scroll to **Show Percentage Off** and toggle on.

### Step 4: Configure Display Options

The sub-options include:

- **Prefix Text**: Text before the percentage (e.g., "Save" or just empty for "20% off")
- **Suffix Text**: Text after the percentage (default: "off")
- **Show in Product Loops**: Display the percentage on archive pages (optional)

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Add the Shortcode to Your Theme

For single product pages:

```php
<?php echo do_shortcode('[percentage_off]'); ?>
```

For product loops, enable the "Show in Product Loops" option and add the shortcode to your theme's loop template.

### Step 7: Use the Shortcode

The `[percentage_off]` shortcode accepts attributes:

- `[percentage_off]`: Default display
- `[percentage_off prefix="Save " suffix=" today"]`: Custom prefix/suffix

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Show Percentage Off** | Master toggle. | Off |
| **Prefix Text** | Text before the percentage. | "" (empty) |
| **Suffix Text** | Text after the percentage. | "off" |
| **Show in Product Loops** | Display in archive pages. | Off |

---

## What Gets Affected

- Single product pages: the percentage display appears (where the shortcode is rendered)
- Product loops (with the option enabled): percentage display on shop, category, archive pages
- Variable products: shows the percentage based on the active variation
- Sale products only: non-sale products don't show the percentage display

## What Does NOT Get Affected

- The sale price itself: WooCommerce's standard sale mechanism handles this
- The savings dollar amount: that's a separate feature ([Show Price Savings](woocommerce-show-price-savings.md))
- Cart or checkout pages: the display is product-page only
- The product's HTML structure: the shortcode is added where you place it

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Actions:**

- `init` calls `cm_init_product_display_features()` (Registers percentage_off shortcode)

```php
// Hooked in woocommerce-functions.php
add_action( 'init', 'cm_init_product_display_features' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The percentage display is not showing

**Cause:** The toggle is off, the product is not on sale, or the shortcode is not in the theme.
**Fix:** Verify the toggle is on. Verify the product is on sale. Verify the shortcode is in the theme template where you want the display.

### The percentage shows 0%

**Cause:** The product is on sale but the sale price equals the regular price (no actual discount).
**Fix:** Verify the sale price is set correctly. The percentage is calculated as `((regular - sale) / regular) * 100`. If both prices are the same, the percentage is 0.

### The percentage is wrong (e.g., 30% for a 25% sale)

**Cause:** The percentage is calculated from the regular and sale prices. If your store has tax or other pricing rules, the calculation may be off.
**Fix:** Verify the regular and sale prices are set correctly. The calculation uses the values WooCommerce stores in the database, which may include or exclude tax depending on the settings.

### The display is duplicating

**Cause:** The shortcode is in the theme template AND the "Show in Product Loops" option is enabled. Both render the display.
**Fix:** Remove the shortcode from one location. Use the option alone (which adds the display automatically via the product loop filter) or the shortcode alone (which requires manual placement), but not both.

---

## Related Articles

- [How to Show Price Savings in WordPress](woocommerce-show-price-savings.md)
- [How to Customize the Add to Cart Button in WordPress](woocommerce-customize-add-to-cart-button.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
