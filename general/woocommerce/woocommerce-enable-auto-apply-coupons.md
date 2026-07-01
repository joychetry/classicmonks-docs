---
title: "How to Enable Auto-Apply Coupons in WordPress | CM"
slug: enable-auto-apply-coupons
description: "Automatically apply eligible coupons in Classic Monks based on cart conditions. Prioritizes highest-value coupons, limits stack count, and supports optional notifications."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/enable-auto-apply-coupons/
---

# How to Enable Auto-Apply Coupons in WordPress

> Enable Auto-Apply Coupons automatically applies eligible coupons when cart conditions are met. Reduces customer friction by applying discounts without requiring coupon codes, with configurable prioritization and stack limits.

## Key Takeaways

- Single toggle, master switch for the feature
- 3 sub-options: prioritize highest value, show notifications, disable all notices
- Configurable maximum stack count (set on each coupon)
- Reduces cart abandonment (no need to find coupon codes)
- Customer-facing notifications confirm the auto-applied discount

## What Is the Enable Auto-Apply Coupons feature?

By default, customers must enter a coupon code at checkout to apply a discount. The Enable Auto-Apply Coupons feature automatically applies eligible coupons when cart conditions are met (e.g., cart total over $50, specific products in cart, specific user role).

This is a one-click conversion optimization: customers who qualify for a discount get it without having to know or enter a code.

## Why You Need It

Many customers abandon carts because they don't have a coupon code or don't know how to find one. Auto-apply solves this:

- **No friction**: Discounts are applied automatically when conditions are met
- **Higher conversion**: Customers see the discount applied without action
- **More revenue**: Customers who see a discount are more likely to complete checkout
- **Configurable control**: Per-coupon stack limits prevent coupon abuse

For most stores, auto-apply is a small but measurable conversion improvement.

---

## How to Enable Auto-Apply Coupons in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Coupons** subtab.

### Step 3: Enable Auto-Apply Coupons

Toggle on **Enable Auto-Apply Coupons**. Nested options expand.

### Step 4: Configure Sub-Options

The 3 sub-options include:

- **Prioritize Highest Value Coupons**: When multiple coupons match, apply the one with the highest discount
- **Show Auto-Apply Notifications**: Display a notice when a coupon is auto-applied
- **Disable All Coupon Notices**: Suppress all coupon-related notifications

### Step 5: Configure Individual Coupons

For each coupon that should be auto-applied, set the coupon's "Auto Apply" option in the coupon data. Also set the "Maximum Stack Count" if you want to limit how many of the same coupon can stack.

### Step 6: Save Changes

Click **Save Changes**.

### Step 7: Test

Add products to the cart that match a coupon's conditions. The coupon should apply automatically without entering a code.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Auto-Apply Coupons** | Master toggle. | Off |
| **Prioritize Highest Value Coupons** | When multiple match, apply the one with the highest discount. | Off |
| **Show Auto-Apply Notifications** | Display a notice when a coupon is auto-applied. | Off |
| **Disable All Coupon Notices** | Suppress all coupon-related notifications. | Off |

Per-coupon settings: "Auto Apply" toggle (in the coupon data) and "Maximum Stack Count" (in the coupon data).

---

## What Gets Affected

- The cart: eligible coupons are applied automatically when conditions are met
- The checkout: the discount appears in the order review
- The order total: includes the auto-applied discount
- The customer-facing notifications: show when a coupon is auto-applied (if enabled)

## What Does NOT Get Affected

- Manual coupon code entry: customers can still enter codes manually
- Coupon eligibility: determined by the coupon's existing restrictions (minimum spend, product restrictions, etc.)
- Coupon usage tracking: auto-applied coupons still count toward the usage limit
- The coupon's effect on the order: the auto-applied discount is the same as a manually-applied one

---

## Advanced Options (Developers)

This feature registers 3 WordPress hooks in `auto-apply-coupons.php`:

**Actions:**

- `woocommerce_cart_loaded_from_session` calls `cm_auto_apply_eligible_coupons()` (Auto-applies eligible coupons on cart load (priority 25))
- `add_meta_boxes` calls `cm_add_auto_apply_coupon_meta_box()` (Adds auto-apply metabox to coupons)
- `save_post_shop_coupon` calls `cm_save_auto_apply_coupon_meta_box()` (Saves auto-apply coupon settings)

```php
// Hooked in auto-apply-coupons.php
add_action( 'woocommerce_cart_loaded_from_session', 'cm_auto_apply_eligible_coupons' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The coupon is not being auto-applied

**Cause:** The toggle is off, the coupon's "Auto Apply" option is not set, or the cart does not match the coupon's conditions.
**Fix:** Verify the toggle is on. Edit the coupon and verify "Auto Apply" is set. Verify the cart meets the coupon's conditions (minimum spend, products, etc.).

### Multiple coupons are being applied but I want only one

**Cause:** Multiple coupons match and the stack count allows them.
**Fix:** Set "Maximum Stack Count" on each coupon to 1. Or use the "Prioritize Highest Value Coupons" option to apply only the best one.

### The auto-apply notification is annoying customers

**Cause:** The "Show Auto-Apply Notifications" option is on.
**Fix:** Disable the option. Or customize the message in the plugin settings.

### The coupon is auto-applied but I want it to require a code

**Cause:** The coupon's "Auto Apply" option is set.
**Fix:** Edit the coupon and disable "Auto Apply". The customer will need to enter the code manually.

---

## Related Articles

- [How to Enable Maximum Discount Amount in WordPress](woocommerce-enable-coupon-max-discount.md)
- [How to Enable URL Coupons in WordPress](woocommerce-enable-url-coupons.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
