---
title: "How to Use Media List View Default in WordPress | CM"
slug: perf-media-list-view
description: "Set the Media Library to list view by default in Classic Monks. Shows files in a detailed list format instead of a grid."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/perf-media-list-view/
---

# How to Use Media List View Default in WordPress

> Media List View Default in Classic Monks sets the Media Library to list view by default. Shows files in a detailed list with file size, dimensions, and other metadata.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

The default WordPress Media Library shows a grid view. List view provides more information (file size, dimensions, date) at a glance.

---

## How to Enable this Feature

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings, then the **Performance** tab, **Media Enhancements** subtab.

### Step 2: Enable the Feature

Toggle on the feature.

### Step 3: Save and Test

Click **Save Changes**. Test on the frontend.

---

## Common Use Cases

### Admin efficiency

List view shows more information per file, making it easier to find the right file without clicking into each one.

### File management

List view shows file sizes and dimensions, which helps with media management decisions.

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
- [How to Enable the Assets Manager in WordPress](performance/assets-manager.md)
- [How to Use the WP Optimizations in WordPress](performance/wp-optimizations.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)


### Developer integration

This feature registers 1 WordPress hook in `media/media-list-view.php`:

**Actions:**

- `admin_init` calls `cm_redirect_media_library_grid_to_list()` (Redirects grid view to list view)

```php
// Hooked in media/media-list-view.php
add_action( 'admin_init', 'cm_redirect_media_library_grid_to_list' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
