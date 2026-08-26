---
title: "How to Enable CDN Rewrite in WordPress"
slug: perf-cdn-rewrite
description: "Rewrite media URLs to use a CDN in Classic Monks. Automatically replaces your domain with a CDN domain in media URLs."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/perf-cdn-rewrite/
---

# How to Enable CDN Rewrite in WordPress

> CDN Rewrite in Classic Monks automatically rewrites media URLs to use a CDN domain. Serves images, CSS, and JavaScript from the CDN instead of your origin server.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

A CDN (Content Delivery Network) caches your static files on servers around the world. Serving files from a CDN closer to the visitor reduces load time and bandwidth costs.

---

## How to Enable this Feature

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings, then the **Performance** tab, **CDN** subtab.

### Step 2: Enable the Feature

Toggle on the feature.

### Step 3: Save and Test

Click **Save Changes**. Test on the frontend.

---

## Common Use Cases

### Global audience sites

Sites with visitors worldwide benefit from CDN caching. A visitor in Tokyo gets the file from a Tokyo server instead of your US-based origin server.

### High-traffic sites

For sites with millions of page views, a CDN reduces origin server load and bandwidth costs.

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

This feature registers 5 WordPress hooks in `cdn-enabler.php`:

**Filters:**

- `the_content` calls `cm_cdn_enabler()` (Rewrites content URLs to CDN (priority 100))
- `wp_get_attachment_url` calls `cm_cdn_enabler()` (Rewrites attachment URLs to CDN)
- `template_directory_uri` calls `cm_cdn_enabler()` (Rewrites theme directory URL to CDN)
- `script_loader_src` calls `cm_cdn_enabler()` (Rewrites script source URLs to CDN)
- `style_loader_src` calls `cm_cdn_enabler()` (Rewrites style source URLs to CDN)

```php
// Hooked in cdn-enabler.php
add_filter( 'the_content', 'cm_cdn_enabler' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
