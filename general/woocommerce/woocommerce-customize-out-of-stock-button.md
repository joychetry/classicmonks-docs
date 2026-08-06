---
title: "How to Customize the Out of Stock Button in WooCommerce"
slug: customize-out-of-stock-button
description: "Replace the WooCommerce out of stock button with your own text and behavior. Disable it, link to the product page, or hide it, and choose where it applies."
last_updated: 2026-08-06
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/customize-out-of-stock-button/
---

# How to Customize the Out of Stock Button in WooCommerce

> Replace the default "Read More" button text for out of stock products with clearer messaging. Choose whether the button is disabled, links to the product page, or is hidden, and control which scopes and products it applies to.

## Key Takeaways

- Set custom out of stock button text (default "Out of Stock")
- Choose the behavior: disabled, link to product page, or hidden
- Apply to product loops and single product pages independently
- Optionally include variable products when every variation is out of stock
- Add a custom CSS class and Gutenberg blocks compatibility for theming

## What Does the Feature Do?

WooCommerce shows a "Read More" button for out of stock products, which is confusing because there is nothing to read into a purchase. The **Customize Out of Stock Button Text** feature replaces that with your own message and controls how the button behaves.

For each out of stock product it applies your chosen text and style, scoped to loops, single pages, or both. Variable products can be included when all of their variations are out of stock.

## Why You Need It

A clear out-of-stock message improves the purchase experience:

- "Read More" tells customers nothing about whether the product returns
- "Out of Stock" or "Sold Out" communicates stock status honestly
- A disabled button prevents dead-end clicks, while a link to the product page lets customers see details or alternatives
- Hiding the button entirely cleans up shop grids for permanently discontinued items
- Consistent messaging across shop and product pages reduces confusion

---

## How to Customize the Out of Stock Button in WooCommerce

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Single Product** settings area.
3. Toggle on **Customize Out of Stock Button Text**. The nested options expand below the toggle.

### Step 2: Set the Button Text

In **Button Text**, enter the message to show (default `Out of Stock`). Use wording that tells customers the product is unavailable, such as `Out of Stock`, `Sold Out`, or `Unavailable`.

### Step 3: Choose the Button Style

Use **Button Style** to control how the button appears:

- **Disabled (Non-clickable)**: the button is visible but cannot be clicked.
- **Link to Product Page**: the button links to the product page so customers can see details or alternatives.
- **Hide Button Completely**: the button does not render at all.

### Step 4: Choose the Scope

- **Apply to Product Loops** (on by default) applies to shop, category, and archive pages.
- **Apply to Single Product Pages** (on by default) applies to individual product pages.
- **Include Variable Products** (on by default) applies to variable products when all variations are out of stock.

### Step 5: Configure Styling Options

- **Gutenberg Blocks Compatibility** (off by default) enables support for WooCommerce Gutenberg blocks (requires additional CSS).
- **Custom CSS Class** (default `out-of-stock-button`) adds the class to out of stock buttons for custom styling.

### Step 6: Save and Test

Click **Save Changes**. Set a product to out of stock (Inventory > Stock status) and visit it on the front end. Verify the text, style, and scope match your configuration.

---

## Configuration Options

| Option | Behavior | Default |
|--------|----------|---------|
| **Customize Out of Stock Button Text** | Master toggle. | Off |
| **Button Text** | Message shown for out of stock products. | `Out of Stock` |
| **Button Style** | Disabled (Non-clickable), Link to Product Page, or Hide Button Completely. | Disabled (Non-clickable) |
| **Apply to Product Loops** | Apply to shop, category, and archive pages. | On |
| **Apply to Single Product Pages** | Apply to individual product pages. | On |
| **Include Variable Products** | Apply when all variations of a variable product are out of stock. | On |
| **Gutenberg Blocks Compatibility** | Support WooCommerce Gutenberg blocks (requires extra CSS). | Off |
| **Custom CSS Class** | CSS class added to out of stock buttons. | `out-of-stock-button` |

---

## What Gets Affected

