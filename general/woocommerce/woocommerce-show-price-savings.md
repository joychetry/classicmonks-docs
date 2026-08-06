---
title: "How to Show the Amount Saved on Sale Products in WooCommerce"
slug: show-price-savings
description: "Display how much customers save on WooCommerce sale products with the price_savings shortcode. Customize the prefix and suffix text with Classic Monks."
last_updated: 2026-08-06
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/show-price-savings/
---

# How to Show the Amount Saved on Sale Products in WooCommerce

> Display the dollar amount a customer saves on a WooCommerce sale product using the `[price_savings]` shortcode. Customize the prefix and suffix text in Classic Monks, and pair it with the `[percentage_off]` shortcode if you also want the percent saved.

## Key Takeaways

- Show the exact amount saved on any sale product with `[price_savings]`
- Customize the prefix (default "You save") and suffix (default "now")
- Place the shortcode anywhere: product page, page builder, or loop template
- Only renders when the current product is on sale
- Pair with `[percentage_off]` for the discount percent

## What Does the Feature Do?

WooCommerce shows the original price crossed out next to the sale price, but it does not tell the shopper how much they actually save. The **Show Price Savings** feature adds a `[price_savings]` shortcode that prints the difference between the regular and sale price with customizable surrounding text.

When placed in a product context, the shortcode reads the current product's regular and sale prices, shows the savings as a formatted WooCommerce price, and wraps it in your prefix and suffix text. If the product is not on sale, it outputs nothing.

## Why You Need It

Displaying the saved amount is a well-known conversion lever:

- It makes the value of a sale concrete instead of abstract
- "You save $20 now" reads as a stronger reason to buy than a crossed-out price
- It works on the product page, archives, and custom layouts
- It is easy to tune: change the prefix and suffix once, and it updates across the site

---

## How to Show the Amount Saved on Sale Products in WooCommerce

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Single Product** settings area.
3. Toggle on **Show Price Savings**.

### Step 2: Set the Surrounding Text

- **Prefix Text** appears before the amount (default `You save`).
- **Suffix Text** appears after the amount (default `now`).

Together, the output reads like "You save $20 now".

### Step 3: Place the Shortcode

Insert the shortcode where you want the savings displayed:

```
[price_savings]
```

This works on the single product page, in page-builder content, and in loop templates, as long as a product is in context. If you also enabled **Show Percentage Off**, use `[percentage_off]` for the discount percent.

### Step 4: Save and Test

Click **Save Changes**. Open a product that is on sale and confirm the savings message appears where you placed the shortcode. Products not on sale show nothing.

---

## Configuration Options

| Option | Behavior | Default |
|--------|----------|---------|
| **Show Price Savings** | Master toggle for the `[price_savings]` shortcode. | Off |
| **Prefix Text** | Text before the saved amount. | `You save` |
| **Suffix Text** | Text after the saved amount. | `now` |
| **Show Percentage Off** | Separate toggle for the `[percentage_off]` shortcode. | Off |

---

## What Gets Affected

- Any page containing the `[price_savings]` shortcode: the saved amount renders when the product is on sale
- Customizable wording: prefix and suffix apply wherever the shortcode is used

## What Does NOT Get Affected

- The WooCommerce price display: the regular and sale prices keep their normal formatting
- Sale prices themselves: savings are calculated from the existing regular and sale prices
- Cart and checkout: the shortcode is for product display, not order totals
- Products not on sale: these output nothing from the shortcode

---

## How the Savings Is Calculated

The shortcode looks at the current product's regular price and sale price, subtracts the sale price from the regular price, and formats the result as a WooCommerce price. The percentage version divides the savings by the regular price and multiplies by 100, shown to two decimal places.

- Amount version (`[price_savings]`): `regular price - sale price`, formatted with the store currency.
- Percent version (`[percentage_off]`): `((regular price - sale price) / regular price) * 100`, shown as e.g. `Flat 25.00% off`.

Both require the current global product to be on sale; otherwise the shortcode returns empty.

---

## Troubleshooting

### The savings message is not showing

**Cause:** The feature toggle is off, the product is not on sale, or the shortcode is not in a product context.
**Fix:** Confirm **Show Price Savings** is on. Verify the product has a sale price lower than its regular price. Place the shortcode where a product is in context, such as the product page or a loop template.

### The amount looks wrong

**Cause:** The regular or sale price is set incorrectly, or tax-inclusive/exclusive settings affect the displayed value.
**Fix:** Check the product's regular and sale prices. Confirm your WooCommerce tax settings show prices as you expect. The savings uses the store's price formatting.

### Nothing appears on archive pages

**Cause:** The shortcode only renders when a product is in context and on sale.
**Fix:** Add the shortcode to the loop template or a page-builder loop block so each product supplies its own prices. Non-sale products in the loop will show nothing, which is expected.

### I want different wording

**Cause:** The prefix and suffix are not what you want.
**Fix:** Change **Prefix Text** and **Suffix Text** in the settings. No template edits are needed; the wording updates wherever the shortcode renders.

---

## Frequently Asked Questions

### What does the `[price_savings]` shortcode output?

It prints the amount saved on a sale product, wrapped in your prefix and suffix. With the defaults that is something like "You save $20 now". It renders nothing when the product is not on sale.

### How is the saved amount calculated?

The shortcode subtracts the sale price from the regular price and formats the result as a WooCommerce price using the store currency. The percentage variant divides the savings by the regular price and multiplies by 100.

### Where can I place the shortcode?

Anywhere a product is in context: the single product page, a page-builder block, or a loop template. It reads the current product's prices from the global product object.

### Is there a separate shortcode for the discount percent?

Yes. If **Show Percentage Off** is enabled, use `[percentage_off]` to display the percent saved (for example, "Flat 25.00% off").

### Does this affect the cart or checkout total?

No. Price savings and percentage off are product-display shortcodes only. They do not change order totals or how WooCommerce calculates discounts.

---

## Related Articles

- [How to Show Percentage Off in WooCommerce](woocommerce-show-percentage-off.md)
- [How to Show Product Price History on Your Store](woocommerce-product-price-history.md)
- [How to Customize the Add to Cart Button Text in WooCommerce](woocommerce-customize-add-to-cart-button.md)
