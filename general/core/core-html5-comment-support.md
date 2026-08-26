---
title: "How to Enable HTML5 Comment Support in Classic Monks"
slug: html5-comment-support
description: "Add HTML5 input types and validation attributes to the WordPress comment form in Classic Monks. Modern browser validation, mobile-friendly keyboards, no breaking changes."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/html5-comment-support/
---

# How to Enable HTML5 Comment Support in WordPress

> HTML5 Comment Support adds HTML5 input types (`email`, `url`) and validation attributes (`required`, `pattern`) to the WordPress comment form, improving mobile usability and browser-native form validation.

## Key Takeaways

- Single toggle, no nested options
- Adds `type="email"` to the email field, `type="url"` to the website field
- Adds `required` attributes for native browser validation
- Progressive enhancement (browsers without HTML5 fall back gracefully)
- Better mobile keyboards (email keyboard on the email field, URL keyboard on the website field)

## What Is the HTML5 Comment Support feature?

WordPress's default comment form uses HTML4 input types: `type="text"` for the name, email, and URL fields, with no validation attributes. The form works, but modern browsers can do better if you give them the right hints.

HTML5 Comment Support updates the comment form's input types to use the HTML5 equivalents:
- Name field: `type="text"` (unchanged, no HTML5-specific type)
- Email field: `type="email"` (triggers email keyboard on mobile, email validation on submit)
- Website field: `type="url"` (triggers URL keyboard on mobile, URL format validation)
- All required fields: adds the `required` attribute for native browser validation

The change is a progressive enhancement. Browsers that support HTML5 use the new types; browsers that don't ignore the new attributes and fall back to the default `type="text"` behavior.

## Why You Need It

- **Mobile usability**: When a mobile user taps the email field, they get the email-optimized keyboard (with @ and .com keys). Without HTML5, they get the standard text keyboard, which is harder for entering email addresses
- **Native validation**: Browsers validate the input format before the form submits. If the user enters an invalid email, the browser shows a tooltip before the form is even sent
- **Better accessibility**: Screen readers announce email and URL fields correctly when the input type is set
- **No breaking changes**: HTML5 is backward-compatible. If a browser doesn't support the new types, it falls back to the default text behavior

The trade-off is essentially zero. The change adds semantic information that modern browsers can use, with no impact on older browsers or on the server-side comment processing.

---

## How to Use HTML5 Comment Support in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Content Subtab

Click on the **Core** menu, then click the **Content** subtab.

### Step 3: Enable HTML5 Comment Support

Scroll to the **Comment System Overrides** section and toggle on **HTML5 Comment Support**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Open any post with comments on the front-end. View the page source and check the comment form: the email field should be `<input type="email">` (not `type="text"`), the website field should be `type="url"`, and the required fields should have the `required` attribute.

On a mobile device (or with mobile device emulation in browser dev tools), tap the email field. The mobile keyboard should show the @ and .com keys.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **HTML5 Comment Support** | Master toggle. | Off |

No nested options.

---

## What Gets Updated

| Field | Before | After |
|-------|--------|-------|
| Name | `<input type="text" name="author">` | `<input type="text" name="author" required>` (required attribute added) |
| Email | `<input type="text" name="email">` | `<input type="email" name="email" required>` |
| Website | `<input type="text" name="url">` | `<input type="url" name="url">` (still optional) |
| Comment textarea | `<textarea name="comment" rows="...">` | `<textarea name="comment" rows="..." required>` (required attribute added) |
| Submit button | `<input type="submit">` | Unchanged |

---

## Advanced Options (Developers)

```php
// Add custom pattern validation to the comment textarea (e.g., minimum length)
add_filter( 'comment_form_defaults', function( $defaults ) {
    $defaults['comment_field'] = '<p class="comment-form-comment"><label for="comment">Comment</label><textarea id="comment" name="comment" cols="45" rows="8" minlength="10" required></textarea></p>';
    return $defaults;
} );

// Customize the placeholder text for the new fields
add_filter( 'comment_form_default_fields', function( $fields ) {
    if ( isset( $fields['email'] ) ) {
        $fields['email'] = str_replace( '<input', '<input placeholder="you@example.com"', $fields['email'] );
    }
    return $fields;
} );

// Add a custom data attribute for analytics
add_filter( 'comment_form_field_email', function( $field ) {
    return str_replace( 'type="email"', 'type="email" data-track="comment-email"', $field );
} );
```

The comment_form_defaults filter is the standard WordPress hook for customizing the comment form. The data-track attribute is a simple way to add analytics tracking without a separate plugin.

---

## Troubleshooting

### The form fields are not showing the new input types

**Cause:** A caching plugin is serving a cached version of the comment form, or another plugin is overriding the form fields.
**Fix:** Clear all caching layers. Disable comment-related plugins one at a time to identify the conflict. The Classic Monks filter runs on `comment_form_default_fields`; if another plugin uses a higher-priority filter on the same hook, it can override the change.

### Mobile keyboards are still showing the text keyboard

**Cause:** The mobile browser doesn't support `type="email"` or `type="url"`, or the browser's user-agent is not being recognized correctly.
**Fix:** Modern iOS Safari and Android Chrome support these types as of 2020+. If the issue persists, check that the mobile device is running a recent browser version. Some custom keyboards (third-party keyboards on Android) may not respect the input type.

### The required attribute is blocking form submission unexpectedly

**Cause:** The required attribute prevents form submission if the field is empty. If a browser's autofill doesn't fill the field (e.g., the user disabled autofill), the form appears stuck.
**Fix:** This is correct browser behavior. Encourage users to enable autofill. For accessibility, ensure the required fields have visible labels (the Classic Monks-generated form already has this).

### I want HTML5 attributes only on specific fields, not all of them

**Cause:** The toggle applies all HTML5 attributes at once.
**Fix:** Use a small custom plugin that filters `comment_form_default_fields` to selectively remove the attributes you don't want. Example: `add_filter( 'comment_form_field_email', function( $field ) { return str_replace( ' required', '', $field ); } );` to remove required from the email field only.

### The browser console shows validation warnings

**Cause:** The form is working as expected. HTML5 validation triggers warnings when invalid input is submitted. These warnings are user-facing only; they don't affect the server.
**Fix:** No action needed. The warnings help users catch typos before submitting. If you want to suppress them, remove the `required` attribute via a custom filter.

---

## Related Articles

- [How to Configure Comments in Classic Monks](core-comments.md)
- [How to Disable Comments in Classic Monks](core-disable-comments.md)
