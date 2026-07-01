---
title: "How to Disable WordPress Emoji via Assets Manager in WordPress | CM"
slug: performance/perf-disable-emoji-assets
description: "Disable the WordPress emoji script via the Assets Manager in Classic Monks. More granular control than the global emoji disable."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/performance/perf-disable-emoji-assets/
---

# How to Disable WordPress Emoji via Assets Manager in WordPress

> Disable WordPress Emoji via Assets Manager in Classic Monks provides page-level control over the emoji script, disabling it only where needed.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

The Assets Manager version is more granular than the global emoji disable. You can disable the emoji script on specific pages while keeping it on others.

---

## How to Enable this Feature

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings, then the **Performance** tab, **Assets Manager** subtab.

### Step 2: Enable the Feature

Toggle on the feature.

### Step 3: Save and Test

Click **Save Changes**. Test on the frontend.

---

## Common Use Cases

### Performance-focused pages

Disable the emoji script on high-traffic pages (blog posts, landing pages) while keeping it on pages where emojis are used.

### A/B testing

Compare page speed with and without the emoji script on specific pages.

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
- [How to Use the WP Optimizations in WordPress](performance/wp-optimizations.md)
- [How to Use the Media Enhancements in WordPress](performance/media-enhancements.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)


### Developer integration

This feature registers 1 WordPress hook in `assets-manager.php`:

**Actions:**

- `template_redirect` calls `conditionally_remove_emoji()` (Removes emoji actions when detected (priority 6))

```php
// Hooked in assets-manager.php
add_action( 'template_redirect', 'conditionally_remove_emoji' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
