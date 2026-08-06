---
title: "How to Enable Custom Order Columns in WordPress | CM"
slug: enable-custom-order-columns
description: "Add additional columns to the WooCommerce orders table in Classic Monks. Includes 19 column options like payment method, shipping details, customer info, and more."
last_updated: 2026-06-24
author: Joy
reading_time: 7 min
canonical: https://classicmonks.com/docs/enable-custom-order-columns/
---

# How to Enable Custom Order Columns in WordPress

> Enable Custom Order Columns adds 19 additional columns to the WooCommerce admin orders table. Configure which columns to show from payment method, shipping details, customer info, order totals, and more.

## Key Takeaways

- Single toggle, master switch for the 19 column options
- 19 column options: payment method, shipping details, customer info, order totals, and more
- Each column is independently enabled
- Columns appear in the orders table after the default columns
- Improves order management efficiency at a glance

## What Is the Enable Custom Order Columns feature?

The default WooCommerce admin orders table shows: order number, date, status, customer, total, items, actions. The Enable Custom Order Columns feature adds the ability to show 19 additional columns:

- **Discount columns**: Total Discount, Total Items
- **Address columns**: City, Postcode/ZIP, Country, State/County
- **Customer columns**: Username, Customer Email, Customer Type, Customer Since
- **Payment columns**: Payment Method
- **Order notes**: Order Notes
- **Shipping columns**: Shipping Method, Shipping Total
- **Tax**: Tax Total
- **Status history**: Status History
- **Product categories**: Product Categories
- **Downloadable items**: Downloadable Items
- **Virtual items**: Virtual Items

Each column is a sub-option that can be independently enabled. The master toggle controls whether ANY custom columns are shown.

## Why You Need It

The default orders table is functional but minimal. For stores that process many orders, having the right columns visible at a glance saves time:

- **Customer service**: See customer details (email, since, type) without opening each order
- **Fulfillment**: See shipping method and address without opening each order
- **Finance**: See payment method and discount without opening each order
- **Reporting**: Quick visual scan of patterns (which payment method, which customer type, etc.)

For most stores, custom columns are a small but measurable efficiency improvement.

---

## How to Enable Custom Order Columns in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Orders** subtab.

### Step 3: Enable Custom Order Columns

Scroll to **Enable Custom Order Columns**. Toggle on to enable the column system. Nested options expand with the 19 column toggles.

### Step 4: Select Columns

Toggle on the columns you want to display. Each column is independent.

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Test

Go to **WooCommerce > Orders** in the WordPress admin. The selected columns should appear in the orders table.

---

## Available Columns

The 19 available columns are:

| Column | Description |
|--------|-------------|
| **Total Discount** | Total discount amount applied to each order. |
| **Total Items** | Total number of items in each order. |
| **City** | Customer's billing city. |
| **Postcode/ZIP** | Customer's billing postcode. |
| **Country** | Customer's billing country. |
| **State/County** | Customer's billing state. |
| **Username** | Customer's WordPress username. |
| **Payment Method** | Payment method used (Stripe, PayPal, etc.). |
| **Order Notes** | Latest order note for each order. |
| **Shipping Method** | Shipping method selected. |
| **Shipping Total** | Shipping cost for the order. |
| **Tax Total** | Tax amount for the order. |
| **Status History** | Number of status changes (click for full history). |
| **Customer Email** | Customer's email address. |
| **Customer Type** | New vs. returning customer. |
| **Customer Since** | Date the customer registered. |
| **Product Categories** | Comma-separated list of categories. |
| **Downloadable Items** | Whether the order contains downloadable products. |
| **Virtual Items** | Whether the order contains virtual products. |

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Custom Order Columns** | Master toggle. | Off |
| **Total Discount** | Toggle for this column. | Off |
| **Total Items** | Toggle for this column. | Off |
| **City** | Toggle for this column. | Off |
| **Postcode/ZIP** | Toggle for this column. | Off |
| **Country** | Toggle for this column. | Off |
| **State/County** | Toggle for this column. | Off |
| **Username** | Toggle for this column. | Off |
| **Payment Method** | Toggle for this column. | Off |
| **Order Notes** | Toggle for this column. | Off |
| **Shipping Method** | Toggle for this column. | Off |
| **Shipping Total** | Toggle for this column. | Off |
| **Tax Total** | Toggle for this column. | Off |
| **Status History** | Toggle for this column. | Off |
| **Customer Email** | Toggle for this column. | Off |
| **Customer Type** | Toggle for this column. | Off |
| **Customer Since** | Toggle for this column. | Off |
| **Product Categories** | Toggle for this column. | Off |
| **Downloadable Items** | Toggle for this column. | Off |
| **Virtual Items** | Toggle for this column. | Off |

---

## What Gets Affected

- The admin orders table: selected columns appear after the default columns
- The column sort order: follows the toggle order in the settings (you can rearrange by changing the toggle order)
- The export (CSV): selected columns are included

## What Does NOT Get Affected

- The customer-facing order summary
- The order detail page in the admin
- The order emails
- The WooCommerce REST API for orders (returns the same data regardless of column toggles)

---

## Advanced Options (Developers)

This feature registers 3 WordPress hooks in `woo-orders.php`:

**Actions:**

- `manage_shop_order_posts_custom_column` calls `cm_custom_order_column_content()` (Displays custom column content)

**Filters:**

- `manage_edit-shop_order_columns` calls `cm_register_custom_order_columns()` (Adds custom columns to order list)
- `manage_edit-shop_order_sortable_columns` calls `cm_custom_order_column_sorting()` (Makes custom columns sortable)

```php
// Hooked in woo-orders.php
add_filter( 'manage_edit-shop_order_columns', 'cm_register_custom_order_columns' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### A column is not showing

**Cause:** The column toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the column toggle is on. Clear all caching layers (page cache, object cache, CDN).

### The column is showing but with empty data

**Cause:** The order doesn't have the relevant data (e.g., a guest order doesn't have a username).
**Fix:** This is expected. The column is shown for all orders, but the data may be empty for orders that don't have the relevant info.

### The column is in the wrong position

**Cause:** The columns are shown in the order they appear in the settings (you toggle them on in a specific order).
**Fix:** Toggle the columns off and on again in the order you want them to appear. The order in the table reflects the order of the toggles.

### The column is showing in the table but not in the CSV export

**Cause:** The CSV export uses a different column list (typically the default WooCommerce columns plus the custom ones, but the order may vary).
**Fix:** Configure in the plugin settings to customize the CSV export columns. The default export includes all visible columns.

---

## Related Articles

- [How to Enable Thank You Page Link in Orders in WordPress](woocommerce-enable-thank-you-page-link-orders.md)
- [How to Create Custom Order Statuses in WooCommerce](woocommerce-enable-custom-order-status.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
