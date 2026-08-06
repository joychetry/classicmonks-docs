---
title: "How to Create Custom Order Statuses in WooCommerce"
slug: enable-custom-order-status
description: "Add and manage custom order statuses in WooCommerce with Classic Monks. Define statuses with labels and keys to track your order workflow beyond the defaults."
last_updated: 2026-08-06
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/enable-custom-order-status/
---

# How to Create Custom Order Statuses in WooCommerce

> Create custom order statuses in WooCommerce to track steps that the default statuses do not cover, such as "Awaiting Materials", "In Production", or "Pending Approval". Define each status with a label and key in the Classic Monks Orders settings.

## Key Takeaways

- Add unlimited custom order statuses to the WooCommerce order workflow
- Create each status with a display label and a lowercase, hyphenated key
- Registered statuses appear in the order Status dropdown and the orders list
- Removes statuses you no longer need from the saved list
- Built into the standard WooCommerce order workflow, not a separate system

## What Does Custom Order Status Do?

WooCommerce ships with a fixed set of order statuses: pending payment, processing, on hold, completed, cancelled, refunded, and failed. For many businesses that is not granular enough. A furniture maker tracks orders through "Awaiting Materials", "In Production", and "Quality Check". A service business needs "Scheduled" and "In Progress". A B2B workflow wants "Pending Approval" and "Invoiced".

The Classic Monks **Enable Custom Order Status** feature lets you define your own statuses. Each status is registered with WooCommerce so it appears wherever order statuses are used: the order edit screen, the orders list, and the status dropdown.

Custom statuses work within the standard WooCommerce order workflow rather than as a separate system, so they integrate with how you already manage orders.

---

## When to Enable It

Enable Custom Order Status when the default statuses do not match how your store actually fulfills orders:

- Manufacturing and production workflows that need staging steps
- Service and appointment businesses that track scheduling and progress
- B2B flows with approval or invoicing milestones
- Any workflow where "Processing" and "Completed" are too coarse

Keep it off if the default WooCommerce statuses already cover your process.

---

## How to Add Custom Order Statuses in WooCommerce

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Orders** settings area.
3. Toggle on **Enable Custom Order Status**. The nested add-status form expands below the toggle.

### Step 2: Add a Status

1. In **Status Label**, enter the name that appears in the orders list (for example, `In Production`).
2. In **Status Key**, enter a lowercase, hyphenated identifier (for example, `in-production`).
3. Click **Add Status**.

The status is saved to the Custom Order Statuses list and registered with WooCommerce.

### Step 3: Use the Status

Edit an order and open the **Status** dropdown. Your custom status appears there alongside the defaults. Select it and the order moves to the new status.

### Step 4: Remove a Status

In the Custom Order Statuses list, click the remove button next to a status to delete it. The status is removed from the saved list and no longer registered.

---

## Configuration Details

| Item | What it controls | Default |
|------|------------------|---------|
| **Enable Custom Order Status** | Master toggle. | Off |
| **Status Label** | The name shown in the orders list and status dropdown (for example, `In Production`). | Blank |
| **Status Key** | Lowercase, hyphenated identifier registered with WooCommerce (for example, `in-production`). | Blank |

- The **Status Key** must use lowercase letters and hyphens only.
- Each saved status stores a label and is registered as a `wc-<key>` status.
- The add form lives in the Classic Monks **Orders** settings; there is no separate page.

---

## What Gets Affected

- The order edit screen: **Status** dropdown includes your custom statuses
- The orders list: custom statuses are shown and filterable in the **Status** column
- Order reports and admin lists: registered statuses appear in status counts
- The saved custom-status list: shows every currently configured status

## What Does NOT Get Affected

- The default WooCommerce statuses: these stay unchanged
- Existing orders: enabling the feature does not reassign any order
- Customer-facing order displays: custom statuses are registered admin-side; extending them to customer-facing emails or pages requires additional template or hook work
- Other plugins' status systems: the feature adds statuses into WooCommerce's own statuses; plugins with separate status systems are unaffected

