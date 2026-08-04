---
title: "Hide the WordPress Version in WordPress: Remove Version Number"
slug: "hide-version"
description: "Hide the WordPress version number from the page source in Classic Monks. Remove the version meta tag and generator tag to improve your website security."
last_updated: 2026-08-04
author: Joy
reading_time: 4 min
canonical: "https://classicmonks.com/docs/hide-version/"
---

# How to Hide the WordPress Version in WordPress

> The WordPress version number appears in the page source and can reveal your platform version to attackers. Classic Monks lets you hide it for better security.

## Key Takeaways

- Remove the WordPress version number from the page source.
- Removes the generator meta tag that reveals your version.
- A security best practice for hiding your platform version.
- A simple toggle, no nested options.

## What Is Hide WP Version

Hide WP Version is a white-label option in the Classic Monks **White Label** tab that removes the WordPress version number from the frontend HTML source. WordPress adds a generator meta tag that reveals the version, such as `<meta name="generator" content="WordPress 6.5">`. Hiding it is a security best practice because attackers can use the version to find known vulnerabilities.

## Hide the WordPress Version

### Step 1: Open the Branding Settings

In your WordPress dashboard, go to **Classic Monks**, open the **White Label** tab, then the **Branding** subtab.

![Classic Monks White Label branding settings](../../images/white-label/branding/branding-settings.png)

### Step 2: Turn On Hide WP Version

In the **Branding** subtab, toggle on **Hide WP Version**.

### Step 3: Save and Test

Click **Save (⌘+S)**. Open your site's frontend and view the page source to confirm the version is gone.

## Verify It Works

After saving, open your site's frontend and inspect the page source:

- The `<meta name="generator" content="WordPress ...">` tag is gone.
- The WordPress version number no longer appears in the source.

If the version still shows, confirm the toggle is on and the changes were saved. Clear any page cache.

## Examples

### Example 1: Hide the Version for Security

A site wants to reduce its attack surface. Toggle on **Hide WP Version**. Attackers can no longer see the WordPress version in the source to target known vulnerabilities.

### Example 2: A Cleaner Source

A developer wants a cleaner page source. Toggle on **Hide WP Version**. The generator meta tag is removed, leaving a cleaner document head.

### Example 3: Combine With Other Cleanup

A site uses **Clean Head Tags** and **Hide WP Version** together. Toggle on **Hide WP Version** to remove the version tag, and **Clean Head Tags** to remove other head meta tags.

### A security-conscious approach

A site that handles sensitive data may want to reduce the information it exposes. Hiding the WordPress version removes a detail that could be used to target known vulnerabilities, so this is a common step in a security cleanup.

### A professional-looking source

For a developer or agency that wants a clean, professional document head, hiding the version removes the generic WordPress generator tag. The source looks more polished and less like a stock WordPress install.

## Troubleshooting

### The version still shows

**Cause:** The toggle is off, a caching plugin is serving the old page, or a theme/plugin adds its own version tag.
**Fix:** Confirm the toggle is on, clear the page cache, and check for plugins that add their own version meta tags.

### The version shows in the admin

**Cause:** This option only hides the version from the frontend source.
**Fix:** Use **Remove WordPress Footer Text and Version** to hide the version from the admin footer.

## Recommendations Before Enabling

- **Combine with Clean Head Tags.** Use Hide WP Version with Clean Head Tags to remove the version tag and other head meta tags in one pass.
- **Remember the admin.** This option hides the version from the frontend source; use Remove WordPress Footer Text and Version to hide it from the admin footer.
- **Clear the cache.** A caching plugin may serve the old page, so clear it after enabling.

## Common Use Cases

### Reduce the attack surface

The WordPress version in the page source lets attackers target known vulnerabilities for that version. Hiding it removes a piece of information that can be used against your site.

### Cleaner page source for developers

A developer who wants a clean document head can remove the generator meta tag. This makes the source easier to read and slightly smaller.

### Combine with other cleanup

Use Hide WP Version with Clean Head Tags to remove the version tag and other unnecessary head meta tags. This gives a lean, clean document head.

## Troubleshooting

## Related Articles

- [How to Clean Head Tags in WordPress](white-label-wl-clean-head-tags.md)
- [How to Remove the WordPress Footer Text and Version](white-label-wl-remove-footer-text.md)
- [How to Use the White Label Tab in Classic Monks: Feature Index](../white-label.md)

---

*Written by Joy. Last updated August 4, 2026. Tested with WordPress 6.x and Classic Monks 2.1.0.*

<!-- schema: Article, TechArticle -->
<!-- schema: BreadcrumbList -->