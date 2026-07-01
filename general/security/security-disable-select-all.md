---
title: "How to Disable Select All in WordPress | CM"
slug: security/disable-select-all
description: "Disable the CTRL+A keyboard shortcut to select all text in Classic Monks. Prevents users from easily selecting all text on the page with a single shortcut."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/security/disable-select-all/
---

# How to Disable Select All in WordPress

> Disable Select All in Classic Monks prevents the CTRL+A (or ⌘+A) keyboard shortcut that selects all text on the page. Prevents casual mass-selection of content.

## Key Takeaways

- Single toggle, no nested options
- Disables selecting all text via the keyboard shortcut via JavaScript
- Use the "Apply to Administrators" sub-option to allow admins to still selecting all text via the keyboard shortcut
- Soft deterrent only, not a security feature
- Easily bypassed by browser dev tools

## What Is the Disable Select All feature?

The selecting all text via the keyboard shortcut behavior is a common browser feature. The Disable Select All feature disables it on your WordPress site, preventing users from using the keyboard shortcut to select all text.

This is a soft deterrent, not a security feature. Determined users can still select all text via the browser's developer tools or by disabling JavaScript.

## Why You Need It

For some types of sites, preventing casual selecting all text is useful:

- **Premium content sites**: Where the content itself is the product
- **Image-heavy sites**: Where images are the unique value
- **Course sites**: Where the lessons are paid
- **Recipe sites**: Where recipes are the unique value

For most sites, this is unnecessary. The content is already protected by copyright.

## Trade-offs vs allowing selecting all text

Disabling selecting all text has trade-offs:

- **Accessibility**: Users with disabilities who rely on selecting all text are affected
- **User experience**: Sharing and quoting become harder
- **Real protection**: Doesn't actually protect the content (anyone with dev tools can select all text)

For most sites, the trade-offs are not worth it.

---

## How to Disable Select All in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Content Protection** subtab.

### Step 3: Enable the Feature

Scroll to **Disable Select All** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit the frontend. Try to select all text. The select-all shortcut should not selecting all text via the keyboard shortcut.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable Select All** | Master toggle. | Off |
| **Apply to Administrators** | Admins can still select all text. | On |

---

## What Gets Affected

- The frontend: selecting all text via the keyboard shortcut via JavaScript is disabled
- The admins: can still select all text (if "Apply to Administrators" is on)
- The accessibility: may affect users who rely on selecting all text

## What Does NOT Get Affected

- The admin: admins can still select all text
- The browser's developer tools: still allow bypassing
- The keyboard shortcuts (other than the disabled one): still work
- The screen readers: usually not affected

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `disable-select-all.php`:

**Actions:**

- `wp_head` calls `cm_disable_select_all_script()` (Injects select-all disable script)

```php
// Hooked in disable-select-all.php
add_action( 'wp_head', 'cm_disable_select_all_script' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The select-all shortcut still works

**Cause:** The toggle is off, or the JavaScript is not running.
**Fix:** Verify the toggle is on. Check the browser console for errors.

### The admins can't select all text

**Cause:** The "Apply to Administrators" option is off.
**Fix:** Enable the "Apply to Administrators" sub-option.

### The select-all shortcut works in some browsers

**Cause:** Different browsers may handle the event differently.
**Fix:** Test in multiple browsers. The feature uses standard browser events, so it should work consistently, but some browsers may have edge cases.

### Users are still using the keyboard shortcut to select all text via dev tools

**Cause:** This is a soft deterrent only.
**Fix:** The Disable Select All feature only prevents casual selecting all text. For real content protection, use copyright, watermarks (for images), or licensing terms.

---

## Related Articles

- [How to Disable Right Click in WordPress](security-disable-right-click.md)
- [How to Disable Text Selection in WordPress](security-disable-text-selection.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
