---
title: "How to Use Clean Image Filenames in WordPress | CM"
slug: perf-clean-filenames
description: "Auto-clean uploaded image filenames in Classic Monks. Removes special characters, spaces, and non-ASCII characters from file names."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/perf-clean-filenames/
---

# How to Use Clean Image Filenames in WordPress

> Clean Image Filenames in Classic Monks auto-cleans uploaded image filenames, removing special characters, spaces, and non-ASCII characters for better URLs.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

WordPress preserves the original file name, which may contain spaces, special characters, or non-ASCII characters. Clean filenames create better URLs and are more SEO-friendly.

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

Clean filenames create shorter, more descriptive URLs that search engines prefer.

### URL compatibility

Special characters in URLs can cause encoding issues on some servers.

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

This feature registers 1 WordPress hook in `media/media-clean-filenames.php`:

**Filters:**

- `sanitize_file_name` calls `CM_Clean_Image_Filenames::clean_filename()` (Converts accent characters to ASCII equivalents (priority 10))

```php
// Hooked in media/media-clean-filenames.php
add_filter( 'sanitize_file_name', 'CM_Clean_Image_Filenames::clean_filename' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
