---
title: "How to Disable Inspect Element in WordPress"
slug: disable-inspect-element
description: "Disable the F12 or CTRL+Shift+I keyboard shortcut to open browser dev tools in Classic Monks. Prevents users from easily inspecting the page's HTML, CSS, and JavaScript."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-inspect-element/
---

# How to Disable Inspect Element in WordPress

> Disable Inspect Element in Classic Monks prevents the F12 (or CTRL+Shift+I) keyboard shortcut that opens browser developer tools. Prevents casual inspection of the page's code.

## Key Takeaways

- Single toggle, no nested options
- Disables opening the browser developer tools via the keyboard shortcut via JavaScript
- Use the "Apply to Administrators" sub-option to allow admins to still opening the browser developer tools via the keyboard shortcut
- Soft deterrent only, not a security feature
- Easily bypassed by browser dev tools

## What Is the Disable Inspect Element feature?

The opening the browser developer tools via the keyboard shortcut behavior is a common browser feature. The Disable Inspect Element feature disables it on your WordPress site, preventing users from using the keyboard shortcut to open the developer tools.

This is a soft deterrent, not a security feature. Determined users can still open the developer tools via the browser's developer tools or by disabling JavaScript.

## Why You Need It

For some types of sites, preventing casual opening the developer tools is useful:

- **Premium content sites**: Where the content itself is the product
- **Image-heavy sites**: Where images are the unique value
- **Course sites**: Where the lessons are paid
- **Recipe sites**: Where recipes are the unique value

For most sites, this is unnecessary. The content is already protected by copyright.

## Trade-offs vs allowing opening the developer tools

Disabling opening the developer tools has trade-offs:

- **Accessibility**: Users with disabilities who rely on opening the developer tools are affected
- **User experience**: Sharing and quoting become harder
- **Real protection**: Doesn't actually protect the content (anyone with dev tools can open the developer tools)

For most sites, the trade-offs are not worth it.

---

## How to Disable Inspect Element in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Content Protection** subtab.

### Step 3: Enable the Feature

Scroll to **Disable Inspect Element** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit the frontend. Try to open the developer tools. The developer tools should not opening the browser developer tools via the keyboard shortcut.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable Inspect Element** | Master toggle. | Off |
| **Apply to Administrators** | Admins can still open the developer tools. | On |

---

## What Gets Affected

- The frontend: opening the browser developer tools via the keyboard shortcut via JavaScript is disabled
- The admins: can still open the developer tools (if "Apply to Administrators" is on)
- The accessibility: may affect users who rely on opening the developer tools

## What Does NOT Get Affected

- The admin: admins can still open the developer tools
- The browser's developer tools: still allow bypassing
- The keyboard shortcuts (other than the disabled one): still work
- The screen readers: usually not affected

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `disable-inspect-element.php`:

**Actions:**

- `wp_head` calls `cm_disable_inspect_element_script()` (Injects inspect element disable script)

```php
// Hooked in disable-inspect-element.php
add_action( 'wp_head', 'cm_disable_inspect_element_script' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The developer tools still opens

**Cause:** The toggle is off, or the JavaScript is not running.
**Fix:** Verify the toggle is on. Check the browser console for errors.

### The admins can't open the developer tools

**Cause:** The "Apply to Administrators" option is off.
**Fix:** Enable the "Apply to Administrators" sub-option.

### The developer tools works in some browsers

**Cause:** Different browsers may handle the event differently.
**Fix:** Test in multiple browsers. The feature uses standard browser events, so it should work consistently, but some browsers may have edge cases.

### Users are still using the keyboard shortcut to open the developer tools via dev tools

**Cause:** This is a soft deterrent only.
**Fix:** The Disable Inspect Element feature only prevents casual opening the developer tools. For real content protection, use copyright, watermarks (for images), or licensing terms.

---

## Related Articles

- [How to Disable Right Click in WordPress](security-disable-right-click.md)
- [How to Disable Text Selection in WordPress](security-disable-text-selection.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
