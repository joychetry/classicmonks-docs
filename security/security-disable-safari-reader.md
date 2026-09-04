---
title: "How to Disable Safari Reader Mode in WordPress"
slug: disable-safari-reader
description: "Disable Safari Reader Mode (⌘+Shift+R) on your WordPress site. Prevents the simplified reading view that strips out branding and styling."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-safari-reader/
---

# How to Disable Safari Reader Mode in WordPress

> Disable Safari Reader Mode in Classic Monks prevents Safari's Reader Mode (⌘+Shift+R) on your site. Keeps users on the full, styled version of your pages with branding intact.

## Key Takeaways

- Single toggle, no nested options
- Disables Safari's Reader Mode (the simplified reading view)
- Keeps users on the full styled version of pages
- Soft deterrent (users can still access content via Reader Mode by changing Safari settings)
- Useful for sites that rely on their styling and branding

## What Is the Disable Safari Reader Mode feature?

Safari's Reader Mode is a feature that strips a webpage down to its essential text content, removing ads, navigation, and styling. The user activates it with ⌘+Shift+R (or by tapping the Reader icon in the address bar).

For most sites, Reader Mode is a positive feature: it makes content easier to read. But for some sites (e.g., brand-focused sites, sites with integrated advertising), it's a problem because it strips the visual experience.

The Disable Safari Reader Mode feature prevents Safari from offering Reader Mode on your site.

## Why You Need It

Reader Mode can be problematic for some sites:

- **Brand-focused sites**: Reader Mode removes the branding, weakening the brand experience
- **Advertising-supported sites**: Reader Mode removes ads, reducing ad revenue
- **Custom layouts**: Reader Mode strips custom layouts, losing design intent
- **Interactive content**: Reader Mode may break interactive elements

For most sites (especially content-focused blogs and news sites), Reader Mode is a positive feature. For sites where branding or layout is critical, disabling it is worth considering.

## Trade-offs vs allowing Reader Mode

Disabling Reader Mode has trade-offs:

- **User experience**: Some users prefer Reader Mode for distraction-free reading
- **Accessibility**: Reader Mode is helpful for users with reading difficulties
- **Sharing and quoting**: Reader Mode makes it easier to share specific paragraphs
- **Mobile experience**: iPhone users in particular use Reader Mode frequently

For most sites, the trade-offs are not worth it.

---

## How to Disable Safari Reader Mode in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Content Protection** subtab.

### Step 3: Enable Disable Safari Reader Mode

Scroll to **Disable Safari Reader Mode** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit your site in Safari (desktop or mobile). Try to activate Reader Mode (⌘+Shift+R or the Reader icon in the address bar). The Reader Mode option should not be available.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable Safari Reader Mode** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- Safari (desktop and iOS): Reader Mode option is hidden
- The browser's address bar: no Reader icon
- The keyboard shortcut (⌘+Shift+R): no effect
- The user experience: users see the full styled version of pages

## What Does NOT Get Affected

- Other browsers: Chrome, Firefox, Edge, etc. are not affected
- Safari users with Reader Mode enabled by default: still see the full styled version (Reader Mode is hidden, not disabled)
- The page content: unchanged
- The SEO: search engines can still read the full content (they use the HTML)

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `disable-safari-reader.php`:

**Actions:**

- `wp_head` calls `cm_disable_safari_reader()` (Adds meta tag to disable Safari Reader Mode)

```php
// Hooked in disable-safari-reader.php
add_action( 'wp_head', 'cm_disable_safari_reader' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### Reader Mode is still available

**Cause:** The toggle is off, or the user is using a different browser.
**Fix:** Verify the toggle is on. Test in Safari specifically. Chrome, Firefox, etc. are not affected.

### The meta tag is not being added

**Cause:** A theme or plugin is removing the meta tag.
**Fix:** Check the browser's developer tools to verify the meta tag is in the page head. If the tag is not present, check for plugins that strip meta tags from the head.

### The page still appears in Reader Mode

**Cause:** Safari may use cached content.
**Fix:** Clear Safari's cache (Safari > Clear History and Website Data). Reload the page.

### I want to allow Reader Mode for specific pages

**Cause:** The feature is global.
**Fix:** Use the `cm_disable_safari_reader_post_types` filter to allow Reader Mode for specific content types. For per-page control, use the `wp_head` action with a conditional check (see Advanced Options).

---

## Related Articles

- [How to Disable Right Click in WordPress](security-disable-right-click.md)
- [How to Disable Text Selection in WordPress](security-disable-text-selection.md)
- [How to Disable Copy/Cut/Paste in WordPress](security-disable-copy-paste.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
