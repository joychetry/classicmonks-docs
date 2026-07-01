---
title: "How to Use Product Swatches in WordPress | CM"
slug: product-swatches
description: "Transform WooCommerce product attributes into visual swatches (color, image, label) in Classic Monks. Configure swatch layout, size, tooltips, and archive display."
last_updated: 2026-06-24
author: Joy
reading_time: 5 min
canonical: https://classicmonks.com/docs/product-swatches/
---

# How to Use Product Swatches in WordPress

> Product Swatches transforms WooCommerce product attributes (color, image, label) into visual swatches on the product page, improving the shopping experience and increasing conversion rates.

## Key Takeaways

- Replace text-based attribute dropdowns with visual swatches (color circles, image thumbnails, or text labels)
- Configurable layout (horizontal/vertical), size, and tooltip behavior
- Display swatches on archive pages (shop, category) for quick variation selection
- Replace text-based layered nav filters with visual swatches
- Disable out-of-stock variations to prevent customer confusion

## What Are Product Swatches?

Product Swatches is a Classic Monks feature that enhances the default WooCommerce variable product display. Instead of dropdown menus for product attributes (e.g., "Size: Small / Medium / Large"), customers see visual swatches: color circles, image thumbnails, or text labels they can click.

The feature includes 7 sub-options for fine-tuning the swatch display (label separator, dimensions, border width, tooltip behavior, etc.).

## Why You Need It

Text dropdowns for product attributes are functional but friction-heavy:

- Customers don't know what a color looks like from "Blue / Red / Green"
- Clicking a dropdown adds an extra step
- Visual swatches reduce purchase hesitation and improve the user experience
- For fashion, beauty, and design products, swatches are standard

For most product types, visual swatches increase conversion rates. For some product types (digital goods, services), they may not add value, so the feature is opt-in.

---

## How to Use Product Swatches in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Product Swatches** subtab.

### Step 3: Enable Product Swatches

Toggle on **Enable Product Swatches**. Nested options expand below the toggle.

### Step 4: Configure Sub-Options

The 7 sub-options let you fine-tune the swatch display:

- **Show Swatches on Archive Pages**: Display swatches on shop/category pages
- **Show Swatches in Filters**: Replace text-based layered nav filters
- **Enable Custom Tooltip**: Custom tooltips instead of browser default
- **Variation Label Separator**: Separator for selected variation labels (e.g., " / " or " > ")
- **Swatch Width / Height / Border Width**: Visual dimensions
- **Disabled Swatch Behavior**: How out-of-stock swatches appear (blur, blur with X, or hide)
- **Tooltip Position, Color, Background**: Custom tooltip styling
- **Swatch Layout**: Horizontal or vertical

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Verify

Visit a variable product on the front-end. The attribute dropdowns should now be visual swatches.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Product Swatches** | Master toggle. | Off |
| **Show Swatches on Archive Pages** | Display swatches on shop, category, and tag pages. | Off |
| **Show Swatches in Filters** | Replace text-based layered nav filters with swatches. | Off |
| **Enable Custom Tooltip** | Custom-styled tooltips on hover. | Off |
| **Variation Label Separator** | Separator between selected variation labels. | " / " |
| **Swatch Width / Height** | Visual dimensions. | 40px / 40px |
| **Swatch Border Width** | Border thickness. | 1px |
| **Disabled Swatch Behavior** | How out-of-stock swatches appear. | Blur |
| **Tooltip Position** | Top or bottom. | Top |

---

## What Gets Affected

- Variable product pages: dropdowns replaced with swatches
- Archive pages (with the option enabled): swatches visible on shop/category pages
- Layered nav filters (with the option enabled): text filters replaced with swatch filters
- AJAX add-to-cart: works normally with swatches
- Variation selection: same behavior, but with visual swatches instead of text

## What Does NOT Get Affected

- Simple products (no variations): no swatches (the feature only applies to variable products)
- External/affiliate products: not affected
- Cart and checkout pages: unchanged
- Admin order details: still show the variation text (e.g., "Size: Medium"), not swatches

---

## Advanced Options (Developers)

This feature registers 4 WordPress hooks in `product-swatches.php`:

**Actions:**

- `wp_head` calls `CM_Product_Swatches::add_vertical_layout_style()` (Injects vertical layout CSS)
- `admin_enqueue_scripts` calls `CM_Product_Swatches_Assets::admin_enqueue_scripts()` (Enqueues admin swatches assets)
- `wp_enqueue_scripts` calls `CM_Product_Swatches_Assets::frontend_enqueue_scripts()` (Enqueues frontend swatches assets)

**Filters:**

- `woocommerce_dropdown_variation_attribute_options_html` calls `CM_Product_Swatches::replace_dropdown_with_swatches()` (Replaces dropdown with swatches (priority 10))

```php
// Hooked in product-swatches.php
add_filter( 'woocommerce_dropdown_variation_attribute_options_html', 'CM_Product_Swatches::replace_dropdown_with_swatches' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### Swatches are not appearing on the product page

**Cause:** The product is not a variable product, or the attribute has no values defined.
**Fix:** Verify the product type is "Variable product" and the product has at least one variation with the relevant attribute defined. Re-save the product to refresh the swatch display.

### Swatches appear but selecting them doesn't change the price or image

**Cause:** A JavaScript error or a theme conflict is preventing the variation change handler from running.
**Fix:** Disable other variation-related plugins (variation swatches, custom add-to-cart). Check the browser console for errors. Switch to a default theme (Twenty Twenty-Four) to test.

### The disabled swatch behavior isn't working as expected

**Cause:** The "Disabled Swatch Behavior" requires the product variations to have stock status set correctly.
**Fix:** Verify the variations are marked as "Out of stock" in WooCommerce > Products > edit variation. Re-save the product.

### Swatches are not styled (look like default dropdowns)

**Cause:** The swatch CSS is not loading due to a theme or plugin conflict.
**Fix:** Check the browser console for CSS 404 errors. Verify the Classic Monks framework CSS is loading. Disable other product page customizations.

### The tooltip text doesn't match the product

**Cause:** The tooltip text is the attribute value (e.g., "Red", "Blue"). If you want custom tooltips, use the "Enable Custom Tooltip" option and customize in the plugin settings.
**Fix:** Use the filter to map attribute values to custom tooltip text. For example, "Red" → "Crimson".

---

## Related Articles

- [How to Disable Out of Stock Variations in WordPress](woocommerce-disable-out-of-stock-variations.md)
- [How to Customize the Add to Cart Button in WordPress](woocommerce-customize-add-to-cart-button.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
