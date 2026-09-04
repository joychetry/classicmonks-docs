---
title: "How to Disable Link in Comments in Classic Monks"
slug: disable-link-in-comments
description: "Strip auto-linking and rendered links from WordPress comment text in Classic Monks. Disables URL-to-anchor conversion and removes existing link tags from comment content."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/disable-link-in-comments/
---

# How to Disable Link in Comment and Disable Auto-linking in WordPress

> Disable Link in Comment strips both auto-linking (WordPress's automatic conversion of bare URLs to clickable anchors) and rendered link tags (existing `<a>` tags in comment text) from comment content.

## Key Takeaways

- Single toggle, two effects
- Prevents WordPress from converting bare URLs in comments to clickable anchors
- Strips existing `<a>` tags from comment text
- Reduces link-based spam effectiveness
- Affects all future comments; existing comments are filtered on display

## What Is the Disable Link in Comment feature?

WordPress comments have two link behaviors:

1. **Auto-linking**: Bare URLs in comment text (e.g., "Check out example.com") are automatically converted to clickable anchor tags when displayed
2. **Rendered links**: Existing `<a>` tags in the comment HTML (e.g., `<a href="...">text</a>`) are displayed as clickable links

Disable Link in Comment turns off both behaviors. URLs appear as plain text (e.g., "Check out example.com" stays as text, not a link), and existing link tags are stripped from the rendered output. The raw comment data is unchanged; only the display is affected.

## Why You Need It

Comment links are a primary vector for comment spam and for users to drive traffic away from your site. Disabling them has several effects:

- **Reduced spam**: Spammers cannot post clickable links; their primary motivation is gone
- **Lower bounce rate**: Visitors who click links in comments leave your site; removing the links keeps them on-page
- **Cleaner appearance**: Long URLs in comments can break formatting; plain text is cleaner
- **Better SEO**: Outbound links from comments pass link equity; removing them concentrates equity on your own content

The trade-off is that legitimate commenters who want to share a URL have to type it as plain text. For most sites, this is acceptable.

---

## How to Use Disable Link in Comment in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Content Subtab

Click on the **Core** menu, then click the **Content** subtab.

### Step 3: Enable Disable Link in Comment

Scroll to the **Comment System Overrides** section and toggle on **Disable Link in Comment and Disable Auto-linking**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Open any post with comments. View the comments on the front-end. URLs in comment text should appear as plain text, not as clickable links.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable Link in Comment and Disable Auto-linking** | Master toggle. Two effects in one. | Off |

No nested options.

---

## What Gets Disabled

| Behavior | Before | After |
|----------|--------|-------|
| Bare URL in comment ("example.com") | Auto-converted to `<a href="example.com">example.com</a>` | Rendered as plain text "example.com" |
| HTML link in comment ("`<a href="...">text</a>`") | Rendered as clickable link | Rendered as plain text "text" (anchor tag stripped) |
| Markdown-style link in comment ("[text](url)") | Rendered as text + URL | Rendered as text + URL (no link) |
| Email link in comment (mailto:) | Rendered as clickable email | Rendered as plain text email address |
| HTML in comment text (other tags) | Rendered as HTML | Rendered as HTML (only links are affected) |
| Comment author's URL field (the website field) | Rendered as clickable author name | Rendered as plain text (or hidden if you also enabled "Remove Comment URLs") |

---

## Developer Notes

Disable Link in Comments removes hyperlinks from comment content. No developer hooks are currently exposed.

**Options used:**
| Option | Type | Default |
|--------|------|---------|
| `disable_link_in_comments` | Boolean | `false` |
---

## Troubleshooting

### Links in comments are still showing as clickable

**Cause:** The toggle is off, or a caching plugin is serving a cached version of the comments with the original link HTML.
**Fix:** Verify the toggle is on. Clear all caching layers (page cache, object cache, CDN). View the page source to confirm the link tags are stripped from the rendered HTML.

### The comment text is showing escaped HTML

**Cause:** If a commenter's text includes raw HTML like `&lt;a&gt;`, the comment system is escaping the HTML for security. This is correct behavior; do not try to render unescaped HTML in comments.
**Fix:** None needed. Comments should never render raw HTML from untrusted sources (XSS risk). The feature strips only the link tags after WordPress's comment sanitization.

### I want to disable link auto-linking but keep existing link tags

**Cause:** The toggle does both at once. There is no separate control.
**Fix:** Use a small custom plugin that filters `make_clickable_rel` (the filter that handles auto-linking) to disable it, but leaves the link-tag-stripping behavior alone. Or use a child theme's `comment_text` filter to selectively re-enable existing links after stripping.

### Comment authors' website URLs are still showing in the comment meta

**Cause:** The comment author's "Website" URL (the URL they enter in the comment form) is rendered separately from the comment text. Disable Link in Comment strips links from the comment text, but the website URL in the comment meta is a different field.
**Fix:** Enable the separate [Remove Comment URLs](core-remove-comment-urls.md) feature, which removes the website field from the form AND strips the website URL from the rendered comment meta.

---

## Related Articles

- [How to Configure Comments in Classic Monks](core-comments.md)
- [How to Remove Comment URLs in Classic Monks](core-remove-comment-urls.md)
- [How to Disable Comments in Classic Monks](core-disable-comments.md)
