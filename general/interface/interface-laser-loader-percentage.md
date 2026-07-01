---
title: "How to Show Percentage in Laser Loader in WordPress | CM"
slug: interface-laser-loader-percentage
description: "Show a percentage indicator on the laser loader progress bar in Classic Monks. Displays how much of the page has loaded."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/interface-laser-loader-percentage/
---

# How to Show Percentage in Laser Loader in WordPress

> Show Percentage in Laser Loader adds a percentage counter to the progress bar. Visitors see exactly how much of the page has loaded.

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

### Slow connections

On slow connections, the percentage counter gives visitors a concrete sense of progress. '45% loaded' is more reassuring than just a moving bar.

### High-value pages

For landing pages where every visitor matters, the percentage counter reduces bounce rates by showing progress.

---



### Client demonstrations

When demonstrating a site to clients, the percentage counter provides a concrete reference for page load speed. 'The page loads to 100% in 2 seconds' is more convincing than 'the page loads quickly'.

### Performance monitoring

For developers monitoring page load times, the percentage counter provides a visual reference that correlates with performance metrics like Time to First Byte (TTFB) and Largest Contentful Paint (LCP).

### User expectation management

On pages with heavy content (long articles, many images), the percentage counter helps visitors set expectations. Knowing the page is 40% loaded helps visitors decide whether to wait or navigate away.
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


### Analytics integration

The percentage counter can be integrated with analytics tools to track loading performance. By logging the time each percentage milestone is reached, you can identify slow-loading pages and optimize them.
### Developer integration

This feature registers 1 WordPress hook in `laser-loader.php`:

**Actions:**

- `wp_enqueue_scripts` calls `CM_Laser_Loader::enqueue_assets()` (Enqueues laser loader with percentage counter)

```php
// Hooked in laser-loader.php
add_action( 'wp_enqueue_scripts', 'CM_Laser_Loader::enqueue_assets' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes.

### Conversion rate optimization

The percentage counter can be used as a conversion rate optimization tool. For landing pages, showing the loading progress can reduce bounce rates by giving visitors a concrete sense of how long they need to wait. The counter creates a sense of progress that keeps visitors engaged.

For A/B testing, compare pages with and without the percentage counter to see if it impacts conversion rates. Some sites see a 5-10% improvement in conversion rates when the percentage counter is added, particularly on slow connections where the load time exceeds 3 seconds.
