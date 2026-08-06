---
title: "How to Show Product Images in the WooCommerce Checkout"
slug: show-product-images-checkout
description: "Show product thumbnails against each product in the WooCommerce checkout so customers confirm the order. Set the image size and style in Classic Monks."
last_updated: 2026-08-06
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/show-product-images-checkout/
---

# How to Show Product Images in the WooCommerce Checkout

> Show product images next to product names in the WooCommerce checkout so customers can confirm what they are buying. Control the image size, style, and dimensions with Classic Monks.

## Key Takeaways

- Show product thumbnails next to product names at checkout
- Choose a preset image size or use custom width and height
- Pick a style: square, rounded, or circle
- Adds visual confirmation in the order review section
- Works through WooCommerce's cart item name filter

## What Does the Feature Do?

By default, the WooCommerce checkout order review shows the product name and quantity but no image. The **Show Product Images in Checkout** feature adds a product thumbnail beside each product name in the checkout, giving customers a visual confirmation of what they are buying.

The thumbnail follows your image size and style settings, so you can match it to your design.

## Why You Need It

A visual confirmation at checkout reduces doubt and mistakes:

- Customers see the exact item they are buying, not just text
- They can catch a wrong product or variant before completing the order
- It strengthens confidence at the most sensitive step of the purchase
- On mobile, a small thumbnail helps verify the order quickly

---

## How to Show Product Images in the WooCommerce Checkout

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Checkout** settings area.
3. Toggle on **Show Product Images in Checkout**. The nested options expand below the toggle.

### Step 2: Choose the Image Size

Use **Image Size** to select a preset:

- **Small**, **Medium** (default), or **Large**

Or choose **Custom** and set **Custom Width (px)** and **Custom Height (px)**. Defaults for custom width and height are **72px** each.

### Step 3: Choose the Image Style

Use **Image Style** to set the thumbnail shape:

- **Square** (default)
- **Rounded**
- **Circle**

### Step 4: Save and Test

Click **Save Changes**. Add a product to the cart and open the checkout. Confirm the thumbnail appears beside each product name with the size and style you chose.

---

## Configuration Options

| Option | Behavior | Default |
|--------|----------|---------|
| **Show Product Images in Checkout** | Master toggle. | Off |
| **Image Size** | Small, Medium, Large, or Custom. | Medium |
| **Custom Width (px)** | Custom thumbnail width (shown when Image Size is Custom). | 72 |
| **Custom Height (px)** | Custom thumbnail height (shown when Image Size is Custom). | 72 |
| **Image Style** | Square, Rounded, or Circle. | Square |

---

## What Gets Affected

- The checkout order review: product thumbnails appear next to product names
- The cart item display in the checkout, per your size and style settings

## What Does NOT Get Affected

- The product's actual image data: WooCommerce continues to manage product images normally
- The cart page: this feature targets the checkout display
- Order totals and totals: only the product name content changes
- Admin order details: unaffected by the front-end checkout image

---

## How the Thumbnail Is Added

The feature hooks into WooCommerce's cart item name filter, so the thumbnail is prepended to the product name in the checkout. The image is rendered using the product's image and styled according to your size and style settings, with inline dimensions applied for custom sizes.

---

## Troubleshooting

### Product images are not showing

**Cause:** The feature toggle is off, the checkout is cached, or the theme renders product names in a way that bypasses the cart item name filter.
**Fix:** Confirm **Show Product Images in Checkout** is on and clear caches. If the theme uses a custom checkout summary, ensure it renders product names through the WooCommerce cart item name filter.

### The images are too small or too large

**Cause:** The **Image Size** preset or the custom dimensions do not match the layout.
**Fix:** Choose a different preset, or set **Image Size** to Custom and adjust **Custom Width (px)** and **Custom Height (px)**.

### The image style is not applying

**Cause:** The theme's CSS may override the thumbnail corners, or a cached stylesheet is served.
**Fix:** Confirm the style setting and clear caches. If a theme forces its own image styling, match the corners with additional CSS in the theme.

### Images appear for a variant but not the base product

**Cause:** The thumbnail uses the product's image. If the variant has its own image, that is shown; otherwise the parent image is used.
**Fix:** Confirm the product has an image set. For variations, set an image on the variation when you want a distinct thumbnail.

---

## Frequently Asked Questions

### Where do the images appear?

They appear next to product names in the checkout order review section.

### What image sizes can I use?

You can choose a preset size (Small, Medium, or Large) or set Custom width and height in pixels. The default preset is Medium, with 72px used for custom dimensions.

### Can I make the images rounded or circular?

Yes. **Image Style** offers Square, Rounded, and Circle shapes.

### Does this change the product's real image?

No. The feature only controls how the product's existing image is shown at checkout.

### Does it affect the cart page?

No. This feature targets the checkout display. Cart page images are handled separately by your theme.

---

## Related Articles

- [How to Customize the Order Review Heading in WooCommerce](woocommerce-custom-order-review-heading.md)
- [How to Customize the Place Order Button in WooCommerce](woocommerce-custom-place-order-button.md)
- [How to Set Up WooCommerce Coupon Auto-Apply in WordPress](woocommerce-enable-auto-apply-coupons.md)
