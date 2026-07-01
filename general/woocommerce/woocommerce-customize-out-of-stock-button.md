---
title: "How to Customize the Out of Stock Button in WordPress | CM"
slug: woocommerce/customize-out-of-stock-button
description: "Customize the out-of-stock button text and behavior in Classic Monks. Choose disabled, link-to-product, or hidden behavior, with optional CSS class and Gutenberg blocks compatibility."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/woocommerce/customize-out-of-stock-button/
---

# How to Customize the Out of Stock Button in WordPress

> Customize the out-of-stock button text and behavior in Classic Monks. Choose how the button appears for unavailable products (disabled, link to product page, or hidden) and customize the text for each product type.

## Key Takeaways

- Three behavior options: disabled, link to product page, or hidden
- Custom text per product type (simple, variable, grouped, external)
- Optional custom CSS class for theme-specific styling
- Gutenberg blocks compatibility for block-based themes
- Optionally include variable products that are completely out of stock

## What Is the Customize Out of Stock Button Text feature?

The default WooCommerce behavior for out-of-stock products is to show a grayed-out "Read More" button (or similar, depending on the theme). This feature lets you customize:

- The button text (e.g., "Out of Stock", "Sold Out", "Notify When Available")
- The button behavior (disabled, link to product page, or hidden)
- The CSS class for theme-specific styling
- Whether the customization applies to variable products that are completely out of stock

## Why You Need It

The default behavior is generic and inconsistent across themes:

- "Read More" is confusing for products that are clearly out of stock
- Customers don't know if the product is coming back
- Some themes show different text, some show no button at all
- For digital products, "out of stock" doesn't apply (the feature still applies if you want consistent messaging)

For most e-commerce sites, custom out-of-stock messaging improves the customer experience.

---

## How to Customize the Out of Stock Button in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Single Product** subtab.

### Step 3: Enable Customize Out of Stock Button Text

Scroll to **Customize Out of Stock Button Text** and toggle on. Nested options expand.

### Step 4: Set the Button Text

Set the button text for each product type:

- **Simple Products Button Text**: Default "Out of Stock"
- **Variable Products Button Text**: Default "Out of Stock"
- **Grouped Products Button Text**: Default "Out of Stock"
- **External Products Button Text**: Default "Out of Stock"

### Step 5: Choose the Button Behavior

Select the **Out of Stock Button Style**:

- **Disabled**: Non-clickable, grayed out
- **Link to Product Page**: Clickable, but links to the product page (lets customers see related products or waitlist)
- **Hidden**: Button does not appear at all

### Step 6: Configure Advanced Options

The 6 sub-options include:

- **Apply to Product Loops**: Use the custom button on archive pages
- **Apply to Single Product Pages**: Use the custom button on detail pages
- **Include Variable Products**: Apply the customization to variable products that are completely out of stock (all variations)
- **Gutenberg Blocks Compatibility**: Enable compatibility with WooCommerce Gutenberg blocks
- **Custom CSS Class for Out of Stock**: Add a custom CSS class for theme styling
- **Custom Button Text**: Override the per-product-type text with a single custom text

### Step 7: Save Changes

Click **Save Changes**.

### Step 8: Test

Set a product to out of stock (Inventory > Stock status). Visit the product on the front-end. Verify the button text and behavior match your configuration.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Customize Out of Stock Button Text** | Master toggle. | Off |
| **Simple Products Button Text** | Text for simple products. | "Out of Stock" |
| **Variable Products Button Text** | Text for variable products. | "Out of Stock" |
| **Grouped Products Button Text** | Text for grouped products. | "Out of Stock" |
| **External Products Button Text** | Text for external products. | "Out of Stock" |
| **Apply to Product Loops** | Use on archive pages. | Off |
| **Apply to Single Product Pages** | Use on detail pages. | On |
| **Include Variable Products** | Apply when all variations are out of stock. | Off |
| **Gutenberg Blocks Compatibility** | Enable for block-based themes. | Off |
| **Custom CSS Class for Out of Stock** | Theme-specific class. | "out-of-stock-btn" |
| **Out of Stock Button Style** | Disabled, Link, or Hidden. | Disabled |

---

## What Gets Affected

- All out-of-stock products on the site (per the configuration)
- The button text and behavior on the front-end
- The CSS class for theme-specific styling
- The button visibility based on the Hidden style

## What Does NOT Get Affected

- The "Add to Cart" button on in-stock products (use [Customize Add to Cart Button](woocommerce-customize-add-to-cart-button.md) for that)
- The "Notify When Available" email subscription (that's a separate plugin)
- The admin order details (the button is front-end only)
- Stock display (the "Out of stock" badge or text in the product meta)

---

## Advanced Options (Developers)

This feature registers 3 WordPress hooks in `variation-display.php`:

**Actions:**

- `wp_head` calls `cm_add_out_of_stock_button_styles()` (Injects out of stock button CSS)

**Filters:**

- `woocommerce_product_add_to_cart_text` calls `cm_customize_out_of_stock_button_text()` (Customizes out of stock button text (priority 5))
- `woocommerce_loop_add_to_cart_link` calls `cm_customize_out_of_stock_button_loop()` (Customizes out of stock loop button (priority 10))

```php
// Hooked in variation-display.php
add_filter( 'woocommerce_product_add_to_cart_text', 'cm_customize_out_of_stock_button_text' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The custom button text is not showing

**Cause:** The toggle is off, or caching is serving the old button text.
**Fix:** Verify the toggle is on. Clear all caching layers. The button is rendered server-side, so caching is the most common cause.

### The button is still clickable when the style is set to "Disabled"

**Cause:** A theme or plugin is overriding the `disabled` attribute via JavaScript.
**Fix:** Check the rendered button HTML (View Source) to verify the `disabled` attribute is present. If a custom JavaScript is removing it, identify and disable that script.

### The customization doesn't apply to variable products

**Cause:** The "Include Variable Products" sub-option is off.
**Fix:** Enable the sub-option. Variable products are only customized if all variations are out of stock (per-variation stock is checked).

### The CSS class doesn't apply

**Cause:** The theme's CSS specificity is overriding the custom class, or the class name is misspelled.
**Fix:** Inspect the rendered button in the browser's DevTools. Verify the class is present. If it is but not styled, your theme's CSS has higher specificity. Add `!important` to the theme CSS rule (as a last resort) or use a more specific selector.

### The button is hidden when it should be disabled

**Cause:** The button style is set to "Hidden" but you wanted "Disabled".
**Fix:** Check the Out of Stock Button Style setting. "Hidden" completely removes the button; "Disabled" keeps it visible but unclickable.

---

## Related Articles

- [How to Customize the Add to Cart Button in WordPress](woocommerce-customize-add-to-cart-button.md)
- [How to Use Product Swatches in WordPress](woocommerce-product-swatches.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
