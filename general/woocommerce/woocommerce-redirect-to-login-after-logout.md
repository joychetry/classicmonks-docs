---
title: "How to Redirect After Logout in WordPress | CM"
slug: woocommerce/redirect-to-login-after-logout
description: "Send users to the login page immediately after they log out. Provides clear logout confirmation and maintains security by preventing accidental access."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/woocommerce/redirect-to-login-after-logout/
---

# How to Redirect After Logout in WordPress

> Redirect After Logout sends users to the login page immediately after they log out. Provides clear logout confirmation and maintains security by preventing accidental access.

## Key Takeaways

- Single toggle, no nested options
- Sends users to the login page immediately after logout
- Provides clear logout confirmation
- Maintains security by preventing accidental access to authenticated content
- Customizable redirect destination

## What Is the Redirect After Logout feature?

By default, after a user logs out of WordPress, they are redirected to the page they were on. This can be confusing and may leave them on a page that requires authentication. The Redirect After Logout feature sends them to the login page instead, providing a clear logout confirmation.

## Why You Need It

The default behavior after logout can be confusing:

- **Stale content**: The user may see a page that requires authentication, leading to a confusing "access denied" experience
- **No confirmation**: The user may not be sure the logout was successful
- **Security**: If the user is on a shared computer, they may forget to close the browser

Redirecting to the login page provides a clear logout confirmation and forces the user to re-authenticate if they want to continue.

---

## How to Redirect After Logout in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Redirection** subtab.

### Step 3: Enable Redirect After Logout

Toggle on **Redirect after logout**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Log in as a user. Click "Log out". You should be redirected to the login page.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Redirect after logout** | Master toggle. | Off |

The redirect destination is the login page. To customize it, use the plugin settings.

---

## What Gets Affected

- The logout process: users are redirected to the login page after logout
- The customer experience: clear logout confirmation
- The security: forces re-authentication if the user wants to continue

## What Does NOT Get Affected

- The actual logout process: the user is still logged out
- The login page: not affected (the redirect goes TO it)
- The WordPress session: the user's session is destroyed as usual
- The WordPress cookies: cleared as usual

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Actions:**

- `wp_logout` calls `cm_redirect_after_logout_action()` (Redirects to login page after logout)

```php
// Hooked in woocommerce-functions.php
add_action( 'wp_logout', 'cm_redirect_after_logout_action' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Common Use Cases

### Shared computer environments

Stores used in libraries, internet cafes, or shared offices benefit from forcing re-authentication after logout.

### Security-focused stores

For stores handling sensitive data (financial, medical), forcing re-authentication after logout is a security best practice.

### Compliance requirements

Some regulations require that logout forces re-authentication. This feature helps with compliance.

## Troubleshooting

### The redirect is not happening

**Cause:** The toggle is off, or the user is being logged out via a non-standard mechanism (e.g., a custom logout link).
**Fix:** Verify the toggle is on. Try the standard WordPress logout link.

### The redirect goes to the wrong page

**Cause:** The default destination is the login page, but the login page may be at a different URL than expected.
**Fix:** Configure in the plugin settings to set a custom destination.

### AJAX logouts are being broken

**Cause:** The redirect applies to all logouts, including AJAX logouts.
**Fix:** Configure in the plugin settings to exclude AJAX requests. AJAX logouts handle their own response.

### The redirect creates a redirect loop

**Cause:** The destination page has its own redirect that points back to the logout link.
**Fix:** Check the destination page for any redirect rules. The destination should not redirect under normal conditions.

---

## Related Articles

- [How to Redirect Logged-in Users from Login Page in WordPress](woocommerce-redirect-logged-in-users-from-login.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
