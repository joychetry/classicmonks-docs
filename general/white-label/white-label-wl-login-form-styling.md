---
title: "How to Style the Login Form in WordPress | CM"
slug: wl-login-form-styling
description: "Customize the WordPress login form styling in Classic Monks. Change colors, borders, shadows, and layout."
last_updated: 2026-07-28
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/wl-login-form-styling/
merged_docs: "How to Enable Login Form Shadow in WordPress"
---

# How to Style the Login Form in WordPress

> Customize the WordPress login form styling in Classic Monks. Change colors, borders, shadows, and layout.

## Key Takeaways

- Customize login form colors, borders, and layout
- Optional shadow effect for depth and visual hierarchy
- Quick admin customization with one click
- Does not affect frontend functionality
- Reversible (disable to restore default)

## Why You Need It

The default WordPress login form is plain. Customizing its styling creates a professional, branded login experience. Adding a shadow effect makes the form stand out from the background.

---

## How to Enable this Feature

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings, then the **White Label** tab.

### Step 2: Enable the Feature

Toggle on **Login Form Styling**.

### Step 3: Enable Shadow (Optional)

Toggle on **Login Form Shadow** to add a shadow effect to the login form. This creates depth and visual hierarchy.

### Step 4: Save and Test

Click **Save Changes**. Check the login page to verify the styling appears correctly.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Login Form Styling** | Master toggle. Enables custom form styling. | Off |
| **Login Form Shadow** | Adds a shadow effect to the login form. | Off |

---

## Common Use Cases

### Client white-labeling

For agencies that build WordPress sites for clients, white-labeling the admin creates a branded experience. The client sees your agency's branding instead of WordPress.

### Brand consistency

For companies that use WordPress as their CMS, white-labeling ensures the admin matches the company's brand guidelines.

### Multi-site management

For companies managing multiple WordPress sites, consistent white-labeling across all sites creates a unified admin experience.

---

## Troubleshooting

### The feature is not taking effect

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the toggle is on. Clear the admin page cache.

### The feature breaks the admin

**Cause:** The white-label feature may conflict with another admin customization plugin.
**Fix:** Disable other admin customization plugins to find the conflict.

---

## Related Articles

- [How to Use Content Management in WordPress](../core/core-content-management.md)
- [How to Use the Admin Menu Manager in WordPress](../interface/interface-admin-menu-manager.md)
- [How to Use the Login Page Customization in WordPress](white-label-wl-login-customization.md)

---

## Developer Notes

This feature registers hooks in `custom-login-page.php`:

**Actions:**

- `login_enqueue_scripts` calls `cm_custom_login_page_style()` (injects CSS for login form styling and shadow; priority 10)

```php
// Hooked in custom-login-page.php
add_action( 'login_enqueue_scripts', 'cm_custom_login_page_style' );
```

The feature modifies WordPress admin output by registering hooks. Disabling it reverses those changes.

### Before you enable this feature

White-label features modify the WordPress admin. Consider:

1. **Client expectations** (white-labeling hides WordPress branding, which may confuse clients)
2. **Brand guidelines** (match the customizations to your brand)
3. **Testing on all admin pages** (some customizations may look wrong on certain pages)
4. **Documentation** (record which customizations are enabled for future reference)

White-label features are designed to be safe, but they modify the admin HTML output. Test on all admin pages before enabling on production.
