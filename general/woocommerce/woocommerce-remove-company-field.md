---
title: "How to Remove the Company Field from WooCommerce Checkout in WordPress | CM"
slug: remove-company-field
description: "Remove the company name field from the WooCommerce checkout form in Classic Monks. Streamlines checkout for B2C customers and reduces form abandonment."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/remove-company-field/
---

# How to Remove the Company Field from WooCommerce Checkout in WordPress

> Remove Company Field strips the company name input from the WooCommerce billing and shipping checkout forms. Streamlines checkout for B2C stores and reduces form abandonment.

## Key Takeaways

- Single toggle, no nested options
- Removes the company field from billing and shipping checkout forms
- Useful for B2C stores where company information is not needed
- Reduces form fields and checkout abandonment
- Does not affect WooCommerce's B2B mode (that's a separate plugin)

## What Is the Remove Company Field feature?

By default, WooCommerce's billing and shipping checkout forms include a "Company name" field. This field is optional, but it adds visual clutter and a small amount of friction.

The Remove Company Field feature removes the company field from both billing and shipping forms. The customer's saved addresses (if any) are unaffected.

## Why You Need It

The company field is useful for B2B stores (businesses selling to other businesses) where the customer's company name is relevant for invoicing and reporting. For B2C stores (businesses selling to consumers), it's noise:

- Most B2C customers don't have a "company" to enter
- The field adds visual clutter to a long checkout form
- Removing it reduces form abandonment (one less field = higher conversion)

For most consumer e-commerce stores, removing the company field is a small win.

---

## How to Remove the Company Field from WooCommerce Checkout in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Checkout** subtab.

### Step 3: Enable Remove Company Field

Toggle on **Remove Company Field**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit the checkout page. The company field should not appear in the billing or shipping forms.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Remove Company Field** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- Billing checkout form: the company field is removed
- Shipping checkout form: the company field is removed
- The customer's saved addresses (in My Account): the company field is still stored (for compatibility with old data), but not displayed in the form
- The order confirmation email: the company name is no longer included
- The admin order details: the company name is still stored in the database (for legacy orders)

## What Does NOT Get Affected

- WooCommerce's B2B mode (a separate plugin, not Classic Monks)
- Custom checkout fields added by other plugins
- The customer's saved addresses (the data is preserved)
- The order in the admin (the company name is stored if it was provided)

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `woocommerce-functions.php`:

**Filters:**

- `woocommerce_checkout_fields` calls `anonymous()` (Removes company field from checkout)

```php
// Hooked in woocommerce-functions.php
add_filter( 'woocommerce_checkout_fields', 'anonymous' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### The company field is still showing

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the toggle is on. Clear all caching layers (page cache, object cache, CDN). The checkout page is a critical conversion path; cache it correctly.

### The field is gone but checkout validation fails

**Cause:** The company field was marked as required in some configurations. Removing it shouldn't cause validation issues, but if your checkout was relying on it, you may need to update.
**Fix:** Verify the checkout validation works without the field. The company field is optional by default, so this is rare.

### I want to hide the field for guest users but show it for logged-in wholesale customers

**Cause:** The toggle is global.
**Fix:** Disable the toggle globally. Configure in the plugin settings to exclude wholesale roles. This way, the field is hidden by default but shows for wholesale customers.

### The field is gone but the order data still has company info

**Cause:** This is expected. The toggle hides the form field. Orders placed before the toggle was enabled retain their company data in the database.
**Fix:** No action needed. The toggle doesn't delete existing data. If you want to clean up old data, do it via the database or a custom migration script.

---

## Related Articles

- [How to Enable Checkout Field Placeholders in WordPress](woocommerce-enable-checkout-field-placeholders.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
