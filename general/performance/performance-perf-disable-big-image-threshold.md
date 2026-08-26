---
title: "How to Disable Big Image Size Threshold in WordPress"
slug: perf-disable-big-image-threshold
description: "Disable the big image size threshold in WordPress via Classic Monks. Prevents WordPress from downsizing images on upload."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/perf-disable-big-image-threshold/
---

# How to Disable Big Image Size Threshold in WordPress

> Disable Big Image Size Threshold in Classic Monks prevents WordPress from automatically downsizing images that exceed the configured threshold (default 2560px).

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

WordPress downsizes images larger than 2560px to save bandwidth. For sites that need full-resolution images (photography, e-commerce), this automatic downsizing is undesirable.

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

### Photography sites

Photographers need full-resolution images for portfolio display. Disabling the threshold preserves the original resolution.

### E-commerce sites

Product images need to be high-resolution for zoom features. Disabling the threshold preserves the original quality.

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

This feature registers 1 WordPress hook in `media-functions.php`:

**Filters:**

- `big_image_size_threshold` calls `__return_false()` (Disables WordPress big image size threshold)

```php
// Hooked in media-functions.php
add_filter( 'big_image_size_threshold', '__return_false' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
