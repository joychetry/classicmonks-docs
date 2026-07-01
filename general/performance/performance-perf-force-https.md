---
title: "How to Force HTTPS Links in WordPress | CM"
slug: perf-force-https
description: "Force all internal links to use HTTPS in Classic Monks. Automatically rewrites HTTP links to HTTPS for a consistent, secure site."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/perf-force-https/
---

# How to Force HTTPS Links in WordPress

> Force HTTPS Links in Classic Monks automatically rewrites all internal WordPress links from HTTP to HTTPS. Ensures consistent HTTPS across your site without manual link editing.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- No configuration required (just enable/disable)
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## What Is this feature?

Force HTTPS Links in Classic Monks automatically rewrites all internal WordPress links from HTTP to HTTPS. Ensures consistent HTTPS across your site without manual link editing. This is one of many WordPress optimization features available in the Performance tab.

## Why You Need It

Mixed content (HTTP links on an HTTPS page) triggers browser warnings, breaks functionality, and hurts SEO. Forcing HTTPS on all internal links eliminates this problem without manually editing each link.

---

## How to Enable this Feature in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Performance Tab

Click on the **Performance** menu, then click the **WP Optimizations** subtab.

### Step 3: Enable the Feature

Toggle on the feature.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Clear your browser cache and visit the frontend. Verify the feature is working as expected.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| This feature | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- The feature behavior: enabled as configured
- The site performance: improved as described

## What Does NOT Get Affected

- The WordPress admin: unchanged
- The site content: unchanged
- The plugin functionality: unchanged

---

## Common Use Cases

### Migrating from HTTP to HTTPS

After installing an SSL certificate, many internal links may still point to HTTP. This feature automatically rewrites them, eliminating mixed content warnings and improving security.

### Sites with external embeds

When embedding content from non-HTTPS sources, the links may break. Forcing HTTPS on internal links ensures the site itself is secure while external content loads as-is.

---

## Troubleshooting

### The feature is not taking effect

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the toggle is on. Clear all caching layers.

### The feature breaks another plugin

**Cause:** Another plugin depends on the functionality that this feature disables.
**Fix:** Disable this feature if it breaks another plugin. The features are designed to be toggled independently.

---

## Related Articles

- [How to Enable Lazy Loading in WordPress](performance/lazy-loading.md)
- [How to Enable the Assets Manager in WordPress](performance/assets-manager.md)
- [How to Use the Media Enhancements in WordPress](performance/media-enhancements.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)


### Developer integration

This feature registers 6 WordPress hooks in `force-https.php`:

**Actions:**

- `init` calls `cm_init_force_https_filters()` (Initializes all HTTPS filters (priority 1))

**Filters:**

- `site_url` calls `cm_force_https_links()` (Converts site_url to HTTPS)
- `home_url` calls `cm_force_https_links()` (Converts home_url to HTTPS)
- `content_url` calls `cm_force_https_links()` (Converts content_url to HTTPS)
- `the_content` calls `cm_force_https_content()` (Converts HTTP URLs in content to HTTPS (priority 99))
- `the_excerpt` calls `cm_force_https_content()` (Converts HTTP URLs in excerpts to HTTPS)

```php
// Hooked in force-https.php
add_action( 'init', 'cm_init_force_https_filters' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
