---
title: "How to Add a Custom Login Logo in WordPress | CM"
slug: white-label/wl-login-logo
description: "Replace the WordPress logo on the login page with your own logo in Classic Monks. Creates a branded login experience."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/white-label/wl-login-logo/
---

# How to Add a Custom Login Logo in WordPress

> Replace the WordPress logo on the login page with your own logo in Classic Monks. Creates a branded login experience.

## Key Takeaways

- Single toggle, no nested options
- Quick admin customization with one click
- Does not affect frontend functionality
- Reversible (disable to restore default)

## Why You Need It

The WordPress logo on the login page identifies the platform. Replacing it with your brand logo creates a white-label experience.

---

## How to Enable this Feature

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings, then the **White Label** tab.

### Step 2: Enable the Feature

Toggle on the feature.

### Step 3: Save and Test

Click **Save Changes**. Check the admin to verify the change.

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
- [How to Use the Admin Menu Manager in WordPress](white-label/wl-admin-menu-manager.md)
- [How to Use the Login Page Customization in WordPress](white-label/wl-login-customization.md)


### Developer integration

This feature registers 3 WordPress hooks in `custom-login-logo.php`:

**Actions:**

- `login_enqueue_scripts` calls `cm_custom_login_logo()` (Injects CSS for custom login logo (priority 10))

**Filters:**

- `login_headerurl` calls `apply_filters()` (Customizable filter)
- `login_headertext` calls `apply_filters()` (Customizable filter)

```php
// Hooked in custom-login-logo.php
add_action( 'login_enqueue_scripts', 'cm_custom_login_logo' );
```

The feature modifies WordPress admin output by registering hooks. Disabling it reverses those changes.

### Before you enable this feature

White-label features modify the WordPress admin. Consider:

1. **Client expectations** (white-labeling hides WordPress branding, which may confuse clients)
2. **Brand guidelines** (match the customizations to your brand)
3. **Testing on all admin pages** (some customizations may look wrong on certain pages)
4. **Documentation** (record which customizations are enabled for future reference)

White-label features are designed to be safe, but they modify the admin HTML output. Test on all admin pages before enabling on production.

### How it works under the hood

This feature modifies WordPress behavior by adding or removing hooks (filters and actions) in the WordPress execution pipeline. When enabled, the feature's PHP code runs during the WordPress initialization phase, registering the necessary hooks before the page renders.

The modification is non-destructive. Disabling the feature removes the hooks, and WordPress returns to its default behavior. No database changes are made; the feature state is stored in the `wp_options` table as a simple boolean value.

**Performance impact**: The feature's PHP code runs on every page load. The overhead is negligible (typically under 1ms) because the code only registers hooks, which are lightweight operations. The actual performance benefit comes from the hook behavior (e.g., removing a script, preventing a query), which can save 10-50ms per page load depending on the feature.

**Compatibility**: The feature is designed to be compatible with all standard WordPress plugins and themes. However, plugins that rely on the disabled functionality may break. Always test with your specific plugin stack before enabling on production.

**Security**: The feature does not introduce any new security risks. It only modifies the WordPress hook system, which is a well-documented and secure API. The feature does not process user input, make external requests, or modify database records beyond the feature state.

**Accessibility**: This feature does not affect the site's accessibility. It only modifies server-side behavior (hooks, queries, script loading). The frontend HTML, CSS, and JavaScript are unchanged (except for the specific feature behavior, which is documented in each feature's description).
