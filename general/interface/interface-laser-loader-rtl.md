---
title: "How to Enable RTL Support in Laser Loader in WordPress | CM"
slug: interface-laser-loader-rtl
description: "Enable right-to-left (RTL) support for the laser loader in Classic Monks. The progress bar moves from right to left for Arabic, Hebrew, and other RTL languages."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/interface-laser-loader-rtl/
---

# How to Enable RTL Support in Laser Loader in WordPress

> RTL Support in Laser Loader makes the progress bar move from right to left for Arabic, Hebrew, Persian, and other right-to-left languages.

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

### Multilingual sites

For sites that serve RTL languages, the laser loader should match the reading direction. RTL support ensures the progress bar moves correctly.

### Middle Eastern markets

Sites targeting Middle Eastern markets need RTL support for the loading experience to feel natural.

---



### Multilingual WordPress sites

WordPress sites that serve multiple languages (via WPML, Polylang, etc.) need RTL support for Arabic, Hebrew, and Persian visitors. The laser loader direction should match the reading direction for a natural experience.

### Middle Eastern e-commerce

E-commerce sites targeting Middle Eastern markets need RTL support throughout, including the loading experience. An RTL laser loader ensures the progress bar moves in the direction that RTL readers expect.

### International organizations

Organizations with global audiences need RTL support to serve all users equally. The laser loader RTL option ensures the loading experience is consistent across all language versions of the site.
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


### Accessibility for RTL users

RTL readers expect all page elements to flow from right to left. The laser loader is no exception. RTL support ensures the progress bar moves in the direction that RTL readers expect, creating a more accessible and natural experience.
### Developer integration

This feature registers 1 WordPress hook in `laser-loader.php`:

**Actions:**

- `wp_enqueue_scripts` calls `CM_Laser_Loader::enqueue_assets()` (Enqueues laser loader with RTL support)

```php
// Hooked in laser-loader.php
add_action( 'wp_enqueue_scripts', 'CM_Laser_Loader::enqueue_assets' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes.

### Language-specific considerations

Arabic and Hebrew readers expect all page elements to flow from right to left. The laser loader is no exception. When the loader bar moves from left to right for RTL users, it creates a disorienting experience that breaks the natural reading flow. RTL support ensures the loader bar moves from right to left, matching the reading direction.

For multilingual sites using WPML or Polylang, the RTL detection is automatic based on the current language. The loader will switch direction when the language changes, providing a seamless experience for multilingual visitors.
