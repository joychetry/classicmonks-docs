---
title: "How to Remove the Clear Variation Link in WooCommerce"
slug: remove-clear-variation-link
description: "Remove the clear selection link from the WooCommerce variation dropdowns and buttons. Keep the selected variation in place with a Classic Monks toggle."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/remove-clear-variation-link/
---

# How to Remove the Clear Variation Link in WooCommerce

> Remove the "clear" link that WooCommerce shows next to variation dropdowns so the selected variation can only be changed, not reset. Classic Monks hides the reset variations link.

## Key Takeaways

- Remove the clear/reset variations link on variable product pages
- Prevents customers from clearing the selected variation
- Hides the link via WooCommerce's reset-variations filter and CSS
- One toggle, no nested options
- The variation can still be changed to a different option

## What Does the Feature Do?

WooCommerce shows a "clear" or reset link next to variation dropdowns that lets a customer remove their selection. The **Remove Clear Variation Link** feature hides that link, so the selected variation is not cleared by the customer.

The feature removes the reset link markup and hides the element that WooCommerce renders for it, keeping the selected variation in place.

## Why You Need It

The clear link can be an unwanted control:

- It lets customers clear the variation, which can break the add-to-cart selection
- The link adds clutter next to the dropdown
- Some stores prefer that customers change to a different option rather than reset
- Removing it keeps the current selection stable on the product page

---

## How to Remove the Clear Variation Link in WooCommerce

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Single Product** settings area.
3. Toggle on **Remove Clear Variation Link**.

### Step 2: Save and Test

Click **Save Changes**. Open a variable product and confirm the clear/reset variation link no longer appears next to the dropdowns, while the dropdowns still let customers pick a different option.

---

## Configuration Options

| Option | Default |
|--------|---------|
| **Remove Clear Variation Link** | Off |

There are no nested options. The feature is a single on/off control.

---

## What Gets Affected

- Variable product pages: the clear/reset variations link is removed
- The reset-variations element: hidden

## What Does NOT Get Affected

- The variation dropdowns: unchanged and still selectable
- The variation data and prices: unchanged
- The ability to change variation: customers can still pick a different option
- The product page layout beyond the removed link

---

## Advanced Options (Developers)

The feature registers its logic in `functions/woocommerce/variation-display.php`:

```php
add_filter( 'woocommerce_reset_variations_link', '__return_empty_string' );
add_action( 'wp_head', function() {
    echo '<style>.reset_variations { display: none !important; }</style>';
} );
```

- **`woocommerce_reset_variations_link`** returns an empty string so WooCommerce does not render the reset link.
- **`wp_head`** injects CSS that hides the `.reset_variations` element for added safety.

---

## Common Use Cases

**Stable selections.** Stores that want the chosen variation to stay fixed on the product page.

**Cleaner dropdowns.** Removing the extra link keeps the variation controls tidy.

**Conversion flow.** Some themes place the reset link awkwardly, and removing it cleans the product page.

---

## Troubleshooting

### The clear link is still showing

**Cause:** The toggle is off, or a theme renders the reset link from its own template.
**Fix:** Confirm the toggle is on and clear caches. If a theme adds its own reset link markup, it is separate from WooCommerce's link.

### Customers can no longer remove a variation

**Cause:** The feature removes the reset link by design.
**Fix:** This is intended. Customers can still change the variation to a different option; only the reset/clear action is removed.

### The variation is stuck on the first selection

**Cause:** Removing the reset link means the variation stays selected once chosen.
**Fix:** If you want customers to reset, keep the feature off.

---

## Frequently Asked Questions

### What does this remove?

The clear/reset variations link that WooCommerce shows next to variation dropdowns on variable product pages.

### Can customers still change the variation?

Yes. They can select a different option. The only thing removed is the ability to clear/reset the current selection.

### Does it affect the variations themselves?

No. The variation data, prices, and dropdowns are unchanged. Only the reset link is hidden.

### Is it on by default?

No. The feature is off until you enable the toggle.

---

## Changing Versus Clearing

Removing the clear link does not stop customers from changing to a different variation. The dropdowns still list every option, and selecting another one updates the selection and price normally. The feature only removes the reset action, so a chosen variation stays put until the customer picks something else. This is useful where the reset link appears beside a dropdown and gets tapped by mistake, clearing the selection the customer intended to keep.

---

## Related Articles

- [How to Update Price on Variation Selection in WooCommerce](woocommerce-update-price-on-variation.md)
- [How to Auto-Select the First Variation in WooCommerce](woocommerce-auto-select-first-variation.md)
- [How to Add Variation Swatches to WooCommerce in WordPress](woocommerce-product-swatches.md)
