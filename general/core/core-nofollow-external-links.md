---
title: "How to Add Nofollow to External Links in Classic Monks"
slug: nofollow-external-links
description: "Automatically add rel=\"nofollow\" and target=\"_blank\" to external links in Classic Monks. Preserve link equity, reduce bounce rate, no theme edits required."
last_updated: 2026-06-24
author: Joy
reading_time: 5 min
canonical: https://classicmonks.com/docs/nofollow-external-links/
---

# How to Add Nofollow to External Links in WordPress

> Add Nofollow to External Links automatically adds `rel="nofollow"` and `target="_blank"` to all external links in your WordPress content, preserving link equity and reducing bounce rate.

## Key Takeaways

- Single toggle, no nested options
- Processes `the_content` filter (covers posts, pages, and custom post types)
- Adds `rel="nofollow"` and `target="_blank"` to links pointing to external domains
- Does not modify internal links (links to your own domain)
- Does not modify existing link attributes (preserves user-set values)

## What Is the Add Nofollow feature?

WordPress's default behavior is to render links as written: `<a href="https://example.com">text</a>`. Add Nofollow intercepts this at the `the_content` filter and adds two attributes to all external links:

- `rel="nofollow"`: Tells search engines not to pass link equity to the linked page
- `target="_blank"`: Opens the link in a new browser tab (keeps the visitor on your site)

Internal links (links pointing to your own domain) are not modified. The feature does not change the link's text, URL, or any other attributes you've manually set.

## Why You Need It

- **SEO**: `rel="nofollow"` tells search engines like Google not to pass PageRank to the linked site. This concentrates your link equity on your own content rather than spreading it to external sites
- **User experience**: `target="_blank"` opens external links in a new tab, so visitors don't navigate away from your site. They can read the external content and still have your site open
- **Spam reduction**: Spammers and low-quality linkers avoid sites that nofollow external links, because the backlink they get from your site has no SEO value
- **Compliance**: Some sites are required by policy or regulation to nofollow certain external links (e.g., sponsored content per Google guidelines)

The trade-off is that some legitimate sites may not link to you if you nofollow all externals (they want the link equity back). For most sites, the SEO and UX benefits outweigh this concern.

---

## How to Use Add Nofollow in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Content Subtab

Click on the **Core** menu, then click the **Content** subtab.

### Step 3: Enable Add Nofollow to External Links

Scroll to the **SEO and Visibility** section and toggle on **Add nofollow to External Links and Open in New Tab**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Verify

Open any post with external links on the front-end. View the page source. External links should have `rel="nofollow" target="_blank"` in their `<a>` tags. Internal links (to your own domain) should be unchanged.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Add nofollow to External Links and Open in New Tab** | Master toggle. Applies both attributes. | Off |

No nested options. The toggle is global.

---

## What Gets Modified

| Link type | Before | After |
|-----------|--------|-------|
| External link in post content (`<a href="https://other-site.com">text</a>`) | No rel, no target | `<a rel="nofollow" target="_blank" href="https://other-site.com">text</a>` |
| Internal link in post content (`<a href="/about/">text</a>`) | Unchanged | Unchanged |
| External link in custom HTML blocks | No rel, no target | Modified (if processed by `the_content` filter) |
| Links in widgets | Depends on widget | Modified (if widget calls `the_content` filter) |
| Links in navigation menus | Unchanged | Unchanged (menus don't go through `the_content`) |
| Links in comments | Unchanged | Unchanged (comments are filtered separately) |

---

## How the Feature Decides "External"

The feature compares each link's host to your site's host (`home_url()`'s host). If they match (including www vs non-www and subdomain handling), the link is internal. If they don't match, the link is external and gets the attributes added.

Edge cases:

- **Subdomain links**: A link to `blog.yoursite.com` is considered internal if your site is at `yoursite.com` AND the subdomain is configured. Otherwise, it's external.
- **Protocol-relative links**: A link starting with `//` (e.g., `//cdn.example.com`) is treated as external by default.
- **Anchor-only links**: A link starting with `#` is not modified (it's a page anchor, not an external link).
- **Mailto and tel links**: A `mailto:` or `tel:` link is not modified (it's not an external HTTP link).
- **Same-site cross-domain**: A link to `yoursite.com` from `www.yoursite.com` is considered internal if both resolve to the same site.

---

## Developer Notes

This feature is a single toggle with no developer hooks currently exposed. The feature-specific logic is loaded conditionally when the toggle is enabled.

**Options used:**
| Option | Type | Default |
|--------|------|---------|
| Feature toggle | Boolean | `false` |
---

## Troubleshooting

### External links are not getting the nofollow attribute

**Cause:** The toggle is off, or a caching plugin is serving a cached version of the page.
**Fix:** Verify the toggle is on. Clear all caching layers. View the page source to confirm the attribute is in the rendered HTML.

### Internal links are also getting nofollow

**Cause:** The site host comparison is failing. This happens when the site URL and the home URL are different (e.g., WordPress is configured with `www.yoursite.com` but the database stores `yoursite.com`).
**Fix:** Check Settings > General > WordPress Address and Site Address. They should match. If they don't, update them to match, or use the `cm_nofollow_external_link_domains` filter to manually define what's external.

### Existing link attributes are being overwritten

**Cause:** The feature's default behavior is to preserve existing attributes, but a custom filter may be overwriting them.
**Fix:** Check for custom code that filters `the_content` and modifies link attributes. The default behavior preserves `rel="dofollow"` and other existing rel values, so this is unusual.

### Sponsored links need rel="sponsored" instead of nofollow

**Cause:** The feature adds nofollow, but Google requires sponsored for paid placements.
**Fix:** Use the `cm_nofollow_link_attributes` filter to add "sponsored": `add_filter( 'cm_nofollow_link_attributes', function( $attrs ) { $attrs[] = 'sponsored'; return $attrs; } );`. This adds both nofollow and sponsored, which is the safest signal for paid content.

### The feature is not working on archive pages

**Cause:** The `the_content` filter only runs on singular post views. Archive pages (categories, tags, search results) use `the_excerpt` or direct template calls.
**Fix:** If you need nofollow on archive pages, extend the filter: `add_filter( 'the_excerpt', function( $excerpt ) { return apply_filters( 'the_content', $excerpt ); } );`. This is a workaround, not a fix; the canonical solution is to use a theme that calls `the_content` on archive pages.

---

## Related Articles

- [How to Enable Nofollow for Post Types in Classic Monks](core-nofollow-post-types.md)
- [How to Use Content Utilities in Classic Monks](core-content-utilities.md)
- [How to Disable Core Sitemaps in Classic Monks](core-disable-core-sitemaps.md)
