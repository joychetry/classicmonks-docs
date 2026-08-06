---
title: "How to Hide the Order Number Column in WooCommerce Admin"
slug: remove-order-number-column
description: "Remove the order number column from the WooCommerce admin orders page. Free up space for other columns while keeping order numbers accessible elsewhere."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/remove-order-number-column/
---

# How to Hide the Order Number Column in WooCommerce Admin

> Remove the order number column from the WooCommerce admin orders table so the other columns have more room. Order numbers remain visible in the order details and customer column.

## Key Takeaways

- Hide the order number column from the admin orders list
- Free horizontal space for other order columns
- Order numbers stay accessible in order details
- One toggle, no nested options
- Works well with custom order columns

## What Does the Feature Do?

The WooCommerce admin orders table starts with an order number column. The **Remove Order Number Column** feature hides it, giving the remaining columns more horizontal room.

Removing the column does not remove the order number itself. The number still appears in the order details page and is often shown within the customer column.

## Why You Need It

The order number column uses valuable space:

- When several columns are enabled, the order number pushes them off-screen
- The number is still available in the order details and URL
- Removing it lets status, date, total, and customer data dominate the row
- It pairs with the custom order columns feature for a dense but readable table

---

## How to Remove the Order Number Column from the WooCommerce Admin

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **My Account** settings area.
3. Toggle on **Remove Order Number Column from Admin Orders Page**.

### Step 2: Save and Test

Click **Save Changes**. Open **WooCommerce > Orders** and confirm the order number column no longer appears, while the other columns fill the freed space.

---

## Configuration Options

| Option | Default |
|--------|---------|
| **Remove Order Number Column from Admin Orders Page** | Off |

There are no nested options. The feature is a single on/off control.

---

## What Gets Affected

- The admin orders list: the order number column is hidden
- The available horizontal space: other columns use the freed room

## What Does NOT Get Affected

- The order number itself: still generated and stored
- The order details page: still shows the order number
- Order emails and the customer account: the number still appears
- The customer column: may still include the order number as it always has

---

## Advanced Options (Developers)

The feature registers one hook in `functions/woocommerce/woocommerce-functions.php`:

```php
add_filter( 'manage_edit-shop_order_columns', 'cm_remove_order_number_column' );
```

**`manage_edit-shop_order_columns`** calls `cm_remove_order_number_column()`, which unsets the `order_number` key so that column is not rendered in the admin orders list.

---

## Common Use Cases

**Dense order tables.** Stores that enable many order columns remove the number column so the rest fit on screen.

**Clean scanning.** Some teams prefer status, date, and customer over a redundant number column.

**Paired with custom columns.** This feature complements the custom order columns feature by freeing space for the added columns.

---

## Troubleshooting

### The column is still showing

**Cause:** The toggle is off, or a caching plugin serves the old table.
**Fix:** Confirm the toggle is on and clear caches.

### The order number is no longer visible anywhere

**Cause:** The feature only hides the list column; the number stays in the order details.
**Fix:** Open an order's details page to locate the number. If the theme layout hides it there separately, check the theme's admin template.

### I want the column back

**Cause:** The toggle is on.
**Fix:** Turn the toggle off and the order number column returns.

---

## Frequently Asked Questions

### Does this delete order numbers?

No. The order number is still generated and stored. Only the list column is hidden.

### Where can I still see the order number?

In the order details page and often within the customer column of the orders list.

### Why remove the column?

To free horizontal space so the other order columns are readable, especially when custom columns are enabled.

### Is it on by default?

No. The feature is off until you enable the toggle.

---

## Working With the Remaining Columns

Once the order number column is gone, the orders table shows the other built-in columns using the freed space. Teams that enable additional order columns from the classic order columns feature can fit more data on screen without the row stretching. The customer column typically still carries the order number or order details link, so staff keep a way to reach a specific order even with the number column hidden. For stores that scan orders by status, date, or total, removing the number column makes those columns the primary anchor points.

---

## Related Articles

- [How to Remove the Display Name from Account Settings in WooCommerce](woocommerce-remove-woocommerce-display-name-option.md)
- [How to Add Custom Columns to the WooCommerce Orders Table](woocommerce-enable-custom-order-columns.md)
- [How to Create Custom Order Statuses in WooCommerce](woocommerce-enable-custom-order-status.md)
