---
title: "How to Lazy Load iFrames in WordPress | CM"
slug: performance/perf-lazy-load-iframes
description: "Enable lazy loading for iFrames in Classic Monks. Defers loading of embedded content (YouTube, Vimeo, maps) until they enter the viewport."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/performance/perf-lazy-load-iframes/
---

# How to Lazy Load iFrames in WordPress

> Lazy Load iFrames in Classic Monks defers iFrame loading until the iFrame enters the viewport. Embedded content (videos, maps) loads only when the user scrolls to them.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

iFrames are heavy resources that load additional HTML, CSS, and JavaScript. Lazy loading iFrames reduces initial page load time.

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

### YouTube embeds

Pages with multiple YouTube embeds benefit from lazy loading. Only the visible video loads initially.

### Google Maps embeds

Map embeds are heavy. Lazy loading them reduces initial page load time.

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



### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
