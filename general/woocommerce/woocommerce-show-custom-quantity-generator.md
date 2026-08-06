---
title: "How to Add a Quantity Input to the WooCommerce Checkout"
slug: show-custom-quantity-generator
description: "Let customers set a quantity amount before paying using a WooCommerce direct checkout link. Enable the quantity input in the One Click Checkout settings."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/show-custom-quantity-generator/
---

# How to Add a Quantity Input to the WooCommerce Checkout

> Show a quantity input on the WooCommerce direct checkout page so customers can set the amount before paying. Enable it in the One Click Checkout settings.

## Key Takeaways

- Show a quantity input on the direct checkout page
- Customers set the amount before completing the order
- Works with direct checkout links
- Enabled by default when the direct checkout feature is on
- Controlled from the One Click Checkout settings

## What Does the Feature Do?

A direct checkout link takes a customer straight to the checkout with a product pre-selected. The **Show Custom Quantity Generator** option decides whether that checkout form shows a quantity input the customer can change before paying.

When enabled, a quantity field appears on the direct checkout page so customers can adjust the amount before placing the order.

## Why You Need It

Quantity control matters for certain direct-checkout flows:

- B2B and wholesale buyers may need more than one unit
- Bulk promotions require a quantity the customer sets
- Some products are bought in multiples
- A single item is often the wrong default for these cases

---

## How to Show a Custom Quantity Input on the WooCommerce Direct Checkout

### Step 1: Enable Direct Checkout

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **One Click Checkout** settings area.
3. Confirm **Enable WooCommerce Direct Checkout Links** is on.

### Step 2: Enable the Quantity Input

In the same settings area, enable **Show Custom Quantity Generator**. It is on by default when the direct checkout feature is active.

### Step 3: Save and Test

Click **Save Changes**. Open a direct checkout link and confirm the quantity input appears on the checkout form so the customer can set the amount.

---

## Configuration Options

| Option | Effect | Default |
|--------|--------|---------|
| **Show Custom Quantity Generator** | Shows a quantity input on the direct checkout page. | On |

The quantity input appears on the direct checkout page created by the **Enable WooCommerce Direct Checkout Links** feature.

---

## What Gets Affected

- The direct checkout page: a quantity input is shown when enabled
- The order placed through the direct link: uses the quantity the customer sets

## What Does NOT Get Affected

- The product page quantity input: unchanged
- The main cart and standard checkout: unaffected
- The direct checkout link's default quantity: still the starting value, now editable

---

## How It Works

The direct checkout page reads the product and quantity from the link. When **Show Custom Quantity Generator** is enabled, the checkout form renders a quantity field prefilled with the link's quantity, letting the customer change it before the order is placed. When disabled, the quantity is locked and the form notes that custom quantity selection is off.

---

## Common Use Cases

**Wholesale link checkout.** A partner shares a direct link and buyers adjust quantity to their order size.

**Bulk promotions.** Customers set how many units they want from a promotion link.

**Repeat purchases.** A returning customer buys more than one unit without a conflict on the product page default.

---

## Troubleshooting

### The quantity input is not showing

**Cause:** **Show Custom Quantity Generator** is off, or the direct checkout feature is off.
**Fix:** Confirm both the direct checkout toggle and **Show Custom Quantity Generator** are enabled in the One Click Checkout settings.

### The quantity is locked and cannot be changed

**Cause:** The option is off, so the direct checkout page fixes the quantity.
**Fix:** Enable **Show Custom Quantity Generator** to make the quantity editable on the form.

### The quantity I enter does not apply

**Cause:** Another plugin or theme may override the direct checkout form.
**Fix:** Check for plugin conflicts on the checkout form and confirm the request to the direct checkout is using the custom quantity handler.

---

## Frequently Asked Questions

### Where does the quantity input appear?

On the WooCommerce direct checkout page that a direct checkout link opens. It is not added to the normal product page or standard checkout.

### Is it on by default?

Yes. **Show Custom Quantity Generator** defaults to on when the direct checkout feature is active.

### Can customers change quantity with a direct link?

Yes, when the option is enabled. The input is prefilled from the link but editable before payment.

### Does it affect the product page?

No. The product page has its own quantity input. This option only affects the direct checkout form.

---

## Related Articles

- [How to Enable WooCommerce Direct Checkout Links](woocommerce-enable-woocommerce-direct-checkout.md)
- [How to Add a Product Selector to the WooCommerce Checkout](woocommerce-enable-checkout-product-selector.md)
- [How to Show Product Images in the WooCommerce Checkout](woocommerce-show-product-images-checkout.md)
