---
title: "How to Redirect Visitors From an Empty Cart in WooCommerce"
slug: redirect-empty-cart
description: "Redirect customers away from an empty WooCommerce cart to the shop page or a custom page you choose. Avoid a dead end and keep them shopping in your store."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/redirect-empty-cart/
---

# How to Redirect Visitors From an Empty Cart in WooCommerce

> Redirect customers away from a WooCommerce cart page when the cart is empty. Choose between the shop page and a custom page so visitors do not hit a dead end.

## Key Takeaways

- Redirect visitors when they open an empty cart
- Send them to the shop page or a custom URL
- Control the destination from the settings
- Keeps customers moving instead of showing an empty cart
- Uses WooCommerce's template redirect hook

## What Does the Feature Do?

When the cart is empty, the WooCommerce cart page shows a message and offers little to do. The **Redirect Empty Cart** feature sends the visitor to a useful destination instead of showing the empty cart page.

The destination is configurable: visitors can go to the shop page or a custom URL you provide.

## Why You Need It

An empty cart is a dead end for a visitor:

- They cannot add anything from inside the cart page
- The empty message gives no path forward
- Redirecting keeps them moving toward your products or a specific page
- A custom URL lets you control the exact landing page

---

## How to Redirect an Empty Cart in WooCommerce

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Redirection** settings area.
3. Toggle on **Redirect if Cart is Empty**.

### Step 2: Choose the Destination

- **Redirect Page**: pick the shop page, a specific site page, or **Custom**.
- If you choose **Custom**, enter a **Custom URL** to send visitors to.

### Step 3: Save and Test

Click **Save Changes**. Open the cart page with an empty cart and confirm you are redirected to the destination you chose. When the cart has items, the cart page shows normally.

---

## Configuration Options

| Option | Behavior | Default |
|--------|----------|---------|
| **Redirect if Cart is Empty** | Master toggle. | Off |
| **Redirect Page** | Shop, a selected page, or Custom. | Shop |
| **Custom URL** | Destination when Redirect Page is set to Custom. | Blank |

---

## What Gets Affected

- The cart page when the cart is empty: visitors are redirected
- The destination page: receives the redirected visitor

## What Does NOT Get Affected

- The cart page when the cart has items: shows normally
- The selected destination page's own content: unchanged
- Saved carts and customer data: unaffected

---

## Advanced Options (Developers)

The feature registers one hook in `functions/woocommerce/woocommerce-functions.php`:

```php
add_action( 'template_redirect', 'cm_redirect_empty_cart' );
```

**`template_redirect`** calls `cm_redirect_empty_cart()` to check the cart state on the cart page and redirect empty carts to the configured destination.

---

## Common Use Cases

**Keep visitors shopping.** Send empty-cart visitors back to the shop so they continue browsing.

**Direct to a sale landing page.** Use a custom URL to route empty-cart traffic to a specific promotion or collection.

**Mobile experience.** On phones, a redirect to a browsable page is more useful than an empty cart message.

---

## Troubleshooting

### The redirect is not happening

**Cause:** The toggle is off, or the cart is not actually empty.
**Fix:** Confirm the toggle is on and that the cart has no items. Clear the cart and test again.

### It redirects to the wrong page

**Cause:** The destination setting points somewhere unexpected.
**Fix:** Review **Redirect Page** and, if Custom, the **Custom URL**. Save and test again.

### A page I want is not in the list

**Cause:** Not every page may appear in the selector.
**Fix:** Use the **Custom** destination with a **Custom URL** to direct visitors to any page.

---

## Frequently Asked Questions

### When does the redirect happen?

It happens when a visitor opens the cart page while the cart is empty. With items in the cart, the page renders normally.

### Where do visitors go?

To the destination you choose: the shop page, a specific page, or a custom URL.

### Does it clear or change the cart?

No. The cart data is untouched. The feature only redirects the visitor away from the empty cart display.

### Can I use a custom URL?

Yes. Set **Redirect Page** to Custom and enter the **Custom URL**.

---

## Related Articles

- [How to Redirect Logged-in Users from the Login Page in WooCommerce](woocommerce-redirect-logged-in-users-from-login.md)
- [How to Redirect After Logout in WooCommerce](woocommerce-redirect-to-login-after-logout.md)
- [How to Redirect My Account for Non-logged-in Users in WooCommerce](woocommerce-enable-redirect-my-account.md)
