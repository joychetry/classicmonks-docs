---
title: "How to Use Native Lazy Loading in WordPress | CM"
slug: performance/perf-lazy-load-native
description: "Use the browser's native lazy loading when available in Classic Monks. Falls back to JavaScript-based lazy loading on older browsers."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/performance/perf-lazy-load-native/
---

# How to Use Native Lazy Loading in WordPress

> Native Lazy Loading in Classic Monks uses the browser's built-in lazy loading (loading='lazy' attribute) when available. Falls back to JavaScript on older browsers.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

Native lazy loading is more efficient than JavaScript-based lazy loading because it's handled by the browser's rendering engine. This option uses native when available, with a JS fallback.

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

### Modern browsers

For sites with mostly modern browser visitors, native lazy loading is faster and lighter than JavaScript-based solutions.

### Progressive enhancement

Using native with a JS fallback ensures all browsers get lazy loading, but modern browsers get the optimized version.

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

This feature registers 2 WordPress hooks in `lazy-loading.php`:

**Actions:**

- `init` calls `cm_disable_native_lazy_loading()` (Conditionally disables WP native lazy loading (priority 5))

**Filters:**

- `wp_lazy_loading_enabled` calls `__return_false()` (Disables native lazy loading attribute)

```php
// Hooked in lazy-loading.php
add_action( 'init', 'cm_disable_native_lazy_loading' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
