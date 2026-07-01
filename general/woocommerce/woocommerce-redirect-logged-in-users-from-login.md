---
title: "How to Redirect Logged-in Users from Login Page in WordPress | CM"
slug: woocommerce/redirect-logged-in-users-from-login
description: "Automatically redirect users who are already logged in away from the login page. Prevents confusion and improves the user experience for already-authenticated users."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/woocommerce/redirect-logged-in-users-from-login/
---

# How to Redirect Logged-in Users from Login Page in WordPress

> Redirect Logged-in Users from Login Page automatically sends users who are already logged in to their account dashboard. Prevents confusion and provides logical navigation for authenticated users.

## Key Takeaks

- Single toggle, no nested options
- Sends logged-in users to the My Account page when they try to access the login page
- Prevents confusion (no point in showing a login form to a logged-in user)
- Customizable redirect destination
- Improves the user experience for already-authenticated users

## What Is the Redirect Logged-in Users from Login Page feature?

When a logged-in user tries to access the WordPress login page, they see the login form again. This is confusing and provides no useful action. The Redirect Logged-in Users from Login Page feature automatically sends them to the My Account page instead.

## Why You Need It

For most sites, showing a login form to a logged-in user is bad UX:

- **Confusion**: Users may wonder why they're seeing a login form when they're already logged in
- **Wasted click**: Users may try to log in again, which could log them out of another session
- **No logical flow**: The login page should only show to users who need to log in

Redirecting logged-in users to their account dashboard provides a logical flow.

---

## How to Redirect Logged-in Users from Login Page in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Redirection** subtab.

### Step 3: Enable Redirect Logged-in Users

Toggle on **Redirect logged-in users from login page**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Log in as a user. Try to access the WordPress login page (e.g., `/wp-login.php`). You should be redirected to the My Account page.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Redirect logged-in users from login page** | Master toggle. | Off |

The redirect destination is the My Account page. To customize it, use the plugin settings.

---

## What Gets Affected

- The WordPress login page: logged-in users are redirected to My Account
- The WooCommerce login page (my-account area): same behavior
- The customer experience: no more seeing a login form when already logged in

## What Does NOT Get Affected

- The WordPress logout: works as usual
- The actual login process: users who are not logged in see the login form normally
- The My Account page: not affected (the redirect goes TO it)
- Password reset flow: separate pages, not affected

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Actions:**

- `template_redirect` calls `cm_redirect_logged_in_users_from_login()` (Redirects logged-in users from login page)

```php
// Hooked in woocommerce-functions.php
add_action( 'template_redirect', 'cm_redirect_logged_in_users_from_login' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Common Use Cases

### B2B stores

Wholesale customers are usually logged in. Sending them to My Account (instead of the login form) is a better experience.

### Membership sites

Members are always logged in. Sending them to My Account provides a direct path to their account.

### Frequent return customers

For customers who log in frequently, the My Account page is a more useful landing than the login form.

## Troubleshooting

### The redirect is not happening

**Cause:** The toggle is off, or the user is not actually logged in (e.g., session expired).
**Fix:** Verify the toggle is on. Log in as a test user and try again.

### The redirect goes to the wrong page

**Cause:** The default destination is the My Account page, but the My Account page may be at a different URL than expected.
**Fix:** Configure in the plugin settings to set a custom destination.

### Logged-in admins are being redirected

**Cause:** The redirect applies to all users.
**Fix:** Configure in the plugin settings to exclude admins. Admins may need to access the login page for testing (e.g., to log in as another user).

### The redirect creates a redirect loop

**Cause:** The destination page has its own redirect that points back to the login page.
**Fix:** Check the destination page for any redirect rules. The destination should not redirect under normal conditions.

---

## Related Articles

- [How to Redirect if Cart is Empty in WordPress](woocommerce-redirect-empty-cart.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
