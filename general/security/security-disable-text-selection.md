---
title: "How to Disable Text Selection in WordPress | CM"
slug: security/disable-text-selection
description: "Disable text selection on the WordPress frontend in Classic Monks. Prevents casual copying of content. Optional NoScript overlay for users with JavaScript disabled."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/security/disable-text-selection/
---

# How to Disable Text Selection in WordPress

> Disable Text Selection in Classic Monks prevents users from selecting and copying text on your WordPress frontend. Includes an optional NoScript overlay for users with JavaScript disabled.

## Key Takeaways

- Single toggle with 4 sub-options (admin bypass, NoScript, allowed elements, NoScript message)
- Prevents text selection via JavaScript
- Optional NoScript overlay (for users with JavaScript disabled)
- Can allow text selection on specific elements
- Optional admin bypass (admins can still select text)
- Not a security feature (only casual copy protection)

## What Is the Disable Text Selection feature?

Some sites want to prevent casual copying of their content. The Disable Text Selection feature uses JavaScript to prevent the browser's default text selection behavior on your site.

This is a soft deterrent, not a security feature. Determined users can still copy the content via the browser's developer tools or by disabling JavaScript.

## Why You Need It

For some types of sites, preventing casual copy is useful:

- **Premium content sites**: Where the content itself is the product
- **Recipe sites**: Where the recipes are the unique value
- **Course sites**: Where the lessons are paid
- **Image-heavy sites**: Where text captions are a key part of the value

For most sites, this is unnecessary. The content is already protected by copyright, and preventing copy doesn't add real security.

## Trade-offs vs allowing selection

Disabling text selection has trade-offs:

- **Accessibility**: Users with disabilities who rely on text selection (e.g., for screen readers) are affected
- **User experience**: Sharing and quoting become harder
- **SEO**: Search engines can still read the content (they use the HTML, not the visual rendering)
- **Real protection**: Doesn't actually protect the content (anyone with dev tools can copy)

For most sites, the trade-offs are not worth it.

---

## How to Disable Text Selection in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Content Protection** subtab.

### Step 3: Enable Disable Text Selection

Scroll to **Disable Text Selection** and toggle on. Nested options expand.

### Step 4: Configure Sub-Options

The 4 sub-options include:

- **Apply to Administrators**: Allow admins to still select text (recommended)
- **NoScript Overlay**: Show an overlay for users with JavaScript disabled
- **Allowed Elements**: CSS selector for elements where text selection is allowed (e.g., `.selectable` for a class on elements users can select)
- **NoScript Message**: The message shown in the overlay

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Test

Visit the frontend. Try to select text. The text should not be selectable. To verify the NoScript overlay, disable JavaScript in your browser and reload the page.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable Text Selection** | Master toggle. | Off |
| **Apply to Administrators** | Admins can still select text. | On |
| **NoScript Overlay** | Show overlay for users with JavaScript disabled. | Off |
| **Allowed Elements** | CSS selector for selectable elements. | (empty) |
| **NoScript Message** | The message shown in the overlay. | "Please enable JavaScript to access this content." |

---

## What Gets Affected

- The frontend: text is not selectable (unless on allowed elements)
- The NoScript users: see an overlay (if enabled)
- The admins: can still select text (if "Apply to Administrators" is on)
- The accessibility: may affect users who rely on text selection

## What Does NOT Get Affected

- The admin: admins can still select text
- The right-click context menu: not disabled (use a separate feature for that)
- The keyboard shortcuts (CTRL+C, etc.): not blocked (only mouse selection is)
- The screen readers: usually not affected (they use the HTML, not the visual rendering)
- The browser's developer tools: still allow copying (this is a soft deterrent only)

---

## Advanced Options (Developers)

This feature registers 2 WordPress hooks in `disable-text-selection.php`:

**Actions:**

- `wp_body_open` calls `cm_disable_text_selection_add_noscript()` (Adds noscript fallback)
- `wp_enqueue_scripts` calls `cm_disable_text_selection_enqueue_assets()` (Enqueues text selection disable CSS/JS)

```php
// Hooked in disable-text-selection.php
add_action( 'wp_body_open', 'cm_disable_text_selection_add_noscript' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The text is still selectable

**Cause:** The JavaScript is not running, or the text is in an "allowed element".
**Fix:** Verify the toggle is on. Check that the text is not in an element matching the "Allowed Elements" selector.

### The admins can't select text

**Cause:** The "Apply to Administrators" option is off.
**Fix:** Enable the "Apply to Administrators" sub-option.

### The NoScript overlay is not showing

**Cause:** The toggle is off, or the user has JavaScript enabled (the overlay only shows when JavaScript is disabled).
**Fix:** Verify the "NoScript Overlay" sub-option is on. Test by disabling JavaScript in your browser.

### The page is not accessible to screen readers

**Cause:** Some screen readers may have trouble if text selection is disabled.
**Fix:** Use the "Allowed Elements" to allow text selection in specific elements. Don't disable text selection on the entire site if accessibility is a concern.

### Users are still copying the content

**Cause:** This is a soft deterrent. Determined users can use browser dev tools.
**Fix:** The Disable Text Selection feature only prevents casual copying. For real content protection, use copyright, watermarks (for images), or licensing terms.

---

## Related Articles

- [How to Disable Right Click in WordPress](security-disable-right-click.md)
- [How to Disable View Source in WordPress](security-disable-view-source.md)
- [How to Disable Copy/Cut/Paste in WordPress](security-disable-copy-paste.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
