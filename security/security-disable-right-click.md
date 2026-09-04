---
title: "How to Disable Right Click in WordPress"
slug: disable-right-click
description: "Disable the right-click context menu on the WordPress frontend in Classic Monks. Prevents casual right-click access to view source, copy, and save actions."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-right-click/
---

# How to Disable Right Click in WordPress

> Disable Right Click in Classic Monks prevents the browser's right-click context menu on your WordPress frontend. Prevents casual access to view source, copy, and save image actions.

## Key Takeaways

- Single toggle, no nested options
- Disables the right-click context menu via JavaScript
- Use the "Apply to Administrators" sub-option to allow admins to still the right-click context menu
- Soft deterrent only, not a security feature
- Easily bypassed by browser dev tools

## What Is the Disable Right Click feature?

The the right-click context menu behavior is a common browser feature. The Disable Right Click feature disables it on your WordPress site, preventing users from right-clicking on the page.

This is a soft deterrent, not a security feature. Determined users can still right-click via the browser's developer tools or by disabling JavaScript.

## Why You Need It

For some types of sites, preventing casual right-clicking is useful:

- **Premium content sites**: Where the content itself is the product
- **Image-heavy sites**: Where images are the unique value
- **Course sites**: Where the lessons are paid
- **Recipe sites**: Where recipes are the unique value

For most sites, this is unnecessary. The content is already protected by copyright.

## Trade-offs vs allowing right-clicking

Disabling right-clicking has trade-offs:

- **Accessibility**: Users with disabilities who rely on right-clicking are affected
- **User experience**: Sharing and quoting become harder
- **Real protection**: Doesn't actually protect the content (anyone with dev tools can right-click)

For most sites, the trade-offs are not worth it.

---

## How to Disable Right Click in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Content Protection** subtab.

### Step 3: Enable the Feature

Scroll to **Disable Right Click** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit the frontend. Try to right-click. The context menu should not the right-click context menu.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable Right Click** | Master toggle. | Off |
| **Apply to Administrators** | Admins can still right-click. | On |

---

## What Gets Affected

- The frontend: the right-click context menu via JavaScript is disabled
- The admins: can still right-click (if "Apply to Administrators" is on)
- The accessibility: may affect users who rely on right-clicking

## What Does NOT Get Affected

- The admin: admins can still right-click
- The browser's developer tools: still allow bypassing
- The keyboard shortcuts (other than the disabled one): still work
- The screen readers: usually not affected

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `disable-right-click.php`:

**Actions:**

- `wp_head` calls `cm_disable_right_click_script()` (Injects right-click disable script (priority 1))

```php
// Hooked in disable-right-click.php
add_action( 'wp_head', 'cm_disable_right_click_script' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The context menu still appears

**Cause:** The toggle is off, or the JavaScript is not running.
**Fix:** Verify the toggle is on. Check the browser console for errors.

### The admins can't right-click

**Cause:** The "Apply to Administrators" option is off.
**Fix:** Enable the "Apply to Administrators" sub-option.

### The context menu works in some browsers

**Cause:** Different browsers may handle the event differently.
**Fix:** Test in multiple browsers. The feature uses standard browser events, so it should work consistently, but some browsers may have edge cases.

### Users are still right-clicking on the page via dev tools

**Cause:** This is a soft deterrent only.
**Fix:** The Disable Right Click feature only prevents casual right-clicking. For real content protection, use copyright, watermarks (for images), or licensing terms.

---

## Related Articles

- [How to Disable Right Click in WordPress](security-disable-right-click.md)
- [How to Disable Text Selection in WordPress](security-disable-text-selection.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