- Out of stock products on loops and single pages, per the scope toggles
- The button text, style, and visibility for those products
- Variable products whose variations are all out of stock, when **Include Variable Products** is on
- Button styling through the custom CSS class and Gutenberg compatibility mode

## What Does NOT Get Affected

- The add to cart button on in stock products (use Customize Add to Cart Button Text for that)
- The in-stock badge, stock quantity, or product meta display
- The admin order details: the button is front end only
- Product data and inventory: the feature only changes the button, not stock status

---

## Advanced Options (Developers)

The feature registers its hooks in `functions/woocommerce/variation-display.php`:

```php
add_filter( 'woocommerce_product_add_to_cart_text', 'cm_customize_out_of_stock_button_text', 5, 2 );
add_filter( 'woocommerce_loop_add_to_cart_link', 'cm_customize_out_of_stock_button_loop', 10, 3 );
add_action( 'wp_head', 'cm_add_out_of_stock_button_styles' );

// When Gutenberg blocks compatibility is enabled:
add_filter( 'woocommerce_blocks_product_grid_item_html', 'cm_customize_gutenberg_out_of_stock_button', 10, 3 );
```

- **`woocommerce_product_add_to_cart_text`** (priority 5) replaces the button text with your custom message.
- **`woocommerce_loop_add_to_cart_link`** (priority 10) rebuilds the loop button according to the chosen style (disabled, link, or hidden).
- **`wp_head`** injects the out of stock button styles and the custom CSS class.
- **`woocommerce_blocks_product_grid_item_html`** is registered only when **Gutenberg Blocks Compatibility** is on.

---

## Troubleshooting

### The custom text is not showing

**Cause:** The feature toggle is off, the relevant scope (loop or single) is off, or caching is serving old HTML.
**Fix:** Confirm **Customize Out of Stock Button Text** is on and that the page context (loop or single) matches an enabled scope. Clear caches if the page is unchanged.

### The button is still clickable when set to Disabled

**Cause:** A theme or plugin re-enables the button with JavaScript.
**Fix:** Inspect the rendered button HTML to confirm the disabled attribute is present. If custom script removes it, find and disable that script.

### The customization does not apply to a variable product

**Cause:** **Include Variable Products** is off, or not every variation is out of stock.
**Fix:** Turn on **Include Variable Products**. The feature customizes a variable product only when all of its variations are out of stock; if any variation is in stock, the button stays a normal add-to-cart action.

### I chose Hidden but the button still shows

**Cause:** The button style is set to Disabled or Link, or the scope is off for the page you are viewing.
**Fix:** Confirm **Button Style** is set to **Hide Button Completely** and that the page context matches an enabled scope. Clear caches.

### The custom CSS class has no effect

**Cause:** The class name differs from the one you are styling, or a theme overrides it.
**Fix:** Confirm the class in **Custom CSS Class** matches your stylesheet. Inspect the rendered button in DevTools to verify the class is present, and account for theme CSS specificity.

---

## Frequently Asked Questions

### What does the out of stock button do by default?

Without the feature, WooCommerce shows the theme's "Read More" style button for out of stock products. This feature replaces its text and controls whether it is disabled, links to the product page, or is hidden.

### Can I keep the button visible but not clickable?

Yes. Choose **Disabled (Non-clickable)**. The button remains in the layout for context but cannot be clicked.

### Does it work for variable products?

Yes, when **Include Variable Products** is on. It applies to a variable product only when every one of its variations is out of stock.

### Will this affect in stock products?

No. In stock products keep the normal add to cart button, which is controlled separately by the Customize Add to Cart Button Text feature.

### How do the Gutenberg blocks get styled?

Enable **Gutenberg Blocks Compatibility** and provide the additional CSS in **Custom CSS Class**. The feature registers a blocks filter to apply your button treatment to block-based product grids.

---

## Related Articles

- [How to Customize the Add to Cart Button Text in WooCommerce](woocommerce-customize-add-to-cart-button.md)
- [How to Disable Out of Stock Variations in WooCommerce](woocommerce-disable-out-of-stock-variations.md)
- [How to Add Variation Swatches to WooCommerce in WordPress](woocommerce-product-swatches.md)
