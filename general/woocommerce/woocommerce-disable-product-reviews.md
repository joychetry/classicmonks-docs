---
title: "How to Disable Product Reviews in WordPress | CM"
slug: disable-product-reviews
description: "Completely disable the WooCommerce product review system in Classic Monks. Removes review forms and review displays from product pages."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-product-reviews/
---

# How to Disable Product Reviews in WordPress

> Disable Product Reviews removes the WooCommerce product review system entirely. Review forms, review displays, and the reviews tab on product pages are all removed.

## Key Takeaways

- Single toggle, site-wide effect
- Removes review submission forms from product pages
- Removes review displays from product pages
- Removes the "Reviews" tab on single product pages
- Existing reviews are preserved in the database (not deleted)

## What Is the Disable Product Reviews feature?

WooCommerce's built-in review system allows customers to leave star ratings and text reviews on products. This feature completely suppresses the review system:

- The "Reviews" tab on single product pages is hidden
- The review submission form is removed
- Existing reviews are no longer displayed on the front-end
- The "Verified owner" review label is hidden

The raw review data (post type `review`) is preserved in the database. Disabling the display does not delete the data.

## Why You Need It

Most stores benefit from reviews, but some use cases don't:

- **B2B / wholesale**: Reviews are for B2C, not for B2B
- **Service businesses**: The product page is for showcasing the service, not for reviews
- **Digital products**: Reviews of digital products (e.g., "great PDF!") are low-value
- **Curated catalogs**: Stores that curate products (rather than sell them) don't need reviews
- **Spam reduction**: Removing the review form eliminates a major spam entry point

For most consumer e-commerce stores, leave reviews enabled. For other business models, this feature simplifies the product page.

---

## How to Disable Product Reviews in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Single Product** subtab.

### Step 3: Enable Disable Product Reviews

Scroll to **Disable Product Reviews** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit any product on the front-end. The Reviews tab should not appear. The review submission form should not be visible.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable Product Reviews** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

| Element | Before | After |
|---------|--------|-------|
| Reviews tab on product page | Visible | Hidden |
| Review submission form | Visible | Hidden |
| Existing review displays | Visible | Hidden |
| Star ratings in product meta | Visible | Hidden |
| Review count in product loop | Visible | Hidden |
| Admin > WooCommerce > Reviews menu | Visible | Hidden |
| Reviews data in the database | Stored | Preserved (not deleted) |

## What Does NOT Get Affected

- Existing review data in the database: not deleted
- Product reviews imported from other sources: still in the database
- The "Reviews" admin menu: hidden in the WP admin, but the data is preserved
- Comment system on regular WordPress posts: not affected (this is product reviews only)

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Actions:**

- `init` calls `cm_disable_woocommerce_reviews()` (Disables WooCommerce product reviews)

```php
// Hooked in woocommerce-functions.php
add_action( 'init', 'cm_disable_woocommerce_reviews' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### Reviews are still showing on the front-end

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the toggle is on. Clear all caching layers. The reviews display is server-side, so caching is the most common cause.

### The Reviews tab is still visible in the admin

**Cause:** The Reviews admin menu is hidden when the toggle is on, but the toggle may not be applying to the admin menu.
**Fix:** Verify the toggle is on. Hard-refresh the admin page. If still visible, the admin menu filter may need to be added (this feature is integrated with the standard WooCommerce reviews admin).

### Existing reviews are still showing as a count

**Cause:** The review count in the product loop is fetched from the database. Disabling the toggle hides the form and display, but the count is still calculated.
**Fix:** If you want the count to also be hidden, disable the reviews count display in the plugin settings under WooCommerce.

### I want to re-enable reviews for a specific product

**Cause:** The toggle is site-wide, not per-product.
**Fix:** Disable the toggle and use a different mechanism to hide reviews on specific products. Or use the `woocommerce_product_reviews_enabled` filter (see Advanced Options).

---

## Related Articles

- [How to Allow Duplicate Reviews in WordPress](woocommerce-allow-duplicate-reviews.md)
- [How to Customize the Add to Cart Button Text in WooCommerce](woocommerce-customize-add-to-cart-button.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
