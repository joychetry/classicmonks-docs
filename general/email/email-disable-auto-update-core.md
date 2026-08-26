---
title: "How to Disable WordPress Core Auto-Update Emails in WordPress"
slug: disable-auto-update-core
description: "Stop WordPress from sending email notifications when the core software auto-updates. Reduces admin email clutter from routine background updates."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-auto-update-core/
---

# How to Disable WordPress Core Auto-Update Emails in WordPress

> Disable Core Auto-Update Emails stops WordPress from sending the "WordPress X.Y.Z is available" or "WordPress has been updated" notification email to site administrators when the core software auto-updates in the background.

## Key Takeaways

- Single toggle, no nested options
- Affects the admin notification only (the auto-update still happens)
- Useful for sites with frequent background updates
- Reduces inbox clutter
- The core update itself still occurs; only the notification is suppressed

## What Is the Disable Core Auto-Update Emails feature?

WordPress has a background update system that automatically updates the core software, plugins, and themes (when enabled). For core updates, the system sends a notification email to the site admin after the update completes. The email looks like "WordPress X.Y.Z is available" or "Your site has been updated to WordPress X.Y.Z".

The Disable Core Auto-Update Emails feature suppresses this email. The auto-update still happens; only the email notification is removed.

## Why You Need It

For sites with frequent background updates, the email becomes noise:

- A site that auto-updates weekly receives 50+ emails per year from core updates alone
- The admin already has other ways to see core updates (the WordPress dashboard widget, the Updates admin page)
- The email doesn't require action; the update is already done

The trade-off: if a core update introduces a bug or security issue, the email is the admin's signal to check the site. Disabling the email removes that signal. For high-stakes sites, leave it enabled.

---

## How to Use Disable Core Auto-Update Emails in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Email Tab

Click on the **Email** menu, then click the **Notifications** subtab.

### Step 3: Enable Disable Core Auto-Update Emails

Scroll to the **Email Notifications** section and toggle on **Disable Auto Update Notification Emails for Core**.

### Step 4: Save Changes

Click **Save Changes**.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable Auto Update Notification Emails for Core** | Master toggle. | Off |

No nested options.

---

## What Gets Suppressed

| Email | Sent when feature off | Sent when feature on |
|-------|----------------------|----------------------|
| "WordPress X.Y.Z is now available" (pre-update) | Yes | Yes (if auto-update is enabled) |
| "Your site has been updated to WordPress X.Y.Z" (post-update) | Yes | **No** |

The pre-update availability email is part of WordPress's standard update notification flow and is independent of the auto-update email. This feature only suppresses the post-update confirmation.

## What Does NOT Get Affected

- **WordPress core auto-update itself**: Still happens (controlled by `WP_AUTO_UPDATE_CORE` in wp-config.php)
- **Plugin auto-update emails**: Separate feature ([Disable Auto Update Emails for Plugins](email-disable-auto-update-plugins.md))
- **Theme auto-update emails**: Separate feature ([Disable Auto Update Emails for Themes](email-disable-auto-update-themes.md))
- **Pre-update availability notifications**: The "WordPress X.Y.Z is available" email that arrives before the update
- **Plugin/theme manual update emails**: Emails sent when you manually click "Update" on a plugin/theme in the admin

---

## Advanced Options (Developers)

This feature registers 2 WordPress hooks in `disable-update-emails.php`:

**Filters:**

- `auto_core_update_email` calls `disable_auto_update_emails()` (Disables core auto-update notification emails (priority 10))
- `auto_core_update_send_email` calls `apply_filters()` (Customizable filter)

```php
// Hooked in disable-update-emails.php
add_filter( 'auto_core_update_email', 'disable_auto_update_emails' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The auto-update email is still being sent

**Cause:** The toggle is off, or another plugin is sending its own core update notification.
**Fix:** Verify the toggle is on. Check for security or monitoring plugins that may send their own update notifications.

### I disabled core auto-updates entirely (WP_AUTO_UPDATE_CORE=false) but still get the email

**Cause:** The email is sent by the notification system, not the update system. If updates are disabled, the email shouldn't be sent. If it is, a different system is involved.
**Fix:** Check your wp-config.php for the WP_AUTO_UPDATE_CORE constant. If updates are truly disabled, the email shouldn't be sent. If you're still receiving it, the email is coming from a different source (e.g., a security plugin).

### I want a daily summary of updates instead of per-update emails

**Cause:** The current system sends one email per update.
**Fix:** Disable all per-update emails (Core, Plugins, Themes), then add a custom cron job that runs daily and emails a summary of all updates from the last 24 hours. Use the `automatic_updates_complete` action to log updates to a transient, and a custom cron to read and email the summary.

### I want to keep the email but change its content

**Cause:** The toggle is global (on/off only).
**Fix:** Leave the toggle off and customize the email content via the `auto_core_update_email` filter. This shows you the email data before it's sent and lets you modify the subject and body.

### I want the email for security updates but not for feature releases

**Cause:** WordPress doesn't distinguish security vs feature updates in the email; it sends one email for all core updates.
**Fix:** This is not currently possible with WordPress's email system. You'd need a custom plugin that intercepts core updates and sends the email only for security versions (a known issue: WordPress does include a `core_update_type` field but it's not exposed to filters).

---

## Related Articles

- [How to Configure SMTP Settings in WordPress](email-smtp-settings.md)
- [How to Disable Plugin Auto-Update Emails in WordPress](email-disable-auto-update-plugins.md)
- [How to Disable Theme Auto-Update Emails in WordPress](email-disable-auto-update-themes.md)
