---
title: "How to Turn Off WooCommerce Admin Features You Do Not Use"
slug: disable-woocommerce-admin-features
description: "Disable WooCommerce's admin analytics and marketing additions in the dashboard. Remove unused admin areas you do not need with a single Classic Monks toggle."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-woocommerce-admin-features/
---

# How to Turn Off WooCommerce Admin Features You Do Not Use

> Disable WooCommerce's admin experience features in the WordPress dashboard, including the analytics and marketing menu areas. Classic Monks removes the parts of the WooCommerce admin you do not use.

## Key Takeaways

- Disable WooCommerce's admin experience areas
- Remove the WooCommerce marketing menu items
- Clear the registered admin feature list
- One toggle, no nested options
- Does not affect the shop or products

## What Does the Feature Do?

WooCommerce adds admin areas for analytics and marketing on top of the core shop. The **Disable WooCommerce Admin Features** feature suppresses those admin experience additions:

- It disables the WooCommerce admin via WooCommerce's `woocommerce_admin_disabled` flag
- It empties the marketing menu items
- It clears WooCommerce's registered admin features

The core shop, products, orders, and settings remain available. Only the admin dashboard additions are suppressed.

## Why You Need It

Not every store uses the analytics and marketing admin areas:

- A lite or product-focused store may not need them
- Removing unused admin UI reduces visual clutter in the dashboard
- It keeps staff focused on the shop and orders
- It lightens the admin for sites that rely on other tools

---

## How to Disable WooCommerce Admin Features

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Optimization** settings area.
3. Toggle on **Disable WooCommerce Admin Features**.

### Step 2: Save and Test

Click **Save Changes**. Reload the WooCommerce admin area. The analytics and marketing dashboard additions the feature targets should no longer appear, while the shop and order management remain.

---

## Configuration Options

| Option | Default |
|--------|---------|
| **Disable WooCommerce Admin Features** | Off |

There are no nested options. The feature is a single on/off control.

---

## What Gets Affected

- WooCommerce's admin experience areas: suppressed
- The marketing menu items: removed from the WooCommerce admin
- The registered admin feature list: cleared

## What Does NOT Get Affected

- Products, orders, customers, and settings: fully available
- The shop and checkout on the front end: unchanged
- Other admin menus in WordPress outside the targeted WooCommerce additions: unaffected

---

## Advanced Options (Developers)

The feature registers its logic in `functions/woocommerce/woocommerce-functions.php`:

```php
add_filter( 'woocommerce_admin_disabled', '__return_true' );
add_filter( 'woocommerce_marketing_menu_items', '__return_empty_array' );
add_filter( 'woocommerce_admin_features', function (array $features): array {
    return [];
}, 90 );
```

When enabled, the feature sets WooCommerce's admin-disabled flag to true, clears the marketing menu, and returns an empty admin features list at priority 90.

---

## Common Use Cases

**Lite stores.** Stores that only sell through the shop do not need analytics and marketing admin areas.

**Staff focus.** Removing unused admin sections keeps the dashboard centered on orders and products.

**Single-purpose sites.** When the admin experience is handled elsewhere, suppressing the WooCommerce admin additions avoids duplication.

---

## Troubleshooting

### The admin features are still showing

**Cause:** The toggle is off, or WooCommerce re-registers the feature areas.
**Fix:** Confirm the toggle is on and reload the admin. If WooCommerce or another plugin re-adds the measures, that code runs in addition to this toggle.

### Products or orders disappear

**Cause:** The feature targets the admin dashboard additions, not the shop.
**Fix:** Confirm the shop and order management still appear. If core shop areas vanished, check for another cause, since this toggle only affects the admin features flagged as disabled.

### The marketing menu returns

**Cause:** A marketing extension may register its own menu item.
**Fix:** Extensions that re-add marketing menus are separate from the core marketing items this feature clears.

---

## Frequently Asked Questions

### What exactly gets disabled?

WooCommerce's admin experience additions: the analytics admin flag, the marketing menu items, and the registered admin feature list are all suppressed.

### Do products and orders still work?

Yes. The feature only removes the admin dashboard additions. The shop, products, orders, customers, and settings remain fully available.

### Is the front-end shop affected?

No. The shop, cart, checkout, and product pages are unchanged.

### Can I turn it back on?

Yes. Disable the toggle to restore WooCommerce's admin features.

---

## Keeping It Set Up

Set the toggle once and it stays active across the site. To change behavior, return to the WooCommerce settings, adjust the option, and save again. The store continues to run normally throughout, and you can turn the feature off at any time to restore the previous default behavior. For teams managing multiple environments, confirm the setting on staging first, then apply it to production and verify a real page load before treating it as live.

---

## Related Articles

- [How to Disable WooCommerce Scripts and Styles on Non-WooCommerce Pages](woocommerce-disable-woocommerce-scripts.md)
- [How to Disable WooCommerce Status Meta Box](woocommerce-disable-woocommerce-status-meta-box.md)
- [How to Remove All WooCommerce Notices](woocommerce-remove-all-woocommerce-notices.md)
