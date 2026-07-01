---
title: "How to Remove Display Name from Account Settings in WordPress | CM"
slug: remove-woocommerce-display-name-option
description: "Remove the display name field from customer account settings in Classic Monks. Simplifies the account management interface for B2C customers."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/remove-woocommerce-display-name-option/
---

# How to Remove Display Name from Account Settings in WordPress

> Remove Display Name from Account Settings hides the display name field from the WooCommerce customer account settings. Simplifies the account management interface for B2C customers who rarely change their display name.

## Key Takeaways

- Single toggle, no nested options
- Removes the display name field from the My Account > Account Details page
- Customer's existing display name is preserved in the database
- Simplifies the account form for B2C stores
- Admin can still set the display name in the admin user edit page

## What Is the Remove Display Name Option feature?

WooCommerce's account settings include a "Display name" field that lets customers choose how their name appears in reviews, comments, and order history. The Remove Display Name Option feature hides this field from the customer-facing account settings page.

The customer's existing display name is preserved in the database. The field is only hidden from the account form; admins can still set the display name in the WordPress admin user edit page.

## Why You Need It

For most B2C stores, the display name field is unnecessary:

- Most customers don't change their display name (they use their first name or full name)
- The field adds visual clutter to the account form
- For B2B stores, the display name may be important (e.g., "Acme Corp" as the display name)
- For B2C stores, removing it simplifies the form

For most consumer e-commerce stores, removing the display name field is a small UX improvement.

---

## How to Remove Display Name from Account Settings in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **My Account** subtab.

### Step 3: Enable Remove Display Name

Toggle on **Remove Display Name from Account Settings**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Log in as a customer. Go to My Account > Account Details. The display name field should not be visible.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Remove Display Name from Account Settings** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- The customer account settings page: the display name field is removed
- The customer's existing display name: preserved in the database
- The customer's reviews and comments: continue to show the display name (no change)
- The admin user edit page: still shows the display name field (admins can still manage it)

## What Does NOT Get Affected

- The customer's existing display name: not deleted
- The customer's username: not affected (this is the WordPress login name)
- The admin user edit page: still shows the display name field
- The customer's reviews and comments: continue to show the display name (no change in display)

---

## Advanced Options (Developers)

This feature registers 2 WordPress hooks in `woocommerce-functions.php`:

**Actions:**

- `woocommerce_edit_account_form` calls `cm_hide_display_name_in_account_form()` (Hides display name field in account form)

**Filters:**

- `woocommerce_save_account_details_required_fields` calls `cm_remove_woocommerce_display_name_option()` (Removes display name from required fields)

```php
// Hooked in woocommerce-functions.php
add_filter( 'woocommerce_save_account_details_required_fields', 'cm_remove_woocommerce_display_name_option' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The display name field is still showing

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the toggle is on. Clear all caching layers (page cache, object cache, CDN).

### The customer's display name disappeared from their reviews

**Cause:** This should not happen. The field is hidden but the data is preserved.
**Fix:** Verify the customer's display name in the WordPress admin user edit page. If it's empty, the customer's display name was set to empty before the toggle was enabled.

### The display name is empty on the customer's profile

**Cause:** The customer's display name was set to empty before the toggle was enabled, or the customer's profile was edited after the toggle.
**Fix:** Edit the customer's profile in the WordPress admin to set a display name. Configure in the plugin settings to provide a default when the display name is empty.

### The field is hidden but the customer wants to change their display name

**Cause:** The toggle hides the field from the customer-facing form.
**Fix:** The customer can request the change via support. Admins can change the display name in the WordPress user edit page.

---

## Related Articles

- [How to Remove Order Number Column from Admin Orders Page in WordPress](woocommerce-remove-order-number-column.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
