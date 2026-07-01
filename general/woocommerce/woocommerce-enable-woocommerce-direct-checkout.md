---
title: "How to Enable WooCommerce Direct Checkout Links in WordPress | CM"
slug: enable-woocommerce-direct-checkout
description: "Create direct checkout links for WooCommerce products in Classic Monks. Use SKU or product ID URL parameters to send customers straight to checkout with a product pre-added."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/enable-woocommerce-direct-checkout/
---

# How to Enable WooCommerce Direct Checkout Links in WordPress

> Enable WooCommerce Direct Checkout Links creates direct checkout links for products using SKU or product ID URL parameters. Send customers straight to checkout with a product pre-added, perfect for email campaigns and affiliate links.

## Key Takeaways

- Generate direct checkout links via URL parameters
- Use product SKU (e.g., `?sku=ABC123`) or product ID (`?product_id=456`)
- Customers land on checkout with the product pre-added
- Optional "Show Custom Quantity Generator" for custom quantities
- Useful for email campaigns, affiliate links, and conversion-optimized landing pages

## What Is the Enable WooCommerce Direct Checkout Links feature?

By default, clicking "Add to Cart" on a product page adds the product to the cart, but the customer still needs to navigate to checkout manually. The Enable WooCommerce Direct Checkout Links feature creates URLs that skip the product page entirely and send the customer straight to checkout with the product pre-added.

The feature supports two URL parameter formats:

- `?sku=ABC123` (using the product SKU)
- `?product_id=456` (using the product ID)

When a customer clicks a direct checkout link, the product is added to their cart and they're taken directly to the checkout page.

## Why You Need It

Direct checkout links are a conversion optimization tool:

- **Email campaigns**: Instead of "Buy Now" linking to the product page (which then requires another click to add to cart), use a direct checkout link
- **Affiliate links**: Affiliates can send customers straight to checkout with the product pre-added
- **Landing pages**: Custom landing pages can use direct checkout links to reduce friction
- **QR codes**: Physical marketing materials (business cards, flyers) with QR codes that link to direct checkout

For most stores, direct checkout links are a small but measurable conversion improvement.

---

## How to Enable WooCommerce Direct Checkout Links in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **One Click Checkout** subtab.

### Step 3: Enable WooCommerce Direct Checkout Links

Toggle on **Enable WooCommerce Direct Checkout Links**. Nested options expand.

### Step 4: (Optional) Show Custom Quantity Generator

Toggle on **Show Custom Quantity Generator** if you want customers to be able to set a custom quantity (e.g., for bulk orders).

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Create Direct Checkout Links

Use the URL format `https://yoursite.com/checkout/?sku=ABC123` or `https://yoursite.com/checkout/?product_id=456` (where ABC123 is the SKU and 456 is the product ID).

To get the SKU and product ID, edit the product in WooCommerce. The SKU is in the Product Data > Inventory section, and the ID is in the URL when editing the product.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable WooCommerce Direct Checkout Links** | Master toggle. | Off |
| **Show Custom Quantity Generator** | Custom quantity input. | Off |

No nested options.

---

## What Gets Affected

- The checkout page: direct checkout URLs add the product and skip the cart page
- Customer flow: the customer lands directly on checkout with the product pre-added
- The URL parameters: `?sku=` and `?product_id=` are recognized
- The cart: the product is added (the cart is updated, not replaced)

## What Does NOT Get Affected

- The product page (the standard "Add to Cart" button still works)
- The cart page (still shows the cart contents)
- The checkout process itself (the direct checkout just skips the intermediate steps)
- The product data (the SKU and product ID are standard WooCommerce fields)

---

## Advanced Options (Developers)

This feature registers 2 WordPress hooks in `direct-checkout-link.php`:

**Actions:**

- `wp_loaded` calls `CM_Direct_Checkout_Link::process_direct_checkout()` (Processes direct checkout link requests (priority 5))
- `add_meta_boxes` calls `CM_Direct_Checkout_Link::add_direct_checkout_metabox()` (Adds direct checkout metabox to products)

```php
// Hooked in direct-checkout-link.php
add_action( 'wp_loaded', 'CM_Direct_Checkout_Link::process_direct_checkout' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The direct checkout link doesn't work

**Cause:** The URL is malformed, the product doesn't exist, or the toggle is off.
**Fix:** Verify the toggle is on. Verify the SKU matches the product's SKU exactly (case-sensitive). Verify the product ID is correct. Test with a known product to isolate the issue.

### The customer lands on the cart page instead of checkout

**Cause:** The redirect is not configured correctly, or a plugin is overriding the flow.
**Fix:** Verify the redirect URL is the checkout page (not the cart page). Disable cart-related plugins to find the conflict.

### The product is not added to the cart

**Cause:** The SKU or product ID is invalid, or the product is out of stock.
**Fix:** Verify the SKU and product ID. Check the product's stock status. Test with a known in-stock product.

### The custom quantity is not working

**Cause:** The "Show Custom Quantity Generator" option is off, or a theme conflict.
**Fix:** Verify the option is on. Check that the URL includes the quantity parameter (e.g., `?sku=ABC123&quantity=3`).

---

## Related Articles

- [How to Enable the Checkout Product Selector in WordPress](woocommerce-enable-checkout-product-selector.md)
- [How to Show Custom Quantity Generator in WordPress](woocommerce-show-custom-quantity-generator.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
