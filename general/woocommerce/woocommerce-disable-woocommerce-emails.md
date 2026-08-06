---
title: "How to Disable the WooCommerce Transactional Emails"
slug: disable-woocommerce-emails
description: "Disable the WooCommerce transactional emails such as order confirmations and shipping notices. Keep online account access working with a Classic Monks option."
last_updated: 2026-08-06
author: Joy
reading_time: 5 min
canonical: https://classicmonks.com/docs/disable-woocommerce-emails/
merged_docs: "How to Disable WooCommerce Emails in WordPress (Email tab)"
---

# How to Disable the WooCommerce Transactional Emails

> Disable WooCommerce's transactional emails, such as order confirmations, shipping notices, and refund notifications. Optionally keep the customer reset password email so account recovery still works.

## Key Takeaways

- Suppress the WooCommerce transactional email classes together
- Reduces customer and admin email volume
- Optionally keep the reset password email for account recovery
- One toggle controls the bulk suppression
- On-screen checkout and order pages are unaffected

## What Does the Feature Do?

WooCommerce sends a range of transactional emails for order events, including order confirmation, processing, completed, refunded, cancelled, failed, and on-hold notices to customers, plus new-order and stock alerts to admins. The **Disable WooCommerce Emails** feature suppresses those transactional email classes.

The customer reset password email is handled through the **Allow Reset Password Email** option, so you can keep account recovery working while the rest of the transactional emails are off.

## Why You Need It

Not every store needs the full transactional email set:

- A store that emails manually or through another system may not want duplicate notifications
- Some workflows want to quiet customer order emails while keeping admin alerts or vice versa
- Test and staging environments avoid noise from transactional emails
- Disabling removes repetitive messages for stores that confirm elsewhere

---

## How to Disable WooCommerce Emails

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Email** settings area.
3. Toggle on **Disable WooCommerce Emails**.

### Step 2: Choose Whether to Keep the Reset Password Email

- **Allow Reset Password Email** (in the same Email settings) keeps the customer reset password email active despite the suppression.
- Leave it off to suppress the reset password email as part of the disable.

### Step 3: Save and Test

Click **Save Changes**. Place a test order and confirm no transactional email is sent, while (if enabled) the reset password email still works.

---

## Configuration Options

| Option | Effect | Default |
|--------|--------|---------|
| **Disable WooCommerce Emails** | Suppresses the WooCommerce transactional email classes. | Off |
| **Allow Reset Password Email** | Exempts the reset password email class from the suppression. | Off |

---

## What Gets Suppressed

- Order confirmation, processing, completed, refunded, cancelled, failed, and on-hold customer emails
- New-order, note, and stock-related admin emails
- Any WooCommerce transactional email class registered through the email classes filter

## What Does NOT Get Suppressed

- The reset password email, when **Allow Reset Password Email** is on
- On-screen order confirmation and account order pages
- WordPress core emails, which are separate

---

## Advanced Options (Developers)

The feature lives in `functions/email/disable-woocommerce-emails.php`:

```php
add_action( 'plugins_loaded', 'cm_maybe_disable_woocommerce_emails' );

function cm_disable_woocommerce_emails($email_classes) {
    $allow_reset_password_email = cm_get_option( 'woocommerce_allow_reset_password_email', false );
    foreach ( $email_classes as $email_class => $email_obj ) {
        if ( $email_class !== 'WC_Email_Customer_Reset_Password' || ! $allow_reset_password_email ) {
            $email_classes[$email_class]->enabled = false;
        }
    }
    return $email_classes;
}
```

- **`plugins_loaded`** calls `cm_maybe_disable_woocommerce_emails()`, which registers the `woocommerce_email_classes` filter at priority 90 only when **Disable WooCommerce Emails** is on.
- The filter disables each email class, skipping `WC_Email_Customer_Reset_Password` when **Allow Reset Password Email** is enabled.

---

## Common Use Cases

**Custom email workflows.** Stores that send confirmations through another system avoid duplicate transactional emails.

**Quiet digital-store flow.** A downloadable store can rely on its download email and skip the order emails.

**Test environments.** Staging sites avoid sending real customer emails during development.

**Controlled rollout.** Teams that want most emails off but account recovery on use both toggles together.

---

## Troubleshooting

### Customers stop receiving order emails

**Cause:** The disable feature is on by design, which suppresses the transactional emails.
**Fix:** Turn the toggle off to restore them. If you want only some emails, manage those individually in WooCommerce > Settings > Emails.

### The reset password email is also disabled

**Cause:** **Allow Reset Password Email** is off.
**Fix:** Turn on **Allow Reset Password Email** so the reset password class is exempted from the suppression.

### Emails still send from a third-party plugin

**Cause:** The feature suppresses WooCommerce's own email classes. A plugin that sends directly via its own mailer is separate.
**Fix:** Disable that plugin's emails from its own settings.

### A custom email class is affected

**Cause:** Extensions that register through the `woocommerce_email_classes` filter are part of the same list this feature disables.
**Fix:** Confirm the extension uses that filter. Plugins that bypass it send independently.

---

## Frequently Asked Questions

### Which emails does this disable?

The WooCommerce transactional email classes: order confirmation, processing, completed, refunded, cancelled, failed, on-hold, new-order, order note, and stock alerts. These appear for customers and admins as configured.

### Can I keep account recovery working?

Yes. Turn on **Allow Reset Password Email** so the reset password email class is excluded from the bulk suppression.

### Does it affect my checkout or order pages?

No. The feature only controls the transactional emails. On-screen checkout, order confirmation, and the account order page are unchanged.

### Is WordPress's own email affected?

No. WordPress core emails (such as new-user and password-change notices) are separate from WooCommerce's email classes and are not controlled here.

### Is the reset password email a WooCommerce email?

Yes. It is served by the `WC_Email_Customer_Reset_Password` class, which WooCommerce registers with the order emails. This feature exceptions it when the option is on.

---

## Related Articles

- [How to Keep the Reset Password Email in WooCommerce](woocommerce-allow-reset-password-email.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
- [How to Log WordPress Emails in Classic Monks](../email/email-logging.md)
