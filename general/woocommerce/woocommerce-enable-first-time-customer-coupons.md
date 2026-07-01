---
title: "How to Enable First-Time Customer Coupons in WordPress | CM"
slug: enable-first-time-customer-coupons
description: "Automatically reward new customers with welcome coupons in Classic Monks. Configurable welcome email with subject, body, and unique code generation."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/enable-first-time-customer-coupons/
---

# How to Enable First-Time Customer Coupons in WordPress

> Enable First-Time Customer Coupons automatically rewards new customers with welcome coupons. Configurable welcome email, unique code generation, and option to exclude sale items for clean welcome promotions.

## Key Takeaways

- Single toggle, master switch for the feature
- 3 sub-options: send welcome email, generate unique codes, exclude sale items
- Configurable welcome email subject and body
- Automatic detection of first-time customers
- Improves new customer acquisition and conversion

## What Is the Enable First-Time Customer Coupons feature?

The Enable First-Time Customer Coupons feature automatically detects new customers (customers who have never placed an order before) and applies a welcome coupon to their first order. The feature includes:

- A welcome email with the coupon code (optional, but recommended)
- Unique code generation per customer (optional, for security)
- Option to exclude sale items (to prevent stacking discounts)

The coupon is configured as a normal WooCommerce coupon with the "First-Time Customer" trigger enabled.

## Why You Need It

First-time customer coupons are a proven conversion tool:

- **Incentivizes first purchase**: Customers who receive a welcome coupon are more likely to complete their first order
- **Sets customer expectations**: A good first-purchase experience leads to repeat business
- **Reduces cart abandonment**: First-time customers often abandon due to sticker shock; a welcome coupon eases this
- **Builds customer loyalty**: A welcome gesture creates goodwill

For most stores, first-time customer coupons are a small but high-ROI feature.

---

## How to Enable First-Time Customer Coupons in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Coupons** subtab.

### Step 3: Enable First-Time Customer Coupons

Toggle on **Enable First-Time Customer Coupons**. Nested options expand.

### Step 4: Configure Sub-Options

The 3 sub-options include:

- **Send Welcome Email**: Send the welcome coupon email to the new customer
- **Generate Unique Coupon Codes**: Create a unique code per customer (for security and tracking)
- **Exclude Sale Items**: Prevent the welcome coupon from being used on already-discounted sale items

### Step 5: Configure the Welcome Coupon

Create or edit a coupon in WooCommerce > Coupons. Set:

- Discount type and amount (e.g., 15% off, or $10 off)
- Usage limit (typically 1 per customer)
- Enable the "First-Time Customer" trigger (in the Classic Monks coupon meta)

### Step 6: Configure Welcome Email

Edit the email subject and body (in the coupon meta or in the plugin settings under WooCommerce > First-Time Customer Coupons).

### Step 7: Save Changes

Click **Save Changes**.

### Step 8: Test

Create a new customer account and place a first order. The coupon should apply automatically, and the welcome email should be sent.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable First-Time Customer Coupons** | Master toggle. | Off |
| **Send Welcome Email** | Send welcome email to new customer. | Off |
| **Generate Unique Coupon Codes** | Unique code per customer. | Off |
| **Exclude Sale Items** | Prevent use on sale items. | Off |

Per-coupon settings: discount type, amount, usage limit, and the "First-Time Customer" trigger (in the coupon meta).

---

## What Gets Affected

- The first order for a new customer: the welcome coupon is applied automatically
- The welcome email: sent to the new customer with the coupon code
- The coupon usage tracking: counts toward the coupon's usage limit
- The customer account: the coupon is associated with the customer (if "Generate Unique Codes" is enabled)

## What Does NOT Get Affected

- The customer's subsequent orders: only the first order gets the welcome coupon
- The customer's existing coupons: not affected
- Other coupons: can stack with the welcome coupon (if the coupon allows stacking)
- The customer's saved payment methods: not affected

---

## Advanced Options (Developers)

This feature registers 3 WordPress hooks in `first-time-customer-coupons.php`:

**Actions:**

- `woocommerce_created_customer` calls `cm_handle_customer_registration()` (Handles customer registration for welcome coupon (priority 10))
- `init` calls `cm_handle_first_visit()` (Tracks first visit for welcome coupon)
- `wp_footer` calls `cm_display_welcome_coupon_popup()` (Displays welcome coupon popup)

```php
// Hooked in first-time-customer-coupons.php
add_action( 'woocommerce_created_customer', 'cm_handle_customer_registration' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The welcome coupon is not being applied

**Cause:** The toggle is off, the coupon is not configured for first-time customers, or the customer has placed orders before.
**Fix:** Verify the toggle is on. Edit the coupon and verify the "First-Time Customer" trigger is enabled. Use a new customer account to test.

### The welcome email is not being sent

**Cause:** The "Send Welcome Email" sub-option is off, or the email is being filtered by another plugin.
**Fix:** Verify the sub-option is on. Check the email logs (WooCommerce > Status > Logs) for errors. Disable email-related plugins to find the conflict.

### The coupon is applied but the customer has placed orders before

**Cause:** The customer detection is based on order history. A customer with completed orders is not "first-time".
**Fix:** Use a fresh customer account to test. For existing customers, manually send them a coupon (the welcome coupon is for new customers only).

### The unique coupon code is not working

**Cause:** The "Generate Unique Coupon Codes" sub-option is off, or the coupon generation is failing.
**Fix:** Verify the sub-option is on. Check the WordPress error log for any issues during coupon generation.

### The welcome coupon is being applied to sale items

**Cause:** The "Exclude Sale Items" sub-option is off.
**Fix:** Verify the sub-option is on. The coupon will then skip items that are on sale.

---

## Related Articles

- [How to Enable BOGO Deals in WordPress](woocommerce-enable-bogo-deals.md)
- [How to Enable Auto-Apply Coupons in WordPress](woocommerce-enable-auto-apply-coupons.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
