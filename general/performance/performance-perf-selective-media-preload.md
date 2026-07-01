---
title: "How to Enable Selective Media Preload in WordPress | CM"
slug: perf-selective-media-preload
description: "Enable selective media preloading in Classic Monks. Preloads specific media files instead of all media on the page."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/perf-selective-media-preload/
---

# How to Enable Selective Media Preload in WordPress

> Selective Media Preload in Classic Monks lets you specify which media files to preload, instead of preloading all media on the page.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

Preloading all media wastes bandwidth. Selective preloading targets only the media that matters most (hero images, above-the-fold content).

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

### Hero sections

Preload only the hero image, not all images on the page.

### Featured content

Preload the featured image or video, not all media on the page.

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

This feature registers 4 WordPress hooks in `selective-media-preload.php`:

**Actions:**

- `add_meta_boxes` calls `cm_add_selective_media_preload_metabox()` (Adds preload metabox to enabled post types)
- `save_post` calls `cm_save_selective_media_preload_data()` (Saves per-post preload media data)
- `wp_head` calls `cm_output_selective_media_preload_tags()` (Outputs link preload tags (priority 1))

**Filters:**

- `wp_img_tag_add_loading_attr` calls `cm_selective_media_prevent_lazy_loading()` (Prevents lazy loading for preloaded images (priority 10))

```php
// Hooked in selective-media-preload.php
add_action( 'add_meta_boxes', 'cm_add_selective_media_preload_metabox' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
