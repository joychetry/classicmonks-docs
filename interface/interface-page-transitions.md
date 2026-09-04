---
title: "How to Use Page Transitions in WordPress"
slug: interface-page-transitions
description: "Add smooth page transitions to your WordPress site in Classic Monks. Pages transition with a smooth animation instead of a hard reload."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/interface-page-transitions/
---

# How to Use Page Transitions in WordPress

> Page Transitions in Classic Monks adds smooth, animated transitions between pages. Instead of a hard reload, pages fade, slide, or crossfade during navigation.

## Key Takeaways

- Single toggle, no nested options
- Configurable per page or per context
- Does not affect page load time (visual only)
- Works with most WordPress themes

## What Is this feature?

This feature is part of the Experience system in Classic Monks. It modifies how your WordPress site behaves or appears to visitors. Each feature is independently configurable.

## Why You Need It

Customizing the site experience allows you to:

- Match the behavior to your site's design and purpose
- Improve user experience for specific contexts (mobile, admin, accessibility)
- Create a more professional or modern impression

---

## How to Configure this Feature

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings, then the **Interface** tab, **Experience** subtab.

### Step 2: Enable the Feature

Toggle on this feature.

### Step 3: Save Changes

Click **Save Changes**.

### Step 4: Test

Visit the frontend (or admin, depending on the feature) and verify the behavior matches your configuration.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| This feature | Master toggle. | Off |

---

## What Gets Affected

- The site behavior: modified per this feature
- The user experience: enhanced or modified for the configured context
- The admin experience: (if admin-related feature) modified for the admin

## What Does NOT Get Affected

- The actual page load time: unchanged
- The page content: unchanged
- The search engine indexing: unchanged

---

## Common Use Cases

### Portfolio and agency sites

Page transitions create a premium, modern feel that matches the visual quality of portfolio and agency websites.

### Single-page-like experiences

For WordPress sites that want to feel like single-page applications, page transitions provide the smoothness without the complexity.

### Client demonstrations

When showing a site to clients, page transitions create a 'wow factor' that differentiates the design.

---



### Brand storytelling sites

For sites where the brand story is told across multiple pages, page transitions create a sense of continuity. The visitor feels like they're moving through a cohesive narrative rather than jumping between disconnected pages.

### Education platforms

For online courses and learning platforms, page transitions between lessons create a smooth learning experience. The student feels like they're progressing through the material, not loading separate pages.

### Restaurant and hospitality sites

For restaurants, hotels, and hospitality sites, page transitions create a premium experience that matches the service quality. The smooth transitions make the site feel as polished as the establishment.
## Troubleshooting

### The feature is not taking effect

**Cause:** The toggle is off, or a theme/plugin conflict is preventing the feature from loading.
**Fix:** Verify the toggle is on. Disable other page transition plugins to find conflicts.

### The feature is showing on pages where it shouldn't

**Cause:** The feature is global (applies to all pages).
**Fix:** Use the filter for this feature to exclude specific pages. See Advanced Options.

### The feature conflicts with another plugin

**Cause:** Another plugin is also modifying the same behavior.
**Fix:** Disable the other plugin's equivalent feature. Classic Monks features are designed to be standalone; using two competing features (e.g., two page transition plugins) will cause conflicts.

---

## Related Articles

- [How to Use Page Transitions in WordPress](interface-page-transitions.md)
- [How to Use Shared Element Transitions in WordPress](interface-shared-element-transitions.md)
- [How to Respect Reduced Motion Preference in WordPress](interface-reduced-motion.md)
- [How to Use Laser Loader in WordPress](interface-laser-loader.md)


### Portfolio showcases

For creative agencies and freelancers, page transitions between portfolio items create a gallery-like experience. Each transition feels intentional and designed, which reinforces the quality of the work being showcased.
### Developer integration

This feature registers 2 WordPress hooks in `page-transitions.php`:

**Actions:**

- `wp_enqueue_scripts` calls `cm_add_page_transitions()` (Enqueues page transitions JS/CSS on frontend)
- `admin_enqueue_scripts` calls `cm_add_admin_page_transitions()` (Enqueues page transitions in admin area)

```php
// Hooked in page-transitions.php
add_action( 'wp_enqueue_scripts', 'cm_add_page_transitions' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes.

### SEO and crawlability impact

Page transitions do not affect SEO or crawlability. Search engine crawlers do not execute JavaScript (in most cases) and do not interact with page transitions. The content is still present in the HTML and is accessible to crawlers.

For accessibility, page transitions respect the prefers-reduced-motion media query. Users who have enabled reduced motion in their OS settings will not see the transitions. This ensures the site is accessible to users with vestibular disorders or motion sensitivity.
