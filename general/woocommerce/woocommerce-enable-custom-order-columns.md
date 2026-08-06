---
title: "How to Add Custom Columns to the WooCommerce Orders Table"
slug: enable-custom-order-columns
description: "Add extra columns to the WooCommerce admin orders table with Classic Monks. Enable discounts, shipping, customer, payment, tax, and product data at a glance."
last_updated: 2026-08-06
author: Joy
reading_time: 6 min
canonical: https://classicmonks.com/docs/enable-custom-order-columns/
---

# How to Add Custom Columns to the WooCommerce Orders Table

> Add extra columns to the WooCommerce admin orders table so payment, shipping, customer, discount, tax, and product data is visible without opening each order. Enable any of 19 optional columns in Classic Monks.

## Key Takeaways

- Add up to 19 optional columns to the WooCommerce admin orders table
- Enable each column independently from the Classic Monks Orders settings
- Columns are inserted after the order number in a fixed order
- Most columns are sortable from the column headers
- Simplifies customer service, fulfillment, finance, and reporting scans

## What Does the Feature Do?

The default WooCommerce admin orders table shows order number, date, status, and customer basics. The **Enable Custom Order Columns** feature adds optional columns so more data is visible at a glance. You turn on the columns you want, and each one appears in the orders list showing live order data.

The full set of available columns covers discounts, item counts, billing address, customer identity, payment, notes, shipping, tax, status history, categories, and downloadable or virtual item counts.

## When to Enable It

Enable Custom Order Columns when you process enough orders that opening each one to check payment, shipping, or customer details wastes time:

- Customer service teams that need billing email and addresses visible on the list
- Fulfillment teams that want shipping method and shipping total at a glance
- Finance and accounting work that uses payment method, discount, and tax columns
- Reporting needs that benefit from a visual scan across many orders

Keep it off if the default columns already give your team what it needs.

---

## How to Add Custom Columns to the WooCommerce Orders Table

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Orders** settings area.
3. Toggle on **Enable Custom Order Columns**. The column toggles expand below it.

### Step 2: Turn On the Columns You Want

Enable the individual toggles for the columns you need. Each column is independent, so you can show only the data that matters to your team. For example: enable **Payment Method**, **Shipping Method**, and **Shipping Total** for fulfillment, or **Customer Email** and **Customer Type** for support.

### Step 3: Save and Verify

Click **Save Changes**, then open **WooCommerce > Orders**. The enabled columns appear in the orders table after the order number. Use the sortable column headers to reorder rows by values such as total discount, shipping total, or customer email.

---

## Available Columns

Each of these is an independent toggle under **Enable Custom Order Columns**:

| Column | Data it shows |
|--------|---------------|
| **Discount** | Total discount applied to the order. |
| **Items** | Total item count for the order. |
| **City** | Billing city. |
| **Postcode** | Billing postcode/ZIP. |
| **Country** | Billing country. |
| **State** | Billing state/county. |
| **Username** | Customer's username, or "Guest" for guest orders. |
| **Payment** | Payment method title (for example, Stripe or PayPal). |
| **Notes** | The last three order notes, trimmed to a short preview. |
| **Shipping Method** | Shipping method used. |
| **Shipping Total** | Shipping cost shown as a price. |
| **Tax Total** | Total tax shown as a price. |
| **Status History** | The last three status changes with dates. |
| **Email** | Customer's billing email. |
| **Customer Type** | Registered or Guest. |
| **Customer Since** | Date of the customer's first order. |
| **Categories** | Product categories across the order, as links. |
| **Downloads** | Count of downloadable item quantities in the order. |
| **Virtual** | Count of virtual item quantities in the order. |

---

## Configuration Options

| Option | Default |
|--------|---------|
| **Enable Custom Order Columns** (master) | Off |
| **Discount / Items / City / Postcode / Country / State / Username / Payment / Notes / Shipping Method / Shipping Total / Tax Total / Status History / Email / Customer Type / Customer Since / Categories / Downloads / Virtual** (19 individual toggles) | Off |

Each column is enabled by turning on its toggle. All 19 columns, plus the default WooCommerce columns, are registered when the feature is on; only the enabled ones are inserted into the orders table.

