---
title: "How to Disable Product Reviews on Your WooCommerce Store"
slug: disable-product-reviews
description: "Remove comment support from WooCommerce products so customers cannot leave or see reviews. Disable the whole review system with a Classic Monks toggle."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-product-reviews/
---

# How to Disable Product Reviews on Your WooCommerce Store

> Disable product reviews across the store by removing comment support from WooCommerce products. Customers can no longer leave reviews on product pages, and existing review areas stop being shown.

## Key Takeaways

- Remove comment support from WooCommerce products
- Hide product review forms and displays
- One toggle, no nested options
- Works at the product post type level
- Store and product data are unaffected

## What Does the Feature Do?

WooCommerce products support comments, which power the product review system. The **Disable Product Reviews** feature removes comment support from the product post type, so the review areas are no longer shown on product pages.

Because the change is at the product post type level, it applies across the whole store rather than product by product.

## Why You Need It

Reviews are not right for every store:

- Some catalogs do not use customer reviews
- Removing reviews hides the review form and display on product pages
- It reduces moderation and spam load
- It keeps product pages focused on the purchase

---

## How to Disable Product Reviews in WooCommerce

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Single Product** settings area.
3. Toggle on **Disable Product Reviews**.

### Step 2: Save and Test

Click **Save Changes**. Open a product page and confirm the review form and review display no longer appear.

---

## Configuration Options

| Option | Default |
|--------|---------|
| **Disable Product Reviews** | Off |

There are no nested options. The feature is a single on/off control.

---

## What Gets Affected

- Product pages: the review form and review display are removed
- The product post type: comment support is removed
- Reviews across the store: the review areas are hidden

## What Does NOT Get Affected

- Product data, prices, and inventory: unchanged
- The store's products and checkout: unaffected
- Existing stored reviews: not deleted, just no longer shown in the product review area
- Regular WordPress comments on posts: separate from product reviews

---

## Advanced Options (Developers)

The feature registers one hook in `functions/woocommerce/woocommerce-functions.php`:

```php
add_action( 'init', 'cm_disable_woocommerce_reviews' );
```

**`init`** calls `cm_disable_woocommerce_reviews()`, which runs `remove_post_type_support('product', 'comments')`. This removes comment support from the product post type, so the review areas no longer render.

---

## Common Use Cases

**Curated catalogs.** Stores that do not use customer reviews keep product pages focused on the sale.

**Spam reduction.** Removing the review form eliminates a spam entry point.

**Consistent product pages.** A store that never enables reviews can show the same clean layout on every product.

---

## Troubleshooting

### Reviews are still showing

**Cause:** The toggle is off, or a theme renders a reviews section from its own template.
**Fix:** Confirm the toggle is on and clear caches. If the theme adds a reviews section independently of WooCommerce comment support, it may render regardless.

### The review form is gone but old reviews remain

**Cause:** The feature hides the review areas but does not delete stored reviews.
**Fix:** This is expected. The review data stays in the database; it is simply no longer displayed through the product review area.

### I want to re-enable reviews

**Cause:** The toggle is on.
**Fix:** Turn the toggle off to restore comment support to products.

---

## Frequently Asked Questions

### What does disabling reviews do?

It removes comment support from the product post type, so the review form and review display are no longer shown on product pages.

### Are existing reviews deleted?

No. Stored reviews remain in the database. They are just no longer displayed through the product review area.

### Does it affect regular blog comments?

No. This targets the product post type. Standard WordPress post comments are separate.

### Is it on by default?

No. The feature is off until you enable the toggle.

---

## Re-Enabling Reviews

The feature can be reversed at any time. Turning the toggle off restores comment support to the product post type, so the review form and review display come back on product pages. Because the stored reviews are never deleted, re-enabling returns the previous review data to view alongside any new reviews. This makes the toggle safe to try: it removes the review areas now, and a later flip brings them back with the existing content intact.

---

## Related Articles

- [How to Allow Multiple Reviews on a Product in WooCommerce](woocommerce-allow-duplicate-reviews.md)
- [How to Customize the Add to Cart Button Text in WooCommerce](woocommerce-customize-add-to-cart-button.md)
- [How to Customize the Out of Stock Button in WooCommerce](woocommerce-customize-out-of-stock-button.md)
