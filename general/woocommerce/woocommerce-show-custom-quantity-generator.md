---
title: "How to Show Custom Quantity Generator in WordPress | CM"
slug: woocommerce/show-custom-quantity-generator
description: "Display a custom quantity input on the WooCommerce direct checkout page in Classic Monks. Lets customers set custom quantities (e.g., for bulk orders) when using direct checkout links."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/woocommerce/show-custom-quantity-generator/
---

# How to Show Custom Quantity Generator in WordPress

> Show Custom Quantity Generator adds a custom quantity input on the direct checkout page. Useful for bulk orders or when customers need to specify a non-default quantity. Works in combination with WooCommerce Direct Checkout Links.

## Key Takeaways

- Sub-option of [Enable WooCommerce Direct Checkout Links](woocommerce-enable-woocommerce-direct-checkout.md)
- Displays a quantity input on the direct checkout page
- Useful for bulk orders, B2B, or any case where customers need a custom quantity
- Single toggle, no nested options

## What Is the Show Custom Quantity Generator feature?

When customers use a WooCommerce Direct Checkout link (e.g., `?sku=ABC123`), they typically land on the checkout page with the product pre-added at quantity 1. The Show Custom Quantity Generator feature adds a quantity input to the direct checkout page, so customers can adjust the quantity before completing checkout.

This is a sub-option of the [Enable WooCommerce Direct Checkout Links](woocommerce-enable-woocommerce-direct-checkout.md) master toggle.

## Why You Need It

For B2B and bulk-order use cases, the default quantity 1 is rarely correct:

- **Wholesale orders**: Customers often need 10, 50, or 100 units
- **Bulk promotions**: "Buy 10 for $X" requires the customer to set quantity
- **Custom orders**: Some products are sold in configurable quantities
- **Gifts and bundles**: Customers may want to buy multiple of the same item

The Show Custom Quantity Generator feature provides a simple quantity input for these cases.

---

## How to Show Custom Quantity Generator in WordPress

### Step 1: Enable WooCommerce Direct Checkout Links

First, enable the master toggle. Go to **WooCommerce > One Click Checkout** and toggle on **Enable WooCommerce Direct Checkout Links**.

### Step 2: Enable Show Custom Quantity Generator

In the same section, toggle on **Show Custom Quantity Generator**. The option appears below the master toggle.

### Step 3: Save Changes

Click **Save Changes**.

### Step 4: Test

Create a direct checkout link: `https://yoursite.com/checkout/?sku=ABC123`. Click the link. The checkout page should show a quantity input that lets you change the quantity before placing the order.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Show Custom Quantity Generator** | Master toggle. | Off |

The master toggle [Enable WooCommerce Direct Checkout Links](woocommerce-enable-woocommerce-direct-checkout.md) must also be on for this to take effect.

---

## What Gets Affected

- The direct checkout page: a quantity input is shown
- The customer's ability to set custom quantities before placing the order
- The cart: the custom quantity is added to the cart

## What Does NOT Get Affected

- The standard checkout page (without the direct checkout link): the quantity input is NOT shown
- The product page: the standard quantity input is still used
- The cart page: the standard cart is still used
- The customer's saved addresses or payment methods: not affected

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Actions:**

- `wp_footer` calls the quantity generator script injection (Injects quantity generator JS)

```php
// Hooked in woocommerce-functions.php
// Quantity generator JS is injected via wp_footer
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The quantity input is not showing

**Cause:** The toggle is off, or the master toggle (Enable WooCommerce Direct Checkout Links) is also off.
**Fix:** Verify both toggles are on. The quantity input only appears on the direct checkout page, not the standard checkout page.

### The quantity input is showing but the cart doesn't update

**Cause:** A theme or plugin conflict is preventing the quantity change from being captured.
**Fix:** Verify the form is submitting correctly. Check the browser console for errors. Disable other cart-related plugins to find the conflict.

### The quantity input allows invalid values (e.g., negative numbers, decimals)

**Cause:** The default WooCommerce quantity input has built-in validation. Some custom inputs may not enforce this.
**Fix:** Configure in the plugin settings to add HTML5 validation (e.g., `min="1"`, `step="1"`).

### The quantity input shows on all checkout pages, not just direct checkout

**Cause:** The hook is firing on all checkout pages, not just the direct checkout page.
**Fix:** Check the request parameters to verify the direct checkout link is being used. Configure in the plugin settings to restrict to direct checkout only.

---

## Related Articles

- [How to Enable WooCommerce Direct Checkout Links in WordPress](woocommerce-enable-woocommerce-direct-checkout.md)
- [How to Enable the Checkout Product Selector in WordPress](woocommerce-enable-checkout-product-selector.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
