---
title: "How to Redirect My Account for Non-logged-in Users in WordPress | CM"
slug: woocommerce/enable-redirect-my-account
description: "Configure redirection for non-logged-in users who try to access the My Account page. Prevents unauthorized access and provides appropriate landing pages for guest users."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/woocommerce/enable-redirect-my-account/
---

# How to Redirect My Account for Non-logged-in Users in WordPress

> Redirect My Account for Non-logged-in Users configures redirection for guest users who try to access the My Account page. Prevents unauthorized access and provides appropriate landing pages for guest users.

## Key Takeaways

- Single toggle, no nested options
- Configures what happens when a non-logged-in user tries to access My Account
- Prevents unauthorized access to account pages
- Provides appropriate landing pages for guest users
- Customizable redirect destination

## What Is the Redirect My Account for Non-logged-in Users feature?

When a guest user (not logged in) tries to access the My Account page, they are typically shown a login form. The Redirect My Account for Non-logged-in Users feature configures where they are redirected, with options for redirecting to the login page, the shop page, or a custom URL.

## Why You Need It

The default behavior (showing a login form) is functional but may not be the best experience:

- **Better flow**: Redirecting to the shop page gives guest users a path to products, not just a login wall
- **Conversion**: Showing products first may lead to a purchase before requiring login
- **Customer choice**: Some customers prefer to browse first, register later

For most stores, redirecting to the shop page is better than the default login wall.

---

## How to Redirect My Account for Non-logged-in Users in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Redirection** subtab.

### Step 3: Enable Redirect My Account

Toggle on **Redirect My Account for non-logged in users**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Log out. Try to access the My Account page. You should be redirected (default: to the login page or shop page, depending on the configuration).

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Redirect My Account for non-logged in users** | Master toggle. | Off |

The redirect destination is configured in the WooCommerce settings (under "My Account" or similar). To customize it, use the plugin settings.

---

## What Gets Affected

- The My Account page: non-logged-in users are redirected
- The customer experience: appropriate landing for guest users

## What Does NOT Get Affected

- The My Account page for logged-in users: shows normally
- The login page: not affected
- The shop page: not affected
- The customer's saved addresses or cart: not affected

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Actions:**

- `template_redirect` calls `cm_redirect_my_account_access()` (Redirects non-logged-in users from my account)

```php
// Hooked in woocommerce-functions.php
add_action( 'template_redirect', 'cm_redirect_my_account_access' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Common Use Cases

### B2C stores with low registration

If most customers don't register, redirecting to the shop page (instead of the login wall) keeps them shopping.

### Stores with social login

If customers usually log in via social login, redirecting to a custom page with both social and email login is better than the default My Account.

### Membership sites

If My Account is for members, redirecting non-logged-in users to a membership page (rather than a generic login) is better.

## Troubleshooting

### The redirect is not happening

**Cause:** The toggle is off, or the user is being treated as logged in (e.g., a stale session).
**Fix:** Verify the toggle is on. Clear the browser cookies and try again.

### The redirect goes to the wrong page

**Cause:** The default destination may not be what you want.
**Fix:** Configure in the plugin settings to set a custom destination. Common options: login page, shop page, registration page, or a custom landing page.

### Logged-in users are being redirected

**Cause:** The redirect applies to all users, not just non-logged-in ones.
**Fix:** Check the configuration. The feature should only redirect non-logged-in users. If logged-in users are being redirected, there may be a conflict with another plugin.

### The redirect creates a redirect loop

**Cause:** The destination page has its own redirect that points back to My Account.
**Fix:** Check the destination page for any redirect rules. The destination should not redirect under normal conditions.

---

## Related Articles

- [How to Redirect if Cart is Empty in WordPress](woocommerce-redirect-empty-cart.md)
- [How to Redirect After Logout in WordPress](woocommerce-redirect-to-login-after-logout.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
