---
title: "How to Enable User Role Coupon Restrictions in WordPress | CM"
slug: enable-user-role-restrictions
description: "Restrict WooCommerce coupons to specific user roles in Classic Monks. Includes WooCommerce customer roles and membership plugin compatibility."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/enable-user-role-restrictions/
---

# How to Enable User Role Coupon Restrictions in WordPress

> Enable User Role Coupon Restrictions restricts coupons to specific user roles. Supports WordPress roles, WooCommerce customer roles, and membership plugin compatibility for sophisticated audience targeting.

## Key Takeaways

- Single toggle, master switch for the feature
- 2 sub-options: include WooCommerce roles, membership plugin compatibility
- Per-coupon role restrictions (set in the coupon data)
- Supports role inheritance (e.g., "all customers" includes "wholesale_customer")
- Compatible with major membership plugins (MemberPress, Paid Memberships Pro, etc.)

## What Is the Enable User Role Coupon Restrictions feature?

WooCommerce coupons apply to all users by default. The Enable User Role Coupon Restrictions feature adds the ability to restrict coupons to specific user roles. A coupon can be set to apply only to "Wholesale customers" or "Subscribers" or any combination of roles.

The feature includes support for WooCommerce customer roles and membership plugin compatibility for sophisticated audience targeting.

## Why You Need It

For stores with different customer types, role-based coupon restrictions enable sophisticated promotions:

- **B2B / wholesale**: Restrict B2B-only discounts to wholesale customer roles
- **Membership tiers**: Restrict premium-member-only coupons to subscription tiers
- **Loyalty programs**: Restrict loyalty rewards to specific customer segments
- **VIP customers**: Restrict VIP-only discounts to specific roles

For most stores with multiple customer types, this is a high-ROI feature.

---

## How to Enable User Role Coupon Restrictions in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Coupons** subtab.

### Step 3: Enable User Role Coupon Restrictions

Toggle on **Enable User Role Coupon Restrictions**. Nested options expand.

### Step 4: Configure Sub-Options

The 2 sub-options include:

- **Include WooCommerce Roles**: Includes WooCommerce-specific customer roles (Customer, Shop Manager) alongside WordPress roles
- **Membership Plugin Compatibility**: Integrates with membership plugins (MemberPress, Paid Memberships Pro) for membership-level targeting

### Step 5: Configure Individual Coupons

For each coupon that should be role-restricted, set the "Allowed Roles" in the coupon data. Multiple roles can be selected.

### Step 6: Save Changes

Click **Save Changes**.

### Step 7: Test

Log in as different users with different roles. Verify the coupon applies only for the configured roles.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable User Role Coupon Restrictions** | Master toggle. | Off |
| **Include WooCommerce Roles** | Include WC customer roles. | Off |
| **Membership Plugin Compatibility** | Integrate with membership plugins. | Off |

Per-coupon settings: "Allowed Roles" multiselect in the coupon data.

---

## What Gets Affected

- The coupon application: the coupon only applies to the configured roles
- The cart validation: error message shown to users who don't have the required role
- The order processing: the discount is preserved if the user keeps the role
- The role inheritance: "all customers" includes both "customer" and "wholesale_customer"

## What Does NOT Get Affected

- The coupon's other restrictions (minimum spend, product restrictions, etc.)
- The customer's saved coupons (applied at the time of order)
- The order's role at the time of the order (if the customer's role changes later, the discount stays)
- Manual coupon code entry (the role check is applied at code entry)

---

## Advanced Options (Developers)

This feature registers 3 WordPress hooks in `user-role-coupon-restrictions.php`:

**Actions:**

- `add_meta_boxes` calls `cm_add_user_role_restriction_meta_box()` (Adds role restriction metabox to coupons)

**Filters:**

- `woocommerce_coupon_is_valid` calls `cm_validate_coupon_user_role()` (Validates coupon against user role (priority 10))
- `woocommerce_coupon_error` calls `cm_custom_user_role_error_message()` (Customizes error message for role-restricted coupons (priority 10))

```php
// Hooked in user-role-coupon-restrictions.php
add_filter( 'woocommerce_coupon_is_valid', 'cm_validate_coupon_user_role' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The role restriction is not working

**Cause:** The toggle is off, or the "Allowed Roles" is not set on the coupon.
**Fix:** Verify the toggle is on. Edit the coupon and verify the "Allowed Roles" is set (not empty).

### The wrong roles are being included

**Cause:** The role inheritance is not working as expected.
**Fix:** Configure in the plugin settings to customize the role check. For example, if you want "all wholesale customers" to include "wholesale_vip", add that logic.

### The membership plugin is not recognized

**Cause:** The "Membership Plugin Compatibility" option is off, or the membership plugin uses a different role structure.
**Fix:** Verify the option is on. Check the membership plugin's documentation for the role names it creates. Configure in the plugin settings to add custom logic for your specific plugin.

### The coupon is restricted to a role the user has, but the coupon still doesn't apply

**Cause:** A caching plugin is serving the old (unrestricted) calculation.
**Fix:** Clear all caching layers. The role check is applied at the time of coupon calculation, so caching can show the old result.

---

## Related Articles

- [How to Enable BOGO Deals in WordPress](woocommerce-enable-bogo-deals.md)
- [How to Enable First-Time Customer Coupons in WordPress](woocommerce-enable-first-time-customer-coupons.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
