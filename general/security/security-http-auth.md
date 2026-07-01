---
title: "How to Enable HTTP Authentication for Staging in WordPress | CM"
slug: http-auth
description: "Add browser-level HTTP authentication to your WordPress site in Classic Monks. Prevents any access (frontend or admin) until the user enters a username and password."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/http-auth/
---

# How to Enable HTTP Authentication for Staging in WordPress

> HTTP Authentication in Classic Monks adds a browser-level username/password prompt before any content loads. Useful for staging sites, private internal tools, and other sites that need to be completely locked down.

## Key Takeaways

- Single toggle, no nested options
- Browser-level authentication (before WordPress even loads)
- Configurable username and password
- Affects all visitors (including admins)
- Pairs with [Staging Protection](security-staging-protection.md) for staging sites

## What Is the HTTP Authentication feature?

HTTP Authentication (also called "Basic Auth" or "htpasswd") is a browser-level authentication mechanism. Before any content is served, the browser shows a username/password prompt. The user must enter valid credentials to access any page, including the wp-admin.

This is different from the WordPress login. WordPress login only protects wp-admin (and some other paths). HTTP Authentication protects the entire site, including the frontend.

## Why You Need It

HTTP Authentication is the strongest form of web authentication because:

- **Browser-level**: The authentication happens before any PHP code runs
- **Universal**: Affects all visitors, not just WordPress users
- **No bypass**: Even if WordPress has a vulnerability, the attacker can't reach it without the HTTP auth
- **Server-level**: The credentials are stored in .htaccess (Apache) or server config (Nginx)

For sites that need maximum security, HTTP Authentication is the gold standard.

## Trade-offs vs WordPress login

HTTP Authentication has trade-offs:

- **No logout button**: Users must close their browser to log out (or use private/incognito mode)
- **No remember me**: Each browser session requires re-authentication
- **No user roles**: HTTP Auth doesn't know about WordPress roles (any valid HTTP auth user can access the site)
- **Less user-friendly**: The browser prompt is more intimidating than the WordPress login form

For most public-facing sites, WordPress login is sufficient. For staging, internal tools, and other private sites, HTTP Authentication is the right choice.

---

## How to Enable HTTP Authentication in WordPress

### Step 1: Set the Credentials

Before enabling, decide on the username and password. Use a strong password (16+ characters, generated).

### Step 2: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 3: Go to the Security Tab

Click on the **Security** menu, then click the **Staging Protection** subtab.

### Step 4: Enable HTTP Authentication

Scroll to **Enable HTTP Authentication** and toggle on. The credentials are configured via filter (see Advanced Options) or in the .htaccess file (default).

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Test

Visit the site in a new browser (or private/incognito mode). The browser should show a username/password prompt. Enter the correct credentials to access the site.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable HTTP Authentication** | Master toggle. | Off |

The credentials are configured in the .htaccess file (Apache) or in the plugin settings under Security > Staging Protection.

---

## What Gets Affected

- All visitors: must enter the HTTP auth username/password
- The frontend: protected by HTTP auth
- The admin: protected by HTTP auth (in addition to WordPress login)
- The API: protected by HTTP auth

## What Does NOT Get Affected

- The server performance: HTTP auth is fast
- The WordPress functionality: works the same after authentication
- The database: not affected
- The user accounts: HTTP auth is separate from WordPress users

---


## Troubleshooting

### The browser is not showing the auth prompt

**Cause:** The credentials are already cached in the browser, or the .htaccess is not configured.
**Fix:** Try a private/incognito window. Verify the .htaccess file has the auth directives.

### The credentials are rejected

**Cause:** The credentials are wrong, or the .htaccess is not configured for the right path.
**Fix:** Verify the credentials. Verify the .htaccess path matches the site structure (e.g., `/wp-admin/.htpasswd` for admin-only auth).

### The auth prompt appears but WordPress login also appears

**Cause:** HTTP auth protects the site, but WordPress login is also active.
**Fix:** This is normal. After HTTP auth, users still need to log in to WordPress. To use only HTTP auth, disable WordPress login via the [Hide Login URL](security-custom-login-url.md) feature.

### I forgot the HTTP auth password

**Cause:** The password is in the .htaccess file or the Classic Monks settings.
**Fix:** Reset the password via the .htaccess file or the filter. Or remove the .htaccess authentication temporarily to regain access.

### The Nginx server is not using .htaccess

**Cause:** Nginx does not support .htaccess files.
**Fix:** Configure HTTP auth at the Nginx server level. Add `auth_basic` and `auth_basic_user_file` directives to your Nginx config.

---

## Related Articles

- [How to Enable Staging Protection in WordPress](security-staging-protection.md)
- [How to Use Site-Wide Password Protection in WordPress](security-site-wide-password.md)
- [How to Use a Custom Login URL in WordPress](security-custom-login-url.md)
- [How to Use the Email Tab in Classic Monks: Feature Index](../email.md)
