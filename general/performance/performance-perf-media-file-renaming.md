---
title: "How to Use Media File Renaming in WordPress | CM"
slug: performance/perf-media-file-renaming
description: "Rename media files in the Media Library in Classic Monks. Change the file name without breaking references."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/performance/perf-media-file-renaming/
---

# How to Use Media File Renaming in WordPress

> Media File Renaming in Classic Monks lets you rename media files in the Media Library. The file name and all references are updated automatically.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

WordPress doesn't allow renaming files after upload. Media File Renaming automates the process: rename the file and all references across the site are updated.

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

### SEO optimization

Renaming files from random strings (IMG_20260624.jpg) to descriptive names (blue-widget-large.jpg) improves SEO.

### File organization

Descriptive file names make the Media Library easier to navigate.

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

This feature registers 4 WordPress hooks in `media/media-file-renaming.php`:

**Actions:**

- `add_meta_boxes_attachment` calls `CM_Media_File_Renaming::register_meta_box()` (Adds rename metabox to attachment edit screen)
- `admin_post_cm_rename_media_file` calls `CM_Media_File_Renaming::handle_rename_request()` (Handles rename form submission)
- `wp_ajax_cm_rename_media_file_ajax` calls `CM_Media_File_Renaming::handle_ajax_rename_request()` (AJAX handler for rename requests)

**Filters:**

- `media_row_actions` calls `CM_Media_File_Renaming::add_media_row_action()` (Adds Rename link to media row actions (priority 10))

```php
// Hooked in media/media-file-renaming.php
add_filter( 'media_row_actions', 'CM_Media_File_Renaming::add_media_row_action' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
