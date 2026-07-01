---
title: "How to Enable Shadow Effect in Laser Loader in WordPress | CM"
slug: interface/interface-laser-loader-shadow
description: "Add a shadow effect to the laser loader in Classic Monks. Creates a glowing, neon-like effect that makes the loader more visually striking."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/interface/interface-laser-loader-shadow/
---

# How to Enable Shadow Effect in Laser Loader in WordPress

> Shadow Effect in Laser Loader adds a glowing, neon-like shadow to the progress bar. Creates a more visually striking loading experience.

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

### Dark-themed sites

On dark backgrounds, a shadow/glow effect makes the laser loader more visible and visually striking.

### Modern design sites

The shadow effect adds a premium, modern feel to the loading experience.

---



### Dark mode sites

Sites with dark mode themes benefit from the shadow effect. The glow makes the laser loader visible on dark backgrounds, where a plain bar might be hard to see.

### Gaming and entertainment sites

For gaming, entertainment, or tech sites, the shadow/glow effect creates a premium, modern feel. It aligns with the visual language of these industries.

### Night mode accessibility

For users who browse at night or in low-light environments, the shadow effect provides better visibility of the loader, ensuring they can see the progress indicator.
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


### Visual hierarchy

The shadow effect creates a visual hierarchy that draws the eye to the loader. This is useful on pages where the loading experience is a key part of the user journey (e.g., product pages, landing pages).
### Developer integration

This feature registers 1 WordPress hook in `laser-loader.php`:

**Actions:**

- `wp_enqueue_scripts` calls `CM_Laser_Loader::enqueue_assets()` (Enqueues laser loader with shadow effect CSS)

```php
// Hooked in laser-loader.php
add_action( 'wp_enqueue_scripts', 'CM_Laser_Loader::enqueue_assets' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes.

### Visual impact on brand perception

The shadow effect creates a premium, modern feel that can positively impact brand perception. Users associate glowing, neon-like effects with cutting-edge technology and modern design. For tech companies, startups, and creative agencies, the shadow effect reinforces the brand's innovation and technical sophistication.

The shadow effect is subtle enough to not be distracting but noticeable enough to create a distinct visual identity. This balance between subtlety and visibility is important for maintaining a professional appearance while still creating a memorable loading experience.

### Shadow configuration

The shadow effect intensity and color can be customized via CSS. The default shadow is a subtle glow that enhances the bar without overwhelming the page. For sites with dark themes, the shadow intensity can be increased for better visibility. For light themes, the shadow can be reduced to a subtle outline effect.
