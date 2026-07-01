---
title: "How to Show the Assets Manager Frontend Icon in WordPress | CM"
slug: perf-show-frontend-icon
description: "Show the Assets Manager icon on the frontend for logged-in admins in Classic Monks. Provides quick access to asset controls from the frontend."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/perf-show-frontend-icon/
---

# How to Show the Assets Manager Frontend Icon in WordPress

> Show Frontend Icon in Classic Monks displays the Assets Manager icon on the frontend for logged-in administrators. Provides quick access to asset controls without navigating to the admin.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

The frontend icon provides quick access to asset controls while viewing the site. This is useful for debugging and testing asset changes.

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

### Debugging

When testing asset changes, the frontend icon provides instant access to the controls.

### Quick toggling

Toggle assets on/off directly from the frontend without navigating to the admin.

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

This feature registers 2 WordPress hooks in `assets-manager.php`:

**Actions:**

- `wp_footer` calls `render_frontend_icon()` (Renders the floating frontend icon (priority 100))
- `admin_bar_menu` calls `add_admin_bar_node()` (Adds Assets Manager node to admin bar (priority 1000))

```php
// Hooked in assets-manager.php
add_action( 'wp_footer', 'render_frontend_icon' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
