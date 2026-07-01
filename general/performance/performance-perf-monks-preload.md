---
title: "How to Enable Intelligent Preloading in WordPress | CM"
slug: performance/perf-monks-preload
description: "Enable intelligent page preloading in Classic Monks. Preloads pages that the user is likely to visit next, based on hover and scroll behavior."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/performance/perf-monks-preload/
---

# How to Enable Intelligent Preloading in WordPress

> Intelligent Preloading in Classic Monks preloads pages the user is likely to visit next, based on hover intent, scroll position, and link proximity.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

Preloading the next page before the user clicks a link makes navigation feel instant. The page is already cached in the browser when the user clicks.

---

## How to Enable this Feature

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings, then the **Performance** tab, **Monks Preloading** subtab.

### Step 2: Enable the Feature

Toggle on the feature.

### Step 3: Save and Test

Click **Save Changes**. Test on the frontend.

---

## Common Use Cases

### High-traffic sites

For sites with many page views per session, preloading the next page creates an instant navigation experience.

### E-commerce

Preloading product pages from the shop page creates instant product page loads.

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

This feature registers 3 WordPress hooks in `monks-preload.php`:

**Actions:**

- `wp_head` calls `cm_preload_critical_images()` (Preloads featured images, logos, above-fold images (priority 1))
- `wp_enqueue_scripts` calls `cm_enqueue_monks_preload()` (Enqueues preload JS with config)

**Filters:**

- `script_loader_tag` calls `cm_add_monks_preload_defer()` (Adds defer attribute to preload script (priority 10))

```php
// Hooked in monks-preload.php
add_action( 'wp_head', 'cm_preload_critical_images' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
