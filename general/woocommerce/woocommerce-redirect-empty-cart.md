---
title: "How to Redirect Empty Cart in WordPress | CM"
slug: woocommerce/redirect-empty-cart
description: "Automatically redirect customers to the shop page when they try to access an empty cart page. Improves the user experience by preventing dead-end pages."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/woocommerce/redirect-empty-cart/
---

# How to Redirect Empty Cart in WordPress

> Redirect Empty Cart automatically redirects customers to the shop page when they try to access an empty cart. Prevents dead-end pages and guides customers back to shopping.

## Key Takeaways

- Single toggle, no nested options
- Automatically redirects customers from the cart page to the shop page when the cart is empty
- Prevents dead-end pages and improves the user experience
- Customizable redirect destination (via filter)
- Useful for stores where the empty cart page is not useful

## What Is the Redirect Empty Cart feature?

By default, the WooCommerce cart page shows a "Your cart is currently empty" message when the cart is empty. While functional, this is a dead end for customers who expected to see their cart. The Redirect Empty Cart feature automatically redirects them to the shop page instead.

## Why You Need It

The empty cart page is a dead end:

- Customers can't add products from the cart page
- The message "Your cart is currently empty" provides no path forward
- Customers may leave the site rather than navigate to the shop

Redirecting to the shop page gives customers an immediate next step.

---

## How to Redirect Empty Cart in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Redirection** subtab.

### Step 3: Enable Redirect Empty Cart

Toggle on **Redirect if cart is empty**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit the cart page when the cart is empty. The page should redirect to the shop page.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Redirect if cart is empty** | Master toggle. | Off |

The redirect destination is the shop page. To customize it, use the plugin settings.

---

## What Gets Affected

- The cart page: customers are redirected to the shop page when the cart is empty
- The customer flow: no dead-end pages

## What Does NOT Get Affected

- The cart page when the cart has items: shows normally
- The shop page: not affected
- The checkout page: not affected
- The customer's saved items: not affected

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Actions:**

- `template_redirect` calls `cm_redirect_empty_cart()` (Redirects empty cart to shop page)

```php
// Hooked in woocommerce-functions.php
add_action( 'template_redirect', 'cm_redirect_empty_cart' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Common Use Cases

### Multi-page stores

Stores with a multi-page checkout may want the cart page to redirect to the checkout instead of the shop. Customize in the plugin settings.

### Conversion-focused stores

Redirecting to the shop page keeps customers shopping. The empty cart page is a dead end for conversions.

### Stores with many product categories

If your shop has many categories, the shop page provides a path to products. The empty cart page provides nothing.

### Mobile-optimized stores

On mobile, the empty cart page is especially dead-end. Redirecting to the shop (which is mobile-optimized) is better UX.

## Troubleshooting

### The redirect is not happening

**Cause:** The toggle is off, or the cart is not actually empty.
**Fix:** Verify the toggle is on. Clear the cart manually and try again.

### The redirect goes to the wrong page

**Cause:** The default destination is the shop page, but the shop page may be a different URL than expected.
**Fix:** Configure in the plugin settings to set a custom destination.

### Logged-in admins are being redirected

**Cause:** The redirect applies to all visitors.
**Fix:** Configure in the plugin settings to exclude admins. The default behavior for logged-in admins is to show the empty cart page (they may need to see it for testing).

### The redirect creates a redirect loop

**Cause:** The destination page has its own redirect that points back to the cart.
**Fix:** Check the destination page for any redirect rules. The destination should not redirect under normal conditions.

---

## Related Articles

- [How to Redirect Logged-in Users from Login Page in WordPress](woocommerce-redirect-logged-in-users-from-login.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
- [How to Use Logs in WordPress](../core/core-logs.md)
