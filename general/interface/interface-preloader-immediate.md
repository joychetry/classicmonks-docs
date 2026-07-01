---
title: "How to Enable Immediate Preloader in WordPress | CM"
slug: interface/preloader-immediate
description: "Show the preloader immediately when a link is clicked in Classic Monks. The preloader appears on click, not after the page starts loading, for a faster perceived response."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/interface/preloader-immediate/
---

# How to Enable Immediate Preloader in WordPress

> Immediate Preloader in Classic Monks shows the preloader immediately when a visitor clicks a link. The preloader appears on click, not after the page starts loading, for a faster perceived response.

## Key Takeaways

- Single toggle, no nested options
- Requires [Preloader](interface-preloader.md) to be enabled first
- Shows preloader on link click (before page load starts)
- Creates the perception of instant page transitions
- Particularly effective for fast-loading sites

## What Is the Immediate Preloader feature?

By default, the preloader shows when the browser starts loading a new page (after the HTTP request). The Immediate Preloader feature shows the preloader as soon as the visitor clicks a link, before the browser starts loading. This creates the perception of an instant page transition.

The difference is timing:

- **Default**: Click → wait for browser → preloader shows → page loads
- **Immediate**: Click → preloader shows → page loads

The second approach feels faster because the visitor sees immediate feedback after clicking.

## Why You Need It

Immediate feedback after a click is a key UX principle:

- **Perceived speed**: The preloader shows instantly, making the site feel faster
- **User confidence**: Visitors know their click was registered
- **Reduced anxiety**: No "did the click work?" uncertainty
- **Professional feel**: Instant feedback creates a premium, app-like experience

For most sites, immediate feedback is better than delayed feedback.

---

## How to Enable Immediate Preloader in WordPress

### Step 1: Enable Preloader

First, enable the Preloader master toggle in the Preloader subtab.

### Step 2: Navigate to Settings

Click into the **Classic Monks** plugin settings, then the **Interface** tab, **Preloader** subtab.

### Step 3: Enable Immediate Preloader

Scroll to **Show preloader immediately when a link is clicked** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Click any internal link on your site. The preloader should appear immediately on click, before the new page starts loading.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Show preloader immediately when a link is clicked** | Master toggle. | Off |

---

## What Gets Affected

- The preloader timing: shows on click instead of on page load
- The perceived speed: the site feels faster
- The user experience: immediate feedback after clicking

## What Does NOT Get Affected

- The actual page load time: unchanged
- The preloader animation: unchanged
- The preloader duration: unchanged

---

### Developer integration

This feature registers 3 WordPress hooks in `preloader.php`:

**Actions:**

- `wp_body_open` calls `cm_output_preloader_html()` (Outputs preloader HTML at body open (priority 1))
- `wp_head` calls `cm_output_preloader_css()` (Injects preloader CSS (priority 1))
- `wp_head` calls `cm_output_preloader_js()` (Injects preloader JavaScript (priority 999))

```php
// Hooked in preloader.php
add_action( 'wp_body_open', 'cm_output_preloader_html' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes.

## Common Use Cases

### High-traffic sites

For sites with millions of visitors per month, the immediate preloader reduces the 'did the click work?' uncertainty, improving engagement.

### Conversion-optimized sites

On landing pages where every click matters, the immediate preloader provides instant feedback, reducing the risk of users clicking away.

### App-like experiences

For WordPress sites that want to feel like native apps, the immediate preloader creates the instant response that users expect from apps.



### Conversion-optimized landing pages

On landing pages where every click matters, the immediate preloader provides instant feedback, reducing the risk of users clicking away before the page loads. This is especially important for paid traffic where the cost per click is high.

### High-traffic news sites

For news sites with millions of visitors, the immediate preloader reduces bounce rates. Visitors see immediate feedback on article clicks, which keeps them engaged through the load time.
## Troubleshooting

### The preloader is not showing immediately

**Cause:** The toggle is off, or the preloader JavaScript is not loading.
**Fix:** Verify both the Preloader master toggle and the Immediate toggle are on. Check the browser console for errors.

### The preloader shows on external links

**Cause:** The feature is triggered on all link clicks, including external links.
**Fix:** Add a CSS class to external links and exclude it via the preloader settings in the plugin dashboard.

### The preloader conflicts with page transitions

**Cause:** Both the preloader and page transitions are active.
**Fix:** Choose one or the other. The preloader is a loading indicator; page transitions are an animation. Using both creates a confusing experience.

---

## Related Articles

- [How to Use Preloader in WordPress](interface-preloader.md)
- [How to Use Laser Loader in WordPress](interface-laser-loader.md)
- [How to Use Page Transitions in WordPress](interface-page-transitions.md)
- [How to Use Shared Element Transitions in WordPress](interface-shared-element-transitions.md)
