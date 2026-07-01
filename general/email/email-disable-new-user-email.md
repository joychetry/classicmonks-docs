---
title: "How to Disable New User Email in WordPress | CM"
slug: email/disable-new-user-email
description: "Stop WordPress from sending the welcome email to admins when new users register. Reduces admin email volume, especially on high-traffic membership sites."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/email/disable-new-user-email/
---

# How to Disable New User Email in WordPress

> Disable New User Email stops WordPress from sending the "New User Registration" notification email to site administrators when new users register. The new user still receives their welcome email.

## Key Takeaways

- Single toggle, no nested options
- Affects admin notification only (new user welcome email is still sent)
- Useful for high-volume membership sites
- Reduces admin inbox clutter
- New user still receives their account confirmation

## What Is the Disable New User Email feature?

When a new user registers on a WordPress site, two emails are typically sent:

1. **Admin notification**: Sent to the site admin email address, notifying them of the new registration
2. **User welcome**: Sent to the new user, welcoming them and (optionally) including a password setup link

The Disable New User Email feature suppresses the first email. The second email (user welcome) is still sent. The new user experience is unchanged; only the admin stops getting notifications.

## Why You Need It

For sites with frequent new user registrations (membership sites, e-commerce with customer accounts, forums, learning platforms), the admin notification email becomes a constant stream:

- A forum with 50 new users per day = 50 admin emails per day = 1,500 per month
- The admin already has other ways to see new users (the WordPress Users admin page, the dashboard widget)
- The email is informational only; it doesn't require action

Suppressing the email frees the admin inbox. The admin can still see all new users via the standard WordPress admin pages.

---

## How to Use Disable New User Email in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Email Tab

Click on the **Email** menu, then click the **Notifications** subtab.

### Step 3: Enable Disable New User Email

Scroll to the **Email Notifications** section and toggle on **Disable New User Email**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Register a new test user. The new user receives their welcome email. The admin does NOT receive a notification.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable New User Email** | Master toggle. | Off |

No nested options.

---

## What Gets Suppressed

| Email | Sent when feature off | Sent when feature on |
|-------|----------------------|----------------------|
| Admin "New User Registration" notification | Yes | **No** |
| User welcome email with password setup link | Yes | Yes (always) |
| User email verification (if email confirmations are enabled) | Yes | Yes (always) |

The feature only suppresses the admin notification. The user-facing emails are unaffected.

## What Does NOT Get Affected

- **User welcome email**: Always sent (unless disabled separately via a different mechanism)
- **User email verification**: If your site has email verification enabled, that flow is independent
- **Admin user list**: The WordPress Users > Add New / All Users page still shows all registered users
- **Custom registration flows**: Membership plugins (MemberPress, Ultimate Member, etc.) handle their own registration emails
- **WooCommerce customer registration**: WooCommerce has its own email flow; see [Disable WooCommerce Emails](email-disable-woocommerce-emails.md)

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `email-functions.php`:

**Filters:**

- `send_password_change_email` calls `cm_disable_password_change_email()` (Disables password change notification emails)

```php
// Hooked in email-functions.php
add_filter( 'send_password_change_email', 'cm_disable_password_change_email' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The admin is still receiving new user emails

**Cause:** The toggle is off, or a custom plugin is sending its own admin notification.
**Fix:** Verify the toggle is on. Check for membership or community plugins that send their own admin notifications on new user registration.

### I want admin notifications for some user roles but not others

**Cause:** The toggle is global.
**Fix:** Disable the toggle globally, then use a custom plugin that filters `user_register` and sends notifications only for specific roles (e.g., only "customer" role, not "subscriber").

### I want to log new user registrations elsewhere (e.g., a CRM)

**Cause:** The admin email was the original mechanism for tracking new users; disabling it removes the trigger.
**Fix:** Add a custom hook on `user_register` that pushes the new user to your CRM via API (e.g., a webhook to HubSpot, Salesforce, etc.). The Classic Monks email log can also track the user welcome email.

### I disabled the email but I still see notifications in another channel

**Cause:** You have a different notification system (e.g., a security plugin, an activity log plugin) that tracks new user registrations independently of email.
**Fix:** Those plugins are independent. Disable their notifications separately, or accept that they exist for security reasons.

### The user welcome email is also being suppressed

**Cause:** The user welcome email is sent via a different WordPress filter. If you've customized the user welcome email or are using a plugin that suppresses it, that suppression is unrelated to this feature.
**Fix:** Verify the user welcome email is sent (the new user should receive a "Your account has been created" email). If it's not sent, check your email configuration and any membership plugins that may be interfering.

---

## Related Articles

- [How to Configure SMTP Settings in WordPress](email-smtp-settings.md)
- [How to Log WordPress Emails in Classic Monks](email-logging.md)
- [How to Enable Comment Reply Email in WordPress](email-comment-reply-email.md)
