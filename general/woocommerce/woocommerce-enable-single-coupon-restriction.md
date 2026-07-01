---
title: "How to Enable Single Coupon Restriction in WordPress | CM"
slug: woocommerce/enable-single-coupon-restriction
description: "Restrict the cart to only one coupon at a time in Classic Monks. Configure which coupon takes priority when multiple are applied."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/woocommerce/enable-single-coupon-restriction/
---

# How to Enable Single Coupon Restriction in WordPress

> Enable Single Coupon Restriction restricts the cart to only one coupon at a time. Prevents coupon stacking abuse and simplifies discount management.

## Key Takeaways

- Single toggle, no nested options
- Replaces any previously applied coupon when a new one is entered
- Prevents multiple coupons from stacking
- Simplifies the customer experience (one discount, clear messaging)
- Reduces profit margin loss from accidental stacking

## What Is the Enable Single Coupon Restriction feature?

WooCommerce allows multiple coupons to be applied to a single cart. For most stores, this is undesirable:

- A 20% off + 10% off + free shipping = 28%+ discount, which can erode profit margins
- Coupon stacking is often a result of confusion (customers apply a new code without removing the old)
- Stacking complicates the customer experience (multiple discount lines, unclear final price)

The Enable Single Coupon Restriction feature prevents coupon stacking by automatically removing the previously-applied coupon when a new one is entered.

## Why You Need It

Coupon stacking is a common problem:

- **Profit margin protection**: A 20%+10%+shipping discount can be devastating on low-margin items
- **Coupon abuse prevention**: Users who find or share stacking coupons can get excessive discounts
- **Customer clarity**: One discount is easier to understand than multiple stacked discounts

For most stores, the single coupon restriction is a small but high-ROI feature.

---

## How to Enable Single Coupon Restriction in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Coupons** subtab.

### Step 3: Enable Single Coupon Restriction

Toggle on **Enable Single Coupon Restriction**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Add a coupon to the cart. Then add a second coupon. The first should be removed automatically.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Single Coupon Restriction** | Master toggle. | Off |

No nested options. The behavior is simple: one coupon at a time, newest replaces oldest.

---

## What Gets Affected

- The cart: only one coupon can be applied at a time
- The coupon application: a new coupon replaces the existing one
- The cart messages: only one "Coupon applied" message is shown
- The order total: reflects the single applied coupon

## What Does NOT Get Affected

- The coupons themselves: each coupon code is unchanged
- The customer's saved coupons: not affected
- The coupon eligibility: each coupon's restrictions are still applied
- The coupon usage tracking: each coupon is still counted toward its usage limit

---

## Advanced Options (Developers)

This feature registers 3 WordPress hooks in `single-coupon-restriction.php`:

**Actions:**

- `woocommerce_before_cart` calls `cm_restrict_to_single_coupon()` (Enforces single coupon restriction in cart (priority 10))
- `woocommerce_before_checkout_form` calls `cm_restrict_to_single_coupon()` (Enforces single coupon restriction in checkout (priority 10))
- `woocommerce_applied_coupon` calls `cm_handle_coupon_applied()` (Handles coupon application with single restriction (priority 10))

```php
// Hooked in single-coupon-restriction.php
add_action( 'woocommerce_before_cart', 'cm_restrict_to_single_coupon' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### A coupon is not being applied because the previous one is still there

**Cause:** The previous coupon has a higher priority (e.g., it's a percent-off and the new one is fixed-amount).
**Fix:** Configure in the plugin settings to customize the priority. The default behavior is to always replace; if you want to keep the higher-discount one, customize the filter.

### The customer sees a confusing error message

**Cause:** The default error message when a coupon is replaced may be too technical.
**Fix:** Configure in the plugin settings to customize the message. Make it clear and customer-friendly.

### Two coupons need to stack (e.g., free shipping + 10% off)

**Cause:** The single coupon restriction prevents stacking.
**Fix:** Configure in the plugin settings to allow specific coupon pairs to stack. Add the combination of coupon codes to the allowed list.

### The replacement is not happening

**Cause:** A caching plugin is serving the old coupon calculation.
**Fix:** Clear all caching layers. The replacement happens at the time of coupon application, so caching can show the old result.

---

## Related Articles

- [How to Enable Auto-Apply Coupons in WordPress](woocommerce-enable-auto-apply-coupons.md)
- [How to Enable Maximum Discount Amount in WordPress](woocommerce-enable-coupon-max-discount.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
