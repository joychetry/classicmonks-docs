---
title: "How to Enable Custom Order Status in WordPress | CM"
slug: enable-custom-order-status
description: "Add and manage custom order statuses in WooCommerce through Classic Monks. Provides more granular order management beyond the default WooCommerce statuses."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/enable-custom-order-status/
---

# How to Enable Custom Order Status in WordPress

> Enable Custom Order Status adds the ability to create and manage custom order statuses in WooCommerce. Provides more granular order management beyond the default WooCommerce statuses (pending, processing, completed, etc.).

## Key Takeaways

- Single toggle, no nested options
- Adds the ability to create custom order statuses
- Custom statuses integrate with WooCommerce's order workflow
- Useful for stores with non-standard fulfillment processes
- No effect on existing orders or default statuses

## What Is the Enable Custom Order Status feature?

WooCommerce's default order statuses (pending, processing, on-hold, completed, cancelled, refunded, failed) cover most e-commerce scenarios. But some stores need custom statuses for:

- Manufacturing or custom production workflows
- Multi-stage fulfillment (e.g., "Awaiting Materials", "In Production", "Quality Check")
- Service businesses (e.g., "Scheduled", "In Progress", "Completed")
- B2B workflows (e.g., "Pending Approval", "Awaiting PO", "Invoiced")

The Enable Custom Order Status feature adds the ability to create and manage these custom statuses within WooCommerce's standard order workflow.

## Why You Need It

The default WooCommerce statuses are too generic for some businesses:

- **Manufacturing**: A furniture maker needs "Awaiting Materials", "In Production", "Quality Check", not just "Processing"
- **Services**: A consulting firm needs "Scheduled", "In Progress", "Completed", not "Shipped"
- **B2B**: An enterprise sales process needs approval workflows, "Pending Approval", "PO Received", "Invoiced"

Custom statuses provide better tracking and reporting, and they integrate with WooCommerce's standard order workflow (emails, reports, etc.).

---

## How to Enable Custom Order Status in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Orders** subtab.

### Step 3: Enable Custom Order Status

Toggle on **Enable Custom Order Status**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Add Custom Statuses

Go to **WooCommerce > Settings > Custom Order Statuses** (or the equivalent location added by the feature). Add your custom statuses with their slugs, labels, and colors.

### Step 6: Use Custom Statuses

When editing an order, the new statuses appear in the Status dropdown. You can change an order's status to any of the custom statuses.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Custom Order Status** | Master toggle. | Off |

No nested options. The custom statuses themselves are configured in the WooCommerce settings after the feature is enabled.

---

## What Gets Affected

- The order edit page: the Status dropdown now includes your custom statuses
- The orders list: custom statuses are shown in the Status column
- The order reports: custom statuses are included
- The WooCommerce REST API: custom statuses are exposed
- The order emails: custom statuses can trigger custom emails (requires additional setup)

## What Does NOT Get Affected

- The default WooCommerce statuses (pending, processing, etc.) are unchanged
- Existing orders' statuses (changing the feature doesn't reassign orders)
- The customer-facing order status display (this is admin-only)
- Other plugins' order management (e.g., custom order plugins that have their own status system)

---

## Advanced Options (Developers)

This feature registers 3 WordPress hooks in `woo-orders.php`:

**Actions:**

- `init` calls `cm_register_custom_status_with_wc()` (Registers custom status with WooCommerce)

**Filters:**

- `woocommerce_register_shop_order_post_statuses` calls `cm_register_custom_order_status()` (Registers custom order status)
- `wc_order_statuses` calls `cm_add_custom_order_status_dropdown()` (Adds custom status to order status dropdown)

```php
// Hooked in woo-orders.php
add_filter( 'woocommerce_register_shop_order_post_statuses', 'cm_register_custom_order_status' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### Custom statuses are not showing in the order edit page

**Cause:** The toggle is off, or the custom status was not registered correctly.
**Fix:** Verify the toggle is on. Check the WooCommerce settings for the custom statuses. Verify the status is registered with `show_in_admin_status_list => true`.

### The custom status is showing but cannot be selected

**Cause:** The status was registered as `public => false` but should be true for admin visibility.
**Fix:** Re-register the status with the correct arguments. The `register_post_status` function requires `public` or `internal` set appropriately.

### The custom status is changing but no email is sent

**Cause:** Custom statuses don't automatically send emails; you need to register an action hook for each status.
**Fix:** Use the `woocommerce_order_status_{slug}` action hook to send custom emails for each status. See the Advanced Options example.

### The custom status is showing in the admin but not in the customer-facing order

**Cause:** Custom statuses are admin-only by default. The customer-facing order uses the default WooCommerce statuses.
**Fix:** Configure in the plugin settings to display custom statuses in the customer-facing order summary, or add a custom email template that includes the custom status.

---

## Related Articles

- [How to Enable Thank You Page Link in Orders in WordPress](woocommerce-enable-thank-you-page-link-orders.md)
- [How to Enable Custom Order Columns in WordPress](woocommerce-enable-custom-order-columns.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
