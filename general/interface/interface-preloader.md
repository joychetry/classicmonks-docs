---
title: "How to Use Preloader in WordPress | CM"
slug: interface/interface-preloader
description: "Add a loading animation to your WordPress site in Classic Monks. Shows a preloader while pages load, creating a smoother perceived performance experience."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/interface/interface-preloader/
---

# How to Use Preloader in WordPress

> Preloader in Classic Monks adds a loading animation to your WordPress site. Shows a preloader while pages load, creating a smoother perceived performance experience.

## Key Takeaways

- Single toggle, no nested options
- Enable Preloader is the master switch
- Works with most WordPress themes
- Configurable loading animation
- Does not affect page load time (visual only)

## What Is the Enable Preloader feature?

The Enable Preloader feature in Classic Monks adds a loading animation to your WordPress site. When a visitor navigates to a new page, the preloader shows while the page loads, then fades out when the page is ready.

This is a visual enhancement only. It does not affect the actual load time; it only changes how the load time is perceived.

## Why You Need It

For sites where visual impression matters:

- **Perceived performance**: A preloader makes the site feel faster
- **Brand consistency**: The preloader can match your brand colors and style
- **User engagement**: Visitors are more patient when they see a loading animation
- **Content protection**: Prevents users from seeing partially loaded content

For most content-heavy sites, a preloader improves the user experience.

---

## How to Use Enable Preloader in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Interface Tab

Click on the **Interface** menu, then click the **Preloader** subtab.

### Step 3: Enable Enable Preloader

Scroll to **Enable Preloader** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit your site on the frontend. The preloader should appear on page navigation.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Preloader** | Master toggle. | Off |

The preloader animation style, color, and speed are configured via CSS and filters (see Advanced Options).

---

## What Gets Affected

- The frontend: preloader appears during page navigation
- The page load: the preloader shows while the page loads
- The user experience: smoother perceived performance

## What Does NOT Get Affected

- The actual load time: unchanged (visual only)
- The page content: unchanged
- The search engine indexing: unchanged
- The accessibility: unchanged (screen readers ignore the preloader)

---

### Developer integration

This feature registers 4 WordPress hooks in `preloader.php`:

**Actions:**

- `wp` calls `cm_init_preloader()` (Initializes preloader settings)
- `wp_head` calls `cm_output_preloader_css()` (Injects preloader CSS (priority 1))
- `wp_head` calls `cm_output_preloader_js()` (Injects preloader JavaScript (priority 999))
- `wp_body_open` calls `cm_output_preloader_html()` (Outputs preloader HTML (priority 1))

```php
// Hooked in preloader.php
add_action( 'wp', 'cm_init_preloader' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes.

## Common Use Cases

### Portfolio and agency sites

A preloader gives the impression that the site is loading content, even if the actual load time is fast. For portfolio and agency sites where visual impact matters, a preloader sets the tone.

### E-commerce sites

A preloader on the shop page creates anticipation and masks slow-loading product images. It can reduce bounce rates by giving visitors something to look at while the page loads.

### Sites with heavy media

If your pages have many high-resolution images, a preloader masks the load time. Visitors are more patient when they see a loading animation than when they see a blank or partially loaded page.

---

## Troubleshooting

### The preloader is not showing

**Cause:** The toggle is off, or the JavaScript is not loading.
**Fix:** Verify the toggle is on. Check the browser console for errors. The preloader requires JavaScript to function.

### The preloader never disappears

**Cause:** The page load is very slow, or the preloader timeout is not set.
**Fix:** The preloader should auto-hide after the page loads. If it doesn't, check the browser console for JavaScript errors. The preloader auto-hides after the page loads. If it doesn't, check the browser console for JavaScript errors.

### The preloader is showing on every page load (including back/forward)

**Cause:** The preloader is configured to show on all navigations.
**Fix:** This is the default behavior. Configure excluded pages in the plugin settings under Interface > Preloader.

### The preloader conflicts with Bricks Builder

**Cause:** The preloader is showing in the Bricks Builder editor.
**Fix:** Disable the preloader inside Bricks Builder using the subtab option.

---

## Related Articles

- [How to Use Laser Loader in WordPress](interface-laser-loader.md)
- [How to Use Page Transitions in WordPress](interface-page-transitions.md)
- [How to Use the Admin Notices Manager in WordPress](interface-admin-notices-manager.md)
- [How to Use Form Desk in WordPress](interface-form-desk.md)
