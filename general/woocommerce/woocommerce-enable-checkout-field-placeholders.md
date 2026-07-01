---
title: "How to Enable Checkout Field Placeholders in WordPress | CM"
slug: woocommerce/enable-checkout-field-placeholders
description: "Add placeholder text inside WooCommerce checkout form fields in Classic Monks. Improves form usability and guides customer input."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/woocommerce/enable-checkout-field-placeholders/
---

# How to Enable Checkout Field Placeholders in WordPress

> Enable Checkout Field Placeholders adds placeholder text inside WooCommerce checkout form fields. Improves form usability by showing example input in empty fields.

## Key Takeaways

- Single toggle, no nested options
- Adds placeholder text to all checkout fields (first name, last name, address, etc.)
- Improves form completion rates (clearer input expectations)
- Customizable in the plugin settings
- Works with all WooCommerce themes and most checkout customizations

## What Is the Enable Checkout Field Placeholders feature?

By default, WooCommerce checkout fields show only the field label (e.g., "First name", "Email address"). The field is empty until the customer types.

The Enable Checkout Field Placeholders feature adds placeholder text inside each field, showing example input. For example:

- First name field: "John" (as placeholder)
- Email field: "you@example.com"
- Phone field: "555-123-4567"
- Address field: "123 Main Street"

The placeholder disappears when the customer starts typing.

## Why You Need It

Placeholder text improves checkout usability:

- **Clearer input expectations**: Customers know what format is expected (e.g., "MM/DD/YYYY" vs "DD/MM/YYYY")
- **Higher completion rates**: Less confusion = more completed checkouts
- **Better mobile experience**: Placeholders show even when the field is collapsed (which is common on mobile keyboards)

For most checkout forms, placeholder text is a standard UX improvement.

---

## How to Enable Checkout Field Placeholders in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the WooCommerce Tab

Click on the **WooCommerce** menu, then click the **Checkout** subtab.

### Step 3: Enable Checkout Field Placeholders

Toggle on **Enable Checkout Field Placeholders**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit the checkout page. Empty fields should show placeholder text. The placeholder disappears when the customer types.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Checkout Field Placeholders** | Master toggle. | Off |

The default placeholder text is provided by Classic Monks. To customize the placeholder text per field, use the plugin settings (see Advanced Options).

---

## What Gets Affected

- All standard WooCommerce checkout fields: first name, last name, company, email, phone, address, city, postcode, country, state
- The placeholder is shown when the field is empty and focused
- The placeholder disappears when the customer types

## What Does NOT Get Affected

- The field labels (still shown above the field)
- The validation messages (still shown when validation fails)
- Custom fields added by other plugins (those plugins handle their own placeholders)
- The order review section (placeholders are not used in review)
- The cart page (placeholders are only on the checkout form)

---

## Advanced Options (Developers)

This feature registers 2 WordPress hooks in `woocommerce-functions.php`:

**Filters:**

- `woocommerce_checkout_fields` calls `cm_add_checkout_placeholders()` (Adds placeholders to checkout fields)
- `woocommerce_default_address_fields` calls `cm_add_address_placeholders()` (Adds placeholders to address fields)

```php
// Hooked in woocommerce-functions.php
add_filter( 'woocommerce_checkout_fields', 'cm_add_checkout_placeholders' );
```

The feature modifies WooCommerce behavior by registering or removing hooks. Disabling it reverses those changes.

## Troubleshooting

### Placeholders are not showing

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the toggle is on. Clear all caching layers. Placeholders are rendered server-side, so caching is the most common cause.

### Placeholders are showing but the field labels are missing

**Cause:** The placeholder is replacing the label, not supplementing it. This is usually a theme issue.
**Fix:** Verify the theme's checkout template includes both the label and the input. Some themes show the label as a placeholder by default (without this feature). Use a child theme to fix.

### The placeholder is in the wrong language

**Cause:** The default placeholder text is in English. Your store may be in a different language.
**Fix:** Configure in the plugin settings to customize the placeholder text per language. Or use a translation plugin (WPML, Polylang) to provide translated placeholders.

### The placeholder overlaps the field label

**Cause:** Some themes render the label as a placeholder, then this feature adds another placeholder, creating visual confusion.
**Fix:** Disable the theme's label-as-placeholder behavior (usually a theme option) or hide the labels with CSS.

---

## Related Articles

- [How to Enable Inline Checkout Field Validation in WordPress](woocommerce-enable-inline-checkout-field-validation.md)
- [How to Remove the Company Field from WooCommerce Checkout in WordPress](woocommerce-remove-company-field.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
