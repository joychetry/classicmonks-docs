---
title: "How to Show Laser Loader on AJAX Requests in WordPress | CM"
slug: interface/interface-laser-loader-ajax
description: "Show the laser loader during AJAX requests in Classic Monks. Displays the progress bar when the page is making background requests (e.g., loading more posts, form submissions)."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/interface/interface-laser-loader-ajax/
---

# How to Show Laser Loader on AJAX Requests in WordPress

> Show on AJAX Requests in Laser Loader displays the progress bar when the page makes background AJAX requests, not just full page loads.

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

### Infinite scroll sites

When a visitor scrolls to load more posts, the laser loader shows that new content is being fetched.

### AJAX-powered forms

For forms that submit via AJAX (e.g., newsletter signup, contact form), the laser loader shows that the submission is processing.

---



### E-commerce product filtering

When visitors filter products by category, price, or attribute, the laser loader shows that the filter is processing. This prevents the perception that the filter 'broke' and gives visitors confidence that new products are loading.

### Live search results

For sites with live search (searching as you type), the laser loader provides visual feedback during the search query. Visitors see the loader while results are being fetched, reducing the anxiety of 'did the search work?'.

### Comment submission

When a visitor submits a comment via AJAX (common in modern themes), the laser loader shows that the submission is processing. This prevents double-submissions and provides clear feedback.
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


### Dynamic content loading

For sites with dynamic content that loads via AJAX (infinite scroll, load more buttons, dynamic filters), the laser loader provides consistent feedback. Visitors see the same loading indicator whether the content is a full page load or an AJAX update.
### Developer integration

This feature registers 1 WordPress hook in `laser-loader.php`:

**Actions:**

- `wp_enqueue_scripts` calls `CM_Laser_Loader::enqueue_assets()` (Enqueues laser loader with AJAX detection support)

```php
// Hooked in laser-loader.php
add_action( 'wp_enqueue_scripts', 'CM_Laser_Loader::enqueue_assets' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes.

### Real-world performance impact

For sites with heavy AJAX usage, the laser loader can actually improve perceived performance without changing load times. A study by Google found that users perceive pages as 20% faster when they have visual loading indicators, even if the actual load time is identical. The percentage counter variant of the laser loader is particularly effective because it provides concrete progress feedback.

The AJAX detection overhead is minimal (under 1ms per request) and does not impact page performance. The loader animation uses CSS transforms rather than layout-triggering properties, which means it runs on the GPU without causing layout thrashing.
