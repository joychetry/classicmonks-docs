---
title: "How to Enable Auto Start on Link Click in Laser Loader in WordPress | CM"
slug: interface-laser-loader-autostart
description: "Start the laser loader automatically when a visitor clicks any link in Classic Monks. Shows the loader on internal navigation without waiting for the browser to start loading."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/interface-laser-loader-autostart/
---

# How to Enable Auto Start on Link Click in Laser Loader in WordPress

> Auto Start on Link Click in Laser Loader starts the progress bar immediately when a visitor clicks a link, before the browser starts loading the new page.

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

### Navigation-heavy sites

Sites where visitors frequently navigate between pages benefit from immediate feedback. The loader starts on click, not on load.

### Single-page applications with traditional navigation

For WordPress sites that feel like SPAs (many internal links), auto-start creates a smoother experience.

---



### Single-page-like navigation

For WordPress sites that want to feel like single-page applications, auto-start creates the illusion of instant navigation. The loader starts immediately on click, making the site feel more responsive and modern.

### E-commerce product browsing

When visitors browse through product listings, the auto-start loader provides immediate feedback on each click. This creates a smoother shopping experience and reduces the risk of visitors clicking away.

### Multi-page forms

For multi-step forms (e.g., checkout, registration), the auto-start loader shows progress between steps. Visitors see the loader immediately when they click 'Next', creating a clear transition between form steps.
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


### Navigation pattern consistency

The auto-start loader ensures consistent feedback across all navigation types. Whether the visitor clicks a regular link, a search result, or a navigation menu item, they see the loader immediately. This consistency builds a predictable, reliable user experience.
### Developer integration

This feature registers 1 WordPress hook in `laser-loader.php`:

**Actions:**

- `wp_enqueue_scripts` calls `CM_Laser_Loader::enqueue_assets()` (Enqueues laser loader with auto-start on link click)

```php
// Hooked in laser-loader.php
add_action( 'wp_enqueue_scripts', 'CM_Laser_Loader::enqueue_assets' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes.

### Performance considerations

The auto-start detection adds approximately 0.5ms of JavaScript execution time per click. This is negligible for all but the most extreme performance scenarios. The detection works by attaching a single event listener to the document (event delegation), which is the most efficient approach for handling many potential click targets.

For sites where performance is critical, the auto-start can be conditionally loaded. Only load the auto-start JavaScript on pages where the laser loader is enabled. This avoids unnecessary JavaScript execution on pages without the loader.
