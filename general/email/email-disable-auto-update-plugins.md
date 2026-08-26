---
title: "How to Disable Plugin Auto-Update Emails in WordPress"
slug: disable-auto-update-plugins
description: "Stop WordPress from sending email notifications when plugins auto-update in the background. Reduces admin email clutter from routine plugin updates."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-auto-update-plugins/
---

# How to Disable Plugin Auto-Update Emails in WordPress

> Disable Plugin Auto-Update Emails stops WordPress from sending the "Some plugins were automatically updated" notification email to site administrators when plugins auto-update in the background.

## Key Takeaways

- Single toggle, no nested options
- Affects the admin notification only (the auto-update still happens)
- Useful for sites with many plugins and frequent background updates
- Reduces inbox clutter
- The plugin update itself still occurs; only the notification is suppressed

## What Is the Disable Plugin Auto-Update Emails feature?

WordPress's background update system can auto-update individual plugins (when enabled via the `auto_update_plugin` filter or the "Enable auto-updates" link on each plugin's row in the Plugins page). When multiple plugins update in the same background run, WordPress sends a single consolidated email to the site admin listing all the updated plugins.

The Disable Plugin Auto-Update Emails feature suppresses this consolidated email. The auto-updates still happen; only the notification is removed.

## Why You Need It

For sites with many plugins and auto-updates enabled, the email becomes a constant stream:

- A site with 30 plugins and auto-updates enabled might receive 5-10 plugin update emails per week
- The admin already has other ways to see plugin updates (the Plugins page, the dashboard widget, the Updates admin page)
- The email doesn't require action; the updates are already done

The trade-off: if a plugin auto-update introduces a bug or breaks compatibility, the email is the admin's signal to test the site. Disabling the email removes that signal. For high-stakes sites, leave it enabled.

---

## How to Use Disable Plugin Auto-Update Emails in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Email Tab

Click on the **Email** menu, then click the **Notifications** subtab.

### Step 3: Enable Disable Plugin Auto-Update Emails

Scroll to the **Email Notifications** section and toggle on **Disable Auto Update Notification Emails for Plugins**.

### Step 4: Save Changes

Click **Save Changes**.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable Auto Update Notification Emails for Plugins** | Master toggle. | Off |

No nested options.

---

## What Gets Suppressed

| Email | Sent when feature off | Sent when feature on |
|-------|----------------------|----------------------|
| "Some plugins have been updated" (after auto-update) | Yes | **No** |
| Manual plugin update email (from clicking "Update") | Yes | Yes (separate flow) |
| Plugin activation/deactivation emails | Yes | Yes (separate flow) |

The feature only suppresses the auto-update-specific email. Manual updates and activation/deactivation notifications are unaffected.

## What Does NOT Get Affected

- **Plugin auto-update itself**: Still happens (controlled by each plugin's "auto-update" setting)
- **WordPress core auto-update emails**: Separate feature ([Disable Core Auto-Update Emails](email-disable-auto-update-core.md))
- **Theme auto-update emails**: Separate feature ([Disable Theme Auto-Update Emails](email-disable-auto-update-themes.md))
- **Manual plugin update emails**: Sent when an admin clicks "Update" on a plugin
- **Plugin activation/deactivation emails**: Different email flow

---

## Advanced Options (Developers)

This feature registers 2 WordPress hooks in `disable-update-emails.php`:

**Filters:**

- `auto_plugin_update_send_email` calls `disable_plugin_update_emails()` (Disables plugin auto-update notification emails (priority 10))
- `auto_plugin_update_send_email` calls `apply_filters()` (Customizable filter)

```php
// Hooked in disable-update-emails.php
add_filter( 'auto_plugin_update_send_email', 'disable_plugin_update_emails' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The plugin auto-update email is still being sent

**Cause:** The toggle is off, or another plugin is sending its own plugin update notification.
**Fix:** Verify the toggle is on. Check for security or monitoring plugins that may send their own update notifications.

### I want a daily summary of plugin updates instead of per-update emails

**Cause:** WordPress sends one email per auto-update run.
**Fix:** Disable all auto-update emails (Core, Plugins, Themes), then add a custom cron job that runs daily and emails a summary of all plugin updates from the last 24 hours. Use the `auto_plugin_update_email` filter to log updates to a transient, and a custom cron to read and email the summary.

### I disabled auto-updates for some plugins but still get the email

**Cause:** The email is only suppressed if there were updates. If no plugins auto-updated, no email is sent. If at least one did, the email is sent (regardless of how many were excluded).
**Fix:** Verify which plugins are set to auto-update (Plugins > All Plugins > auto-update column). If at least one plugin is set to auto-update, the email will be sent when that plugin updates.

### I want to keep the email but suppress the body

**Cause:** The toggle is global.
**Fix:** Disable the toggle and add a custom filter that intercepts the email and replaces the body with an empty string. This effectively mutes the email while keeping the option enabled (which is useful if the toggle is managed by a configuration management system).

### I want the email for security-related plugin updates only

**Cause:** WordPress does not distinguish security vs feature plugin updates in the email.
**Fix:** This is not currently possible with WordPress's email system. Plugin update emails are sent for all plugin auto-updates, not just security ones. You'd need a custom plugin that tracks which plugins have security flags and sends emails only for those.

---

## Related Articles

- [How to Configure SMTP Settings in WordPress](email-smtp-settings.md)
- [How to Disable WordPress Core Auto-Update Emails](email-disable-auto-update-core.md)
- [How to Disable Theme Auto-Update Emails in WordPress](email-disable-auto-update-themes.md)
