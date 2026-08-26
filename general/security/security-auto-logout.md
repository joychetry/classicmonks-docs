---
title: "How to Use Auto Logout in WordPress"
slug: auto-logout
description: "Automatically log out idle users after a configurable timeout in Classic Monks. Reduces risk of unauthorized access on shared or unattended computers."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/auto-logout/
---

# How to Use Auto Logout in WordPress

> Auto Logout automatically logs out users after a configurable period of inactivity. Reduces risk of unauthorized access on shared, public, or unattended computers.

## Key Takeaways

- Single toggle with 1 sub-option (timeout duration)
- Logs out users after a configurable period of inactivity
- Protects against unauthorized access on shared computers
- Resets on user activity (clicking, typing, scrolling)
- Configurable timeout in minutes

## What Is the Auto Logout feature?

By default, WordPress keeps users logged in indefinitely (until they explicitly log out or their session cookie expires, which is typically 48 hours or 2 weeks depending on the "Remember Me" setting). The Auto Logout feature adds a configurable idle timeout: after a set period of inactivity, the user is automatically logged out.

This is a critical security feature for any WordPress site with admin users logging in from shared, public, or unattended computers.

## Why You Need It

WordPress's default behavior assumes the user controls the device:

- An admin walks away from a logged-in computer
- A public library computer stays logged in after the user leaves
- A shared device in an office or co-working space remains accessible
- A laptop is stolen while still logged in

Auto Logout reduces these risks by enforcing a session timeout.

---

## How to Use Auto Logout in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **WP Protection** subtab.

### Step 3: Enable Auto Logout

Scroll to **Enable Auto Logout** and toggle on. Nested options expand.

### Step 4: Set the Timeout

Set the **Auto Logout Timeout** in minutes. Common values:

- **15 minutes**: For high-security sites (banking, healthcare)
- **30 minutes**: For most business sites
- **60 minutes**: For low-risk internal sites
- **120 minutes**: For very low-risk sites where convenience matters

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Test

Log in as a user. Wait for the configured timeout. You should be automatically logged out.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Auto Logout** | Master toggle. | Off |
| **Auto Logout Timeout** | Timeout in minutes. | 30 |

The timeout is reset on any user activity (clicking, typing, scrolling).

---

## What Gets Affected

- The user's session: expires after the timeout
- The user's cookies: cleared on auto-logout
- The WordPress admin: redirects to the login page after timeout
- The user's unsaved changes: may be lost (this is expected)

## What Does NOT Get Affected

- The user's saved preferences: preserved (in user meta)
- The user's posts or content: not affected
- The customizer or editor drafts: preserved (auto-saved before the timeout)
- API tokens: not affected (use a different auth flow)

---

## Advanced Options (Developers)

This feature registers 2 WordPress hooks in `auto-logout.php`:

**Actions:**

- `wp_enqueue_scripts` calls `cm_auto_logout_enqueue_scripts()` (Enqueues auto-logout countdown timer JS)
- `init` calls `cm_auto_logout_check_timeout()` (Checks session timeout on each page load)

```php
// Hooked in auto-logout.php
add_action( 'wp_enqueue_scripts', 'cm_auto_logout_enqueue_scripts' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The user is logged out too quickly

**Cause:** The timeout is set too low, or the activity detection is not working.
**Fix:** Increase the timeout. Check that the JavaScript for activity detection is loading (View Source on any admin page; the activity tracker should be present).

### The user is not logged out

**Cause:** The toggle is off, or the JavaScript is not running.
**Fix:** Verify the toggle is on. Check the browser console for errors. The auto-logout feature uses client-side JavaScript to track activity; if JavaScript is disabled, auto-logout won't work.

### The user is logged out but the screen is not redirected

**Cause:** A theme or plugin is intercepting the redirect.
**Fix:** Check for plugins that disable redirects. Test with a default theme.

### The auto-logout timer is being reset by background activity

**Cause:** A long-running process (e.g., video, audio) is generating activity events.
**Fix:** Use the `cm_auto_logout_activities` filter to remove noisy events. Or use a more restrictive set of activity events (e.g., only "click" and "keypress").

### The user is logged out during form filling

**Cause:** The user paused for too long while filling a form.
**Fix:** Increase the timeout. The form should be saved frequently (WordPress auto-saves posts and pages; for other forms, the user can use browser form restoration).

---

## Related Articles

- [How to Enable Login Lockdown in WordPress](security-login-lockdown.md)
- [How to Use a Custom Login URL in WordPress](security-custom-login-url.md)
- [How to Enable Stay Logged In in WordPress](security-stay-logged-in.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
