---
title: "How to Use Image Converter in WordPress | CM"
slug: performance/perf-image-converter
description: "Convert images between formats in Classic Monks. Supports WebP, AVIF, JPEG, and PNG conversion with batch processing."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/performance/perf-image-converter/
---

# How to Use Image Converter in WordPress

> Image Converter in Classic Monks converts images between formats (WebP, AVIF, JPEG, PNG) with batch processing support. Reduces image file sizes while maintaining quality.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

Modern image formats like WebP and AVIF offer significantly better compression than JPEG and PNG. Converting images can reduce file sizes by 30-50% without visible quality loss.

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

### Migration to WebP

If you're migrating from JPEG/PNG to WebP, the Image Converter can batch-convert your existing media library.

### Performance optimization

WebP images load faster and use less bandwidth. Converting your image library to WebP improves page speed across the site.

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



### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
