---
title: "How to Disable WooCommerce Emails in WordPress | CM"
slug: woocommerce/disable-woocommerce-emails
description: "Disable all WooCommerce transactional emails including order confirmations, shipping notices, and admin notifications. Provides complete control over customer communications."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/woocommerce/disable-woocommerce-emails/
---

# How to Disable WooCommerce Emails in WordPress

> Disable WooCommerce Emails suppresses all WooCommerce-specific transactional emails, including order confirmations, shipping notices, refund notifications, and admin alerts. The customer still receives order confirmation via the on-screen checkout flow.

## Key Takeaways

- Single toggle, site-wide effect
- Disables all WooCommerce transactional emails
- Customer still receives order confirmation via the checkout page
- The customer reset password email is controlled by a separate feature (see related)
- Useful for stores with custom email systems or that want a quieter customer experience

## What Is the Disable WooCommerce Emails feature?

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

Most stores benefit from WooCommerce emails, but some use cases don't:

- **B2B / wholesale**: Order confirmations go through a custom sales-team workflow
- **Digital products**: The download email is sufficient; the WooCommerce order emails are redundant
- **Custom email systems**: The store uses a third-party email platform (e.g., Klaviyo, Mailchimp) for all customer communications
- **Test environments**: The store is a staging or development environment where emails would be noise

For most consumer e-commerce stores, leave the emails enabled. For other business models, this feature simplifies the email flow.

---

## How to Disable WooCommerce Emails in WordPress

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

The customer reset password email is controlled by a separate toggle: [Allow Reset Password Email](woocommerce-allow-reset-password-email.md).

---

## What Gets Affected

- All WooCommerce transactional emails: suppressed
- The customer's order confirmation page: still shown on the front-end
- The admin order notifications: suppressed
- The admin new order email: suppressed

## What Does NOT Get Affected

- The customer reset password email: controlled by [Allow Reset Password Email](woocommerce-allow-reset-password-email.md)
- The WordPress core emails (password change, new user, etc.): controlled by separate features in the Email tab > Notifications subtab
- The on-screen order confirmation: still shown
- The customer's cart and checkout experience: unchanged

---

## Advanced Options (Developers)

This feature registers 2 WordPress hooks in `disable-woocommerce-emails.php`:

**Actions:**

- `plugins_loaded` calls `cm_maybe_disable_woocommerce_emails()` (Conditionally disables WooCommerce emails)

**Filters:**

- `woocommerce_email_classes` calls `cm_disable_woocommerce_emails()` (Removes selected WooCommerce email classes (priority 90))

```php
// Hooked in disable-woocommerce-emails.php
add_action( 'plugins_loaded', 'cm_maybe_disable_woocommerce_emails' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The customer is not receiving order emails

**Cause:** The toggle is on, and the customer reset password email is controlled by a separate feature.
**Fix:** Verify the toggle is on. If you want to allow the reset password email, enable the [Allow Reset Password Email](woocommerce-allow-reset-password-email.md) feature.

### The admin is not receiving new order notifications

**Cause:** The toggle suppresses admin notifications too.
**Fix:** If you want admin notifications but not customer emails, use the plugin settings to re-enable the admin email class (e.g., `WC_Email_New_Order`).

### The customer is receiving the on-screen confirmation but no email

**Cause:** This is the expected behavior when the toggle is on.
**Fix:** This is by design. If you want both the on-screen confirmation and the email, disable the toggle.

### I want to disable specific emails but not all

**Cause:** The toggle is global.
**Fix:** Configure in the plugin settings to selectively re-enable specific emails. Or use WooCommerce's built-in email settings (WooCommerce > Settings > Emails) to disable individual email types.

---

## Related Articles

- [How to Allow Reset Password Email in WordPress](woocommerce-allow-reset-password-email.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
