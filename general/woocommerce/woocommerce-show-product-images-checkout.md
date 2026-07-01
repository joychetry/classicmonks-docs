---
title: "How to Show Product Images in WooCommerce Checkout in WordPress | CM"
slug: show-product-images-checkout
description: "Display product images on the WooCommerce checkout page in Classic Monks. Configurable size, style, and dimensions for visual purchase confirmation."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/show-product-images-checkout/
---

# How to Show Product Images in WooCommerce Checkout in WordPress

> Show Product Images in Checkout displays product images on the WooCommerce checkout page next to product names. Configurable size, style, and dimensions for visual purchase confirmation.

## Key Takeaways

- Display product images next to product names in checkout
- Configurable image size (thumbnail, medium, large, custom)
- Configurable style (rounded, square, circle, hidden border, etc.)
- Custom width and height options
- Improves customer confidence through visual confirmation

## What Is the Show Product Images in Checkout feature?

By default, the WooCommerce checkout page shows the product name and quantity, but no product image. Customers see "Product Name × 2" in the order review, but no visual representation.

The Show Product Images in Checkout feature adds the product image next to the product name in the checkout. The image appears in the order review section.

## Why You Need It

Showing product images at checkout improves the customer experience:

- **Visual confirmation**: Customers see what they're buying, reducing "wait, what did I order?" anxiety
- **Reduces cart abandonment**: Visual reinforcement at the critical conversion moment
- **Better mobile experience**: On mobile, the small product thumbnails help customers verify their order
- **Reduces order errors**: Customers can catch a mistake (wrong size, wrong product) before completing checkout

For most e-commerce stores, this is a small but high-impact UX improvement.

---

## How to Show Product Images in WooCommerce Checkout in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Checkout** subtab.

### Step 3: Enable Show Product Images in Checkout

Toggle on **Show Product Images in Checkout**. Nested options expand.

### Step 4: Configure Image Settings

The 4 sub-options include:

- **Image Width**: Custom pixel width (default 50px)
- **Image Height**: Custom pixel height (default 50px)
- **Image Size**: Thumbnail, medium, large, or full (uses the WordPress image sizes)
- **Image Style**: Rounded corners, square, circle, hidden border, etc.

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Test

Add a product to cart and proceed to checkout. The product image should appear in the order review section.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Show Product Images in Checkout** | Master toggle. | Off |
| **Image Width** | Custom pixel width. | 50px |
| **Image Height** | Custom pixel height. | 50px |
| **Image Size** | Thumbnail, medium, large, or full. | Thumbnail |
| **Image Style** | Rounded, square, circle, hidden border. | Square |

---

## What Gets Affected

- The order review section on the checkout page: product images appear next to product names
- The "Thank you" order confirmation page: product images also appear (depending on the theme)
- The email order confirmation: product images appear in the order summary (depending on the email template)
- The CSS class on the image: based on the Image Style option (used for theme-specific styling)

## What Does NOT Get Affected

- The product image in the cart page (separate feature, may need additional customization)
- The product image in the order review on the order confirmation page (theme-dependent)
- The product image in the admin order details
- The product's actual image data (WooCommerce standard image handling)

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Filters:**

- `woocommerce_cart_item_name` calls `cm_add_checkout_product_thumbnail()` (Adds product thumbnail to checkout (priority 10))

```php
// Hooked in woocommerce-functions.php
add_filter( 'woocommerce_cart_item_name', 'cm_add_checkout_product_thumbnail' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### Product images are not showing

**Cause:** The toggle is off, or the theme is not displaying the order review section in a compatible way.
**Fix:** Verify the toggle is on. Check that the theme's checkout template uses WooCommerce's standard `woocommerce_checkout_order_review` action (most themes do).

### The images are too small or too large

**Cause:** The Image Width and Image Height settings may not match the theme's container.
**Fix:** Adjust the Width and Height values. The default 50x50 works for most themes, but some themes may need different values.

### The image style is not applying

**Cause:** The theme's CSS is overriding the Custom Monks styles.
**Fix:** Inspect the rendered image in the browser's DevTools. Verify the class is present. If it is but the styles don't apply, your theme has higher-specificity CSS. Add `!important` to the theme's CSS (as a last resort).

### The image is showing for virtual products (where it shouldn't)

**Cause:** The default behavior shows the image for all product types.
**Fix:** Configure in the plugin settings to hide the image for specific product types (e.g., virtual, downloadable).

---

## Related Articles

- [How to Customize the Order Review Heading in WordPress](woocommerce-custom-order-review-heading.md)
- [How to Customize the Place Order Button in WordPress](woocommerce-custom-place-order-button.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
