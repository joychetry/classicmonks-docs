---
title: "How to Send Logged-in Users Away From the Login Page"
slug: redirect-logged-in-users-from-login
description: "Send users who are already logged in away from the WordPress login page to My Account or to a custom URL you choose. Pick the destination in Classic Monks."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/redirect-logged-in-users-from-login/
---

# How to Send Logged-in Users Away From the Login Page

> Send users who are already logged in away from the login page, since showing them a login form is pointless. Choose the destination with Classic Monks.

## Key Takeaways

- Redirect logged-in users who try to open the login page
- Send them to My Account or a custom URL
- Choose the destination from the settings
- Avoids the pointless login form for authenticated users
- Uses WooCommerce's template redirect hook

## What Does the Feature Do?

When a logged-in user visits the WordPress login page, they see a login form they do not need. The **Redirect Logged-in Users from Login Page** feature sends them to a useful destination instead, such as the My Account page or a custom URL.

The destination is configurable, and a custom URL lets you send users anywhere you choose.

## Why You Need It

Showing a login form to an authenticated user is poor UX:

- Users may wonder why they are asked to log in again
- The login form is a dead end for someone already signed in
- Redirecting provides a logical next step for authenticated users
- A custom URL lets you control the exact destination

---

## How to Redirect Logged-in Users from the Login Page

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Redirection** settings area.
3. Toggle on **Redirect Logged-in Users from Login Page**.

### Step 2: Choose the Destination

- **Redirect Page**: pick the My Account page, a specific page, or **Custom**.
- If you choose **Custom**, enter a **Custom URL**.

### Step 3: Save and Test

Click **Save Changes**. Log in, open the login page, and confirm you are redirected to your chosen destination.

---

## Configuration Options

| Option | Behavior | Default |
|--------|----------|---------|
| **Redirect Logged-in Users from Login Page** | Master toggle. | Off |
| **Redirect Page** | My Account, a selected page, or Custom. | My Account |
| **Custom URL** | Destination when Redirect Page is set to Custom. | Blank |

---

## What Gets Affected

- The login page for logged-in users: they are redirected away from it
- The destination page: receives the redirected user

## What Does NOT Get Affected

- The login process for guests: users who are not logged in still see the login form
- Logout: works normally
- Password reset: separate from this redirect
- The account dashboard: it is a redirect target, not altered

---

## Advanced Options (Developers)

The feature registers one hook in `functions/woocommerce/woocommerce-functions.php`:

```php
add_action( 'template_redirect', 'cm_redirect_logged_in_users_from_login' );
```

**`template_redirect`** calls `cm_redirect_logged_in_users_from_login()` to detect the login page and redirect authenticated users to the configured destination.

---

## Common Use Cases

**Frequent users.** Authenticated customers get sent to their account instead of a login form.

**Membership stores.** Members who are always logged in avoid the redundant login screen.

**B2B and wholesale.** Wholesale accounts land directly on their account or dashboard.

---

## Troubleshooting

### The redirect is not happening

**Cause:** The toggle is off, or the user is not actually recognized as logged in.
**Fix:** Confirm the toggle is on and that the visitor has an active logged-in session. Test as a logged-in user.

### It redirects to the wrong page

**Cause:** The destination setting points somewhere unexpected.
**Fix:** Review **Redirect Page** and, if Custom, the **Custom URL**. Save and test again.

### A page is not in the list

**Cause:** Not every page may appear in the selector.
**Fix:** Use the **Custom** destination with a **Custom URL** to send users to any page.

---

## Frequently Asked Questions

### Who gets redirected?

Users who are already logged in when they open the login page.

### Where do they go?

To the destination you choose: My Account, a specific page, or a custom URL.

### Do guests still see the login form?

Yes. Users who are not logged in see the login form normally.

### Can I use a custom URL?

Yes. Set **Redirect Page** to Custom and enter the **Custom URL**.

---

## Keeping It Set Up

Set the toggle once and it stays active across the site. To change behavior, return to the WooCommerce settings, adjust the option, and save again. The store continues to run normally throughout, and you can turn the feature off at any time to restore the previous default behavior. For teams managing multiple environments, confirm the setting on staging first, then apply it to production and verify a real page load before treating it as live.

---

## Related Articles

- [How to Redirect an Empty Cart in WooCommerce](woocommerce-redirect-empty-cart.md)
- [How to Redirect After Logout in WooCommerce](woocommerce-redirect-to-login-after-logout.md)
- [How to Redirect My Account for Non-logged-in Users in WooCommerce](woocommerce-enable-redirect-my-account.md)
