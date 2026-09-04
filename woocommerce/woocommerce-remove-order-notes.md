---
title: "How to Remove Order Notes from WooCommerce Checkout"
slug: remove-order-notes
description: "Remove the order notes text area from the WooCommerce checkout form. Shorten the checkout for stores that do not collect order instructions with Classic Monks."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/remove-order-notes/
---

# How to Remove Order Notes from WooCommerce Checkout

> Remove the order notes text area from the WooCommerce checkout form so customers cannot leave a note, coming, or instruction at checkout. Classic Monks strips the field when you need a shorter form.

## Key Takeaways

- Remove the order notes text area from the checkout form
- One toggle, no nested options
- Shortens the checkout for stores that do not need order instructions
- Does not delete previously saved order notes
- Admin order notes remain available

## What Does the Feature Do?

WooCommerce shows an optional order notes text area on the checkout form where customers can leave instructions. The **Remove Order Notes** feature removes that text area from the form when enabled.

Existing order notes already saved in the database are not deleted. The feature only stops the checkout from presenting the field, so new customers cannot add an order note at checkout.

## Why You Need It

For many stores the order notes field adds length without value:

- Most customers leave it blank
- A text area lengthens the checkout form
- Digital, service, and delivery-on-standard stores rarely need instructions
- Admin order notes are still available even when the customer field is removed

---

## How to Remove Order Notes from WooCommerce Checkout

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Checkout** settings area.
3. Toggle on **Remove Order Notes**.

### Step 2: Save and Test

Click **Save Changes**. Visit the checkout page and confirm the order notes text area no longer appears.

---

## Configuration Options

| Option | Default |
|--------|---------|
| **Remove Order Notes** | Off |

There are no nested options. The feature is a single on/off control.

---

## Common Use Cases

**Digital and service stores.** Stores that sell downloadable products, course access, or services usually do not need delivery instructions, so removing the field shortens the form.

**Standard delivery routes.** Fulfillment flows with fixed shipping rules rarely need a customer-provided note, making the field unnecessary overhead.

**Simpler checkout.** Any store aiming for a shorter, cleaner checkout can remove the field while keeping admin order notes for internal use.

---

## What Gets Affected

- The checkout form: the order notes text area is removed
- New orders: customers can no longer add an order note at checkout

## What Does NOT Get Affected

- Previously saved order notes: existing data stays in the database
- Admin order notes: the admin order screen can still hold notes you add there
- Other checkout fields: only the order notes area is removed
- Saved address data: unrelated to this feature

---

## Advanced Options (Developers)

The feature registers one hook in `functions/woocommerce/woocommerce-functions.php`:

```php
add_filter( 'woocommerce_checkout_fields', 'cm_remove_order_notes' );
```

**`woocommerce_checkout_fields`** calls `cm_remove_order_notes()` to remove the order notes field from the checkout form when the feature is enabled.

---

## Troubleshooting

### The order notes field is still showing

**Cause:** The feature toggle is off, the checkout is cached, or a theme re-adds the field.
**Fix:** Confirm **Remove Order Notes** is on and clear caches. If a theme or custom checkout builder re-registers the order notes field, it renders despite the removal.

### I still want to see order notes in the admin

**Cause:** Removing the customer field does not remove admin order notes.
**Fix:** The feature only hides the checkout field. Admin order notes added in the order editor remain available.

### Previously entered notes are gone

**Cause:** The feature removed the input for new orders but should not delete stored notes.
**Fix:** Verify notes were entered before the change and are stored on the order. The feature does not delete order note data; it only removes the checkout input.

---

## Frequently Asked Questions

### Do customers lose the ability to leave a note?

Yes, when the feature is on, customers can no longer enter an order note at checkout because the field is removed from the form.

### Are old order notes deleted?

No. Order notes already stored on existing orders remain in the database. The feature only removes the checkout input for new orders.

### Can staff still add order notes?

Yes. Admin order notes in the order editor are separate from the customer-facing checkout field and remain available.

### Will this affect shipping or billing fields?

No. Only the order notes text area is removed. The rest of the checkout form is unchanged.

---

## Related Articles

- [How to Remove the Company Field from WooCommerce Checkout](woocommerce-remove-company-field.md)
- [How to Add Placeholders to WooCommerce Checkout Fields](woocommerce-enable-checkout-field-placeholders.md)
- [How to Customize the Place Order Button in WooCommerce](woocommerce-custom-place-order-button.md)
