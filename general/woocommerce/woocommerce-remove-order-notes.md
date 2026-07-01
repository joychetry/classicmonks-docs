---
title: "How to Remove Order Notes from WooCommerce Checkout in WordPress | CM"
slug: woocommerce/remove-order-notes
description: "Remove the optional order notes field from the WooCommerce checkout form in Classic Monks. Streamlines the checkout experience by reducing form fields."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/woocommerce/remove-order-notes/
---

# How to Remove Order Notes from WooCommerce Checkout in WordPress

> Remove Order Notes strips the optional order notes text area from the WooCommerce checkout form. Streamlines the checkout experience by reducing form fields.

## Key Takeaways

- Single toggle, no nested options
- Removes the order notes text area from checkout
- The customer cannot leave special instructions at checkout
- Order notes are still stored in the admin (if you add them manually)
- Streamlines the checkout flow for stores that don't need order notes

## What Is the Remove Order Notes Field feature?

By default, WooCommerce's checkout form includes an "Order notes" text area where customers can leave special instructions (e.g., "Please leave at the front door", "Gift wrap this order"). The field is optional and doesn't affect most orders.

The Remove Order Notes Field feature removes this text area from the checkout form. The customer's saved order notes (if any were entered before the toggle was enabled) are preserved in the database.

## Why You Need It

For most e-commerce stores, the order notes field is rarely used:

- Most customers don't add notes
- The field adds visual clutter to a long checkout form
- For digital products or services, the field is completely irrelevant

For stores where the order notes field is critical (e.g., custom gifts, delivery instructions), keep the field enabled. For most other stores, removing it is a small UX win.

---

## How to Remove Order Notes from WooCommerce Checkout in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Checkout** subtab.

### Step 3: Enable Remove Order Notes

Toggle on **Remove Order Notes**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit the checkout page. The order notes text area should not appear.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Remove Order Notes** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- The checkout form: the order notes text area is removed
- The customer's saved addresses (if any had notes): the notes are still stored in the database
- The order confirmation email: the order notes are not included (since the customer couldn't enter them)
- The admin order details: the notes field is still shown in the admin (for manually-entered notes)

## What Does NOT Get Affected

- The customer's saved order notes (if they had any before the toggle was enabled)
- The order notes field in the admin (you can still add notes manually)
- Custom fields added by other plugins
- The checkout form's other fields

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Filters:**

- `woocommerce_checkout_fields` calls `cm_remove_order_notes()` (Removes order notes field from checkout)

```php
// Hooked in woocommerce-functions.php
add_filter( 'woocommerce_checkout_fields', 'cm_remove_order_notes' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The order notes field is still showing

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the toggle is on. Clear all caching layers.

### The order notes field is missing but I want it for some customers

**Cause:** The toggle is global.
**Fix:** Configure in the plugin settings to exclude specific roles. For example, keep the field for wholesale customers but hide it for retail customers.

### The customer's saved notes are not showing in the admin

**Cause:** The notes are stored in the order meta, not as a separate field. The admin order details page should show them under "Order notes".
**Fix:** Verify the notes are in the order meta by exporting the order as CSV. The toggle doesn't delete notes; it only hides the form field.

### I want a different type of field instead (e.g., a delivery date picker)

**Cause:** The toggle only controls the standard order notes field.
**Fix:** Disable the toggle and use a custom checkout field plugin to add a different field. Or use the `woocommerce_checkout_fields` filter to add a custom field after disabling the standard one.

---

## Related Articles

- [How to Enable Checkout Field Placeholders in WordPress](woocommerce-enable-checkout-field-placeholders.md)
- [How to Remove the Company Field from WooCommerce Checkout in WordPress](woocommerce-remove-company-field.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
