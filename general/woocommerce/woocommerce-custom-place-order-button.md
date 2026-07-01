---
title: "How to Customize the Place Order Button in WordPress | CM"
slug: woocommerce/custom-place-order-button
description: "Customize the Place Order button text and icon on the WooCommerce checkout page in Classic Monks. Configurable text, icon, and icon position."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/woocommerce/custom-place-order-button/
---

# How to Customize the Place Order Button in WordPress

> Custom Place Order Button replaces the default "Place Order" button text on the WooCommerce checkout page. Add an icon, customize the position, and align with your store's branding.

## Key Takeaways

- Customizable button text (default "Place order")
- Optional icon (cart, check, lock, etc.)
- Configurable icon position (left or right of the text)
- Improves conversion with action-oriented language
- Persists across checkout updates

## What Is the Custom Place Order Button feature?

The default WooCommerce "Place Order" button is functional but generic. The Custom Place Order Button feature lets you:

- Change the button text (e.g., "Complete Purchase", "Confirm Order", "Pay Now")
- Add an icon next to the text (e.g., a lock icon for security, a cart icon for clarity)
- Position the icon (left or right of the text)

The button still triggers the standard WooCommerce checkout completion; only the appearance changes.

## Why You Need It

The Place Order button is the most important button in the entire checkout flow. It's the moment the customer commits to the purchase:

- **Action-oriented language**: "Complete Purchase" is more decisive than "Place Order"
- **Security messaging**: A lock icon reassures customers about payment security
- **Brand consistency**: Match the button to your store's voice and design

For most stores, the default is fine. For stores that optimize the checkout flow, this is a small but high-impact change.

---

## How to Customize the Place Order Button in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Checkout** subtab.

### Step 3: Enable Custom Place Order Button

Toggle on **Custom Place Order Button**. Nested options expand.

### Step 4: Configure Button Settings

The 3 sub-options include:

- **Button Text**: The button label (default "Place order")
- **Button Icon**: Optional icon (cart, check, lock, or empty for no icon)
- **Icon Position**: Left or right of the text

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Test

Visit the checkout page. The Place Order button should show your custom text and icon.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Custom Place Order Button** | Master toggle. | Off |
| **Button Text** | The button label. | "Place order" |
| **Button Icon** | Optional icon (cart, check, lock). | (empty) |
| **Icon Position** | Left or right. | Right |

The icon is a Themify icon name (e.g., "ti-shopping-cart", "ti-check", "ti-lock"). The available icons are bundled with Classic Monks; see the Themify Icons documentation for the full list.

---

## What Gets Affected

- The checkout page: the Place Order button text and icon
- The "Thank you" order confirmation page: may also use this button (depending on the theme)

## What Does NOT Get Affected

- The cart page (different button, "Proceed to Checkout")
- The order details in the customer's account
- The admin order details
- The checkout process itself (only the button appearance changes)

---

## Advanced Options (Developers)

This feature registers 3 WordPress hooks in `woocommerce-functions.php`:

**Actions:**

- `wp_footer` calls `cm_checkout_place_order_button_js()` (Injects checkout button JS (priority 999))

**Filters:**

- `woocommerce_order_button_text` calls `cm_custom_place_order_button_text()` (Customizes place order button text)
- `woocommerce_order_button_html` calls `cm_custom_place_order_button_html()` (Customizes place order button HTML)

```php
// Hooked in woocommerce-functions.php
add_filter( 'woocommerce_order_button_text', 'cm_custom_place_order_button_text' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The button is not changing

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the toggle is on. Clear all caching layers.

### The button text changes but the icon doesn't show

**Cause:** The icon name is misspelled or not a valid Themify icon.
**Fix:** Use a valid icon name (e.g., "ti-shopping-cart" for cart, "ti-check" for check, "ti-lock" for lock). See the Themify Icons documentation for the full list.

### The button looks different in different themes

**Cause:** The theme's CSS is styling the button differently.
**Fix:** Customize the button with the `cm_custom_place_order_button_html` filter to add specific CSS classes. Then style those classes in your theme's CSS.

### The button is duplicated (showing two buttons)

**Cause:** A custom theme is also rendering the Place Order button, creating a duplicate.
**Fix:** Disable the custom place order button in the theme (via the theme's settings or a child theme). Keep the Classic Monks version.

---

## Related Articles

- [How to Customize the Order Review Heading in WordPress](woocommerce-custom-order-review-heading.md)
- [How to Show Product Images in WooCommerce Checkout in WordPress](woocommerce-show-product-images-checkout.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
