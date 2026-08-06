---
title: "How to Customize the Add to Cart Button Text in WooCommerce"
slug: customize-add-to-cart-button
description: "Change the WooCommerce add to cart button text per product type. Set wording for simple, variable, grouped, and external products, and choose where it applies."
last_updated: 2026-08-06
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/customize-add-to-cart-button/
---

# How to Customize the Add to Cart Button Text in WooCommerce

> Change the WooCommerce add to cart button text for each product type. Set distinct wording for simple, variable, grouped, and external products, and control whether the custom text applies on single product pages, product loops, or both.

## Key Takeaways

- Set custom add to cart text per product type: simple, variable, grouped, and external
- Control where it applies: single product pages, loops, or both
- Leave a field blank to fall back to that product type's default text
- Uses WooCommerce's standard text filters, so cart and checkout buttons are unchanged

## What Does the Feature Do?

The default add to cart button says "Add to Cart" everywhere, which does not always fit the product type. A variable product with options works better with "Select Options", a grouped product with "View Products", and an external or affiliate product with "Buy Product".

The **Customize Add to Cart Button Text** feature lets you set text per product type. It hooks into WooCommerce's add-to-cart text filters on both single product pages and product loops, replacing the default wording with your own when a field is filled in.

## Why You Need It

Clear, context-appropriate button text improves the purchase path:

- Digital products can use "Download Now" or "Get Instant Access"
- Variable products can use "Select Options" to signal choices come first
- Grouped products can use "View Products" to set expectations
- External or affiliate items can use "Buy Product" instead of a misleading cart label
- Consistent messaging across shop, category, and product pages builds trust

---

## How to Customize the Add to Cart Button Text in WooCommerce

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Single Product** settings area.
3. Toggle on **Customize Add to Cart Button Text**. The nested fields expand below the toggle.

### Step 2: Set the Text per Product Type

Fill in the button text for the product types you want to customize:

- **Simple Products Button Text**: text for simple products (default `Add to Cart`).
- **Variable Products Button Text**: text for variable products (default `Select Options`).
- **Grouped Products Button Text**: text for grouped products (default `View Products`).
- **External Products Button Text**: text for external/affiliate products (default `Buy Product`).

Leave a field blank to keep WooCommerce's default text for that product type.

### Step 3: Choose Where It Applies

- **Apply to Product Loops** (on by default) applies the custom text to shop, category, and archive pages.
- **Apply to Single Product Pages** (on by default) applies it to individual product pages.

Turn each on or off to control the scope.

### Step 4: Save and Test

Click **Save Changes**. Visit a single product page and a shop page, and confirm the button text matches what you set for each product type. Products whose type field is blank keep their default text.

---

## Configuration Options

| Option | Behavior | Default |
|--------|----------|---------|
| **Customize Add to Cart Button Text** | Master toggle. | Off |
| **Simple Products Button Text** | Text for simple products; blank uses default. | `Add to Cart` |
| **Variable Products Button Text** | Text for variable products; blank uses default. | `Select Options` |
| **Grouped Products Button Text** | Text for grouped products; blank uses default. | `View Products` |
| **External Products Button Text** | Text for external/affiliate products; blank uses default. | `Buy Product` |
| **Apply to Product Loops** | Use custom text on shop, category, and archive pages. | On |
| **Apply to Single Product Pages** | Use custom text on single product pages. | On |

---

## What Gets Affected

- The add to cart button on single product pages and product loops, per the scope toggles
- Product types with filled-in fields: simple, variable, grouped, and external

## What Does NOT Get Affected

- The cart and checkout buttons: those use separate WooCommerce buttons ("View cart", "Checkout")
- Button styling, icons, and AJAX add-to-cart behavior: only the text changes
- Product types with blank fields: these keep the default text
- Quick view modals or cart widget buttons from other plugins

---

## Advanced Options (Developers)

The feature registers hooks in `functions/woocommerce/woocommerce-functions.php`, gated on the **Customize Add to Cart Button Text** toggle and scope options:

```php
add_filter( 'woocommerce_product_single_add_to_cart_text', 'cm_custom_add_to_cart_text', 10, 2 );
add_filter( 'woocommerce_product_add_to_cart_text', 'cm_custom_add_to_cart_text', 10, 2 );
```

- **`woocommerce_product_single_add_to_cart_text`** is applied when **Apply to Single Product Pages** is on.
- **`woocommerce_product_add_to_cart_text`** is applied when **Apply to Product Loops** is on.

Both call `cm_custom_add_to_cart_text()` with priority 10 and two arguments. The function returns the configured text for the product type, or the default when the field is blank.

---

## Troubleshooting

### The custom text is not showing

**Cause:** The feature toggle is off, the product type's field is blank, or the relevant scope toggle (single or loop) is off.
**Fix:** Confirm **Customize Add to Cart Button Text** is on. Fill in the field for the product type you are testing, and make sure the scope (single or loop) that matches your page is enabled. Clear caches if a till-now-unchanged page shows old text.

### The text changes only on the product page, not loops

**Cause:** **Apply to Product Loops** is off.
**Fix:** Turn on **Apply to Product Loops** so the custom text also renders on shop, category, and archive pages.

### Variable products still say "Add to Cart"

**Cause:** The **Variable Products Button Text** field is blank.
**Fix:** Enter text in the **Variable Products Button Text** field (for example, `Select Options`). A blank field falls back to WooCommerce's default.

### The cart button is changing

**Cause:** A theme or another plugin may reuse the add-to-cart text on the cart page.
**Fix:** The feature targets WooCommerce's product add-to-cart text filters. If a cart button reflects your text, confirm the change originates from this customization and not a theme that mirrors the product button label.

---

## Frequently Asked Questions

### Can I set a different text for each product type?

Yes. Simple, variable, grouped, and external products each have their own text field under the feature, so you can tailor the wording per product type.

### What happens if I leave a text field blank?

The product type uses WooCommerce's default add to cart text. Each field is optional, so you can customize just the types that need it.

### Does this change the cart or checkout buttons?

No. The feature uses WooCommerce's product add-to-cart text filters, which only affect the add-to-cart button. The cart and checkout buttons are separate.

### Both scope options are on by default, is that right?

Yes. **Apply to Product Loops** and **Apply to Single Product Pages** both default to on, so your text is consistent across the shop and product pages. Turn an option off if you want the text only on one context.

### Do grouped or external products need special handling?

Grouped products often work best with "View Products" and external products with "Buy Product". Set their fields accordingly; leaving them blank keeps the defaults.

---

## Related Articles

- [How to Customize the Out of Stock Button in WooCommerce](woocommerce-customize-out-of-stock-button.md)
- [How to Add Variation Swatches to WooCommerce in WordPress](woocommerce-product-swatches.md)
- [How to Customize the Place Order Button in WooCommerce](woocommerce-custom-place-order-button.md)