---

## What Gets Affected

- The admin orders table: enabled columns appear after the order number
- Sorting: most numeric and text columns are sortable from their headers
- The orders list becomes more informative at a glance for enabled data

## What Does NOT Get Affected

- The default WooCommerce columns: these stay in place
- The order detail page and order editor: custom columns are list-only
- Customer-facing pages: the feature is admin-only; order emails and the account page are unchanged
- The WooCommerce REST API: order data returned by the API is unchanged by the column toggles

---

## Advanced Options (Developers)

The feature registers four hooks in `functions/woocommerce/woo-orders.php`:

```php
add_filter( 'manage_edit-shop_order_columns', 'cm_register_custom_order_columns' );
add_action( 'manage_shop_order_posts_custom_column', 'cm_custom_order_column_content' );
add_filter( 'manage_edit-shop_order_sortable_columns', 'cm_custom_order_column_sorting' );
add_action( 'pre_get_posts', 'cm_custom_order_column_orderby' );
```

- **`manage_edit-shop_order_columns`** calls `cm_register_custom_order_columns()`, which inserts the enabled columns immediately after the order number.
- **`manage_shop_order_posts_custom_column`** calls `cm_custom_order_column_content()`, which populates each column from the order data.
- **`manage_edit-shop_order_sortable_columns`** calls `cm_custom_order_column_sorting()`, making the numeric and text columns sortable. Sortable columns include discount, items, city, postcode, country, state, username, payment, shipping total, tax total, email, customer type, and customer since. Notes, status history, categories, downloads, and virtual are registered for display but not made sortable.
- **`pre_get_posts`** calls `cm_custom_order_column_orderby()`, which maps the sortable column to the underlying order meta (for example, shipping total sorts by `_order_shipping`).

The registration and sorting functions gate on the **Enable Custom Order Columns** toggle. If it is off, the columns are not added and sorting is unchanged.

---

## Troubleshooting

### A column is not showing

**Cause:** The column toggle is off, or the feature toggle is off.
**Fix:** Confirm **Enable Custom Order Columns** is on, then turn on the specific column you expect to see. Save and reload the orders page.

### A column shows empty data

**Cause:** The order does not have that data. A guest order has no username (shows "Guest"), and an order with no tax or shipping shows nothing in those columns.
**Fix:** This is expected per order. The column applies to all rows, but its value can be blank for orders without the relevant data.

### A column is in an unexpected position

**Cause:** Enabled columns are inserted after the order number in a fixed code order, not in the order you turned them on.
**Fix:** This is by design. Column position follows the plugin's fixed insertion order; it is not controlled by toggle order.

### A column is not sortable

**Cause:** Notes, status history, categories, downloads, and virtual columns are display-only and are not registered as sortable.
**Fix:** This is by design. For data you must sort, use one of the sortable columns (such as discount, shipping total, or customer email).

---

## Frequently Asked Questions

### How many columns can I add to the orders table?

Up to 19. All of them are optional toggles, so you can add a single column or the entire set depending on what your team needs to see.

### Where do the custom columns appear?

They are inserted immediately after the order number in the orders table. They do not replace the default WooCommerce columns.

### Can I sort orders by the custom columns?

Most numeric and text columns are sortable, including discount, items, city, postcode, country, state, username, payment, shipping total, tax total, email, customer type, and customer since. Notes, status history, categories, downloads, and virtual are display-only.

### Do customers see these columns?

No. The custom columns appear only in the WordPress admin orders table. Customer-facing order emails and the My Account order view are unaffected.

### Will the columns change the order data or exports?

No. The columns only change what is displayed in the admin list. The underlying order data and the WooCommerce REST API responses are unchanged.

---

## Related Articles

- [How to Access the Thank You Page from a WooCommerce Order](woocommerce-enable-thank-you-page-link-orders.md)
- [How to Create Custom Order Statuses in WooCommerce](woocommerce-enable-custom-order-status.md)
- [How to Remove Order Number Column from Admin Orders Page in WordPress](woocommerce-remove-order-number-column.md)


