---
title: "How to Show Percent Off on WooCommerce Sale Products"
slug: show-percentage-off
description: "Display the discount percentage on WooCommerce sale products with the percentage_off shortcode. Customize the prefix and suffix text with Classic Monks."
last_updated: 2026-08-06
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/show-percentage-off/
---

# How to Show Percent Off on WooCommerce Sale Products

> Display the discount percentage on a WooCommerce sale product using the `[percentage_off]` shortcode. Customize the prefix and suffix text in Classic Monks, so a sale renders as something like "Flat 25.00% off".

## Key Takeaways

- Show the percent saved on any sale product with `[percentage_off]`
- Customize the prefix (default "Flat") and suffix (default "off")
- Place the shortcode on the product page, in page builder content, or in a loop
- Only renders when the current product is on sale
- Works alongside `[price_savings]` to show both amount and percent

## What Does the Feature Do?

A crossed-out regular price tells a shopper the product is on sale but not how much they are saving in percentage terms. The **Show Percentage Off** feature adds a `[percentage_off]` shortcode that computes the discount percent from the product's regular and sale prices and prints it with customizable surrounding text.

With the defaults, the output reads like "Flat 25.00% off". If the product is not on sale, the shortcode outputs nothing.

## Why You Need It

Percentages are often a clearer deal signal than a raw amount:

- "25% off" is immediately understandable to most shoppers
- It highlights the value of the discount without crowding the price line
- It pairs with the saved amount for a complete savings message
- The prefix and suffix let you match the wording to your store's voice

---

## How to Show the Percentage Off on Sale Products in WooCommerce

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Single Product** settings area.
3. Toggle on **Show Percentage Off**.

### Step 2: Set the Surrounding Text

- **Prefix Text** appears before the percentage (default `Flat`).
- **Suffix Text** appears after the percentage (default `off`).

Together, the default output reads like "Flat 25.00% off".

### Step 3: Place the Shortcode

Insert the shortcode where you want the percentage displayed:

```
[percentage_off]
```

This works on the single product page, in page-builder content, and in loop templates, as long as a product is in context. If you also enabled **Show Price Savings**, use `[price_savings]` for the saved amount.

### Step 4: Save and Test

Click **Save Changes**. Open a product that is on sale and confirm the percentage appears where you placed the shortcode. Products not on sale show nothing.

---

## Configuration Options

| Option | Behavior | Default |
|--------|----------|---------|
| **Show Percentage Off** | Master toggle for the `[percentage_off]` shortcode. | Off |
| **Prefix Text** | Text before the percentage. | `Flat` |
| **Suffix Text** | Text after the percentage. | `off` |
| **Show Price Savings** | Separate toggle for the `[price_savings]` shortcode. | Off |

---

## What Gets Affected

- Any page containing the `[percentage_off]` shortcode: the discount percent renders when the product is on sale
- Customizable wording: prefix and suffix apply wherever the shortcode is used

## What Does NOT Get Affected

- The WooCommerce price display: regular and sale prices keep their normal formatting
- Sale prices themselves: no prices are changed
- Cart and checkout: the shortcode is for product display only
- Products not on sale: these output nothing from the shortcode

---

## How the Percentage Is Calculated

The shortcode reads the current product's regular price and sale price, computes the discount as `regular price - sale price`, then divides by the regular price and multiplies by 100. The result is shown to two decimal places.

For example, a product with a $100 regular price and a $75 sale price produces `((100 - 75) / 100) * 100 = 25.00`, rendered as "Flat 25.00% off". The shortcode returns empty when the current product is not on sale.

---

## Troubleshooting

### The percentage is not showing

**Cause:** The feature toggle is off, the product is not on sale, or the shortcode is not in a product context.
**Fix:** Confirm **Show Percentage Off** is on. Verify the product has a sale price lower than its regular price, and place the shortcode where a product is in context.

### The percentage looks wrong

**Cause:** The calculation divides the savings by the regular price, so an incorrect regular or sale price produces an incorrect percent.
**Fix:** Check the product's regular and sale prices. If tax-inclusive prices are enabled, confirm the displayed values match what you expect.

### The number has too many or too few decimals

**Cause:** The shortcode always formats to two decimal places.
**Fix:** This is by design. The percentage is shown to two decimals regardless of the store's general price precision.

### Nothing appears on archive pages

**Cause:** The shortcode only renders when a product is in context and on sale.
**Fix:** Add the shortcode to the loop template or a page-builder loop block. Non-sale products in the loop show nothing, which is expected.

---

## Frequently Asked Questions

### What does the `[percentage_off]` shortcode output?

It prints the discount percent for a sale product, wrapped in your prefix and suffix. With the defaults that is something like "Flat 25.00% off". It renders nothing when the product is not on sale.

### How is the percentage calculated?

The shortcode subtracts the sale price from the regular price, divides by the regular price, and multiplies by 100, showing the result to two decimal places.

### Where can I place the shortcode?

Anywhere a product is in context: the single product page, a page-builder block, or a loop template. It reads the current product's prices from the global product object.

### Can I show both the amount and the percentage?

Yes. Enable **Show Price Savings** and **Show Percentage Off**, then use `[price_savings]` for the amount and `[percentage_off]` for the percent in the same page.

### Does this change the sale price or cart total?

No. The percentage shortcode is display-only. It does not alter prices or affect the cart or checkout totals.

---

## Related Articles

- [How to Show the Amount Saved on Sale Products in WooCommerce](woocommerce-show-price-savings.md)
- [How to Show Product Price History on Your Store](woocommerce-product-price-history.md)
- [How to Add Variation Swatches to WooCommerce in WordPress](woocommerce-product-swatches.md)