---

## Advanced Options (Developers)

The feature registers its statuses and hooks in `functions/woocommerce/woo-orders.php`:

```php
add_filter( 'woocommerce_register_shop_order_post_statuses', 'cm_register_custom_order_status' );
add_filter( 'wc_order_statuses', 'cm_add_custom_order_status_dropdown' );
add_action( 'init', 'cm_register_custom_status_with_wc' );
```

- **`woocommerce_register_shop_order_post_statuses`** calls `cm_register_custom_order_status()` to add each saved status to WooCommerce's registered order statuses. Each entry is registered with `public => true`, `show_in_admin_all_list => true`, and `show_in_admin_status_list => true`.
- **`wc_order_statuses`** calls `cm_add_custom_order_status_dropdown()` to add the custom status labels to the status dropdown.
- **`init`** calls `cm_register_custom_status_with_wc()`, which runs `register_post_status('wc-<key>', ...)` for each saved status so it is fully recognized by WordPress and WooCommerce.

All three functions gate on the **Enable Custom Order Status** toggle and the saved `cm_custom_order_statuses` option. If either is empty, they return unchanged.

---

## Troubleshooting

### A custom status is not showing in the order edit page

**Cause:** The master toggle is off, the status is not in the saved list, or the status key is invalid.
**Fix:** Confirm **Enable Custom Order Status** is on and the status appears in the **Custom Order Statuses** list. Verify the **Status Key** uses lowercase letters and hyphens only (for example, `in-production`), then re-add the status.

### A status is missing from the orders list

**Cause:** The status was removed from the saved list, or the toggle is off so it is not registered.
**Fix:** Re-add the status in the Orders settings and confirm the toggle is on. Registered statuses honor `show_in_admin_status_list => true`, so a present status should appear.

### The status dropdown cuts off or loses a status

**Cause:** A status was deleted, or the key does not match what you expect.
**Fix:** Open the **Custom Order Statuses** list and add the status again with a clean, lowercase, hyphenated key. Remove any duplicate keys.

### Orders do not change automatically to a custom status

**Cause:** Custom statuses are applied manually through the order's **Status** dropdown; no automatic transition is configured.
**Fix:** Select the custom status in the order editor when moving an order. If you want an automatic trigger, handle it with a hook (for example, `woocommerce_order_status_<key>`) rather than relying on the feature.

---

## Frequently Asked Questions

### Can I create as many custom order statuses as I want?

Yes. There is no fixed limit. Each status you add is saved to the Custom Order Statuses list and registered with WooCommerce using a unique lowercase, hyphenated key.

### What should the status key look like?

The key uses lowercase letters and hyphens only, for example `in-production` or `awaiting-materials`. It becomes the `wc-<key>` identifier that WooCommerce and any hooks use to reference the status.

### Do custom statuses affect the default WooCommerce statuses?

No. Enabling the feature adds new statuses; it does not change or remove the defaults. Existing orders keep whatever status they already have.

### Can customers see custom order statuses?

Custom statuses are registered admin-side and appear in the order editor and orders list. Showing them in customer-facing views (order emails or the account order page) requires extending those templates or hooks yourself.

### Do custom statuses auto-transition orders?

No. Changing an order to a custom status is manual, using the **Status** dropdown on the order edit screen. The feature registers the statuses; it does not define automatic status transitions.

---

## Related Articles

- [How to Add Custom Columns to the WooCommerce Orders Table](woocommerce-enable-custom-order-columns.md)
- [How to Enable Thank You Page Link in Orders in WordPress](woocommerce-enable-thank-you-page-link-orders.md)
- [How to Enable Auto-Completion for Virtual/Downloadable Orders in WordPress](woocommerce-enable-woocommerce-auto-completion.md)


