---
title: "How to Hide Laser Loader on Mobile Devices in WordPress | CM"
slug: interface/interface-laser-loader-mobile
description: "Hide the laser loader on mobile devices in Classic Monks. Prevents the progress bar from appearing on phones and tablets where loading animations are less effective."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/interface/interface-laser-loader-mobile/
---

# How to Hide Laser Loader on Mobile Devices in WordPress

> Hide on Mobile Devices in Laser Loader prevents the progress bar from appearing on mobile devices. Mobile users benefit more from fast content delivery than from loading animations.

## Key Takeaways

- Single toggle, no nested options
- Works with [Laser Loader](interface-laser-loader.md) (must be enabled first)
- Configurable per page or per context
- Does not affect page load time (visual only)

## What Is this feature?

This feature is part of the Laser Loader system in Classic Monks. It modifies how the laser-style progress bar behaves or appears on your site. The Laser Loader must be enabled first (see [Laser Loader](interface-laser-loader.md)).

## Why You Need It

Customizing the laser loader behavior allows you to:

- Match the loader to your site's design (color, animation, speed)
- Optimize the loader for different devices (desktop vs mobile)
- Create a more professional or branded loading experience

---

## How to Configure this Feature

### Step 1: Enable Laser Loader

First, enable the Laser Loader master toggle in the Laser Loader subtab.

### Step 2: Navigate to Settings

Click into the **Classic Monks** plugin settings, then the **Interface** tab, **Laser Loader** subtab.

### Step 3: Enable the Feature

Toggle on this feature.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit the frontend and navigate between pages. Verify the laser loader behavior matches your configuration.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| This feature | Master toggle. | Off |

---

## What Gets Affected

- The laser loader behavior: modified per this feature
- The page load: unchanged (visual only)
- The user experience: modified for the configured context

## What Does NOT Get Affected

- The actual page load time: unchanged
- The page content: unchanged
- The search engine indexing: unchanged

---

## Common Use Cases

### Mobile-first sites

If your site is primarily used on mobile, the laser loader may be unnecessary. Mobile users expect fast loads and may find the animation distracting.

### Progressive Web Apps (PWAs)

PWA sites already have a smooth loading experience. The laser loader may conflict with PWA loading indicators.

---



### Mobile performance optimization

Mobile devices have limited processing power and often slower connections. A complex loading animation can actually slow down the mobile experience rather than improve it. Disabling the loader on mobile ensures the fastest possible perceived load time.

### Progressive Web Apps (PWAs)

PWA sites already have a smooth loading experience built into the PWA framework. Adding a laser loader on top of the PWA loading would create a confusing double-loading experience. Disabling the loader on mobile avoids this conflict.

### AMP pages

For sites using AMP (Accelerated Mobile Pages), the laser loader may conflict with AMP's own loading indicators. Disabling the loader on mobile ensures AMP pages work as expected.
## Troubleshooting

### The feature is not taking effect

**Cause:** The Laser Loader master toggle is not enabled, or a page caching plugin is serving old content.
**Fix:** Verify both toggles are on. Clear all caching layers.

### The laser loader shows on pages where it shouldn't

**Cause:** The laser loader is showing on all pages by default.
**Fix:** Use the `cm_laser_loader_excluded_pages` filter to exclude specific pages.

---

## Related Articles

- [How to Use Laser Loader in WordPress](interface-laser-loader.md)
- [How to Use Preloader in WordPress](interface-preloader.md)
- [How to Use Page Transitions in WordPress](interface-page-transitions.md)


### Performance-conscious users

Users who browse on mobile devices are often conscious of data usage and battery life. Disabling the laser loader on mobile respects these concerns and provides a cleaner, more efficient mobile experience.
### Developer integration

This feature registers 1 WordPress hook in `laser-loader.php`:

**Actions:**

- `wp_enqueue_scripts` calls `CM_Laser_Loader::enqueue_assets()` (Enqueues laser loader with mobile device detection)

```php
// Hooked in laser-loader.php
add_action( 'wp_enqueue_scripts', 'CM_Laser_Loader::enqueue_assets' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes.

### Mobile-specific optimizations

When the laser loader is disabled on mobile, the page transitions are handled differently. The mobile experience uses a simpler, faster transition that does not include the progress bar. This ensures mobile users get the fastest possible experience without the overhead of the laser loader.

For sites that want a mobile loader, consider using the Preloader feature instead. The Preloader is designed to be lighter than the Laser Loader and works better on mobile devices. The Preloader uses simple CSS animations that are more efficient than the Laser Loader's JavaScript-driven progress bar.
