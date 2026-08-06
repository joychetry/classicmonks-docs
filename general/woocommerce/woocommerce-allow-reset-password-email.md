---
title: "How to Keep the Reset Password Email in WooCommerce"
slug: allow-reset-password-email
description: "Keep the WooCommerce customer reset password email working even when the other WooCommerce emails are disabled. Preserve account recovery with Classic Monks."
last_updated: 2026-08-06
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/allow-reset-password-email/
merged_docs: "How to Only Allow Reset Password Email in WordPress (Email tab)"
---

# How to Keep the Reset Password Email in WooCommerce

> Keep the WooCommerce customer reset password email active even when the other WooCommerce emails are disabled. Classic Monks lets you preserve account recovery while suppressing the rest of the transactional emails.

## Key Takeaways

- Keep the customer reset password email working
- Works together with the Disable WooCommerce Emails feature
- Ensures customers can always recover account access
- One toggle inside the WooCommerce Email settings
- Suppresses all other email classes when the disable feature is active

## What Does the Feature Do?

The **Allow Reset Password Email** option controls whether the WooCommerce customer reset password email stays active when the **Disable WooCommerce Emails** feature is turned on.

When you disable all WooCommerce emails, every WooCommerce email class is normally suppressed. If you also enable **Allow Reset Password Email**, the reset password email class is excluded from that suppression, so customers can still recover their accounts even though the other transactional emails are off.

## Why You Need It

Account recovery is too important to lose:

- A customer who cannot receive a password reset email may lose access to their account and orders
- Disabling all emails can unintentionally break the password reset flow
- Keeping this one email active preserves security and self-service recovery
- It lets you quiet the rest of the transactional emails without a support burden

---

## How to Keep the Reset Password Email When Other WooCommerce Emails Are Off

### Step 1: Disable the Other WooCommerce Emails

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Email** settings area.
3. Toggle on **Disable WooCommerce Emails** to suppress the transactional email classes.

### Step 2: Keep the Reset Password Email

1. In the same **Email** settings area, toggle on **Allow Reset Password Email**.
2. With both on, the reset password email class continues to work while the other WooCommerce emails are suppressed.

### Step 3: Save and Test

Click **Save Changes**. Use the forgot-password flow at login and confirm the reset password email still reaches the customer, while other transactional emails (such as new-order notifications) are suppressed.

---

## Configuration Options

| Option | Effect | Default |
|--------|--------|---------|
| **Disable WooCommerce Emails** | Suppresses the WooCommerce transactional email classes. | Off |
| **Allow Reset Password Email** | Excepts the reset password email class from the suppression. | Off |

The option only matters when **Disable WooCommerce Emails** is also on. With the disable feature off, all emails send normally and this toggle has no visible effect.

---

## What Gets Affected

- The customer reset password email: kept active when the disable feature is on and this toggle is enabled
- The other WooCommerce email classes: still suppressed by the disable feature

## What Does NOT Get Affected

- WooCommerce's other transactional emails when the disable feature is on: these remain suppressed
- On-screen checkout and order pages: unaffected
- WordPress core emails: separate, not controlled here

---

## How It Works

The reset password email is kept alive inside `cm_disable_woocommerce_emails()`. When the disable feature runs, it iterates over the WooCommerce email classes and disables each one, but it **skips** the `WC_Email_Customer_Reset_Password` class when the **Allow Reset Password Email** option is enabled. The result is that only the reset password email survives the bulk suppression.

---

## Common Use Cases

**Quiet email flow with account security.** Stores that want to stop most transactional emails but keep customer account recovery working.

**Self-service support.** Keeping password reset reduces customer support requests for locked accounts.

**Controlled email rollouts.** Using WooCommerce for emails while suppressing the extra transactional noise.

---

## Troubleshooting

### The reset password email is not sending

**Cause:** The **Allow Reset Password Email** toggle is off, the disable feature is off (so emails send normally but this toggle is moot), or the password reset flow itself is not triggering.
**Fix:** Confirm both toggles are set as intended. For an issue with the flow itself, check that the WordPress lost-password mechanism works, since WooCommerce sends through that path.

### All emails are suppressed including reset password

**Cause:** **Allow Reset Password Email** is off while **Disable WooCommerce Emails** is on.
**Fix:** Turn on **Allow Reset Password Email** so the reset password email class is exempted from suppression.

### The other emails still send

**Cause:** The disable feature is off, so no suppression applies.
**Fix:** If you want the other emails suppressed, turn on **Disable WooCommerce Emails**. The reset password setting only takes effect alongside it.

---

## Frequently Asked Questions

### Why would I keep only the reset password email?

To stop most transactional email noise while ensuring customers can still recover accounts they have accidentally locked themselves out of. It preserves security and reduces support load.

### Do I need to enable both toggles?

To keep reset password working while suppressing the rest, yes: **Disable WooCommerce Emails** on and **Allow Reset Password Email** on.

### Does this change my checkout or order processing?

No. The feature only controls the WooCommerce email classes. Orders and checkout work normally.

### Is the reset password email a WooCommerce email?

Yes. It is the `WC_Email_Customer_Reset_Password` class, which WooCommerce registers alongside the order emails. This feature exceptions that one class from the bulk disable.

---

## Related Articles

- [How to Disable the WooCommerce Transactional Emails](woocommerce-disable-woocommerce-emails.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
- [How to Log WordPress Emails in Classic Monks](../email/email-logging.md)
