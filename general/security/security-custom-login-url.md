---
title: "How to Use a Custom Login URL in WordPress | CM"
slug: security/custom-login-url
description: "Change the default WordPress login URL from /wp-login.php to a custom slug in Classic Monks. Adds a custom whitelist, redirect, and a hidden protection against brute force attacks."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/security/custom-login-url/
---

# How to Use a Custom Login URL in WordPress

> Change the default WordPress login URL from `/wp-login.php` to a custom slug (e.g., `/sign-in`). Hides the standard login page from automated bots and reduces brute force attacks by 90%+.

## Key Takeaways

- Single toggle with 3 sub-options (URL, redirect, whitelist)
- Changes the login URL from `/wp-login.php` to a custom slug
- Adds an extra layer of security (bots won't find the login form)
- Configure a whitelist of users who can still use the default URL (handy for development)
- Compatible with WooCommerce, custom login forms, and password reset flows

## What Is the Custom Login URL feature?

The default WordPress login URL is `/wp-login.php`. Every bot, scanner, and brute force attacker knows this. The Custom Login URL feature changes the login URL to a custom slug of your choice, so the standard `/wp-login.php` is no longer accessible.

This is a stealth security measure: bots continue to hit `/wp-login.php` and fail, while your real users access the custom URL.

## Why You Need It

`/wp-login.php` is one of the most attacked URLs on the internet:

- 90%+ of WordPress brute force attacks target `/wp-login.php`
- Login lockdown plugins still process the failed attempts (server load)
- The standard URL appears in leaked databases, password dumps, and botnet lists
- Even if the attack fails, the IP is logged and your server processes the request

Changing the URL eliminates the most common attack surface entirely.

---

## How to Use a Custom Login URL in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **WP Protection** subtab.

### Step 3: Enable Custom Login URL

Scroll to **Enable Custom Login URL** and toggle on. Nested options expand.

### Step 4: Configure the Custom URL

Set the **Custom Login URL** field to your desired slug. The slug is appended to your site URL:

- `sign-in` → `https://yoursite.com/sign-in`
- `my-account` → `https://yoursite.com/my-account`
- `portal` → `https://yoursite.com/portal`

Avoid common terms like "login", "admin", or "wp" which bots may also try.

### Step 5: Configure the Redirect

Set the **Redirect wp-login.php to** field. When a user visits the default `/wp-login.php`, they will be redirected to this URL:

- `home_url('/')` → Site homepage (recommended)
- `404` → 404 page
- Custom URL → Any URL of your choice

### Step 6: Configure the Whitelist (Optional)

If you want certain user roles or IPs to still access `/wp-login.php`, add them to the **URL Whitelist** field (one per line). Useful for:

- Development environments
- Specific admin users who prefer the standard URL
- Trusted IP addresses

### Step 7: Save Changes

Click **Save Changes**.

### Step 8: Test

Log out. Try to access `/wp-login.php`. You should be redirected (per the redirect setting). Then access your custom URL. The login form should appear.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Custom Login URL** | Master toggle. | Off |
| **Custom Login URL** | The custom slug. | (empty) |
| **Redirect wp-login.php to** | Where the default URL redirects. | (empty) |
| **URL Whitelist** | IPs and roles that can still use the default URL. | (empty) |

---

## What Gets Affected

- The login form: accessible at the custom URL, not at `/wp-login.php`
- The default URL: redirects to the configured URL
- The password reset flow: uses the custom URL
- The wp-admin login: still uses the same flow (you'll be redirected to the custom URL)
- The REST API: not affected (this is a frontend URL change, not an API change)

## What Does NOT Get Affected

- The WordPress admin (after login): works normally
- The REST API endpoints: still accessible at `/wp-json/`
- Cron jobs: not affected
- The user's saved credentials: not affected
- Other plugins that reference the login URL: may need updating

---

## Advanced Options (Developers)

This feature registers 6 WordPress hooks in `custom-login-url.php`:

**Actions:**

- `init` calls `CM_Custom_Login_URL::handle_custom_login_url()` (Intercepts login URL requests)
- `template_redirect` calls `CM_Custom_Login_URL::block_login_aliases()` (Blocks access to default login URLs (priority 9))
- `wp_login_failed` calls `CM_Custom_Login_URL::handle_login_failed()` (Handles failed login attempts (priority 999))

**Filters:**

- `site_url` calls `CM_Custom_Login_URL::filter_login_urls()` (Rewrites login-related site URLs)
- `login_url` calls `CM_Custom_Login_URL::filter_wp_login_url()` (Filters the wp_login_url() return value)
- `logout_redirect` calls `apply_filters()` (Customizable filter)

```php
// Hooked in custom-login-url.php
add_action( 'init', 'CM_Custom_Login_URL::handle_custom_login_url' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The custom URL shows a 404

**Cause:** The custom URL is not flushed to the rewrite rules. WordPress may need to regenerate its permalinks.
**Fix:** Go to Settings > Permalinks and click "Save Changes" (no need to change anything). This flushes the rewrite rules.

### The default /wp-login.php still loads

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the toggle is on. Clear all caching layers. Note: `/wp-login.php` may still be accessible for admin users by default (WordPress core behavior).

### I'm locked out after changing the URL

**Cause:** You forgot the new URL, or a plugin conflict is preventing the redirect.
**Fix:** Access the database directly (`wp_options` table, look for `cm_custom_login_url` option). Or rename the plugin folder via FTP to disable it temporarily. Then set the URL back to `/wp-login.php`.

### The wp-admin shows a login loop

**Cause:** The wp-admin login form is set to redirect to `/wp-login.php` by default, which now redirects to the custom URL, which then redirects to wp-admin.
**Fix:** This is usually a theme or plugin conflict. Test with a default theme. Disable other login-related plugins to find the conflict.

### The password reset email uses the wrong URL

**Cause:** The password reset email is generated by WordPress core, which uses the default URL.
**Fix:** Use the `retrieve_password_message` filter to replace the URL in the email body with your custom URL.

---

## Related Articles

- [How to Enable Login Lockdown in WordPress](security-login-lockdown.md)
- [How to Use Cloudflare Turnstile in WordPress](security-cloudflare-turnstile.md)
- [How to Use Math Captcha in WordPress](security-math-captcha.md)
- [How to Use the Email Tab in Classic Monks: Feature Index](../email.md)
