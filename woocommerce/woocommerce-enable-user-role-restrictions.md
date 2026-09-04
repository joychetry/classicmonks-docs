---
title: "How to Restrict Coupons by User Role in WooCommerce"
slug: enable-user-role-restrictions
description: "Restrict WooCommerce coupons to specific user roles with Classic Monks. Set ANY/ALL role logic, control guest access, and add membership plugin compatibility."
last_updated: 2026-08-06
author: Joy
reading_time: 5 min
canonical: https://classicmonks.com/docs/enable-user-role-restrictions/
---

# How to Restrict WooCommerce Coupons by User Role in WordPress

> Restrict a WooCommerce coupon so only customers with certain user roles can use it. Choose ANY or ALL role logic, decide how guests are handled, include WooCommerce roles, and enable membership plugin compatibility.

## Key Takeaways

- Limit a coupon to one or more specific user roles
- Choose ANY (user has at least one role) or ALL (user has every role) logic
- Control whether guests can use role-restricted coupons
- Optionally include WooCommerce roles and membership plugin roles
- Ideal for wholesale, VIP, employee, and membership-tier offers

## What Are WooCommerce User Role Coupon Restrictions?

WooCommerce coupons apply to everyone by default. The Classic Monks **Enable User Role Coupon Restrictions** feature lets you confine a coupon to specific user roles, so only a logged-in user with the required role can redeem it. This powers B2B, wholesale, VIP, employee, and membership-tier pricing.

When you enable the feature, the coupon editor gains a **User Role Restrictions** section where you select which roles may use the coupon.

## Why You Need It

Role-restricted coupons enforce audience targeting at checkout:

- **B2B and wholesale.** Offer wholesale pricing only to wholesale-customer roles, keeping public pricing intact for retail buyers.
- **Membership tiers.** Give premium members exclusive codes that casual visitors cannot redeem.
- **VIP and loyalty.** Restrict elite offers to your best customers' roles.
- **Employee and partner offers.** Issue internal discounts that are unusable by outsiders.
- **Segment cleanup.** Prevent a broad public coupon from being reused by audiences it was not meant for.

---

## How to Restrict WooCommerce Coupons by User Role in WordPress

### Step 1: Enable the Feature

1. Open **Classic Monks** in your WordPress admin sidebar.
2. Open the **WooCommerce** tab.
3. Open the **Coupons** subtab.
4. Toggle on **Enable User Role Coupon Restrictions**. The nested options expand below the toggle.

### Step 2: Configure the Role Logic

- **Multiple Role Logic** controls how coupons restricted to several roles behave:
  - **User has ANY of the selected roles** (default): the customer only needs to belong to one of the selected roles.
  - **User has ALL of the selected roles**: the customer must belong to every selected role.

### Step 3: Configure the Guest Policy

- **Guest User Policy** decides what happens for non-logged-in users:
  - **Deny role-restricted coupons for guests** (default): guests cannot use coupons that have a role restriction.
  - **Allow unrestricted coupons only for guests**: guests may still use coupons that have no role restriction.
  - **Treat guests as Customer role**: guests are treated as if they hold the default Customer role.

### Step 4: Include Extra Roles

- **Include WooCommerce Roles** (On by default) automatically adds WooCommerce-specific roles (Customer, Shop Manager) to the role-selection list alongside the default WordPress roles.
- **Membership Plugin Compatibility** (Off by default) adds support for popular membership plugins such as WooCommerce Memberships and Paid Memberships Pro, exposing their membership levels in the role list.

### Step 5: Assign Roles to a Coupon

1. Go to **WooCommerce > Coupons** and open the coupon.
2. In the **User Role Restrictions** section, select which roles may use the coupon.
3. Save the coupon.

### Step 6: Save Changes and Test

Click **Save Changes** in the Classic Monks settings. Log in as a user in one of the allowed roles and confirm the coupon applies; log out (or log in as a disallowed role) and confirm it does not.

---

## Configuration Options

| Option | Behavior | Default |
|--------|----------|---------|
| **Enable User Role Coupon Restrictions** | Master toggle for the feature. | Off |
| **Multiple Role Logic** | ANY of the selected roles, or ALL of the selected roles. | ANY |
| **Guest User Policy** | Deny role-restricted coupons for guests, allow unrestricted only, or treat guests as Customer. | Deny role-restricted coupons for guests |
| **Include WooCommerce Roles** | Add Customer, Shop Manager, and other WooCommerce roles to the role list. | On |
| **Membership Plugin Compatibility** | Expose membership levels from supported plugins in the role list. | Off |

Per-coupon, the **User Role Restrictions** section lists which roles can redeem that coupon.

---

## What Gets Affected

- Coupon validity: a coupon only applies for users holding an allowed role
- Cart validation: users without the required role get a coupon error at application
- Order processing: the discount is preserved as long as the user keeps the qualifying role
- Guest behavior: controlled by the guest policy setting, ranging from deny to treat-as-customer

## What Does NOT Get Affected

