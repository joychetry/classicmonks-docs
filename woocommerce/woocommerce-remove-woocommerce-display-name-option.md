---
title: "How to Remove the Display Name Field from the Account Form"
slug: remove-woocommerce-display-name-option
description: "Remove the display name field from the WooCommerce account details form so customers cannot edit it there. Simplify the form with a Classic Monks toggle."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/remove-woocommerce-display-name-option/
---

# How to Remove the Display Name Field from the Account Form

> Remove the display name field from the WooCommerce account settings so customers cannot edit it there. Simplify the account details form with Classic Monks.

## Key Takeaways

- Remove the display name field from the account settings form
- Drop the field from required account fields
- One toggle, no nested options
- Existing display names stay intact
- Admin user editing still manages the display name

## What Does the Feature Do?

The WooCommerce account settings form includes a display name field where customers choose how their name appears. The **Remove Display Name from Account Settings** feature removes that field from the account form and from the required account fields.

Existing display names already set are preserved. Customs cannot edit the display name in the account area, but admins can still change it from the WordPress user editing screen.

## Why You Need It

The display name field is often unnecessary:

- Few customers change their display name on the account page
- Removing it shortens the account form
- It reduces editing choices for stores that manage names centrally
- Admins can still correct a display name in the user screen

---

## How to Remove the Display Name Field from the WooCommerce Account

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **My Account** settings area.
3. Toggle on **Remove Display Name from Account Settings**.

### Step 2: Save and Test

Click **Save Changes**. Log in as a customer and open **My Account > Account Details**. The display name field should no longer appear.

---

## Configuration Options

| Option | Default |
|--------|---------|
| **Remove Display Name from Account Settings** | Off |

There are no nested options. The feature is a single on/off control.

---

## What Gets Affected

- The customer account details form: the display name field is removed
- The required account fields: the display name is dropped

## What Does NOT Get Affected

- Existing display names: preserved in the database
- The WordPress admin user edit screen: still shows and manages the display name
- Usernames and other account fields: unchanged
- Reviews and comments: these keep using the display name as they always have

---

## Advanced Options (Developers)

The feature registers hooks in `functions/woocommerce/woocommerce-functions.php`:

```php
add_filter( 'woocommerce_save_account_details_required_fields', 'cm_remove_woocommerce_display_name_option' );
add_filter( 'woocommerce_edit_account_form', 'cm_remove_woocommerce_display_name_option' );
add_action( 'woocommerce_edit_account_form', 'cm_hide_display_name_in_account_form' );
```

- **`woocommerce_save_account_details_required_fields`** and **`woocommerce_edit_account_form`** call `cm_remove_woocommerce_display_name_option()`, which unsets `account_display_name` so the field is not processed or rendered as required.
- **`woocommerce_edit_account_form`** also runs `cm_hide_display_name_in_account_form()`, which hides the field's row in the rendered form.

---

## Common Use Cases

**Simpler account form.** Stores that manage names server-side remove the field to shorten the form.

**Centralized naming.** Teams that control how names appear prefer that customers not edit the display name.

**Cleaner profile UX.** Removing an rarely-used field keeps the account settings focused.

---

## Troubleshooting

### The display name field is still showing

**Cause:** The toggle is off, or a theme re-renders the account form.
**Fix:** Confirm the toggle is on and clear caches. If a theme builds the account form independently, it may render the field from its own markup.

### The display name disappeared but shows on comments

**Cause:** The feature removes the editable field and required status, but the stored display name is still used where WooCommerce displays it.
**Fix:** This is expected. The stored value keeps being used for display; the customer simply cannot edit it in the account form.

### Admins can still change the name

**Cause:** The admin user edit screen is separate from the customer account form.
**Fix:** This is by design. Admins change display names in the WordPress user profile screen.

---

## Frequently Asked Questions

### Does this delete display names?

No. Existing display names are preserved. The field is only removed from the customer account form.

### Can I still change a display name?

Admins can change it through the WordPress user edit screen. Customers can no longer edit it in the account details form.

### Is it different from the username?

Yes. The username is the login name and is unchanged. This feature removes the display name field, which controls how a name appears publicly.

### Does it affect reviews and comments?

The stored display name continues to be used in reviews and comments. The feature only stops customers from editing it in the account form.

---

## Related Articles

- [How to Remove the Order Number Column from the WooCommerce Admin](woocommerce-remove-order-number-column.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
- [How to Remove All WooCommerce Notices](woocommerce-remove-all-woocommerce-notices.md)
