---
title: "How to Enable Auto-Completion for Virtual/Downloadable Orders in WordPress | CM"
slug: enable-woocommerce-auto-completion
description: "Auto-complete orders for virtual and downloadable products in Classic Monks. Streamline digital product fulfillment with configurable product type logic and email notifications."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/enable-woocommerce-auto-completion/
---

# How to Enable Auto-Completion for Virtual/Downloadable Orders in WordPress

> Enable Auto-Completion for Virtual/Downloadable Orders automatically marks orders as completed upon payment. Streamlines digital product fulfillment with configurable product type logic and email notifications.

## Key Takeaways

- Single toggle, master switch for the feature
- 3 sub-options: log actions, send completion notification, disable customer note
- Configurable product type logic (virtual only, downloadable only, both, or all)
- Streamlines digital product fulfillment
- Eliminates manual order processing for digital products

## What Is the Enable Auto-Completion feature?

By default, WooCommerce orders remain in "Processing" status until the admin manually marks them as "Completed". For digital products (e.g., ebooks, software, courses), the fulfillment is automatic (the customer downloads the product), so manual order completion is unnecessary overhead.

The Enable Auto-Completion for Virtual/Downloadable Orders feature automatically marks orders as "Completed" when the payment is received, with configurable logic for which product types trigger auto-completion.

## Why You Need It

For digital product stores, the default WooCommerce workflow is inefficient:

- **Manual work**: Every order requires manual "Mark as Completed" after payment
- **Customer experience**: The customer is charged but doesn't get a "Completed" status email
- **Reporting**: Orders stay in "Processing" status indefinitely, skewing fulfillment reports

Auto-completion solves these:

- **Eliminates manual work**: Orders complete automatically
- **Improves customer experience**: Customers get the completed status email (with download links)
- **Better reporting**: Orders show correct status from payment onward

For most digital product stores, this is a high-ROI feature.

---

## How to Enable Auto-Completion for Virtual/Downloadable Orders in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Orders** subtab.

### Step 3: Enable Auto-Completion

Toggle on **Enable Auto-Completion for Virtual/Downloadable Products**. Nested options expand.

### Step 4: Configure Sub-Options

The 3 sub-options include:

- **Log Auto-Completion Actions**: Record auto-completion in the order notes (recommended for audit)
- **Send Completion Notification**: Send the standard WooCommerce "Completed order" email (recommended)
- **Disable Send Customer Note**: Skip the customer note email (the completion email is enough)

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Test

Place a test order for a virtual or downloadable product. After payment, the order status should automatically change to "Completed".

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Auto-Completion for Virtual/Downloadable Products** | Master toggle. | Off |
| **Log Auto-Completion Actions** | Log to order notes. | Off |
| **Send Completion Notification** | Send the Completed email. | Off |
| **Disable Send Customer Note** | Skip the customer note email. | Off |
| **Product Type Logic** | (configured in the code, not the UI) | Virtual and Downloadable |

The Product Type Logic is configured at the code level (which product types trigger auto-completion). Default is virtual and downloadable products.

---

## What Gets Affected

- Orders for virtual/downloadable products: automatically marked as "Completed" after payment
- The order status: changes from "Processing" to "Completed" without manual intervention
- The completion email: sent to the customer (if enabled)
- The order notes: includes a log entry (if enabled)
- The order reports: shows correct status from payment onward

## What Does NOT Get Affected

- Orders for physical products: still require manual completion
- The customer-facing order confirmation page: still shows the order details
- The cart and checkout processes: unchanged
- The WooCommerce REST API: still returns the same order data

---

## Advanced Options (Developers)

This feature registers 2 WordPress hooks in `auto-completion.php`:

**Actions:**

- `woocommerce_payment_complete` calls `cm_auto_complete_virtual_orders()` (Auto-completes virtual/downloadable orders on payment)
- `woocommerce_order_status_processing` calls `cm_auto_complete_virtual_orders()` (Auto-completes virtual orders on processing status)

```php
// Hooked in auto-completion.php
add_action( 'woocommerce_payment_complete', 'cm_auto_complete_virtual_orders' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### Orders are not being auto-completed

**Cause:** The toggle is off, the product is not virtual or downloadable, or the order hasn't been paid yet.
**Fix:** Verify the toggle is on. Verify the product is set as "Virtual" or "Downloadable" in the product data. Verify the order has been paid (processing status).

### The completion email is not being sent

**Cause:** The "Send Completion Notification" sub-option is off, or the email is filtered by another plugin.
**Fix:** Verify the sub-option is on. Check the email logs (WooCommerce > Status > Logs) for errors. Disable email-related plugins to find the conflict.

### The order note is not being logged

**Cause:** The "Log Auto-Completion Actions" sub-option is off.
**Fix:** Verify the sub-option is on. The note is added as an order note (visible in the admin order details).

### The customer note is still being sent

**Cause:** The "Disable Send Customer Note" sub-option is off.
**Fix:** Verify the sub-option is on. The customer note is a separate email from the completion email.

### Auto-completion is too aggressive (happens for products I don't want)

**Cause:** The default product type logic includes all virtual and downloadable products.
**Fix:** Configure in the plugin settings to limit which types trigger auto-completion. Or use the plugin settings to skip specific orders.

---

## Related Articles

- [How to Enable Thank You Page Link in Orders in WordPress](woocommerce-enable-thank-you-page-link-orders.md)
- [How to Create Custom Order Statuses in WooCommerce](woocommerce-enable-custom-order-status.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
