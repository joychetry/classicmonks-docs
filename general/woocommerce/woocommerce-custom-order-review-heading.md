---
title: "How to Customize the Order Review Heading in WordPress | CM"
slug: woocommerce/custom-order-review-heading
description: "Customize the Order Review heading text on the WooCommerce checkout page in Classic Monks. Creates consistent branding throughout the checkout flow."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/woocommerce/custom-order-review-heading/
---

# How to Customize the Order Review Heading in WordPress

> Custom Order Review Heading replaces the default "Order Review" heading text on the WooCommerce checkout page. Creates consistent branding throughout the checkout flow.

## Key Takeaways

- Single configuration field, no nested options
- Customizes the "Order Review" heading on the checkout page
- Supports any text (including emoji or HTML)
- Replaces the default in one place
- Persists across checkout updates

## What Is the Custom Order Review Heading feature?

The default WooCommerce checkout page shows "Order review" as the heading above the cart summary. This is functional but generic.

The Custom Order Review Heading feature lets you replace it with any text, including:

- "Review your order" (more action-oriented)
- "Almost done!" (urgency messaging)
- "Confirm your purchase" (action-focused)
- Brand-specific language (e.g., "Confirm your [Brand] order")

## Why You Need It

The Order Review heading is a small but high-visibility element at a critical moment in the checkout flow:

- **Branding consistency**: Match the heading to your store's voice
- **Conversion optimization**: Action-oriented language ("Confirm your order") can improve completion
- **Customer orientation**: Clear, specific language reduces hesitation

For most stores, the default is fine. For stores that optimize the checkout flow, this is a small win.

---

## How to Customize the Order Review Heading in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Checkout** subtab.

### Step 3: Enable Custom Order Review Heading

Toggle on **Custom Order Review Heading**.

### Step 4: Set the Heading Text

Enter the heading text in the **Order Review Heading** field. Default is "Order review".

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Test

Visit the checkout page. The Order Review section should show your custom heading.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Custom Order Review Heading** | Master toggle. | Off |
| **Order Review Heading** | The heading text. | "Order review" |

No nested options.

---

## What Gets Affected

- The checkout page: the "Order review" heading is replaced with your custom text
- The "Thank you" order confirmation page: may also use this heading (depending on the theme)

## What Does NOT Get Affected

- The cart page (different heading)
- The order details in the customer's account
- The admin order details
- Other checkout section headings (Billing, Shipping, Payment)

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Filters:**

- `gettext` calls `cm_custom_order_review_heading()` (Customizes order review heading text (priority 20))

```php
// Hooked in woocommerce-functions.php
add_filter( 'gettext', 'cm_custom_order_review_heading' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The heading is not changing

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the toggle is on. Clear all caching layers.

### The heading is changing but has the wrong CSS

**Cause:** The theme's CSS styles the heading in a way that conflicts with your custom text length.
**Fix:** Configure in the plugin settings to add a custom CSS class. Then style that class in your theme's CSS.

### The heading is showing on other pages too

**Cause:** The heading text is applied wherever the `woocommerce_checkout_order_review` action fires, which some themes also use in mini-cart or order review widgets.
**Fix:** If the heading is showing in unintended places, use the `cm_custom_order_review_heading` filter to check the context (page ID, is_cart(), etc.) and return different text.

### The heading is empty after enabling

**Cause:** The Order Review Heading field is empty.
**Fix:** Enter the desired heading text. An empty value would show no heading, which breaks the layout. Default to "Order review" if you want to keep the standard wording.

---

## Related Articles

- [How to Customize the Place Order Button in WordPress](woocommerce-custom-place-order-button.md)
- [How to Show Product Images in WooCommerce Checkout in WordPress](woocommerce-show-product-images-checkout.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
