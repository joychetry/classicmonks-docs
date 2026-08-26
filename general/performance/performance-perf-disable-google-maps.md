---
title: "How to Disable Google Maps in WordPress"
slug: perf-disable-google-maps
description: "Disable Google Maps loading on the frontend in Classic Monks. Prevents the Google Maps JavaScript from loading unless explicitly needed."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/perf-disable-google-maps/
---

# How to Disable Google Maps in WordPress

> Disable Google Maps in Classic Monks prevents the Google Maps JavaScript from loading on the frontend, reducing external requests and page load time.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- No configuration required (just enable/disable)
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## What Is this feature?

Disable Google Maps in Classic Monks prevents the Google Maps JavaScript from loading on the frontend, reducing external requests and page load time. This is one of many WordPress optimization features available in the Performance tab.

## Why You Need It

WordPress loads Google Maps JavaScript on pages that contain map embeds. For sites without maps, this JavaScript is unnecessary overhead.

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

### GDPR compliance

Google Maps makes requests to Google servers, which can be flagged as a GDPR violation. Disabling them eliminates this compliance risk.

### Sites without maps

If your site doesn't use Google Maps, the Maps JavaScript is dead weight. Disabling it improves performance.

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

This feature registers 2 WordPress hooks in `google-maps.php`:

**Actions:**

- `wp_enqueue_scripts` calls `cm_disable_google_maps()` (Dequeues and deregisters Google Maps script)

**Filters:**

- `pre_cm_update_option_disable_google_maps` calls `cm_toggle_google_maps()` (Toggle function for live enable/disable)

```php
// Hooked in google-maps.php
add_action( 'wp_enqueue_scripts', 'cm_disable_google_maps' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
