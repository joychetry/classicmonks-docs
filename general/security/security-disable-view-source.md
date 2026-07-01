---
title: "How to Disable View Source in WordPress | CM"
slug: security/disable-view-source
description: "Disable the keyboard shortcut to view page source in Classic Monks. Prevents users from easily viewing the page's HTML source code via CTRL+U or ⌘+U."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/security/disable-view-source/
---

# How to Disable View Source in WordPress

> Disable View Source in Classic Monks prevents the CTRL+U (or ⌘+U) keyboard shortcut that opens the page source. Prevents casual viewing of the page's HTML.

## Key Takeaways

- Single toggle, no nested options
- Disables viewing the page source via the keyboard shortcut via JavaScript
- Use the "Apply to Administrators" sub-option to allow admins to still viewing the page source via the keyboard shortcut
- Soft deterrent only, not a security feature
- Easily bypassed by browser dev tools

## What Is the Disable View Source feature?

The viewing the page source via the keyboard shortcut behavior is a common browser feature. The Disable View Source feature disables it on your WordPress site, preventing users from using the keyboard shortcut to view the page source.

This is a soft deterrent, not a security feature. Determined users can still view the source via the browser's developer tools or by disabling JavaScript.

## Why You Need It

For some types of sites, preventing casual viewing the source is useful:

- **Premium content sites**: Where the content itself is the product
- **Image-heavy sites**: Where images are the unique value
- **Course sites**: Where the lessons are paid
- **Recipe sites**: Where recipes are the unique value

For most sites, this is unnecessary. The content is already protected by copyright.

## Trade-offs vs allowing viewing the source

Disabling viewing the source has trade-offs:

- **Accessibility**: Users with disabilities who rely on viewing the source are affected
- **User experience**: Sharing and quoting become harder
- **Real protection**: Doesn't actually protect the content (anyone with dev tools can view the source)

For most sites, the trade-offs are not worth it.

---

## How to Disable View Source in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Content Protection** subtab.

### Step 3: Enable the Feature

Scroll to **Disable View Source** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit the frontend. Try to view the source. The view-source shortcut should not viewing the page source via the keyboard shortcut.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable View Source** | Master toggle. | Off |
| **Apply to Administrators** | Admins can still view the source. | On |

---

## What Gets Affected

- The frontend: viewing the page source via the keyboard shortcut via JavaScript is disabled
- The admins: can still view the source (if "Apply to Administrators" is on)
- The accessibility: may affect users who rely on viewing the source

## What Does NOT Get Affected

- The admin: admins can still view the source
- The browser's developer tools: still allow bypassing
- The keyboard shortcuts (other than the disabled one): still work
- The screen readers: usually not affected

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `disable-view-source.php`:

**Actions:**

- `wp_head` calls `cm_disable_view_source_script()` (Injects view-source disable script)

```php
// Hooked in disable-view-source.php
add_action( 'wp_head', 'cm_disable_view_source_script' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The view-source shortcut still opens

**Cause:** The toggle is off, or the JavaScript is not running.
**Fix:** Verify the toggle is on. Check the browser console for errors.

### The admins can't view the source

**Cause:** The "Apply to Administrators" option is off.
**Fix:** Enable the "Apply to Administrators" sub-option.

### The view-source shortcut works in some browsers

**Cause:** Different browsers may handle the event differently.
**Fix:** Test in multiple browsers. The feature uses standard browser events, so it should work consistently, but some browsers may have edge cases.

### Users are still using the keyboard shortcut to view the page source via dev tools

**Cause:** This is a soft deterrent only.
**Fix:** The Disable View Source feature only prevents casual viewing the source. For real content protection, use copyright, watermarks (for images), or licensing terms.

---

## Related Articles

- [How to Disable Right Click in WordPress](security-disable-right-click.md)
- [How to Disable Text Selection in WordPress](security-disable-text-selection.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
