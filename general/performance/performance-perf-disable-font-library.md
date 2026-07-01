---
title: "How to Disable the WordPress Font Library in WordPress | CM"
slug: performance/perf-disable-font-library
description: "Disable the WordPress Font Library in Classic Monks. Removes the font manager from the admin, preventing unexpected font loading."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/performance/perf-disable-font-library/
---

# How to Disable the WordPress Font Library in WordPress

> Disable WordPress Font Library in Classic Monks removes the WordPress 6.5+ font manager from the admin, preventing fonts from being loaded unexpectedly.

## Key Takeaways

- Single toggle, no nested options
- Quick WordPress optimization with one click
- No configuration required (just enable/disable)
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## What Is this feature?

Disable WordPress Font Library in Classic Monks removes the WordPress 6.5+ font manager from the admin, preventing fonts from being loaded unexpectedly. This is one of many WordPress optimization features available in the Performance tab.

## Why You Need It

The WordPress Font Library (added in WP 6.5) allows users to upload and manage fonts in the admin. This can load unexpected fonts and increase page size.

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

### Sites with custom fonts

If you're using custom fonts (self-hosted or from a theme), the WordPress Font Library can conflict. Disabling it prevents conflicts.

### Minimal admin experience

The Font Library is a new feature that may confuse admins. Disabling it keeps the admin simple and focused.

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

- `init` calls `cm_disable_font_library()` (Deregisters font library assets)

```php
// Hooked in disablers.php
add_action( 'init', 'cm_disable_font_library' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend

### How it works under the feature

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.
