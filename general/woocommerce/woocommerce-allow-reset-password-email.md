---
title: "How to Allow Reset Password Email in WordPress | CM"
slug: woocommerce/allow-reset-password-email
description: "Allow the WooCommerce customer reset password email even when all other WooCommerce emails are disabled. Ensures customers can always recover their account access."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/woocommerce/allow-reset-password-email/
---

# How to Allow Reset Password Email in WordPress

> Allow Reset Password Email maintains the customer reset password email even when all other WooCommerce emails are disabled. Ensures customers can always recover their account access, which is critical for account security.

## Key Takeaways

- Single toggle, no nested options
- Allows the customer reset password email specifically
- Works in combination with Disable WooCommerce Emails (which suppresses other emails)
- Ensures account recovery is always possible
- Critical for account security and user trust

## What Is the Allow Reset Password Email feature?

When the Disable WooCommerce Emails feature is on, all WooCommerce transactional emails are suppressed, including the customer reset password email. The Allow Reset Password Email feature re-enables the reset password email specifically, ensuring customers can always recover their account access.

## Why You Need It

The reset password email is critical for account security:

- **Account recovery**: Customers who forget their password can recover access
- **Security**: Without the email, customers who suspect compromise cannot reset their password
- **User trust**: A store that "disables password reset" is suspicious
- **Account security best practice**: Always allow password reset

This is the one WooCommerce email that should never be disabled.

---

## How to Allow Reset Password Email in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Email** subtab.

### Step 3: Enable Allow Reset Password Email

Toggle on **Allow Reset Password Email**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Log out. Click "Lost your password?" on the login page. Enter a customer email. The reset password email should be sent (even if Disable WooCommerce Emails is on).

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Allow Reset Password Email** | Master toggle. | Off |

This feature works in combination with the [Disable WooCommerce Emails](woocommerce-disable-woocommerce-emails.md) feature. The reset password email is the one exception to the disable.

---

## What Gets Affected

- The customer reset password email: always sent (regardless of Disable WooCommerce Emails)
- The customer's account recovery: always possible
- All other WooCommerce emails: still controlled by Disable WooCommerce Emails

## What Does NOT Get Affected

- Other WooCommerce transactional emails: still suppressed if Disable WooCommerce Emails is on
- The WordPress core emails: controlled by separate features in the Email tab > Notifications subtab
- The customer's saved passwords or sessions

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `disable-woocommerce-emails.php`:

**Filters:**

- `woocommerce_email_classes` calls `cm_disable_woocommerce_emails()` (Controls which WooCommerce emails are sent (priority 90))

```php
// Hooked in disable-woocommerce-emails.php
add_filter( 'woocommerce_email_classes', 'cm_disable_woocommerce_emails' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Common Use Cases

### B2B / wholesale stores

Wholesale customers may forget passwords more often due to multi-account usage. Always allow the reset password email to prevent account lockouts.

### Multi-user accounts

Stores where the same customer has multiple accounts (e.g., business + personal). The reset email ensures the customer can always recover access.

### Compliance

Some regulations require that customers can always recover their accounts. The reset password email is a basic security feature.

## Troubleshooting

### The reset password email is not being sent

**Cause:** The toggle is off, or the user is in a role that's excluded by another filter.
**Fix:** Verify the toggle is on. Test with a regular customer account.

### The reset password email is being suppressed by Disable WooCommerce Emails

**Cause:** The two features work together. The reset password email is the exception.
**Fix:** Verify both toggles are correctly configured. If only Disable WooCommerce Emails is on, the reset password email should still be sent (because Allow Reset Password Email is also on).

### I want to disable the reset password email too (for testing)

**Cause:** The toggle is on by default when Disable WooCommerce Emails is on.
**Fix:** Turn off Allow Reset Password Email. The reset password email will be suppressed.

### The customer reset password email is being blocked by a security plugin

**Cause:** A security plugin (e.g., Wordfence) is blocking the email as part of its brute-force protection.
**Fix:** Check the security plugin's logs. Whitelist the WooCommerce reset password endpoint if needed.

---

## Related Articles

- [How to Disable WooCommerce Emails in WordPress](woocommerce-disable-woocommerce-emails.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
