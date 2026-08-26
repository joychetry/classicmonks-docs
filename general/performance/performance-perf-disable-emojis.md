---
title: "How to Disable Emojis in WordPress"
slug: perf-disable-emojis
description: "Disable the WordPress emoji script in Classic Monks. Removes the JavaScript and DNS prefetch that handle emoji rendering, reducing page load time."
last_updated: 2026-08-03
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/perf-disable-emojis/
---

# How to Disable Emojis in WordPress

> Disable Emojis in Classic Monks removes the WordPress emoji detection script, styles, feed filters, and DNS prefetch that handle converting text emoticons into images, reducing page load time.

## Key Takeaways

- Single toggle, no nested options
- Removes the emoji script from the frontend and admin, plus emoji processing in feeds and emails
- One of several WordPress cleanup toggles under the Performance tab
- No configuration required (just enable or disable)
- Reversible (disable to restore the default WordPress behavior)

## What Is This Feature?

Disable Emojis in Classic Monks removes the WordPress emoji handling that loads a JavaScript file on every page to convert text emoticons into images. Enabling it removes the emoji detection script, the emoji stylesheet, the emoji staticization filters on feeds and emails, and the DNS prefetch for the emoji CDN. It is one of many WordPress optimization features available in the Performance tab.

## Why You Need It

WordPress loads a JavaScript file and a stylesheet on every page to render emojis. For sites that do not use emojis in their content, this is unnecessary overhead that adds a request and a few kilobytes to every page load. Disabling emoji handling is a common, low-risk optimization for business and portfolio sites that rarely use emojis.

---

## How to Enable this Feature in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Performance Tab

Click on the **Performance** menu, then click the **WP Optimizations** subtab.

### Step 3: Find the Disable Emojis Toggle

Scroll to the **Performance Wins** category. The toggle is labeled **Disable Emojis**, with the note "Removes WordPress emoji scripts and styles."

### Step 4: Enable the Feature

Toggle the **Disable Emojis** switch on.

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Test

Clear your browser cache and visit the frontend. Verify the emoji script is no longer loaded.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| Disable Emojis | Removes WordPress emoji scripts and styles. | Off |

No nested options. This is a single toggle.

---

## What Gets Affected

- The emoji detection script and stylesheet are removed from the frontend and admin
- Emoji staticization on feeds and emails is removed
- The DNS prefetch for the emoji CDN is removed
- The `wpemoji` TinyMCE plugin is removed from the editor

## What Does NOT Get Affected

- Your site content and existing emojis already in post content
- The WordPress admin layout and functionality
- Other plugin functionality

---

## Common Use Cases

### Business and portfolio sites

Business sites rarely use emojis in their content. Disabling the emoji script removes an unnecessary request and a few kilobytes from every page load, which is a small but real win for page speed.

### Performance-focused sites

If you are chasing PageSpeed and Lighthouse scores, removing the emoji script eliminates one fewer request and one fewer stylesheet on the critical path. Combined with other Performance tab cleanups, this reduces page weight.

### Email and feed-heavy sites

The emoji feature also runs staticization filters on `wp_mail` and RSS feeds. Disabling it removes that processing overhead for sites that send many emails or publish feeds.

### Minimalist design

If your theme does not use emojis and your visitors never see them, keeping the emoji script loaded is pure waste. Disabling it gives visitors a slightly faster load with no visible change.

### Agencies managing many client sites

For an agency, disabling emojis on every client site is a standard, low-risk optimization in a performance checklist. It is a single toggle per site with no configuration and no downside for sites that do not use emojis.

---

## Verify It Works

After enabling and saving, open your site's frontend in a browser and check the **Network** tab. You should no longer see `wp-emoji-release.min.js` in the loaded scripts. The emoji stylesheet and the `s.w.org` emoji DNS prefetch should also be gone.

---

## Note: This Is Different From the Assets Manager Emoji Toggle

Classic Monks has two emoji-related features. This doc covers the global **Disable Emojis** toggle in the WP Optimizations subtab, which removes emoji handling on the entire site. A separate **Disable WordPress Emoji** toggle in the Assets Manager subtab gives page-level control, letting you disable the emoji script on specific pages while keeping it elsewhere. Choose the global toggle for a sitewide cleanup, or the Assets Manager toggle for granular control.

---

## Troubleshooting

### The emoji script is still loading

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the **Disable Emojis** toggle is on and **Save Changes** was clicked. Clear all caching layers (object cache, page cache, CDN cache) and re-test.

### Emojis are missing from content

**Cause:** The feature is enabled on a site that actually uses emojis in content.
**Fix:** Emojis already stored in your content will still display, but live emoji rendering that relied on the script may stop. If you need emojis, disable the toggle or use the Assets Manager version for page-level control.

### The feature breaks another plugin

**Cause:** Another plugin depends on the emoji functionality that this feature disables.
**Fix:** Disable this feature if it breaks another plugin. The features are designed to be toggled independently.

---

## Related Articles

- [How to Enable Lazy Loading in WordPress](performance-perf-lazy-loading.md)
- [How to Enable the Assets Manager in WordPress](performance-perf-assets-manager.md)
- [How to Disable WordPress Emoji via Assets Manager in WordPress](performance-perf-disable-emoji-assets.md)
- [How to Disable Embeds in WordPress](performance-perf-disable-embeds.md)

---

## Developer Notes

This feature registers 4 WordPress hooks in `emoji-disabler.php`:

**Actions:**

- `init` calls `cm_disable_emojis()` (Removes emoji detection scripts and styles, feed and email staticization filters, the TinyMCE plugin, and the DNS prefetch)

**Filters:**

- `tiny_mce_plugins` calls `cm_disable_emojis_tinymce()` (Removes the `wpemoji` TinyMCE plugin)
- `wp_resource_hints` calls `cm_disable_emojis_remove_dns_prefetch()` (Removes the emoji CDN DNS prefetch)
- `pre_cm_update_option_disable_emojis` calls `cm_toggle_emojis()` (Adds or removes the `init` action when the option is updated)

```php
// Hooked in emoji-disabler.php
add_action( 'init', 'cm_disable_emojis' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior. No database schema changes are made. The feature state is stored as a boolean value in the `wp_options` table and can be toggled at any time from the admin settings.