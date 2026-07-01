---
title: "How to Use Secure Downloads in WordPress | CM"
slug: performance/perf-secure-downloads
description: "Add secure download links to media files in Classic Monks. Prevents direct file access by using signed, time-limited URLs for downloads."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/performance/perf-secure-downloads/
---

# How to Use Secure Downloads in WordPress

> Secure Downloads in Classic Monks replaces direct file URLs with signed, time-limited download links. Prevents hotlinking and unauthorized access to media files.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

Direct file URLs allow anyone to download your media files without visiting your site. Secure Downloads uses signed URLs that expire after a configurable time, preventing hotlinking and unauthorized access.

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

### Premium content sites

Sites offering downloadable content (ebooks, courses, templates) benefit from secure downloads that prevent unauthorized sharing.

### Membership sites

Members-only content should not be accessible via direct file URLs. Secure Downloads ensures only authenticated users can access files.

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
