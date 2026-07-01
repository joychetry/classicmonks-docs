---
title: "How to Use Mobile-Specific Preloader Customization in WordPress | CM"
slug: interface/interface-preloader-mobile
description: "Customize the preloader behavior specifically for mobile devices in Classic Monks. Different preloader settings for mobile vs desktop to optimize for mobile load times."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/interface/interface-preloader-mobile/
---

# How to Use Mobile-Specific Preloader Customization in WordPress

> Mobile-Specific Preloader Customization in Classic Monks lets you configure a different preloader behavior for mobile devices. Optimize the preloader for mobile load times and user experience.

## Key Takeaways

- Single toggle, no nested options
- Enable Mobile-Specific Customization is the master switch
- Works with most WordPress themes
- Configurable loading animation
- Does not affect page load time (visual only)

## What Is the Enable Mobile-Specific Customization feature?

The Enable Mobile-Specific Customization feature in Classic Monks adds a loading animation to your WordPress site. When a visitor navigates to a new page, the preloader shows while the page loads, then fades out when the page is ready.

This is a visual enhancement only. It does not affect the actual load time; it only changes how the load time is perceived.

## Why You Need It

For sites where visual impression matters:

- **Perceived performance**: A preloader makes the site feel faster
- **Brand consistency**: The preloader can match your brand colors and style
- **User engagement**: Visitors are more patient when they see a loading animation
- **Content protection**: Prevents users from seeing partially loaded content

For most content-heavy sites, a preloader improves the user experience.

---

## How to Use Enable Mobile-Specific Customization in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Interface Tab

Click on the **Interface** menu, then click the **Preloader** subtab.

### Step 3: Enable Enable Mobile-Specific Customization

Scroll to **Enable Mobile-Specific Customization** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit your site on the frontend. The preloader should appear on page navigation.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Mobile-Specific Customization** | Master toggle. | Off |

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

This feature registers 1 WordPress hook in `preloader.php`:

**Actions:**

- `wp` calls `cm_init_preloader()` (Initializes preloader with mobile device detection)

```php
// Hooked in preloader.php
add_action( 'wp', 'cm_init_preloader' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes.

## Common Use Cases

### Mobile-first sites

If your traffic is primarily mobile (60%+), mobile-specific preloader settings ensure the best experience for your most common visitors.

### Slow mobile connections

Mobile connections are often slower. A lighter preloader (or no preloader) on mobile reduces perceived load time compared to a complex animation.

### Responsive design testing

When testing your responsive design, mobile-specific preloader settings let you verify the mobile experience independently.

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
