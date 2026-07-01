---
title: "How to Use Laser Loader in WordPress | CM"
slug: interface/interface-laser-loader
description: "Add a laser-style page load progress bar to your WordPress site in Classic Monks. Shows a progress bar that sweeps across the page as it loads."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/interface/interface-laser-loader/
---

# How to Use Laser Loader in WordPress

> Laser Loader in Classic Monks adds a laser-style progress bar that sweeps across the page as it loads. Shows visitors that the page is loading, reducing perceived wait time.

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

### Content-heavy sites

For blogs and news sites with long articles, a progress bar shows visitors how far the page has loaded. This reduces the 'is it loading?' anxiety on slow connections.

### E-commerce sites

A laser-style loader on product pages shows the page loading progress. Visitors are more patient when they can see progress.

### Client demonstrations

When showing a site to clients, a laser loader creates a professional, modern impression.

---



### Custom loading experience

The laser loader can be customized to match your brand colors and style. The default is a thin bar at the top of the page, but it can be configured to appear in different positions (top, bottom, left side) with different colors and speeds. This customization creates a loading experience that's unique to your site.

### Performance indicator

For sites with slow hosting or heavy content, the laser loader serves as a performance indicator. Visitors can see how far the page has loaded, which reduces the perception of slowness. This is particularly effective for sites with many images or complex layouts that take a few seconds to fully render.

### Marketing and demos

When demonstrating a site to clients or during marketing presentations, the laser loader creates a polished, professional impression. It signals that the site is modern and well-built, which builds confidence in the design and development work.
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


### Brand customization

The laser loader can be customized to match your brand colors and visual identity. The default green can be replaced with any hex color, and the bar can be positioned at the top, bottom, or side of the page. This customization ensures the loading experience aligns with your brand.
### Developer integration

This feature registers 3 WordPress hooks in `laser-loader.php`:

**Actions:**

- `wp_enqueue_scripts` calls `CM_Laser_Loader::enqueue_assets()` (Enqueues laser loader CSS and JS)
- `wp_footer` calls `CM_Laser_Loader::render_loader()` (Renders the laser loader HTML (priority 999))

**Filters:**

- `cm_laser_loader_config` calls `apply_filters()` (Customizable filter)

```php
// Hooked in laser-loader.php
add_action( 'wp_enqueue_scripts', 'CM_Laser_Loader::enqueue_assets' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes.
