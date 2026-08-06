---
title: "How to Hide the Default Variation Price in WooCommerce"
slug: hide-default-variation-price
description: "Hide the default variation price on WooCommerce variable products so the price shows after a variation is selected. Target the price element in Classic Monks."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/hide-default-variation-price/
---

# How to Hide the Default Variation Price in WooCommerce

> Hide the default price on a WooCommerce variable product so the price appears only after a variation is selected. Choose the CSS selector that targets the default price element with Classic Monks.

## Key Takeaways

- Hide the default variation price display until a variation is selected
- Set the CSS selector for the price element to hide
- Pairs with Update Price on Variation Selection for a clean experience
- Reduce confusion from "From $X" or wide price ranges
- One master toggle plus one target selector

## What Does the Feature Do?

Variable products show a price range or a "From" price based on their variations. For products with many options across a wide range, that default display can confuse customers about the price they will actually pay.

The **Hide Default Variation Price** feature hides the default price element until the customer selects a variation. Once a variation is chosen, the featured price shows for that specific selection, so the customer sees the exact price instead of a range.

## Why You Need It

The default range display is not always helpful:

- "From $10" suggests the cheapest option, but the customer may want a $50 variation
- A wide range makes a product look unpredictable
- Customers cannot tell which variation is priced where until they select it
- Showing the price only after selection makes the choice specific and clear

If the range itself is a selling point (for example, "From $5"), keep the default display and leave this off.

---

## How to Hide the Default Variation Price in WooCommerce

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Single Product** settings area.
3. Toggle on **Hide Default Variation Price**.

### Step 2: Set the Target Class

In **Default Variation Price Class**, set the CSS selector that targets the default price element. The default is `.woocommerce-variation-price`, which matches most themes. Adjust it if your theme uses a different class for the variation price area.

### Step 3: Save and Test

Click **Save Changes**. Open a variable product. Before selecting a variation, no default price should be shown. Select a variation and confirm the specific price appears.

---

## Configuration Options

| Option | Behavior | Default |
|--------|----------|---------|
| **Hide Default Variation Price** | Master toggle. | Off |
| **Default Variation Price Class** | CSS selector for the default price element to hide. | `.woocommerce-variation-price` |

---

## What Gets Affected

- Variable product pages: the default price element is hidden until a variation is selected
- The price element matched by **Default Variation Price Class**

## What Does NOT Get Affected

- The variation's actual price data: these are set in WooCommerce > Products > Variations
- Simple products and non-variable products: unaffected
- The selected variation's price: this still shows after selection
- Cart and checkout: prices are final at that point

---

## Advanced Options (Developers)

The feature registers its logic in `functions/woocommerce/variation-display.php`, gated on the **Hide Default Variation Price** option:

```php
add_action( 'wp_head', function() {
    echo '<style>.woocommerce-variation-price { display: none !important; }</style>';
} );
```

**`wp_head`** injects CSS that hides the default variation price element. The **Default Variation Price Class** option supplies the selector, defaulting to `.woocommerce-variation-price`. The same selector value is passed to the update-price-on-variation scripts so the behavior stays consistent.

---

## Troubleshooting

### The default price is still showing

**Cause:** The feature toggle is off, the selector does not match your theme's price element, or caching serves old HTML.
**Fix:** Confirm the toggle is on and that **Default Variation Price Class** matches the price element in your theme. Clear caches.

### The price does not reappear after selecting a variation

**Cause:** A theme or plugin blocks the variation price refresh after the default is hidden.
**Fix:** Confirm the feature pairs with the Update Price on Variation Selection behavior, and check that the variation price container matches **Price Container Class** in that feature. Review the browser console for JS errors.

### It hides the price on a product with a single variation

**Cause:** The selector matches a price element even when a product has effectively one price.
**Fix:** This is expected if the element matches. For products you do not want hidden, adjust the selector or leave the single-price product unmanaged by this feature.

### Only part of the price is hidden

**Cause:** The default element contains nested price parts, and the selector matches only part of it.
**Fix:** Use a selector that targets the full price container (for example, `.woocommerce-variation-price` rather than just the inner `.price`), or add a comma-separated list of classes if supported by your theme markup.

---

## Frequently Asked Questions

### What exactly gets hidden?

The element matched by **Default Variation Price Class** (default `.woocommerce-variation-price`), which holds the default variation price display. The selected variation's price appears after selection.

### Why would I hide the default price?

To avoid the confusion of a "From $" or wide range on variable products. Showing the price only after a selection makes the displayed amount specific to the chosen variation.

### Does this work with Update Price on Variation Selection?

Yes. The two features are designed to work together: the default price is hidden, and the update-price feature refreshes the displayed price when a variation is selected.

### Can I hide the price on all my variable products?

Yes, the toggle applies to variable product pages. Products whose price element matches the selector will have the default price hidden until a variation is selected.

### Will this affect the cart or checkout?

No. The feature only hides the default price display on product pages. The price at cart and checkout is unaffected.

---

## Related Articles

- [How to Update Price on Variation Selection in WooCommerce](woocommerce-update-price-on-variation.md)
- [How to Auto-Select the First Variation in WooCommerce](woocommerce-auto-select-first-variation.md)
- [How to Show the Amount Saved on Sale Products in WooCommerce](woocommerce-show-price-savings.md)
