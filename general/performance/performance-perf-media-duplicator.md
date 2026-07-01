---
title: "How to Use Media Duplicator in WordPress | CM"
slug: performance/perf-media-duplicator
description: "Duplicate media files in the Media Library in Classic Monks. Create a copy of any media file without re-uploading."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/performance/perf-media-duplicator/
---

# How to Use Media Duplicator in WordPress

> Media Duplicator in Classic Monks creates a copy of any media file in the Media Library. The duplicate is a separate file with its own metadata.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

The default WordPress Media Library doesn't have a duplicate function. Media Duplicator fills this gap by copying the file and creating new metadata.

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

### Template images

Duplicate a template image to use as a base for a new variation (e.g., same layout, different text).

### Version control

Duplicate an image before editing it to keep the original as a backup.

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

This feature registers 4 WordPress hooks in `media/media-duplicator.php`:

**Actions:**

- `admin_notices` calls `cm_display_bulk_duplicate_notice()` (Shows notice after bulk duplicate completes)

**Filters:**

- `media_row_actions` calls `cm_add_duplicate_media_action()` (Adds Duplicate link to media row actions (priority 10))
- `bulk_actions-upload` calls `cm_add_bulk_duplicate_media_action()` (Adds Bulk Duplicate to upload bulk actions)
- `handle_bulk_actions-upload` calls `cm_handle_bulk_duplicate_media()` (Processes bulk duplicate requests (priority 10))

```php
// Hooked in media/media-duplicator.php
add_filter( 'media_row_actions', 'cm_add_duplicate_media_action' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
