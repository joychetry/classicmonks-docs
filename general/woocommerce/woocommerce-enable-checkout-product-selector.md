---
title: "How to Enable the Checkout Product Selector in WordPress | CM"
slug: woocommerce/enable-checkout-product-selector
description: "Add a product selector widget to the WooCommerce checkout page in Classic Monks. Enables last-minute product additions and supports variable product pricing."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/woocommerce/enable-checkout-product-selector/
---

# How to Enable the Checkout Product Selector in WordPress

> Enable Checkout Product Selector adds a product selector widget to the WooCommerce checkout page. Customers can add last-minute products (upsells, accessories, gift wrapping) without leaving the checkout flow.

## Key Takeaways

- Add a product selector widget to the checkout page
- Show prices on the selector (optional)
- Support variable products in the selector (optional)
- Optional "show custom quantity generator" (custom product adder)
- Increases average order value through last-minute upsells

## What Is the Enable Checkout Product Selector feature?

By default, the WooCommerce checkout page only shows the items already in the cart. The Enable Checkout Product Selector feature adds a widget to the checkout that lets customers:

- Browse additional products (upsells, accessories, gift wrapping)
- Add them to their current order
- See prices (if the "Show Product Prices" option is enabled)
- Choose variations (if the "Enable Variable Product Support" option is enabled)

This is a one-click upsell widget that can increase average order value.

## Why You Need It

Many e-commerce sites have products that customers often add at the last minute (gift wrapping, expedited shipping, related accessories). The Enable Checkout Product Selector feature provides a frictionless way for customers to add these:

- **Increased average order value**: Last-minute upsells convert well because the customer is already in a buying mood
- **Reduced checkout abandonment**: Customers who add last-minute products are less likely to abandon the order
- **Better customer experience**: One-page shopping without leaving the checkout flow

For most e-commerce stores, this is a conversion optimization worth implementing.

---

## How to Enable the Checkout Product Selector in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **One Click Checkout** subtab.

### Step 3: Enable Checkout Product Selector

Toggle on **Enable Checkout Product Selector**. Nested options expand.

### Step 4: Configure Sub-Options

The 2 sub-options include:

- **Show Product Prices**: Display prices next to the products in the selector
- **Enable Variable Product Support**: Allow variable products (with variation dropdowns) in the selector

### Step 5: (Optional) Add Custom Quantity Generator

If you want customers to be able to add custom quantities (e.g., for bulk orders), also enable the separate "Show Custom Quantity Generator" toggle.

### Step 6: Save Changes

Click **Save Changes**.

### Step 7: Test

Visit the checkout page. The product selector should be visible. Try adding a product to the order without leaving checkout.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Checkout Product Selector** | Master toggle. | Off |
| **Show Product Prices** | Display prices in the selector. | Off |
| **Enable Variable Product Support** | Allow variable products in the selector. | Off |

Related toggle: **Show Custom Quantity Generator** allows customers to add custom quantities (e.g., for bulk orders).

---

## What Gets Affected

- The checkout page: a product selector widget appears
- Customer flow: customers can add products to the order without leaving checkout
- The cart: the new products are added to the existing cart (not a separate order)
- The order review: shows all products (original + new)

## What Does NOT Get Affected

- The product data (the products in the selector are regular WooCommerce products)
- The cart page (different display)
- The checkout process itself (the selector is additive, not a replacement)
- Other checkout widgets (the selector is added to the existing checkout)

---

## Advanced Options (Developers)

This feature registers 3 WordPress hooks in `checkout-product-selector.php`:

**Actions:**

- `add_meta_boxes` calls `WC_Checkout_Product_Selector::add_checkout_selection_metabox()` (Adds product selector metabox)
- `wp_enqueue_scripts` calls `WC_Checkout_Product_Selector::enqueue_checkout_scripts()` (Enqueues checkout selector scripts)
- `wp_ajax_wc_checkout_product_selector` calls `WC_Checkout_Product_Selector::handle_product_selection()` (AJAX handler for product selection)

```php
// Hooked in checkout-product-selector.php
add_action( 'add_meta_boxes', 'WC_Checkout_Product_Selector::add_checkout_selection_metabox' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The product selector is not showing

**Cause:** The toggle is off, or the theme is not compatible.
**Fix:** Verify the toggle is on. The selector requires a theme that uses WooCommerce's standard checkout hooks. If the theme uses a custom checkout, the selector may not appear.

### The selector is showing products that are already in the cart

**Cause:** The default behavior shows all products.
**Fix:** Configure in the plugin settings to hide products already in the cart.

### The selector is showing variable products but the variation dropdown is not working

**Cause:** The "Enable Variable Product Support" option is off, or a theme conflict.
**Fix:** Verify the option is on. Variable products require variation dropdowns; some themes may not render these correctly on the checkout page.

### The selector is showing too many products

**Cause:** The default query returns all published products.
**Fix:** Configure in the plugin settings to limit which products appear (e.g., by category, by tag, by stock status).

---

## Related Articles

- [How to Enable WooCommerce Direct Checkout Links in WordPress](woocommerce-enable-woocommerce-direct-checkout.md)
- [How to Show Custom Quantity Generator in WordPress](woocommerce-show-custom-quantity-generator.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
