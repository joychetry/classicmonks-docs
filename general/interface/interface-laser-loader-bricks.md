---
title: "How to Disable Laser Loader Inside Bricks Builder in WordPress | CM"
slug: interface/interface-laser-loader-bricks
description: "Disable the laser loader when editing in Bricks Builder in Classic Monks. Prevents the progress bar from appearing during the visual editor."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/interface/interface-laser-loader-bricks/
---

# How to Disable Laser Loader Inside Bricks Builder in WordPress

> Disable Laser Loader in Bricks Builder prevents the laser-style progress bar from appearing when editing in the Bricks Builder editor.

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

### Bricks Builder users

The laser loader should not appear when designing pages in the Bricks Builder editor, as it interferes with the design workflow.

### Visual editor workflows

Designers need to see the page without loading animations. Disabling the laser loader in the editor provides a clean design environment.

---



### Design workflow

When designing pages in Bricks Builder, the designer needs to see the page as it will appear to visitors. The laser loader would interfere with this by showing during every page change in the editor. Disabling it in the editor provides a clean, unobstructed design environment.

### Testing the loader behavior

To test the laser loader behavior, designers need to see the page both with and without the loader. Disabling it in the editor allows for easy comparison: design without the loader, then view the frontend with the loader active.
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


### Elementor and other page builders

While this specific feature targets Bricks Builder, the concept applies to any visual page builder. If you use Elementor, Divi, or another builder, the same principle applies: disable the laser loader in the editor to avoid visual interference.

### Live preview workflow

When designing in Bricks Builder, the designer toggles between the editor and the live preview. Disabling the laser loader in the editor ensures the editor view is clean, while the live preview shows the loader as visitors would see it.
### Developer integration

This feature registers 1 WordPress hook in `laser-loader.php`:

**Actions:**

- `init` calls `cm_init_laser_loader()` (Initializes laser loader with Bricks Builder detection)

```php
// Hooked in laser-loader.php
add_action( 'init', 'cm_init_laser_loader' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes.

### Testing and development workflow

When developing with Bricks Builder, you can test the laser loader by viewing the page in a separate browser tab (not the Bricks preview). The Bricks preview disables the loader, but the live frontend shows it. This dual-view approach lets you design without the loader interfering, then check the final result.

The Bricks detection is based on the page URL, not the browser state. If you open the same page in a new tab (not the Bricks editor), the laser loader will appear normally. This ensures the loader is only disabled in the actual Bricks editor context.
