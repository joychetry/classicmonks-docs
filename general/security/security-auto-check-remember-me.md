---
title: "How to Auto-check Remember Me in WordPress | CM"
slug: security/auto-check-remember-me
description: "Auto-check the Remember Me checkbox on the WordPress login form. Ensures users always have the longest session possible by default."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/security/auto-check-remember-me/
---

# How to Auto-check Remember Me in WordPress

> Auto-check Remember Me in Classic Monks automatically checks the "Remember Me" checkbox on the WordPress login form. Users always get the longest session by default, without needing to manually check the box.

## Key Takeaways

- Single toggle, no nested options
- Pre-checks the "Remember Me" checkbox on the login form
- Pairs with [Stay Logged In](security-stay-logged-in.md) for maximum session duration
- Users can still uncheck it manually if they want a session-only login
- Useful for sites where long sessions are preferred

## What Is the Auto-check Remember Me feature?

By default, the WordPress login form has an unchecked "Remember Me" checkbox. Users who want a long session (14 days by default, 30 days with [Stay Logged In](security-stay-logged-in.md)) need to manually check the box.

The Auto-check Remember Me feature pre-checks the box on page load, so users automatically get the long session unless they uncheck it.

## Why You Need It

The default behavior (unchecked) assumes most users want short sessions. But for many sites, this is the opposite of what users want:

- **Most users prefer long sessions**: They don't want to log in every 2 weeks
- **Manual check is friction**: Forgetting to check means a shorter session
- **Forgotten sessions hurt UX**: Users who get logged out unexpectedly blame the site, not themselves
- **Internal sites**: For company intranets or member sites, users expect to stay logged in

The Auto-check Remember Me feature is for sites where long sessions are the default expectation.

## Trade-offs vs manual check

Auto-checking has trade-offs:

- **Shared devices**: Users who share devices (e.g., library computers) may forget to uncheck
- **Stolen devices**: A stolen device with auto-check has a longer valid session
- **Public computers**: Kiosks and public computers should never have Remember Me checked
- **Compliance**: Some regulations require short sessions for sensitive data

For most public-facing sites, the default (unchecked) is appropriate. For internal sites or trusted environments, auto-check is useful.

---

## How to Auto-check Remember Me in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Stay Logged In** subtab.

### Step 3: Enable Auto-check Remember Me

Scroll to **Auto-check Remember Me on Login Page** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit the login form. The "Remember Me" checkbox should be pre-checked. If you want a session-only login, uncheck the box before submitting.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Auto-check Remember Me** | Master toggle. | Off |

No nested options. The pre-check applies to all users (no per-role control).

---

## What Gets Affected

- The login form: the "Remember Me" checkbox is pre-checked
- The default session duration: users get the long session by default
- The user experience: one less thing to remember to check

## What Does NOT Get Affected

- The user's ability to uncheck: users can still uncheck the box manually
- The session duration itself: still controlled by WordPress core + [Stay Logged In](security-stay-logged-in.md)
- The wp-admin: not affected (after login)
- The user roles: not affected

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `stay-logged-in.php`:

**Actions:**

- `login_footer` calls `cm_remember_me_checked()` (Auto-checks Remember Me checkbox on login form)

```php
// Hooked in stay-logged-in.php
add_action( 'login_footer', 'cm_remember_me_checked' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The Remember Me checkbox is not pre-checked

**Cause:** The toggle is off, or a custom login form is being used.
**Fix:** Verify the toggle is on. The feature only affects the default WordPress login form. Custom login forms (e.g., WooCommerce, theme login) are not affected.

### Users are being logged out unexpectedly on shared devices

**Cause:** The Remember Me is auto-checked, and users forget to uncheck it.
**Fix:** Disable the toggle. Or adjust the affected roles in the plugin settings under Security > Auto Check Remember Me.

### I want different behavior for different forms

**Cause:** The feature is global.
**Fix:** Use the `cm_auto_check_remember_me_enabled` filter to check the form context. Different forms have different `$context` values (e.g., 'login', 'lostpassword').

### The cookie is not being set as expected

**Cause:** Browser settings or a caching plugin is interfering.
**Fix:** Check browser settings (e.g., "Block all cookies" should be off). Verify the cookie is being set by viewing the page's cookies in the browser's developer tools.

---

## Related Articles

- [How to Enable Stay Logged In in WordPress](security-stay-logged-in.md)
- [How to Hide the Remember Me Checkbox in WordPress](security-hide-remember-me.md)
- [How to Use Auto Logout in WordPress](security-auto-logout.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
