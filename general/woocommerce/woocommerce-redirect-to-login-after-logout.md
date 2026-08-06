---
title: "How to Redirect Users After They Log Out of WooCommerce"
slug: redirect-to-login-after-logout
description: "Send users to the login page or a custom URL immediately after they log out of your store. Control the logout destination with a Classic Monks toggle."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/redirect-to-login-after-logout/
---

# How to Redirect Users After They Log Out of WooCommerce

> Send users to the login page or a custom URL immediately after they log out. Choose the destination in Classic Monks for a clear logout flow.

## Key Takeaways

- Redirect users to a chosen page right after logout
- Send them to the login page or a custom URL
- Choose the destination from the settings
- Provides a clear logout hand-off
- Confirmed to run on the logout action

## What Does the Feature Do?

After a user logs out, WordPress usually leaves them where they were or returns to a default location. The **Redirect After Logout** feature sends them to a chosen destination immediately on logout, such as the login page or a custom URL.

The destination is configurable, and a custom URL lets you send users anywhere you choose.

## Why You Need It

A clear logout destination improves the flow:

- Users get clear confirmation that they logged out
- They are not left on a page that requires authentication
- A login destination lets them sign back in cleanly
- A custom URL allows a specific next step

---

## How to Redirect After Logout

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Redirection** settings area.
3. Toggle on **Redirect After Logout**.

### Step 2: Choose the Destination

- **Redirect Page**: pick the login page, a specific page, or **Custom**.
- If you choose **Custom**, enter a **Custom URL**.

### Step 3: Save and Test

Click **Save Changes**. Log in, log out, and confirm you land on the destination you chose.

---

## Configuration Options

| Option | Behavior | Default |
|--------|----------|---------|
| **Redirect After Logout** | Master toggle. | Off |
| **Redirect Page** | Login, a selected page, or Custom. | Login |
| **Custom URL** | Destination when Redirect Page is set to Custom. | Blank |

---

## What Gets Affected

- The logout flow: users are redirected to the chosen destination on logout

## What Does NOT Get Affected

- The login process: unchanged
- The account dashboard: it is not the default target unless you select it
- Browser cookies and sessions: cleared normally on logout

---

## Advanced Options (Developers)

The feature registers one hook in `functions/woocommerce/woocommerce-functions.php`:

```php
add_action( 'wp_logout', 'cm_redirect_after_logout_action' );
```

**`wp_logout`** calls `cm_redirect_after_logout_action()`, which reads the configured destination (login or custom URL) and performs a safe redirect after the user logs out.

---

## Common Use Cases

**Shared devices.** Sending users back to the login page on shared computers encourages a clean hand-off.

**Clear confirmation.** A login destination tells users the logout worked.

**Specific next steps.** A custom URL can route logged-out users to a landing page or promotion.

---

## Troubleshooting

### The redirect is not happening

**Cause:** The toggle is off, or the logout was triggered by a non-standard mechanism.
**Fix:** Confirm the toggle is on. Test logout with the standard logout link, since the redirect runs on the WordPress logout action.

### It goes to the wrong page

**Cause:** The destination setting points somewhere unexpected.
**Fix:** Review **Redirect Page** and, if Custom, the **Custom URL**. Save and test again.

### A page is not in the list

**Cause:** Not every page may appear in the selector.
**Fix:** Use the **Custom** destination with a **Custom URL**.

---

## Frequently Asked Questions

### When does the redirect happen?

Immediately on logout, when the user triggers the WordPress logout action.

### Where do users go?

To the destination you choose: the login page, a specific page, or a custom URL.

### Does this affect the login process?

No. The redirect runs only on logout.

### Can I use a custom URL?

Yes. Set **Redirect Page** to Custom and enter the **Custom URL**.

---

## Keeping It Set Up

Set the toggle once and it stays active across the site. To change behavior, return to the WooCommerce settings, adjust the option, and save again. The store continues to run normally throughout, and you can turn the feature off at any time to restore the previous default behavior. For teams managing multiple environments, confirm the setting on staging first, then apply it to production and verify a real page load before treating it as live.

---

## Related Articles

- [How to Redirect Logged-in Users from the Login Page in WooCommerce](woocommerce-redirect-logged-in-users-from-login.md)
- [How to Redirect an Empty Cart in WooCommerce](woocommerce-redirect-empty-cart.md)
- [How to Redirect My Account for Non-logged-in Users in WooCommerce](woocommerce-enable-redirect-my-account.md)
