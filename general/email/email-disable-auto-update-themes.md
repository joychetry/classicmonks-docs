---
title: "How to Disable Theme Auto-Update Emails in WordPress"
slug: disable-auto-update-themes
description: "Stop WordPress from sending email notifications when themes auto-update in the background. Reduces admin email clutter from routine theme updates."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-auto-update-themes/
---

# How to Disable Theme Auto-Update Emails in WordPress

> Disable Theme Auto-Update Emails stops WordPress from sending the "Some themes were automatically updated" notification email to site administrators when themes auto-update in the background.

## Key Takeaways

- Single toggle, no nested options
- Affects the admin notification only (the auto-update still happens)
- Useful for sites with multiple installed themes and auto-updates enabled
- Reduces inbox clutter
- The theme update itself still occurs; only the notification is suppressed

## What Is the Disable Theme Auto-Update Emails feature?

WordPress's background update system can auto-update installed themes (when enabled). When themes auto-update, WordPress sends a notification email to the site admin listing the updated themes.

The Disable Theme Auto-Update Emails feature suppresses this email. The auto-updates still happen; only the notification is removed.

## Why You Need It

For sites with multiple themes installed (common for staging environments, multi-brand deployments, or theme testing workflows), the email can be a constant stream:

- A site with 5 themes and auto-updates enabled might receive 5-10 theme update emails per month
- Most sites only actively use one theme; the other themes are dormant
- The email doesn't require action; the updates are already done

The trade-off: if a theme auto-update introduces a bug or breaks the design, the email is the admin's signal to test the site. Disabling the email removes that signal. For high-stakes sites, leave it enabled.

---

## How to Use Disable Theme Auto-Update Emails in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Email Tab

Click on the **Email** menu, then click the **Notifications** subtab.

### Step 3: Enable Disable Theme Auto-Update Emails

Scroll to the **Email Notifications** section and toggle on **Disable Auto Update Notification Emails for Themes**.

### Step 4: Save Changes

Click **Save Changes**.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable Auto Update Notification Emails for Themes** | Master toggle. | Off |

No nested options.

---

## What Gets Suppressed

| Email | Sent when feature off | Sent when feature on |
|-------|----------------------|----------------------|
| "Some themes have been updated" (after auto-update) | Yes | **No** |
| Manual theme update email (from clicking "Update") | Yes | Yes (separate flow) |
| Theme activation/switch emails | Yes | Yes (separate flow) |

The feature only suppresses the auto-update-specific email. Manual updates and theme switching notifications are unaffected.

## What Does NOT Get Affected

- **Theme auto-update itself**: Still happens (controlled by each theme's "auto-update" setting)
- **WordPress core auto-update emails**: Separate feature ([Disable Core Auto-Update Emails](email-disable-auto-update-core.md))
- **Plugin auto-update emails**: Separate feature ([Disable Plugin Auto-Update Emails](email-disable-auto-update-plugins.md))
- **Manual theme update emails**: Sent when an admin clicks "Update" on a theme
- **Theme switch emails**: Different email flow (when an admin switches the active theme)

---

## Advanced Options (Developers)

This feature registers 2 WordPress hooks in `disable-update-emails.php`:

**Filters:**

- `auto_theme_update_send_email` calls `disable_theme_update_emails()` (Disables theme auto-update notification emails)
- `auto_theme_update_send_email` calls `apply_filters()` (Customizable filter)

```php
// Hooked in disable-update-emails.php
add_filter( 'auto_theme_update_send_email', 'disable_theme_update_emails' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The theme auto-update email is still being sent

**Cause:** The toggle is off, or another plugin is sending its own theme update notification.
**Fix:** Verify the toggle is on. Check for security or monitoring plugins that may send their own update notifications.

### I disabled theme auto-updates for all my themes but still get the email

**Cause:** The email is only suppressed if there were updates. If no themes auto-updated, no email is sent. If at least one did, the email is sent (regardless of how many were excluded).
**Fix:** Verify which themes are set to auto-update (Appearance > Themes > Theme Details > auto-update toggle). If at least one theme is set to auto-update, the email will be sent when that theme updates.

### I want a daily summary of theme updates instead of per-update emails

**Cause:** WordPress sends one email per auto-update run.
**Fix:** Disable all auto-update emails (Core, Plugins, Themes), then add a custom cron job that runs daily and emails a summary of all theme updates from the last 24 hours. Use the `auto_theme_update_email` filter to log updates to a transient, and a custom cron to read and email the summary.

### I disabled theme auto-updates via wp-config.php (DISALLOW_FILE_MODS)

**Cause:** The `DISALLOW_FILE_MODS` constant blocks theme auto-updates entirely; the email is irrelevant.
**Fix:** The email will not be sent because updates are not happening. The toggle is irrelevant in this case. The toggle is for sites that allow updates but want to suppress the email.

### I want the email for security-related theme updates only

**Cause:** WordPress does not distinguish security vs feature theme updates in the email.
**Fix:** This is not currently possible with WordPress's email system. You'd need a custom plugin that tracks which themes have security flags and sends emails only for those.

---

## Related Articles

- [How to Configure SMTP Settings in WordPress](email-smtp-settings.md)
- [How to Disable WordPress Core Auto-Update Emails](email-disable-auto-update-core.md)
- [How to Disable Plugin Auto-Update Emails in WordPress](email-disable-auto-update-plugins.md)
