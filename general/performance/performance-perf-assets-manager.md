---
title: "How to Enable the Assets Manager in WordPress | CM"
slug: perf-assets-manager
description: "Control which CSS and JavaScript files load on each page in Classic Monks. Disable unnecessary assets per page for optimal performance."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/perf-assets-manager/
---

# How to Enable the Assets Manager in WordPress

> Assets Manager in Classic Monks lets you control which CSS and JavaScript files load on each page. Disable unnecessary assets per page for optimal performance.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

Most WordPress sites load the same CSS and JavaScript on every page, even when not needed. Assets Manager lets you disable specific assets on specific pages, reducing page weight.

---

## How to Enable this Feature

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings, then the **Performance** tab, **Assets Manager** subtab.

### Step 2: Enable the Feature

Toggle on the feature.

### Step 3: Save and Test

Click **Save Changes**. Test on the frontend.

---

## Common Use Cases

### Blog posts

Blog posts typically don't need WooCommerce JavaScript. Disabling WooCommerce assets on blog posts improves load time.

### Landing pages

Custom landing pages may not need plugin assets. Disabling them improves page speed.

---

## Troubleshooting

### The feature is not taking effect

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the toggle is on. Clear all caching layers.

### The feature breaks another plugin

**Cause:** Another plugin depends on the functionality that this feature disables.
**Fix:** Disable this feature if it breaks another plugin.

---

## Related Articles

- [How to Enable Lazy Loading in WordPress](performance/lazy-loading.md)
- [How to Use the WP Optimizations in WordPress](performance/wp-optimizations.md)
- [How to Use the Media Enhancements in WordPress](performance/media-enhancements.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)


### Developer integration

This feature registers 6 WordPress hooks in `assets-manager.php`:

**Actions:**

- `plugins_loaded` calls `CM_Assets_Manager_Module::initialize()` (Main entry point (priority 20))
- `template_redirect` calls `detect_content_type()` (Detects content type for asset rules (priority 5))
- `wp_print_styles` calls `unload_enqueued_styles()` (Dequeues disabled styles (priority 100000))
- `wp_print_scripts` calls `unload_enqueued_scripts()` (Dequeues disabled scripts (priority 100000))
- `wp_footer` calls `unload_enqueued_styles()` (Footer style dequeue for WP 6.9+ (priority 1))
- `wp_ajax_cm_assets_manager_update` calls `handle_ajax_update()` (AJAX handler for saving rules)

```php
// Hooked in assets-manager.php
add_action( 'plugins_loaded', 'CM_Assets_Manager_Module::initialize' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
