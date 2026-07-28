---
title: "How to Enable Lazy Rendering in WordPress | CM"
slug: perf-lazy-rendering
description: "Enable lazy rendering for off-screen content in Classic Monks. Defers rendering of backgrounds, iFrames, and videos that are not visible in the viewport."
last_updated: 2026-07-28
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/perf-lazy-rendering/
merged_docs: "How to Lazy Render Background Images in WordPress, How to Lazy Render iFrames in WordPress, How to Lazy Render Videos in WordPress"
---

# How to Enable Lazy Rendering in WordPress

> Lazy Rendering in Classic Monks defers the rendering of off-screen content. The DOM is not processed until the content enters the viewport, reducing initial rendering time.

## Key Takeaways

- Defers rendering for backgrounds, iFrames, and videos
- Reduces initial page render time
- Does not affect core WordPress functionality
- Reversible (disable to restore default behavior)

## Why You Need It

Lazy rendering goes beyond lazy loading images. It defers the entire rendering process for off-screen elements, reducing the work the browser does on initial load.

---

## How to Enable this Feature

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings, then the **Performance** tab, **Lazy Loading** subtab.

### Step 2: Enable Lazy Rendering

Toggle on **Enable Lazy Rendering**.

### Step 3: Configure Content Types

Toggle on the specific content types you want to lazy render:

- **Lazy Render Background Images**: Defers CSS background image rendering until the element enters the viewport
- **Lazy Render iFrames**: Defers iFrame rendering (YouTube embeds, maps, etc.) until the iFrame is visible
- **Lazy Render Videos**: Defers video element rendering until the video enters the viewport

### Step 4: Save and Test

Click **Save Changes**. Test on the frontend.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Lazy Rendering** | Master toggle. | Off |
| **Lazy Render Background Images** | Defers CSS background image rendering. | Off |
| **Lazy Render iFrames** | Defers iFrame rendering. | Off |
| **Lazy Render Videos** | Defers video element rendering. | Off |

---

## What Gets Affected

- Background images: rendered lazily instead of on initial load
- iFrames (YouTube, maps, etc.): rendered lazily instead of on initial load
- Video elements: rendered lazily instead of on initial load
- Initial page render time: reduced by deferring off-screen content

## What Does NOT Get Affected

- Above-the-fold content: rendered normally
- The actual content: unchanged
- Search engine indexing: unchanged

---

## Common Use Cases

### Complex layouts

Pages with many DOM elements benefit from lazy rendering. The browser renders fewer elements initially.

### Mobile performance

On mobile devices, lazy rendering significantly improves initial load time by reducing the rendering workload.

### Hero sections

Hero sections with background images are rendered lazily, improving initial load.

### YouTube embeds

Lazy rendering YouTube embeds reduces the initial rendering work on pages with many videos.

### Map embeds

Map embeds (Google Maps, OpenStreetMap) are expensive to render. Lazy rendering defers this work until the map is visible.

### Video galleries

Pages with many video elements benefit from lazy rendering. Only the visible videos render initially.

### Background videos

Background videos that are off-screen are not rendered until the user scrolls to them.

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

- [How to Enable Lazy Loading in WordPress](performance-perf-lazy-loading.md)
- [How to Enable the Assets Manager in WordPress](performance-perf-assets-manager.md)

---

## Developer Notes

This feature runs during the WordPress initialization phase. When enabled, its PHP code registers hooks that modify specific WordPress behaviors. The changes are non-destructive and reversible.

No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.

### Before you enable this feature

1. **Test on staging first** to verify no conflicts with your theme or other plugins
2. **Check dependent plugins** that may rely on the functionality being modified
3. **Monitor after enabling** for any unexpected behavior on the frontend
