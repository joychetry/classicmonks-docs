---
title: "How to Disable WooCommerce Emails in WordPress | CM"
slug: disable-woocommerce-emails
description: "Disable all WooCommerce transactional emails including order confirmations, shipping notices, and admin notifications. Provides complete control over customer communications."
last_updated: 2026-07-28
author: Joy
reading_time: 5 min
canonical: https://classicmonks.com/docs/disable-woocommerce-emails/
merged_docs: "How to Disable WooCommerce Emails in WordPress (Email tab)"
---

# How to Disable WooCommerce Emails in WordPress

> Disable WooCommerce Emails suppresses all WooCommerce-specific transactional emails, including order confirmations, shipping notices, refund notifications, and admin alerts. The customer still receives order confirmation via the on-screen checkout flow.

## Key Takeaways

- Single toggle, site-wide effect
- Disables all WooCommerce transactional emails
- Customer still receives order confirmation via the checkout page
- The customer reset password email is controlled by a separate feature (see related)
- Useful for stores with custom email systems or that want a quieter customer experience

## What Is the Disable WooCommerce Emails Feature?

WooCommerce sends several types of transactional emails by default:

- **Order confirmation** (customer)
- **Processing order** (customer)
- **Completed order** (customer)
- **Refunded order** (customer)
- **Cancelled order** (customer)
- **Failed order** (customer)
- **Order on-hold** (customer)
- **New order** (admin)
- **Low stock** (admin)
- **Out of stock** (admin)
- **Customer note** (customer)

The Disable WooCommerce Emails feature suppresses all of these. The on-screen checkout experience (order confirmation page, thank you page) is unchanged.

## Why You Need It

Most stores benefit from WooCommerce emails, but some use cases do not:

- **B2B / wholesale**: Order confirmations go through a custom sales-team workflow
- **Digital products**: The download email is sufficient; the WooCommerce order emails are redundant
- **Custom email systems**: The store uses a third-party email platform (e.g., Klaviyo, Mailchimp) for all customer communications
- **Test environments**: The store is a staging or development environment where emails would be noise
- **Compliance**: Some regulated industries require all transactional email to go through a specific compliance system

For most consumer e-commerce stores, leave the emails enabled. For other business models, this feature simplifies the email flow.

---

## How to Disable WooCommerce Emails in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Email** subtab.

### Step 3: Enable Disable WooCommerce Emails

Toggle on **Disable WooCommerce Emails**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Place a test order. The on-screen checkout should still show the order confirmation, but no email should be sent to the customer or admin.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable WooCommerce Emails** | Master toggle. | Off |

The customer reset password email is controlled by a separate toggle: [Allow Reset Password Email](../woocommerce/woocommerce-allow-reset-password-email.md).

---

## What Gets Suppressed

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
| Customer reset password | Yes | Yes (controlled by [Allow Reset Password Email](../woocommerce/woocommerce-allow-reset-password-email.md)) |

## What Does NOT Get Affected

- **Customer reset password email**: Controlled separately by the "Allow Reset Password Email" feature. This is intentional so customers can still recover their accounts even when all other WooCommerce emails are disabled.
- **WordPress core emails**: New user emails, password change emails, etc. are controlled by separate features in the Email tab > Notifications subtab.
- **On-screen checkout experience**: The customer still sees the order confirmation page and the order details in their account dashboard. The feature only affects emails.
- **Admin order list in the WordPress dashboard**: Still shows all orders.
- **Custom WooCommerce email add-ons**: Plugins that extend the WooCommerce email system with custom email classes are affected if they register via `woocommerce_email_classes`. Plugins that bypass WooCommerce and send via `wp_mail()` directly are not affected.

---

## Advanced Options (Developers)

This feature registers 2 WordPress hooks in `disable-woocommerce-emails.php`:

**Actions:**

- `plugins_loaded` calls `cm_maybe_disable_woocommerce_emails()` (conditionally registers the filter)

**Filters:**

- `woocommerce_email_classes` calls `cm_disable_woocommerce_emails()` (disables all WooCommerce email classes except `WC_Email_Customer_Reset_Password` when the Allow Reset Password Email feature is off; priority 90)

```php
// Hooked in disable-woocommerce-emails.php
add_action( 'plugins_loaded', 'cm_maybe_disable_woocommerce_emails' );
```

The feature modifies WooCommerce behavior by disabling email classes via the `woocommerce_email_classes` filter. Disabling it reverses those changes.

## Troubleshooting

### Customers are not receiving order confirmations

**Cause:** The toggle is on, which suppresses all WooCommerce emails by design.
**Fix:** Disable the toggle to re-enable order confirmations. If you want to keep most emails disabled but enable only order confirmations, use WooCommerce's built-in settings (WooCommerce > Settings > Emails) to manage individual email types.

### The customer reset password email is also disabled

**Cause:** The customer reset password email is NOT affected by this feature by default. If `woocommerce_allow_reset_password_email` is also enabled, the reset password email continues to work. If it is not being sent, the issue is elsewhere.
**Fix:** Verify the "Allow Reset Password Email" feature is enabled in the WooCommerce > Email subtab. If the password reset flow itself is not triggering, check that the WordPress password reset mechanism is working.

### New orders are not showing in the admin

**Cause:** The Disable WooCommerce Emails feature only suppresses emails, not admin order management.
**Fix:** Check WooCommerce > Orders in the WordPress admin. The admin order list is independent of email settings.

### WooCommerce admin notifications are still being sent

**Cause:** A custom plugin or theme function is sending its own admin notification.
**Fix:** The Classic Monks feature suppresses WooCommerce's built-in emails only. Custom plugins that send their own admin notifications on new orders are independent. Check the custom plugin's settings or hooks.

### I want to disable some WooCommerce emails but not all

**Cause:** The feature is global (all on or all off).
**Fix:** For selective suppression, use WooCommerce's built-in settings (WooCommerce > Settings > Emails) to disable individual email types one by one.

### I disabled the feature but the email is still being sent

**Cause:** The feature only suppresses emails sent via WooCommerce's standard `WC_Email` system. If a custom plugin is sending the email directly via `wp_mail()` (bypassing WooCommerce's email system), the feature does not catch it.
**Fix:** Identify the custom plugin and disable its email sending. Or filter `pre_wp_mail` to suppress the email globally.

---

## Related Articles

- [How to Allow Reset Password Email in WordPress](woocommerce-allow-reset-password-email.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
- [How to Log WordPress Emails in Classic Monks](../email/email-logging.md)
