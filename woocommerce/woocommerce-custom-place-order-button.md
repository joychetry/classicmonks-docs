---
title: "How to Customize the Place Order Button in WooCommerce"
slug: custom-place-order-button
description: "Change the place order button text and add an icon image on the WooCommerce checkout page. Set the text, an optional image, and its position in Classic Monks."
last_updated: 2026-08-06
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/custom-place-order-button/
---

# How to Customize the Place Order Button in WooCommerce

> Change the WooCommerce place order button on the checkout so it uses your own text and an optional icon image. Set the button text, add an image, and choose whether the image sits before or after the text.

## Key Takeaways

- Replace the default "Place Order" text with your own wording
- Add an optional icon image to the button
- Choose the icon position: before or after the text
- Requires checkout admin screens in WordPress
- The button still completes the order normally; only its appearance changes

## What Does the Feature Do?

The **Custom Place Order Button** feature changes the wording and appearance of the checkout button that submits an order. It replaces the button text with your chosen label, and optionally adds an icon image beside the text.

When you set an icon, the feature inserts the image into the button at the position you choose. The button keeps its normal checkout behavior; only the label and image change.

## Why You Need It

The place order button is the final action in the checkout flow:

- Action-oriented text ("Complete Purchase", "Pay Now", "Confirm Order") can feel more decisive than the default
- A small icon, like a shopping cart or lock, adds visual context
- Matching the button to your store's voice improves brand consistency
- It is a small change with a clear effect on the checkout

---

## How to Customize the Place Order Button in WooCommerce

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Checkout** settings area.
3. Toggle on **Custom Place Order Button**. The nested options expand below the toggle.

### Step 2: Set the Button Text

In **Button Text**, enter the label for the place order button. If you leave it blank, the feature falls back to `Pay Now`.

### Step 3: Add an Icon Image (Optional)

In **Button Icon**, enter the URL of the image to show on the button. The field accepts an uploaded image URL, which is rendered inside the button. Leave it blank for text only.

### Step 4: Set the Icon Position

Use **Icon Position** to place the icon before or after the text. The default is **Before**.

### Step 5: Save and Test

Click **Save Changes**. Visit the checkout page and confirm the place order button shows your text and (if set) the icon in the chosen position.

---

## Configuration Options

| Option | Behavior | Default |
|--------|----------|---------|
| **Custom Place Order Button** | Master toggle. | Off |
| **Button Text** | Label on the place order button; blank falls back to `Pay Now`. | Blank (uses "Pay Now") |
| **Button Icon** | Image URL shown on the button. | Blank (no icon) |
| **Icon Position** | Before or after the button text. | Before |

---

## What Gets Affected

- The checkout page: the place order button text and optional image
- The button markup: an image is inserted when an icon URL is set

## What Does NOT Get Affected

- The checkout process: the button still submits the order normally
- The cart page: this feature targets the checkout place order button
- Payment processing: no change to the order or payment flow
- The button styling beyond the inserted image: theme CSS still applies

---

## Advanced Options (Developers)

The feature registers hooks in `functions/woocommerce/woocommerce-functions.php`:

```php
add_filter( 'woocommerce_order_button_text', 'cm_custom_place_order_button_text' );
add_filter( 'woocommerce_order_button_html', 'cm_custom_place_order_button_html' );
add_action( 'wp_footer', 'cm_checkout_place_order_button_js', 999 );
```

- **`woocommerce_order_button_text`** sets the button label. If **Button Text** is empty, it returns `Pay Now`.
- **`woocommerce_order_button_html`** inserts the icon image. When an icon URL is set, it renders an `<img>` inside the button, positioned before or after the button text according to **Icon Position**.
- **`wp_footer`** (priority 999) injects the small jQuery handler that applies the icon to the `#place_order` button on the checkout page for three-digit-safe display when the button is not replaced by the HTML filter.

---

## Troubleshooting

### The button text is not changing

**Cause:** The feature toggle is off, or the checkout is cached.
**Fix:** Confirm **Custom Place Order Button** is on and clear caches. The button text is applied through the WooCommerce order button text filter.

### The button shows "Pay Now" unexpectedly

**Cause:** **Button Text** is blank, so the fallback `Pay Now` is used.
**Fix:** Enter the exact label you want in **Button Text**. The feature falls back to `Pay Now` when the field is empty.

### The icon is not showing

**Cause:** **Button Icon** is blank, or the URL does not point to a valid image.
**Fix:** Set **Button Icon** to a valid image URL. Confirm the URL loads a real image. The icon is inserted only when a URL is provided.

### The icon appears on the wrong side

**Cause:** **Icon Position** is not set to what you expect.
**Fix:** Set **Icon Position** to Before to place the image ahead of the text, or After to place it after.

### The icon shows but the text is misaligned

**Cause:** The inserted image may need matching to your theme's button spacing.
**Fix:** The feature applies a standard vertical alignment to the image. Adjust spacing with theme CSS targeting the button's inserted image element.

---

## Frequently Asked Questions

### What happens if I leave the button text blank?

The feature falls back to `Pay Now` when **Button Text** is empty.

### How do I add an icon?

Set **Button Icon** to the URL of an image you want on the button. The field accepts an uploaded or hosted image URL and renders it inside the button.

### Can I place the icon before or after the text?

Yes. **Icon Position** offers Before (default) and After.

### Does this change how the order is processed?

No. Only the button's text and optional image change. The order submits exactly as before.

### Is the icon a font icon?

No. The **Button Icon** field takes an image URL, and the feature renders it as an image inside the button. It does not accept a Themify icon name.

---

## Related Articles

- [How to Customize the Order Review Heading in WooCommerce](woocommerce-custom-order-review-heading.md)
- [How to Show Product Images in the WooCommerce Checkout](woocommerce-show-product-images-checkout.md)
- [How to Customize the Add to Cart Button Text in WooCommerce](woocommerce-customize-add-to-cart-button.md)
