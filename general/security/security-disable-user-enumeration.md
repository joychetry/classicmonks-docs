---
title: "How to Disable User Enumeration in WordPress | CM"
slug: disable-user-enumeration
description: "Block WordPress user enumeration attacks via REST API and author archives. Prevents attackers from discovering valid usernames by querying your site."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-user-enumeration/
---

# How to Disable User Enumeration in WordPress

> Disable User Enumeration in Classic Monks blocks common user enumeration attacks. Prevents attackers from discovering valid usernames by querying your site's REST API or author archive pages.

## Key Takeaways

- Single toggle, no nested options
- Blocks user enumeration via the REST API (`/wp-json/wp/v2/users`)
- Blocks user enumeration via author archive pages (`/?author=1`)
- Returns 404 or 403 instead of user data
- Critical security hardening for any public WordPress site

## What Is the Disable User Enumeration feature?

User enumeration is a common WordPress attack where bad actors try to discover valid usernames. With a valid username, an attacker can:

- Launch targeted password brute-force attacks
- Use leaked password databases to test for credential reuse
- Combine the username with social engineering
- Build a profile of the site (admins, editors, etc.)

WordPress exposes user data in two main places:

1. **REST API**: `/wp-json/wp/v2/users` returns user data
2. **Author Archives**: `/?author=1` redirects to the author's archive page (revealing the username)

The Disable User Enumeration feature blocks both methods.

## Why You Need It

Username enumeration is the first step in most WordPress attacks:

- **Brute force attacks**: Need a valid username to attack
- **Credential stuffing**: Use leaked username/password combos
- **Phishing**: Combine username with other leaked data
- **Reconnaissance**: Build a profile of the site

Blocking enumeration is a critical security measure.

---

## How to Disable User Enumeration in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **WP Protection** subtab.

### Step 3: Enable Disable User Enumeration

Scroll to **Disable User Enumeration** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Try to access `/wp-json/wp/v2/users` in your browser. The response should be 404 (or an empty array). Try to access `/?author=1`, the page should not redirect to an author archive.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable User Enumeration** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- The REST API users endpoint: returns 404 or empty
- The REST API users search: blocked
- The author archive pages: return 404 for non-logged-in users
- The author query in WP_Query: blocked for non-authorized users

## What Does NOT Get Affected

- The WordPress admin: not affected (admins can still see user lists)
- The wp-admin users page: still works for admins
- The user profile pages (author=me): still work for the logged-in user
- The REST API for logged-in users: still works (the user is authenticated)

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `security-functions.php`:

**Actions:**

- `init` calls `cm_disable_user_enumeration()` (Blocks user enumeration via author archives and REST API)

```php
// Hooked in security-functions.php
add_action( 'init', 'cm_disable_user_enumeration' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The REST API users endpoint is still returning data

**Cause:** The toggle is off, or a caching plugin is serving the old response.
**Fix:** Verify the toggle is on. Clear all caching layers (especially if using a page cache that caches REST API responses).

### The author archive is still accessible

**Cause:** The toggle may not be blocking the author archive if your theme has its own author page template.
**Fix:** Check the theme's author.php or archive.php. The Disable User Enumeration feature returns 404 for the author query; if the theme catches this and shows content, the page is technically not blocking the user enumeration.

### I need to allow specific users to be enumerated

**Cause:** The feature blocks all user enumeration.
**Fix:** Adjust the allowed roles in the plugin settings under Security > Disable User Enumeration. Or adjust the author archive settings in the plugin settings.

### The WordPress admin Users page is broken

**Cause:** The admin uses a different mechanism to list users, but some admin tools (e.g., author dropdowns) may use the REST API.
**Fix:** The Disable User Enumeration feature should not affect the admin. If the admin is broken, check for plugin conflicts. The admin uses authenticated requests, which should pass through.

### The block author archive is showing 404 for logged-in users

**Cause:** The default behavior is to block for all users, including logged-in.
**Fix:** Adjust the allowed roles in the plugin settings under Security > Disable User Enumeration. Or adjust the author archive settings in the plugin settings.

---

## Related Articles

- [How to Remove REST API Links in WordPress](security-remove-rest-api-links.md)
- [How to Use a Custom Login URL in WordPress](security-custom-login-url.md)
- [How to Enable Login Lockdown in WordPress](security-login-lockdown.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
