---
title: "How to Enable BOGO Deals in WordPress | CM"
slug: enable-bogo-deals
description: "Create Buy One Get One promotions in Classic Monks. Supports same-product BOGO, quantity scaling, and category-based offers."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/enable-bogo-deals/
---

# How to Enable BOGO Deals in WordPress

> Enable BOGO Deals creates Buy One Get One promotions in Classic Monks. Supports same-product BOGO, quantity scaling, and category-based offers for sophisticated promotional campaigns.

## Key Takeaways

- Single toggle, master switch for the feature
- 4 sub-options: same product, quantity scaling, category-based, cart messages
- Configurable BOGO discount amount (100% for free, 50% for half off, etc.)
- Auto-applies to cart when conditions are met
- Increases average order value through smart promotions

## What Is the Enable BOGO Deals feature?

The Enable BOGO Deals feature adds the ability to create Buy One Get One (BOGO) promotions. Common BOGO patterns supported:

- **Buy 1 Get 1 Free**: Customer adds 2 items, the second is free
- **Buy 2 Get 1 at 50% Off**: Customer adds 3 items, the cheapest is half off
- **Buy from Category A, Get from Category B**: Cross-category promotions (e.g., buy shoes, get socks free)
- **Quantity scaling**: Buy 2 get 1, buy 4 get 2 (scaling discount)

The BOGO is configured per coupon in the coupon data, with the "Enabled BOGO Deals" master toggle as a prerequisite.

## Why You Need It

BOGO promotions are a classic e-commerce tool for increasing average order value:

- **Encourages larger orders**: Customers add more items to get the deal
- **Clears inventory**: BOGO on slow-moving items moves stock
- **Increases perceived value**: Customers feel they're getting a deal
- **Simple to communicate**: "Buy 2 Get 1 Free" is clear and compelling

For most stores, BOGO is a high-ROI promotional tool.

---

## How to Enable BOGO Deals in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Coupons** subtab.

### Step 3: Enable BOGO Deals

Toggle on **Enable BOGO (Buy One Get One) Deals**. Nested options expand.

### Step 4: Configure Sub-Options

The 4 sub-options include:

- **Allow Same Product BOGO**: Customer can buy and get the same product (e.g., Buy 1 Get 1 Free on a specific product)
- **Enable Quantity Scaling**: BOGO scales with quantity (e.g., buy 2 get 1, buy 4 get 2)
- **Enable Category-Based BOGO**: Buy from one category, get from another
- **Show Cart Messages**: Display informational messages in the cart about active BOGO deals

### Step 5: Configure Individual BOGO Coupons

For each BOGO coupon, configure the BOGO settings in the coupon data:

- The products the BOGO applies to
- The discount amount (100% for free, 50% for half off, etc.)
- The quantity thresholds (buy 1, get 1 free / buy 2, get 1 free / etc.)

### Step 6: Save Changes

Click **Save Changes**.

### Step 7: Test

Add the BOGO products to the cart. The discount should apply automatically.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable BOGO (Buy One Get One) Deals** | Master toggle. | Off |
| **Allow Same Product BOGO** | Customer can buy and get the same product. | Off |
| **Enable Quantity Scaling** | BOGO scales with quantity. | Off |
| **Enable Category-Based BOGO** | Cross-category promotions. | Off |
| **Show Cart Messages** | Informational messages in cart. | Off |

Per-coupon settings: products, discount amount, quantity thresholds (all configured in the coupon data).

---

## What Gets Affected

- The cart: BOGO discounts apply automatically when conditions are met
- The checkout: the discount appears in the order review
- The cart messages: informational messages show the available BOGO deal
- The order total: includes the BOGO discount

## What Does NOT Get Affected

- The customer's saved coupons: not affected by BOGO
- Other coupons: BOGO can stack with other coupons (if the coupon allows stacking)
- The product data: the products and prices are unchanged
- The cart page display: BOGO may or may not show depending on the theme

---

## Advanced Options (Developers)

This feature registers 4 WordPress hooks in `bogo-deals.php`:

**Actions:**

- `woocommerce_cart_loaded_from_session` calls `cm_validate_bogo_coupons()` (Validates BOGO coupons on cart load (priority 20))
- `woocommerce_before_single_product_summary` calls `cm_display_bogo_product_badge()` (Displays BOGO badge on product page (priority 15))

**Filters:**

- `woocommerce_coupon_discount_types` calls `cm_add_bogo_discount_type()` (Registers BOGO discount type)
- `woocommerce_coupon_get_discount_amount` calls `cm_bogo_coupon_discount_amount()` (Calculates BOGO discount amount (priority 10))

```php
// Hooked in bogo-deals.php
add_filter( 'woocommerce_coupon_discount_types', 'cm_add_bogo_discount_type' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The BOGO is not being applied

**Cause:** The toggle is off, the coupon's BOGO is not configured, or the cart does not meet the BOGO conditions.
**Fix:** Verify the toggle is on. Edit the coupon and verify the BOGO settings are configured. Verify the cart has the required products and quantity.

### The BOGO discount is wrong

**Cause:** The discount amount is misconfigured.
**Fix:** Edit the coupon and verify the discount amount. For "Buy 1 Get 1 Free", set the discount to 100%. For "Buy 2 Get 1 at 50% Off", set the discount to 50%.

### The customer is getting the BOGO on the wrong products

**Cause:** The BOGO product selection is misconfigured.
**Fix:** Edit the coupon and verify which products are eligible for the BOGO. The "Allow Same Product BOGO" option must be enabled for same-product BOGO to work.

### The cart messages are showing but the BOGO isn't applying

**Cause:** The cart messages are showing but the BOGO calculation is failing.
**Fix:** Verify the BOGO conditions (quantity, products). Check the browser console for JavaScript errors. Disable other cart-related plugins to find the conflict.

---

## Related Articles

- [How to Enable First-Time Customer Coupons in WordPress](woocommerce-enable-first-time-customer-coupons.md)
- [How to Enable Auto-Apply Coupons in WordPress](woocommerce-enable-auto-apply-coupons.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
