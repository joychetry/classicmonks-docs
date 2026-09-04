---
title: "How to Auto-Select the First Variation in WooCommerce"
slug: auto-select-first-variation
description: "Auto-select the first available variation on WooCommerce variable product pages. Reduce the steps a customer needs before they can add an item to cart."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/auto-select-first-variation/
---

# How to Auto-Select the First Variation in WooCommerce

> Auto-select the first variation on a WooCommerce variable product so a purchase starts with an option already chosen. This removes one manual step before the add to cart action becomes available.

## Key Takeaways

- Preselect the first variation option on variable product pages
- Reduces the clicks a customer needs before adding to cart
- Applies when a variation dropdown has options to choose from
- Simple on/off toggle, no nested options

## What Does the Feature Do?

On a variable product page, WooCommerce leaves every variation unselected until the customer picks one. That is one extra step before the add to cart action can be used. The **Auto-Select First Variation** feature preselects the first option in each variation dropdown as soon as the page renders.

It works through the dropdown argument filter, so when a dropdown has options, the first one is set as the selected value.

## Why You Need It

Preselecting the first variation removes friction:

- Customers reach the add to cart action faster
- The default option is already chosen, so the price and selection state render immediately
- Stores with the most popular option listed first give new customers a sensible default
- The customer can still change the selection to any other variation

---

## How to Auto-Select the First Variation in WooCommerce

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Single Product** settings area.
3. Toggle on **Auto-Select First Variation**.

### Step 2: Save and Test

Click **Save Changes**. Visit a variable product on the front end. The first option in each variation dropdown should be preselected, and the customer can still pick another variation.

---

## Configuration Options

| Option | Default |
|--------|---------|
| **Auto-Select First Variation** | Off |

There are no nested options. The feature is a single on/off control.

---

## What Gets Affected

- Variable product pages: the first option in each variation dropdown is preselected on load
- The selection state: a variation is chosen as soon as the page renders

## What Does NOT Get Affected

- The variation choices themselves: all options remain available to change
- The product data and prices: these are unchanged
- Non-variable products: the feature only applies to variable products with dropdown options
- The cart: the feature preselects an option; it does not add anything to the cart

---

## Advanced Options (Developers)

The feature registers its logic in `functions/woocommerce/variation-display.php`, gated on the **Auto-Select First Variation** option:

```php
add_filter( 'woocommerce_dropdown_variation_attribute_options_args', function($args) {
    if (count($args['options']) > 0) {
        $args['selected'] = $args['options'][0];
    }
    return $args;
});
```

**`woocommerce_dropdown_variation_attribute_options_args`** modifies the dropdown options before rendering. When the dropdown has at least one option, the first one is set as the `selected` value.

---

## Troubleshooting

### The first variation is not preselected

**Cause:** The feature toggle is off, or the dropdown has no options available to select from.
**Fix:** Confirm **Auto-Select First Variation** is on. Check that the variable product is configured with variations for its attributes, and that the dropdown has options to choose from.

### The preselected option is not one the customer wants

**Cause:** The first option in the dropdown is preselected; the customer can change it.
**Fix:** Reorder the variations in the product's Variations tab if you want a different default. The customer can still select any other option after the page loads.

### It has no effect on my theme's dropdown

**Cause:** A theme or plugin may build variation attributes outside WooCommerce's standard dropdown filter.
**Fix:** Confirm the dropdown renders through the standard WooCommerce variation attribute options. Custom dropdown markup that bypasses this filter will not be affected.

---

## Frequently Asked Questions

### Which variation gets selected?

The first option in each variation dropdown is preselected when the dropdown has options. The customer can change it to any other listed variation.

### Does this add an item to the cart?

No. It only preselects a variation on the product page. Adding to cart still requires the customer to use the add to cart action.

### Can the customer still choose a different variation?

Yes. The selected option is just a default. All variations remain selectable after the page renders.

### Does it affect single attribute or multiple attribute products?

It applies to any variable product that uses dropdown attribute selection. Each dropdown gets its first option preselected when options exist.

---

## Related Articles

- [How to Update Price on Variation Selection in WooCommerce](woocommerce-update-price-on-variation.md)
- [How to Hide the Default Variation Price in WooCommerce](woocommerce-hide-default-variation-price.md)
- [How to Disable Out of Stock Variations in WooCommerce](woocommerce-disable-out-of-stock-variations.md)
