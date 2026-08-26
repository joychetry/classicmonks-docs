---
title: "How to Disable Admin Email Change Notification in WordPress"
slug: disable-admin-email-change
description: "Stop WordPress from sending the verification email when the site admin email address is changed. Speeds up admin email updates and removes the verification step."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-admin-email-change/
---

# How to Disable Admin Email Change Notification in WordPress

> Disable Admin Email Change removes the verification email that WordPress sends when the site admin email address is changed. The change takes effect immediately without requiring email confirmation.

## Key Takeaways

- Single toggle, no nested options
- Removes the verification step for admin email changes
- Admin email updates take effect immediately
- Useful for sites with multiple admins or managed WordPress
- Reduces friction for routine admin email updates

## What Is the Disable Admin Email Change feature?

When the site admin email address is changed (in Settings > General > Administration Email Address), WordPress sends a verification email to the new address. The new address is not active until the new admin clicks a confirmation link in the email. This is a security measure to prevent unauthorized admin email changes.

The Disable Admin Email Change feature removes this verification step. The new admin email address becomes active immediately upon saving the change, without requiring email confirmation.

## Why You Need It

For most sites, the verification step is unnecessary friction:

- **Single-admin sites**: The person making the change is the only admin. Verification just adds an extra step.
- **Managed WordPress**: Sites managed by agencies or hosting providers update the admin email as part of routine operations. Verification is friction without security value.
- **Multisite networks**: Network admins update admin emails frequently. The verification step doesn't add value in trusted network contexts.
- **Trusted internal teams**: When multiple admins work on the same site, the verification is unnecessary because the change is intentional.

The trade-off: the verification is a security measure to prevent an attacker who has compromised an admin account from changing the admin email (which would let them reset the password). For high-security sites, leave verification enabled.

---

## How to Use Disable Admin Email Change in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Email Tab

Click on the **Email** menu, then click the **Notifications** subtab.

### Step 3: Enable Disable Admin Email Change

Scroll to the **Email Notifications** section and toggle on **Disable Admin Email Change**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Go to **Settings > General** in WordPress. Change the **Administration Email Address** to a new address you control. Click **Save Changes**. The new address becomes active immediately. No verification email is sent.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable Admin Email Change** | Master toggle. | Off |

No nested options.

---

## What Gets Suppressed

| Action | When feature off | When feature on |
|--------|------------------|------------------|
| Change admin email | New address is pending until confirmation link is clicked | New address is active immediately |
| Verification email sent | Yes | **No** |
| Confirmation link required | Yes | **No** |

The change is permanent and immediate once saved. There is no rollback to the old address unless the admin manually changes it back.

## What Does NOT Get Affected

- **User email changes**: When individual users change their own email in their profile, the normal WordPress verification flow is used (separate from the admin email change)
- **New admin email notifications**: When a new user is created with the "admin" role, they receive their own welcome email
- **Password reset emails**: Separate flow with its own verification
- **Multisite network admin email changes**: Controlled by network admin settings, not site settings

---

## Advanced Options (Developers)

This feature registers 2 WordPress hooks in `email-functions.php`:

**Filters:**

- `send_site_admin_email_change_email` calls `cm_disable_admin_email_change()` (Disables admin email change notification)
- `send_site_admin_email_change_email` calls `apply_filters()` (Customizable filter)

```php
// Hooked in email-functions.php
add_filter( 'send_site_admin_email_change_email', 'cm_disable_admin_email_change' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The admin email change still requires verification

**Cause:** The toggle is off, or another plugin is enforcing verification.
**Fix:** Verify the toggle is on. Check for security plugins that may enforce admin email verification independently.

### I disabled it but the verification email is still being sent

**Cause:** The verification email is sent by WordPress core via the `send_site_admin_email_change_email` filter. The Classic Monks feature hooks into this filter. If another plugin is also hooking into this filter and forcing `true`, the verification is sent.
**Fix:** Disable other admin-related plugins to find the conflict. Or use the `send_site_admin_email_change_email` filter with a higher priority to force `false`.

### The admin email change didn't take effect

**Cause:** The change requires saving Settings > General in addition to the Classic Monks toggle.
**Fix:** After enabling the Classic Monks feature, go to **Settings > General > Administration Email Address** and change it. The change takes effect immediately on save.

### I want to keep verification for high-security changes but allow routine ones

**Cause:** The toggle is global.
**Fix:** Disable the toggle globally and implement a custom plugin that filters `pre_update_option_admin_email` to skip verification for specific user roles (e.g., only allow admin email changes for super admins without verification).

### I want to send a custom notification (e.g., to a Slack channel) when the admin email changes

**Cause:** The verification email is one signal; you may want other signals too.
**Fix:** Use the `update_option_admin_email` action (or `pre_update_option_admin_email` filter) to trigger a custom notification via Slack, Discord, SMS, etc. The action runs whenever the option is updated, regardless of whether the verification email is sent.

---

## Related Articles

- [How to Configure SMTP Settings in WordPress](email-smtp-settings.md)
- [How to Disable Password Change Email in WordPress](email-disable-password-change-email.md)
- [How to Disable New User Email in WordPress](email-disable-new-user-email.md)
