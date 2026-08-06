---
title: "How to Remove the WooCommerce Status Box from the Dashboard"
slug: disable-woocommerce-status-meta-box
description: "Remove the WooCommerce status meta box from the WordPress dashboard so it stays clean and focused. Keep the whole admin tidy with one Classic Monks toggle."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-woocommerce-status-meta-box/
---

# How to Remove the WooCommerce Status Box from the Dashboard

> Remove the WooCommerce status meta box from the WordPress dashboard. Classic Monks keeps your dashboard clean by dropping the status widget when you do not use it.

## Key Takeaways

- Remove the WooCommerce status meta box from the dashboard
- Clear the dashboard of the built-in status widget
- One toggle, no nested options
- Does not affect WooCommerce itself or the shop
- Re-certify the dashboard area for the widgets you use

## What Does the Feature Do?

WooCommerce adds a status meta box to the WordPress dashboard that summarizes orders and stock. The **Disable WooCommerce Status Meta Box** feature removes that meta box from the dashboard, so it no longer appears among your dashboard widgets.

The change is cosmetic to the dashboard. It does not affect WooCommerce functionality, orders, products, or the shop.

## Why You Need It

The dashboard status widget may not suit everyone:

- A single-purpose store may not need the built-in summary
- Removing it frees the dashboard area for the widgets you use
- It reduces visual clutter for staff who track orders elsewhere
- It keeps the dashboard focused on the tools that matter to your workflow

---

## How to Disable the WooCommerce Status Meta Box

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Optimization** settings area.
3. Toggle on **Disable WooCommerce Status Meta Box**.

### Step 2: Save and Test

Click **Save Changes**. Open the WordPress dashboard and confirm the WooCommerce status meta box no longer appears.

---

## Configuration Options

| Option | Default |
|--------|---------|
| **Disable WooCommerce Status Meta Box** | Off |

There are no nested options. The feature is a single on/off control.

---

## What Gets Affected

- The WordPress dashboard: the WooCommerce status meta box is removed

## What Does NOT Get Affected

- WooCommerce actions, orders, products, and settings: fully functional
- The shop and checkout: unchanged
- Other dashboard widgets: unaffected

---

## Advanced Options (Developers)

The feature registers one hook in `functions/woocommerce/woocommerce-functions.php`:

```php
add_action( 'wp_dashboard_setup', 'cm_disable_woocommerce_status_meta_box' );
```

**`wp_dashboard_setup`** calls `cm_disable_woocommerce_status_meta_box()`, which runs `remove_meta_box('woocommerce_dashboard_status', 'dashboard', 'normal')` to drop the status widget from the dashboard.

---

## Common Use Cases

**Clean dashboards.** Stores that track orders through WooCommerce > Orders rather than the dashboard benefit from removing the summary widget.

**Focused staff.** Teams that only need specific dashboard widgets get a cleaner view.

**Custom dashboards.** When another dashboard solution is in use, the built-in status widget is redundant.

---

## Troubleshooting

### The status box is still showing

**Cause:** The toggle is off, or a theme re-adds the dashboard widget.
**Fix:** Confirm the toggle is on and reload the dashboard. If another plugin re-registers the status meta box, that plugin is independent of this feature.

### The status data is missing elsewhere

**Cause:** The feature removes the dashboard widget only; order and stock data remain available.
**Fix:** Verify totals in **WooCommerce > Orders** and the product inventory. The data is still stored and displayed there.

---

## Frequently Asked Questions

### What is the WooCommerce status meta box?

It is the dashboard widget WooCommerce adds with a summary of orders and stock. This feature removes it from the dashboard.

### Does it affect orders or products?

No. Only the dashboard widget is removed. Orders, products, and stock data remain fully available in their own admin screens.

### Can I bring it back?

Yes. Disable the toggle to restore the dashboard status widget.

---

## Keeping It Set Up

Set the toggle once and it stays active across the site. To change behavior, return to the WooCommerce settings, adjust the option, and save again. The store continues to run normally throughout, and you can turn the feature off at any time to restore the previous default behavior. For teams managing multiple environments, confirm the setting on staging first, then apply it to production and verify a real page load before treating it as live.

---

## Where the Data Still Lives

Removing the dashboard widget does not remove the underlying order and stock data. The same totals are available in the WooCommerce order list and product inventory screens. This makes the toggle a safe way to clean the dashboard without losing any reporting. Teams that track fulfillment through WooCommerce > Orders can use this to remove the redundant summary while keeping all the data they rely on intact.

---

## Related Articles

- [How to Disable WooCommerce Admin Features](woocommerce-disable-woocommerce-admin-features.md)
- [How to Remove All WooCommerce Notices](woocommerce-remove-all-woocommerce-notices.md)
- [How to Disable WooCommerce Scripts and Styles on Non-WooCommerce Pages](woocommerce-disable-woocommerce-scripts.md)
