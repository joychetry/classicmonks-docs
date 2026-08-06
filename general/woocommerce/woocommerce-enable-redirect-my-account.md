---
title: "How to Redirect Guests From the WooCommerce My Account Page"
slug: enable-redirect-my-account
description: "Send guests who visit the WooCommerce My Account page to the login page or a custom URL. Choose the destination for non-logged-in users in Classic Monks."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/enable-redirect-my-account/
---

# How to Redirect Guests From the WooCommerce My Account Page

> Send visitors who are not logged in away from the WooCommerce My Account page. Choose whether they go to the login page or a custom URL in Classic Monks.

## Key Takeaways

- Redirect guests who open My Account
- Send them to the login page or a custom URL
- Choose the destination from the settings
- Keeps account content restricted to logged-in users
- Uses WooCommerce's template redirect hook

## What Does the Feature Do?

The WooCommerce My Account page contains order history and account details, which guests cannot use. The **Redirect My Account for Non-logged-in Users** feature sends guests who open that page to a useful destination instead, such as the login page or a custom URL.

The destination is configurable, and a custom URL lets you control where guests land.

## Why You Need It

Guests browsing My Account see content they cannot use:

- Order history and account details need a login
- Sending guests to the login page gives them a clear path in
- A custom URL can route them to a registration or landing page
- Logged-in users still see the account page normally

---

## How to Redirect My Account for Non-logged-in Users

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Redirection** settings area.
3. Toggle on **Redirect My Account for Non-logged-in Users**.

### Step 2: Choose the Destination

- **Redirect Page**: pick the login page, a specific page, or **Custom**.
- If you choose **Custom**, enter a **Custom URL**.

### Step 3: Save and Test

Click **Save Changes**. Log out, open the My Account page, and confirm you are redirected to your chosen destination. Log in and confirm the account page shows normally.

---

## Configuration Options

| Option | Behavior | Default |
|--------|----------|---------|
| **Redirect My Account for Non-logged-in Users** | Master toggle. | Off |
| **Redirect Page** | Login, a selected page, or Custom. | Login |
| **Custom URL** | Destination when Redirect Page is set to Custom. | Blank |

---

## What Gets Affected

- The My Account page for guests: they are redirected away from it
- The destination page: receives the redirected guest

## What Does NOT Get Affected

- The My Account page for logged-in users: shows normally
- The login page: it is a redirect target, not altered
- Saved addresses and carts: unaffected

---

## Advanced Options (Developers)

The feature registers one hook in `functions/woocommerce/woocommerce-functions.php`:

```php
add_action( 'template_redirect', 'cm_redirect_my_account_access' );
```

**`template_redirect`** calls `cm_redirect_my_account_access()` to detect when a guest opens the My Account page and redirect them to the configured destination.

---

## Common Use Cases

**Drive login or registration.** Sending guests to the login page (or a custom registration page) encourages account creation.

**Standard landing.** A custom URL routes guests to the page that makes most sense for your store.

**Protect account data.** Guests do not see order history and account content they cannot access.

---

## Troubleshooting

### The redirect is not happening

**Cause:** The toggle is off, or the visitor is recognized as logged in.
**Fix:** Confirm the toggle is on and that the visitor has no active session. Test as a logged-out guest.

### It goes to the wrong page

**Cause:** The destination setting points somewhere unexpected.
**Fix:** Review **Redirect Page** and, if Custom, the **Custom URL**. Save and test again.

### Logged-in users are redirected too

**Cause:** The redirect applies only to non-logged-in users.
**Fix:** Confirm the visitor being tested is truly logged out. If logged-in users redirect, check for a conflicting plugin.

---

## Frequently Asked Questions

### Who gets redirected?

Visitors who are not logged in when they open the My Account page.

### Where do they go?

To the destination you choose: the login page, a specific page, or a custom URL.

### Do logged-in users see the account page?

Yes. Logged-in users view My Account normally.

### Can I use a custom URL?

Yes. Set **Redirect Page** to Custom and enter the **Custom URL**.

---

## Keeping It Set Up

Set the toggle once and it stays active across the site. To change behavior, return to the WooCommerce settings, adjust the option, and save again. The store continues to run normally throughout, and you can turn the feature off at any time to restore the previous default behavior. For teams managing multiple environments, confirm the setting on staging first, then apply it to production and verify a real page load before treating it as live.

---

## Related Articles

- [How to Redirect Logged-in Users from the Login Page in WooCommerce](woocommerce-redirect-logged-in-users-from-login.md)
- [How to Redirect After Logout in WooCommerce](woocommerce-redirect-to-login-after-logout.md)
- [How to Redirect an Empty Cart in WooCommerce](woocommerce-redirect-empty-cart.md)
