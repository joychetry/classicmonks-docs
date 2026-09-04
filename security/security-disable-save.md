---
title: "How to Disable Save in WordPress"
slug: disable-save
description: "Disable the CTRL+S keyboard shortcut to save the page in Classic Monks. Prevents users from easily saving the page to their local disk."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-save/
---

# How to Disable Save in WordPress

> Disable Save in Classic Monks prevents the CTRL+S (or ⌘+S) keyboard shortcut that saves the current page to the local disk. Prevents casual saving of the page.

## Key Takeaways

- Single toggle, no nested options
- Disables saving the page via the keyboard shortcut via JavaScript
- Use the "Apply to Administrators" sub-option to allow admins to still saving the page via the keyboard shortcut
- Soft deterrent only, not a security feature
- Easily bypassed by browser dev tools

## What Is the Disable Save feature?

The saving the page via the keyboard shortcut behavior is a common browser feature. The Disable Save feature disables it on your WordPress site, preventing users from using the keyboard shortcut to save the page.

This is a soft deterrent, not a security feature. Determined users can still save the page via the browser's developer tools or by disabling JavaScript.

## Why You Need It

For some types of sites, preventing casual saving the page is useful:

- **Premium content sites**: Where the content itself is the product
- **Image-heavy sites**: Where images are the unique value
- **Course sites**: Where the lessons are paid
- **Recipe sites**: Where recipes are the unique value

For most sites, this is unnecessary. The content is already protected by copyright.

## Trade-offs vs allowing saving the page

Disabling saving the page has trade-offs:

- **Accessibility**: Users with disabilities who rely on saving the page are affected
- **User experience**: Sharing and quoting become harder
- **Real protection**: Doesn't actually protect the content (anyone with dev tools can save the page)

For most sites, the trade-offs are not worth it.

---

## How to Disable Save in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Content Protection** subtab.

### Step 3: Enable the Feature

Scroll to **Disable Save** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit the frontend. Try to save the page. The save shortcut should not saving the page via the keyboard shortcut.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable Save** | Master toggle. | Off |
| **Apply to Administrators** | Admins can still save the page. | On |

---

## What Gets Affected

- The frontend: saving the page via the keyboard shortcut via JavaScript is disabled
- The admins: can still save the page (if "Apply to Administrators" is on)
- The accessibility: may affect users who rely on saving the page

## What Does NOT Get Affected

- The admin: admins can still save the page
- The browser's developer tools: still allow bypassing
- The keyboard shortcuts (other than the disabled one): still work
- The screen readers: usually not affected

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `disable-save.php`:

**Actions:**

- `wp_head` calls `cm_disable_save_script()` (Injects save/disable script)

```php
// Hooked in disable-save.php
add_action( 'wp_head', 'cm_disable_save_script' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The save shortcut still works

**Cause:** The toggle is off, or the JavaScript is not running.
**Fix:** Verify the toggle is on. Check the browser console for errors.

### The admins can't save the page

**Cause:** The "Apply to Administrators" option is off.
**Fix:** Enable the "Apply to Administrators" sub-option.

### The save shortcut works in some browsers

**Cause:** Different browsers may handle the event differently.
**Fix:** Test in multiple browsers. The feature uses standard browser events, so it should work consistently, but some browsers may have edge cases.

### Users are still using the keyboard shortcut to save the page via dev tools

**Cause:** This is a soft deterrent only.
**Fix:** The Disable Save feature only prevents casual saving the page. For real content protection, use copyright, watermarks (for images), or licensing terms.

---

## Related Articles

- [How to Disable Right Click in WordPress](security-disable-right-click.md)
- [How to Disable Text Selection in WordPress](security-disable-text-selection.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
