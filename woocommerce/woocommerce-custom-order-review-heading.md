---
title: "How to Customize the Order Review Heading in WooCommerce"
slug: custom-order-review-heading
description: "Replace the default order review heading on the WooCommerce checkout with your own text. Match the final checkout step to your brand in Classic Monks."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/custom-order-review-heading/
---

# How to Customize the Order Review Heading in WooCommerce

> Replace the default "Your order" heading above the checkout order review section with your own text. Set the heading in Classic Monks and it appears on the checkout page.

## Key Takeaways

- Change the "Your order" heading at the checkout order review
- Set the heading text in the Checkout settings
- Works on the checkout page, not on the order-received page
- One master toggle plus one text field
- Pairs with custom order review theming

## What Does the Feature Do?

WooCommerce shows a heading, often "Your order", above the order review section at checkout. The **Custom Order Review Heading** feature lets you replace that text with your own wording, such as "Review your order", "Almost done", or a brand-specific phrase.

The change targets the checkout form specifically, so it does not alter the order-received (thank you) page heading.

## Why You Need It

The order review heading is a visible element at a key moment:

- It sets the tone for the final confirmation step
- Action-oriented wording can encourage completion
- Branded language keeps the checkout consistent with your store
- It is a small change with a visible effect on the checkout form

---

## How to Customize the Order Review Heading in WooCommerce

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Checkout** settings area.
3. Toggle on **Custom Order Review Heading**.

### Step 2: Set the Heading Text

In **Heading Text**, enter the wording you want to appear above the order review. Leave it blank to keep the default "Your order".

### Step 3: Save and Test

Click **Save Changes**. Visit the checkout page and confirm the order review section shows your custom heading.

---

## Configuration Options

| Option | Behavior | Default |
|--------|----------|---------|
| **Custom Order Review Heading** | Master toggle. | Off |
| **Heading Text** | Text shown above the order review at checkout. | Blank (uses "Your order") |

---

## Common Use Cases

**Reassurance at the final step.** A calm, clear heading like "Review your order" helps customers confirm what they are about to buy.

**Brand consistency.** Wording that matches your store's voice keeps the checkout on-brand.

**Conversion focus.** An action-oriented heading can nudge hesitant customers toward completing the order.

---

## What Gets Affected

- The checkout page: the order review heading text is replaced
- The order review section's visible label

## What Does NOT Get Affected

- The order-received (thank you) page heading: the feature targets the checkout form
- Order review content and totals: only the heading text changes
- Other checkout section headings: billing, shipping, and payment headings are unchanged
- The checkout process itself: only the label changes

---

## Advanced Options (Developers)

The feature registers a hook in `functions/woocommerce/woocommerce-functions.php`:

```php
add_filter( 'gettext', 'cm_custom_order_review_heading', 20, 3 );
```

**`gettext`** calls `cm_custom_order_review_heading` at priority 20 with three arguments. The function replaces the "Your order" string when it appears in the WooCommerce context on an `is_checkout()` page that is not the `order-received` endpoint, returning the custom heading text.

---

## Troubleshooting

### The heading is not changing

**Cause:** The feature toggle is off, the heading text is blank, or the checkout is cached.
**Fix:** Confirm the toggle is on and that **Heading Text** is not empty. Clear caches and reload the checkout page.

### The heading changes on a non-checkout page

**Cause:** The text filter may also match the same string elsewhere.
**Fix:** The filter is scoped to the WooCommerce context on the checkout page. If another string matches "Your order" in that context, check whether a theme or plugin alters the page context used by the filter.

### The custom heading is empty

**Cause:** The **Heading Text** field is blank.
**Fix:** Enter the heading text you want. A blank value keeps the default "Your order".

---

## Frequently Asked Questions

### What is the default heading?

The default is the WooCommerce "Your order" heading shown above the checkout order review. Leave **Heading Text** blank to keep it.

### Does it change the thank you page?

No. The feature targets the checkout page, not the order-received (thank you) page.

### Can I use any text?

Yes. Enter any wording you want in **Heading Text**, and it replaces the checkout order review heading.

### Where is the setting?

Under **Classic Monks > WooCommerce > Checkout**, in the **Custom Order Review Heading** settings.

---

## Related Articles

- [How to Show Product Images in the WooCommerce Checkout](woocommerce-show-product-images-checkout.md)
- [How to Customize the Place Order Button in WooCommerce](woocommerce-custom-place-order-button.md)
- [How to Remove Order Notes from WooCommerce Checkout](woocommerce-remove-order-notes.md)
