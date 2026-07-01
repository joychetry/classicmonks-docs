---
title: "How to Disable Image Drag in WordPress | CM"
slug: security/disable-image-drag
description: "Disable the mouse drag action on images in Classic Monks. Prevents users from easily dragging images to their desktop or another tab."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/security/disable-image-drag/
---

# How to Disable Image Drag in WordPress

> Disable Image Drag in Classic Monks prevents the mouse drag action on images. Prevents casual dragging of images to the desktop or another tab.

## Key Takeaways

- Single toggle, no nested options
- Disables dragging images with the mouse via JavaScript
- Use the "Apply to Administrators" sub-option to allow admins to still dragging images with the mouse
- Soft deterrent only, not a security feature
- Easily bypassed by browser dev tools

## What Is the Disable Image Drag feature?

The dragging images with the mouse behavior is a common browser feature. The Disable Image Drag feature disables it on your WordPress site, preventing users from dragging images with the mouse.

This is a soft deterrent, not a security feature. Determined users can still drag images via the browser's developer tools or by disabling JavaScript.

## Why You Need It

For some types of sites, preventing casual dragging images is useful:

- **Premium content sites**: Where the content itself is the product
- **Image-heavy sites**: Where images are the unique value
- **Course sites**: Where the lessons are paid
- **Recipe sites**: Where recipes are the unique value

For most sites, this is unnecessary. The content is already protected by copyright.

## Trade-offs vs allowing dragging images

Disabling dragging images has trade-offs:

- **Accessibility**: Users with disabilities who rely on dragging images are affected
- **User experience**: Sharing and quoting become harder
- **Real protection**: Doesn't actually protect the content (anyone with dev tools can drag images)

For most sites, the trade-offs are not worth it.

---

## How to Disable Image Drag in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Content Protection** subtab.

### Step 3: Enable the Feature

Scroll to **Disable Image Drag** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit the frontend. Try to drag images. The image drag should not dragging images with the mouse.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable Image Drag** | Master toggle. | Off |
| **Apply to Administrators** | Admins can still drag images. | On |

---

## What Gets Affected

- The frontend: dragging images with the mouse via JavaScript is disabled
- The admins: can still drag images (if "Apply to Administrators" is on)
- The accessibility: may affect users who rely on dragging images

## What Does NOT Get Affected

- The admin: admins can still drag images
- The browser's developer tools: still allow bypassing
- The keyboard shortcuts (other than the disabled one): still work
- The screen readers: usually not affected

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `disable-image-drag.php`:

**Actions:**

- `wp_head` calls `cm_disable_image_drag_script()` (Injects image drag disable script)

```php
// Hooked in disable-image-drag.php
add_action( 'wp_head', 'cm_disable_image_drag_script' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The image drag still works

**Cause:** The toggle is off, or the JavaScript is not running.
**Fix:** Verify the toggle is on. Check the browser console for errors.

### The admins can't drag images

**Cause:** The "Apply to Administrators" option is off.
**Fix:** Enable the "Apply to Administrators" sub-option.

### The image drag works in some browsers

**Cause:** Different browsers may handle the event differently.
**Fix:** Test in multiple browsers. The feature uses standard browser events, so it should work consistently, but some browsers may have edge cases.

### Users are still dragging images with the mouse via dev tools

**Cause:** This is a soft deterrent only.
**Fix:** The Disable Image Drag feature only prevents casual dragging images. For real content protection, use copyright, watermarks (for images), or licensing terms.

---

## Related Articles

- [How to Disable Right Click in WordPress](security-disable-right-click.md)
- [How to Disable Text Selection in WordPress](security-disable-text-selection.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