- The coupon's other restrictions: minimum spend, product, category, and usage limits still apply
- Coupons with no role selected: such coupons behave as before
- Existing orders: changing a role later does not retroactively alter a past order's discount
- Manual code entry mechanics: the role check happens when the coupon is validated, regardless of how it was entered

---

## Advanced Options (Developers)

The feature registers its hooks in `functions/woocommerce/coupons/user-role-coupon-restrictions.php`:

```php
add_filter( 'woocommerce_coupon_is_valid', 'cm_validate_coupon_user_role', 10, 2 );
add_action( 'woocommerce_coupon_validate_usage_restrictions', 'cm_validate_coupon_user_role_usage', 10, 2 );
add_filter( 'woocommerce_coupon_error', 'cm_custom_user_role_error_message', 10, 3 );

add_action( 'add_meta_boxes', 'cm_add_user_role_restriction_meta_box' );
add_action( 'save_post', 'cm_save_user_role_restriction_meta_box' );
```

- **`woocommerce_coupon_is_valid`** runs `cm_validate_coupon_user_role()` to enforce the role check when a coupon is validated.
- **`woocommerce_coupon_validate_usage_restrictions`** runs a parallel usage restriction check.
- **`woocommerce_coupon_error`** customizes the error message shown to users who lack the required role.
- When membership compatibility is on, `init` sets up `cm_setup_membership_compatibility()` (priority 20), and hooks on `wc_memberships_user_membership_status_changed` and `pmpro_after_change_membership_level` clear the role cache when a membership changes.
- `woocommerce_new_order` and `woocommerce_order_status_completed` clear the customer status cache.

---

## Common Use Cases

**Wholesale-only pricing.** Restrict a wholesale coupon to the `wholesale_customer` role so trade buyers get their rate while retail customers see standard prices. Use **Include WooCommerce Roles** to make sure custom wholesale roles register in the list.

**VIP and loyalty tiers.** Issue role-restricted coupons for a `vip_customer` role, so only your highest-value members redeem elite offers. Use ANY logic if a VIP might hold multiple qualifying roles.

**Employee and partner discounts.** Give staff and partners a dedicated role and a coupon restricted to it, so the discount is unusable outside the team.

**Membership gating.** With **Membership Plugin Compatibility** on, tie a coupon to a paid membership level so only active members redeem it, and depend on the membership-change hooks to keep access current.

**Guest control.** If your B2B coupons should never reach anonymous visitors, keep the default **Deny role-restricted coupons for guests** policy so a shared link cannot be redeemed by a non-logged-in shopper.

---

## Troubleshooting

### The role-restricted coupon is not applying for an allowed user

**Cause:** The coupon's role list is empty, the user's role is not selected, or the guest policy blocks it.
**Fix:** Confirm the coupon has at least one role selected in **User Role Restrictions**. Verify the logged-in user actually holds that exact role. If the user is a guest, check **Guest User Policy**.

### A guest can use a coupon I restricted

**Cause:** **Guest User Policy** is set to allow, or the coupon has no role selected.
**Fix:** Set **Guest User Policy** to Deny role-restricted coupons for guests. Make sure the coupon actually has roles selected (an empty list means no restriction).

### My custom wholesale or membership role does not appear

**Cause:** **Include WooCommerce Roles** or **Membership Plugin Compatibility** is off, or the role is registered elsewhere.
**Fix:** Turn on **Include WooCommerce Roles** for WooCommerce roles and **Membership Plugin Compatibility** for membership levels. If the role is from a custom plugin, check it appears in the role selector; otherwise the feature's supported-list may not include it.

### The coupon fails for a user who should qualify under ANY logic

**Cause:** The coupon is set to ALL logic and the user does not hold every selected role.
**Fix:** Confirm **Multiple Role Logic** matches the intent. For "user has at least one of these roles," choose **User has ANY of the selected roles**.

---

## Frequently Asked Questions

### Do I have to restrict every coupon?

No. Role restrictions are per coupon. A coupon with no roles selected in **User Role Restrictions** is unrestricted and available to everyone as before.

### What is the difference between ANY and ALL role logic?

ANY means the user needs just one of the listed roles. ALL means the user must hold every listed role at once, which is rarer and only useful when a customer can simultaneously occupy multiple qualifying roles.

### Can guests use a role-restricted coupon?

Only if **Guest User Policy** allows it. The default denies role-restricted coupons to guests; you can instead let guests use only unrestricted coupons, or treat them as the Customer role.

### Do I need a user-role plugin to use this?

No. The feature reads standard WordPress and WooCommerce user roles. A membership plugin is only needed if you want to target membership levels, and enabling **Membership Plugin Compatibility** handles that.

### Will existing saved coupons be affected?

No. Enabling the feature does not change existing coupons until you edit each one and select its allowed roles.

---

## Related Articles

- [How to Set Up WooCommerce Coupon Auto-Apply in WordPress](woocommerce-enable-auto-apply-coupons.md)
- [How to Create BOGO (Buy One Get One) Deals in WooCommerce](woocommerce-enable-bogo-deals.md)
- [How to Offer Rewards to New Customers in WooCommerce](woocommerce-enable-first-time-customer-coupons.md)
