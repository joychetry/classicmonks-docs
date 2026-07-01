---
title: "How to Enable Lazy Loading in WordPress | CM"
slug: performance/perf-lazy-loading
description: "Enable lazy loading for images, iFrames, videos, and backgrounds in Classic Monks. Defers loading of off-screen content for faster initial page load."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/performance/perf-lazy-loading/
---

# How to Enable Lazy Loading in WordPress

> Lazy Loading in Classic Monks defers the loading of images, iFrames, videos, and background images until they are about to enter the viewport. Reduces initial page load time.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

Lazy loading delays the loading of off-screen content until the user scrolls to it. This dramatically reduces initial page load time by loading only the visible content first.

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

### Image-heavy pages

Pages with many images (galleries, portfolios, e-commerce) benefit from lazy loading. Only the visible images load initially.

### Long-form content

Long articles with embedded videos and images benefit from lazy loading. The initial load is faster because only the first screen loads.

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

This feature registers 5 WordPress hooks in `lazy-loading.php`:

**Actions:**

- `wp_enqueue_scripts` calls `cm_enqueue_lazy_loading_scripts()` (Enqueues lazy loading JS and config)
- `init` calls `cm_wordpress_lazy_load()` (Registers lazy loading on 13 content hooks)
- `init` calls `cm_woocommerce_lazy_load()` (Registers lazy loading on WooCommerce hooks)

**Filters:**

- `the_content` calls `cm_enhance_critical_images()` (Adds fetchpriority high to critical images (priority 20))
- `wp_get_attachment_image_attributes` calls `cm_unset_loading_on_attachment_images()` (Removes native loading attribute when custom lazy is active)

```php
// Hooked in lazy-loading.php
add_action( 'wp_enqueue_scripts', 'cm_enqueue_lazy_loading_scripts' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
