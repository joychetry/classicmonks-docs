---
title: "How to Enable Thank You Page Link in Orders in WordPress | CM"
slug: woocommerce/enable-thank-you-page-link-orders
description: "Add a direct link to the order's thank you page in the WooCommerce admin orders table in Classic Monks. Provides quick access to the customer-facing order confirmation."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/woocommerce/enable-thank-you-page-link-orders/
---

# How to Enable Thank You Page Link in Orders in WordPress

> Enable Thank You Page Link in Orders adds a direct link to the order's thank you page in the WooCommerce admin orders table. Provides quick access to the customer-facing order confirmation for support and verification.

## Key Takeaways

- Single toggle, no nested options
- Adds a "Thank You Page" link to the orders table row actions
- Clicking opens the customer-facing order confirmation in a new tab
- Useful for support and troubleshooting
- No effect on the customer-facing experience

## What Is the Enable Thank You Page Link in Orders feature?

The default WooCommerce admin orders table has row actions for processing orders, editing, viewing the order detail, etc. The Enable Thank You Page Link in Orders feature adds an additional row action that opens the customer-facing thank you page (the same page the customer sees after completing checkout).

This is an admin-only feature. It does not affect the customer-facing experience.

## Why You Need It

The thank you page is the page the customer sees immediately after completing checkout. For support and troubleshooting, having quick access to this page is useful:

- **Support**: When a customer reports a problem, you can see exactly what they saw at checkout
- **Verification**: Confirm the order is processing correctly (the thank you page shows the order details)
- **Training**: When training new staff, the thank you page is a great reference for the customer experience

For most stores, this is a small admin UX improvement.

---

## How to Enable Thank You Page Link in Orders in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Orders** subtab.

### Step 3: Enable Thank You Page Link in Orders

Toggle on **Enable Thank You Page Link in Orders**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Go to **WooCommerce > Orders** in the WordPress admin. Hover over any order row. The "Thank You Page" action should appear in the row actions menu (under "View" or "Edit").

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Thank You Page Link in Orders** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- The admin orders table: a "Thank You Page" link is added to the row actions
- The link opens the customer-facing order confirmation page in a new tab
- The link is admin-only; customers are not affected

## What Does NOT Get Affected

- The customer-facing checkout process
- The actual thank you page (its content and behavior)
- The admin orders detail page
- The customer-facing "Thank you" page (which is the same page the link opens)

---

## Advanced Options (Developers)

This feature registers 3 WordPress hooks in `thank-you-page-link.php`:

**Filters:**

- `woocommerce_admin_order_actions` calls `cm_add_thank_you_page_action_button()` (Adds view thank you page button to order actions (priority 10))
- `woocommerce_order_actions` calls `cm_add_thank_you_order_action_dropdown()` (Adds view thank you page to order action dropdown (priority 9999))
- `determine_current_user` calls `cm_admin_becomes_customer_for_thank_you_page()` (Allows admin to view thank you page as customer (priority 20))

```php
// Hooked in thank-you-page-link.php
add_filter( 'woocommerce_admin_order_actions', 'cm_add_thank_you_page_action_button' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The link is not showing in the row actions

**Cause:** The toggle is off, or a custom admin theme is hiding the action.
**Fix:** Verify the toggle is on. Check the browser's DevTools to see if the action is being rendered but hidden by CSS.

### The link opens a 404 page

**Cause:** The thank you page URL is not correctly generated (e.g., the order ID is invalid, or the permalink structure is unusual).
**Fix:** Verify the permalink structure (Settings > Permalinks). Test the order's thank you page URL manually.

### The link opens the wrong page

**Cause:** A custom redirect is in place, or the thank you page slug is different.
**Fix:** Verify the WooCommerce thank you page settings. The default is `/checkout/order-received/`, but some plugins or themes change this.

### The link is showing for non-completed orders (e.g., pending or cancelled)

**Cause:** The default behavior shows the link for all orders with status that has a thank-you page (which is most statuses).
**Fix:** Configure in the plugin settings to limit the link to specific statuses (e.g., only completed or processing).

---

## Related Articles

- [How to Enable Custom Order Status in WordPress](woocommerce-enable-custom-order-status.md)
- [How to Enable Custom Order Columns in WordPress](woocommerce-enable-custom-order-columns.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
