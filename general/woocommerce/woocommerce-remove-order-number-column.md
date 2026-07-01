---
title: "How to Remove Order Number Column from Admin Orders Page in WordPress | CM"
slug: remove-order-number-column
description: "Hide the order number column from the WooCommerce admin orders page in Classic Monks. Provides more space for other important order information."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/remove-order-number-column/
---

# How to Remove Order Number Column from Admin Orders Page in WordPress

> Remove Order Number Column from Admin Orders Page hides the order number column from the WooCommerce admin orders table. Provides more space for other important order information.

## Key Takeaways

- Single toggle, no nested options
- Hides the order number column from the orders list table
- The order number is still accessible in the order details
- Saves horizontal space for other columns
- Useful when other columns (like custom order columns) are more important

## What Is the Remove Order Number Column feature?

By default, the WooCommerce admin orders table shows: order number, date, status, customer, total, items, actions. The order number is the first column. The Remove Order Number Column feature hides this column, freeing horizontal space for other columns (like the custom order columns added by the [Enable Custom Order Columns](woocommerce-enable-custom-order-columns.md) feature).

## Why You Need It

The order number column is useful but takes up horizontal space:

- **Many custom columns**: If you've added several custom order columns, the order number column may push them off-screen
- **Order number is accessible elsewhere**: The order number is shown in the order details page, in the customer column (e.g., "John Smith - #1234"), and in the URL when editing
- **Order number is redundant**: The order details page always shows it

For most stores with many custom columns, removing the order number column improves admin efficiency.

---

## How to Remove Order Number Column from Admin Orders Page in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **My Account** subtab.

### Step 3: Enable Remove Order Number Column

Toggle on **Remove Order Number Column from Admin Orders Page**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Go to **WooCommerce > Orders** in the WordPress admin. The order number column should not be visible.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Remove Order Number Column from Admin Orders Page** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- The admin orders list table: the order number column is hidden
- The order number is still accessible in:
  - The order details page (top of the page)
  - The customer column (often shown as "Customer Name - #1234")
  - The order URL (post=1234)
  - The order actions menu

## What Does NOT Get Affected

- The order number itself: still generated and stored as the post ID
- The order edit page: still shows the order number
- The order in the customer account: still shows the order number
- The order emails: still include the order number

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Filters:**

- `manage_edit-shop_order_columns` calls `cm_remove_order_number_column()` (Removes order number column from order list)

```php
// Hooked in woocommerce-functions.php
add_filter( 'manage_edit-shop_order_columns', 'cm_remove_order_number_column' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The order number column is still showing

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the toggle is on. Clear all caching layers.

### The order number is not accessible anywhere

**Cause:** The order number column is hidden, but the order number should still be in the order details and URL.
**Fix:** Verify the order number is shown in the order details page. If not, check the theme's admin template.

### The orders table is now hard to scan

**Cause:** Removing the order number column makes the table look different.
**Fix:** Use the `manage_edit-shop_order_columns` filter to reorder the remaining columns. Put the most important columns (status, date, total, customer) first.

### I want the order number back

**Cause:** The toggle is on, and the order number column is hidden.
**Fix:** Disable the toggle. The order number column will reappear.

---

## Related Articles

- [How to Remove Display Name from Account Settings in WordPress](woocommerce-remove-woocommerce-display-name-option.md)
- [How to Enable Custom Order Columns in WordPress](woocommerce-enable-custom-order-columns.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
