---
title: "How to Remove the Company Field from WooCommerce Checkout"
slug: remove-company-field
description: "Remove the company field from the WooCommerce checkout billing form to shorten it. Ideal for consumer stores that want a faster, cleaner checkout form."
last_updated: 2026-08-06
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/remove-company-field/
---

# How to Remove the Company Field from WooCommerce Checkout

> Remove the company name field from the WooCommerce billing form. Classic Monks strips the field from the checkout, leaving a shorter form for stores that do not collect company names.

## Key Takeaways

- Remove the company name input from the checkout billing form
- One toggle, no nested options
- Shortens the checkout form for consumer stores
- Leaves existing order and address data intact
- Does not affect any saved company values already in the database

## What Does the Feature Do?

WooCommerce's billing form includes a company name field by default. The **Remove Company Field** feature removes that input from the checkout form, so customers no longer see or fill in a company name.

The existing data is untouched: orders placed before or after still store whatever company value exists. The feature only stops the field from being shown and collected at checkout.

## Why You Need It

The company field is aimed at B2B invoicing. For consumer-facing stores it is often unnecessary:

- Few retail customers enter a company name
- An unused field adds length to the checkout form
- Removing it shortens the form and focuses customers on what matters
- B2B stores that need the field can keep it off

---

## How to Remove the Company Field from WooCommerce Checkout

### Step 1: Enable the Feature

1. In WordPress admin, open **Classic Monks > WooCommerce**.
2. Open the **Checkout** settings area.
3. Toggle on **Remove Company Field**.

### Step 2: Save and Test

Click **Save Changes**. Visit the checkout page and confirm the company name field no longer appears in the billing form.

---

## Configuration Options

| Option | Default |
|--------|---------|
| **Remove Company Field** | Off |

There are no nested options. The feature is a single on/off control.

---

## Common Use Cases

**Consumer stores.** Retail and consumer checkouts rarely need a company name, so removing the field shortens the form.

**Faster mobile checkout.** Fewer fields make the form quicker to complete on a phone.

**B2B invoicing elsewhere.** If company data matters, capture it through invoicing or order details rather than a checkout field.

---

## What Gets Affected

- The checkout billing form: the company name field is removed
- The checkout experience: customers no longer see or enter a company name

## What Does NOT Get Affected

- Existing saved company values: data already in the database is preserved
- Order records: any company value captured previously remains stored
- Custom checkout fields from other plugins: those are separate
- Billing and shipping address fields other than company: these stay in place

---

## Advanced Options (Developers)

The feature is wired in `functions/woocommerce/woocommerce-functions.php`:

```php
add_filter( 'woocommerce_checkout_fields', function($fields) {
    unset( $fields['billing']['billing_company'] );
    return $fields;
} );
```

**`woocommerce_checkout_fields`** runs an inline filter that unsets `billing_company` from the billing fields, so the input is no longer rendered at checkout.

---

## Troubleshooting

### The company field is still showing

**Cause:** The feature toggle is off, the checkout is cached, or a theme re-adds the field.
**Fix:** Confirm **Remove Company Field** is on and clear caches. If a theme or custom checkout builder re-registers a company field, it will render even with the default one removed.

### Only the billing company field disappears but not another

**Cause:** The feature removes the standard billing company field. A duplicate added by another plugin is separate.
**Fix:** Identify the source of the remaining field. The built-in field is removed by the feature's checkout-field filter.

### Existing orders still show a company name

**Cause:** The feature hides the field going forward; it does not delete stored data.
**Fix:** This is expected. Historical orders keep whatever company value they were saved with.

---

## Frequently Asked Questions

### Does this delete company names from existing orders?

No. The feature only removes the field from the checkout form. Company values already stored with prior orders remain in the database.

### Will new customers still be able to enter a company name?

No. With the field removed, customers no longer see or fill in a company name at checkout.

### Does it remove the field from the shipping form too?

The feature removes the company field from the billing checkout fields. If the shipping form also exposes a company field from another source, removal would target that field separately.

### Is this the same as hiding it for certain customers?

No. The toggle removes the field for everyone at checkout. It does not selectively show or hide based on customer role or order type.

---

## Related Articles

- [How to Add Placeholders to WooCommerce Checkout Fields](woocommerce-enable-checkout-field-placeholders.md)
- [How to Remove Order Notes from WooCommerce Checkout](woocommerce-remove-order-notes.md)
- [How to Customize the Place Order Button in WooCommerce](woocommerce-custom-place-order-button.md)
