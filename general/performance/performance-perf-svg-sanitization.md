---
title: "How to Enable SVG Security Sanitization in WordPress"
slug: perf-svg-sanitization
description: "Sanitize SVG files on upload to prevent malicious code injection in Classic Monks. Strips potentially dangerous elements from SVG files."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/perf-svg-sanitization/
---

# How to Enable SVG Security Sanitization in WordPress

> SVG Security Sanitization in Classic Monks sanitizes SVG files on upload, stripping potentially dangerous elements (JavaScript, event handlers, external references) while preserving the visual content.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

SVG files can contain malicious JavaScript. Sanitization strips dangerous elements while preserving the visual content, making SVG uploads safe.

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

### Safe SVG uploads

Sanitization ensures that SVG files uploaded to the Media Library don't contain malicious code that could execute in browsers.

### Client site security

For sites managed by multiple users, sanitization prevents accidental upload of malicious SVG files.

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
