---
title: "How to Disable Google Fonts in WordPress | CM"
slug: performance/perf-disable-google-fonts
description: "Disable Google Fonts loading on the frontend in Classic Monks. Prevents external font requests that slow down page load and compromise privacy."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/performance/perf-disable-google-fonts/
---

# How to Disable Google Fonts in WordPress

> Disable Google Fonts in Classic Monks prevents Google Fonts from loading on the frontend, eliminating external font requests that slow down page load and raise privacy concerns.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- No configuration required (just enable/disable)
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## What Is this feature?

Disable Google Fonts in Classic Monks prevents Google Fonts from loading on the frontend, eliminating external font requests that slow down page load and raise privacy concerns. This is one of many WordPress optimization features available in the Performance tab.

## Why You Need It

Google Fonts make external requests to Google's servers, which adds latency and raises privacy concerns. Disabling them eliminates both issues.

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

Google Fonts make requests to Google servers, which can be flagged as a GDPR violation. Disabling them eliminates this compliance risk.

### Performance optimization

External font requests add latency to page load. Disabling Google Fonts removes this latency.

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

This feature registers 1 WordPress hook in `disablers.php`:

**Actions:**

- `wp_enqueue_scripts` calls `cm_disable_google_fonts()` (Deregisters Google Fonts stylesheets)

```php
// Hooked in disablers.php
add_action( 'wp_enqueue_scripts', 'cm_disable_google_fonts' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
