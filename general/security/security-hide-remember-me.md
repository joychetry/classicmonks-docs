---
title: "How to Hide the Remember Me Checkbox in WordPress"
slug: hide-remember-me
description: "Hide the Remember Me checkbox on the WordPress login form. Forces all logins to expire at the end of the session, improving security for shared or public computers."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/hide-remember-me/
---

# How to Hide the Remember Me Checkbox in WordPress

> Hide Remember Me Checkbox removes the "Remember Me" option from the WordPress login form. Forces all sessions to expire when the browser closes, which is more secure for shared or public computers.

## Key Takeaways

- Single toggle, no nested options
- Removes the "Remember Me" checkbox from the login form
- All sessions expire when the browser closes
- Pairs well with the [Auto Logout](security-auto-logout.md) feature
- Use this for high-security sites where long sessions are a concern

## What Is the Hide Remember Me Checkbox feature?

By default, the WordPress login form has a "Remember Me" checkbox. When checked, the user's session persists for 14 days (even if the browser is closed). When unchecked, the session expires when the browser closes.

The Hide Remember Me Checkbox feature removes this checkbox from the login form, forcing all sessions to expire at browser close.

## Why You Need It

Long sessions are convenient but create security risks:

- **Shared computers**: An admin who forgets to log out leaves a persistent session
- **Lost or stolen devices**: A 14-day session is still valid even after the device is gone
- **Public computers**: Anyone using the computer after the admin can stay logged in

For high-security sites, forcing session expiry at browser close is a critical hardening step.

---

## How to Hide the Remember Me Checkbox in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **WP Protection** subtab.

### Step 3: Enable Hide Remember Me Checkbox

Scroll to **Hide Remember Me Checkbox** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Log out. Visit the login form. The "Remember Me" checkbox should not be visible.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Hide Remember Me Checkbox** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- The login form: the "Remember Me" checkbox is removed
- The user sessions: all sessions expire when the browser closes
- The default session duration: changed from 14 days to "session" (browser close)

## What Does NOT Get Affected

- The wp-admin: not affected (after login)
- The user experience: users don't notice the difference unless they try to stay logged in
- The custom login forms: not affected (only the default WordPress login form)
- The remember me functionality: still works if the user manually sets the cookie (not via the checkbox)

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `security-functions.php`:

**Actions:**

- `login_head` calls `cm_hide_remember_me()` (Hides Remember Me checkbox via CSS)

```php
// Hooked in security-functions.php
add_action( 'login_head', 'cm_hide_remember_me' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The Remember Me checkbox is still showing

**Cause:** The toggle is off, or a custom login form is being used.
**Fix:** Verify the toggle is on. The feature only affects the default WordPress login form (`wp-login.php`). Custom login forms (e.g., WooCommerce's login) are not affected.

### Users are being logged out too frequently

**Cause:** The session is now expiring at browser close, which is more frequent than the default 14-day remember me.
**Fix:** This is the expected behavior of the feature. If you need longer sessions, use the Stay Logged In feature (see related articles) which adds a "stay logged in" checkbox that can be configured for longer sessions.

### The custom login form is not affected

**Cause:** The Hide Remember Me feature only affects the default WordPress login form.
**Fix:** If you use a custom login form (e.g., WooCommerce, a custom theme login), use the `login_form` action to remove the checkbox from the custom form. Or use a CSS selector to hide it.

### The session is still 14 days

**Cause:** A caching plugin or another plugin is setting the auth cookie duration.
**Fix:** Check for plugins that override the auth cookie duration. Use the `auth_cookie_expiration` filter to set a custom duration.

---

## Related Articles

- [How to Use Auto Logout in WordPress](security-auto-logout.md)
- [How to Enable Stay Logged In in WordPress](security-stay-logged-in.md)
- [How to Use a Custom Login URL in WordPress](security-custom-login-url.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
