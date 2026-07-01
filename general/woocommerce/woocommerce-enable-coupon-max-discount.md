---
title: "How to Enable Maximum Coupon Discount in WordPress | CM"
slug: woocommerce/enable-coupon-max-discount
description: "Cap coupon discounts in Classic Monks with the Maximum Discount Amount feature. Supports time-based, role-based, category-specific, and tiered limits."
last_updated: 2026-06-24
author: Joy
reading_time: 5 min
canonical: https://classicmonks.com/docs/woocommerce/enable-coupon-max-discount/
---

# How to Enable Maximum Coupon Discount in WordPress

> Enable Maximum Discount Amount caps coupon discounts in Classic Monks. Protects profit margins with time-based, role-based, category-specific, and tiered limits on how much a coupon can discount.

## Key Takeaways

- Single toggle, master switch for the feature
- 6 sub-options for different limit types (time, role, category, tiered, analytics, preview)
- Caps the discount amount that any single coupon can apply
- Protects profit margins while still allowing flexible promotions
- Real-time admin preview for testing limits

## What Is the Enable Maximum Discount Amount feature?

WooCommerce coupons apply their discount without limits. If a coupon says "20% off" and the cart total is $1000, the discount is $200. For high-value carts, this can erode profit margins.

The Enable Maximum Discount Amount feature caps the discount at a configured limit. The coupon's calculated discount is applied up to the limit; the customer pays the cart total minus the capped discount.

## Why You Need It

For stores with high-value products, unlimited coupon discounts are a risk:

- **Profit margin protection**: A 50% off coupon on a $5000 order is a $2500 loss
- **Promotional control**: Different limits for different times (e.g., higher limits during sales) or customer types
- **Abuse prevention**: Limits prevent coupon abuse by limiting the maximum benefit

For most stores with high-value products, this is a high-ROI feature.

---

## How to Enable Maximum Discount Amount in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Coupons** subtab.

### Step 3: Enable Maximum Discount Amount

Toggle on **Enable Maximum Discount Amount for Coupons**. Nested options expand.

### Step 4: Configure the Limit Type

The 6 sub-options control the limit behavior:

- **Enable Time-Based Maximum Discounts**: Set time-of-day or day-of-week limits
- **Enable Role-Based Maximum Discounts**: Different limits per user role
- **Enable Category-Specific Maximum Discounts**: Different limits per product category
- **Enable Tiered Maximum Discounts**: Different limits based on cart total (e.g., $50 cap for carts under $100, $100 cap for carts over $100)
- **Enable Maximum Discount Analytics**: Track how often limits are hit
- **Enable Real-Time Discount Preview**: Show the admin a preview of the capped discount

### Step 5: Set the Global Maximum

Use the coupon edit screen to set a maximum discount amount per coupon. The Maximum Discount Amount metabox is added to the coupon data.

### Step 6: Save Changes

Click **Save Changes**.

### Step 7: Test

Add a product to cart, apply a coupon, and verify the discount is capped at the configured limit.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Maximum Discount Amount for Coupons** | Master toggle. | Off |
| **Enable Time-Based Maximum Discounts** | Time-of-day or day-of-week limits. | Off |
| **Enable Role-Based Maximum Discounts** | Per-role limits. | Off |
| **Enable Category-Specific Maximum Discounts** | Per-category limits. | Off |
| **Enable Tiered Maximum Discounts** | Cart-total-based limits. | Off |
| **Enable Maximum Discount Analytics** | Track limit hits. | Off |
| **Enable Real-Time Discount Preview** | Admin preview. | Off |

The actual maximum discount amount is set per coupon in the coupon edit screen.

---

## What Gets Affected

- Coupon application: the discount is capped at the configured maximum
- The cart total: the customer pays the capped amount (not the full coupon discount)
- The order total: reflects the capped discount
- The order meta: includes the original and capped discount amounts (for audit)

## What Does NOT Get Affected

- The coupon code itself: the code is unchanged
- The coupon's discount percentage or fixed amount: unchanged
- The coupon's other conditions (minimum spend, product restrictions, etc.): unchanged
- The customer's cart UI: the discount line shows the capped amount (not the original)

---

## Advanced Options (Developers)

This feature registers 3 WordPress hooks in `coupon-max-discount.php`:

**Actions:**

- `add_meta_boxes` calls `cm_add_max_discount_coupon_meta_box()` (Adds max discount metabox to coupons)

**Filters:**

- `woocommerce_coupon_get_discount_amount` calls `cm_coupon_apply_max_discount_limit()` (Applies max discount limit to coupon (priority 10))
- `woocommerce_coupon_is_valid` calls `cm_coupon_validate_max_discount()` (Validates coupon max discount limit (priority 10))

```php
// Hooked in coupon-max-discount.php
add_filter( 'woocommerce_coupon_get_discount_amount', 'cm_coupon_apply_max_discount_limit' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The maximum discount is not being applied

**Cause:** The toggle is off, or no maximum is set for the specific coupon.
**Fix:** Verify the toggle is on. Edit the coupon and set a maximum discount amount in the Maximum Discount Amount metabox.

### The maximum is too low

**Cause:** The maximum is set lower than the actual coupon discount.
**Fix:** Edit the coupon and increase the maximum discount amount. The cap is per-coupon, so you can set different caps for different coupons.

### The maximum is too restrictive

**Cause:** The maximum is set very low, blocking otherwise valid coupons.
**Fix:** Edit the coupon and increase the maximum. Use the "Enable Real-Time Discount Preview" option to see the capped discount before saving.

### The maximum is set but not respected

**Cause:** A caching plugin is serving the old discount calculation.
**Fix:** Clear all caching layers. The maximum is applied at the time of coupon calculation, so caching can show the old (uncapped) amount.

---

## Related Articles

- [How to Enable Auto-Apply Coupons in WordPress](woocommerce-enable-auto-apply-coupons.md)
- [How to Enable URL Coupons in WordPress](woocommerce-enable-url-coupons.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
