---
title: "How to Allow Reset Password Email in WordPress | CM"
slug: allow-reset-password-email
description: "Allow the WooCommerce customer reset password email even when all other WooCommerce emails are disabled. Ensures customers can always recover their account access."
last_updated: 2026-07-28
author: Joy
reading_time: 5 min
canonical: https://classicmonks.com/docs/allow-reset-password-email/
merged_docs: "How to Only Allow Reset Password Email in WordPress (Email tab)"
---

# How to Allow Reset Password Email in WordPress

> Allow Reset Password Email maintains the customer reset password email even when all other WooCommerce emails are disabled. Ensures customers can always recover their account access, which is critical for account security.

## Key Takeaways

- Single toggle, no nested options
- Allows the customer reset password email specifically
- Works in combination with Disable WooCommerce Emails (which suppresses other emails)
- Ensures account recovery is always possible
- Critical for account security and user trust

## What Is the Allow Reset Password Email Feature?

When the Disable WooCommerce Emails feature is on, all WooCommerce transactional emails are suppressed, including the customer reset password email. The Allow Reset Password Email feature re-enables the reset password email specifically, ensuring customers can always recover their account access.

This is most useful in combination with the [Disable WooCommerce Emails](woocommerce-disable-woocommerce-emails.md) feature. The Disable feature suppresses all emails; the Allow feature re-enables the one email that is critical for account access.

The two features can also be used independently: this feature alone ensures the password reset email is the only one sent, even without the broader disable.

## Why You Need It

In some environments, transactional emails are not desired at all, but account recovery is non-negotiable:

- **B2B / wholesale**: Wholesale customers may forget passwords more often due to multi-account usage. Always allow the reset password email to prevent account lockouts.
- **Headless commerce**: The frontend handles all customer communication; WooCommerce is the backend, and the only customer-facing email is the password reset
- **Test environments**: Developers do not want test orders to spam real customers, but they need the password reset to work for their own admin access
- **Compliance**: Some regulated industries require all transactional email to be suppressed, but account recovery is a legal requirement

The feature ensures that even with all other emails off, the customer (or admin) can still recover their password.

---

## How to Allow Reset Password Email in Classic Monks

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

## What Gets Suppressed and What Does Not

| Email | Sent when feature off | Sent when feature on |
|-------|----------------------|----------------------|
| Order confirmation (customer) | Yes | **No** |
| Processing order (customer) | Yes | **No** |
| Completed order (customer) | Yes | **No** |
| Refunded order (customer) | Yes | **No** |
| Cancelled order (customer) | Yes | **No** |
| Failed order (customer) | Yes | **No** |
| Order on-hold (customer) | Yes | **No** |
| New order (admin) | Yes | **No** |
| Low stock (admin) | Yes | **No** |
| Out of stock (admin) | Yes | **No** |
| Customer note (customer) | Yes | **No** |
| **Customer reset password** | Yes | **Yes (always)** |

The reset password email is ALWAYS sent, regardless of the toggle. The toggle controls whether everything else is suppressed.

## What Does NOT Get Affected

- **WordPress core password reset email**: The WordPress core password reset (for admin users) is a separate flow. Use the [Disable Password Change Email](../email/email-disable-password-change-email.md) feature to suppress the confirmation email for admin password changes.
- **Other plugin password reset emails**: Custom plugins may have their own password reset flows. The Classic Monks feature only affects WooCommerce's specific email.
- **WordPress core user emails**: New user emails, etc. are controlled by separate features in the Notifications subtab.
- **Customer saved passwords or sessions**: Unaffected.

---

## Advanced Options (Developers)

This feature shares the same implementation file as Disable WooCommerce Emails (`disable-woocommerce-emails.php`). The option `woocommerce_allow_reset_password_email` controls whether `WC_Email_Customer_Reset_Password` is the exception to the suppression.

**Filters:**

- `woocommerce_email_classes` calls `cm_disable_woocommerce_emails()` (disables all WooCommerce email classes except `WC_Email_Customer_Reset_Password` when this feature is on; priority 90)

```php
// Hooked in disable-woocommerce-emails.php
add_filter( 'woocommerce_email_classes', 'cm_disable_woocommerce_emails' );
```

The feature modifies WooCommerce behavior by filtering the email classes. Disabling it reverses those changes.

## Troubleshooting

### The reset password email is not being sent

**Cause:** The toggle is off, or the user is in a role that is excluded by another filter.
**Fix:** Verify the toggle is on. Test with a regular customer account. Check your [SMTP settings](../email/email-smtp-settings.md).

### The reset password email is being suppressed by Disable WooCommerce Emails

**Cause:** The two features work together. The reset password email is the exception only when this toggle is on.
**Fix:** Verify both toggles are correctly configured. If Disable WooCommerce Emails is on and Allow Reset Password Email is also on, the reset password email should still be sent.

### I want to disable the reset password email too (for testing)

**Cause:** The toggle is on by default when Disable WooCommerce Emails is on.
**Fix:** Turn off Allow Reset Password Email. The reset password email will be suppressed.

### The customer reset password email is being blocked by a security plugin

**Cause:** A security plugin (e.g., Wordfence) is blocking the email as part of its brute-force protection.
**Fix:** Check the security plugin's logs. Whitelist the WooCommerce reset password endpoint if needed.

### The reset password email arrives but goes to spam

**Cause:** The email is sent but the recipient's mail server filters it as spam.
**Fix:** Check the spam folder. Verify the recipient's email address. Ensure your [SMTP settings](../email/email-smtp-settings.md) are configured for high deliverability.

### I have other password reset flows I want to keep

**Cause:** The feature only affects WooCommerce's customer reset password. Other password reset flows (WordPress core, custom plugins) are independent.
**Fix:** For other flows, you need to disable them via their own mechanisms. The Classic Monks feature is WooCommerce-specific.

---

## Common Use Cases

### B2B / wholesale stores

Wholesale customers may forget passwords more often due to multi-account usage. Always allow the reset password email to prevent account lockouts.

### Multi-user accounts

Stores where the same customer has multiple accounts (e.g., business + personal). The reset email ensures the customer can always recover access.

### Compliance

Some regulations require that customers can always recover their accounts. The reset password email is a basic security feature.

---

## Related Articles

- [How to Disable WooCommerce Emails in WordPress](woocommerce-disable-woocommerce-emails.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
- [How to Log WordPress Emails in Classic Monks](../email/email-logging.md)
