---
title: "How to Exclude Above-the-Fold Images from Lazy Loading in WordPress | CM"
slug: perf-exclude-above-fold
description: "Exclude above-the-fold images from lazy loading in Classic Monks. Ensures visible images load immediately."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/perf-exclude-above-fold/
---

# How to Exclude Above-the-Fold Images from Lazy Loading in WordPress

> Exclude Above-the-Fold Images in Classic Monks excludes images that are visible on first load from the lazy loading queue. These images load immediately.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

Above-the-fold images should not be lazy loaded because they are visible on first load. Excluding them ensures a smooth initial experience.

---

## How to Enable this Feature

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings, then the **Performance** tab, **Lazy Loading** subtab.

### Step 2: Enable the Feature

Toggle on the feature.

### Step 3: Save and Test

Click **Save Changes**. Test on the frontend.

---

## Common Use Cases

### First screen optimization

The first screen should load immediately. Excluding above-the-fold images ensures this.

### No flash of unloaded content

Lazy loading above-the-fold images causes a flash of empty space. Excluding them prevents this.

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

- [How to Enable the Assets Manager in WordPress](performance/assets-manager.md)
- [How to Use the WP Optimizations in WordPress](performance/wp-optimizations.md)
- [How to Use the Media Enhancements in WordPress](performance/media-enhancements.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)


### Developer integration

This feature registers 1 WordPress hook in `lazy-loading.php`:

**Filters:**

- `cm_above_fold_patterns` calls `custom()` (Filterable list of CSS class patterns for above-fold detection)

```php
// Hooked in lazy-loading.php
add_filter( 'cm_above_fold_patterns', 'custom' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
