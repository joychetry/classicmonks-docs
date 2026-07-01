---
title: "How to Exclude Noindex Posts from Search Results in Classic Monks | CM"
slug: core/exclude-noindex-from-search
description: "Exclude noindexed posts from WordPress internal search results in Classic Monks. Keeps noindex tags in place but hides them from site search."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/core/exclude-noindex-from-search/
---

# How to Exclude Noindex Posts from Search Results in WordPress

> Exclude Noindex Posts from Search removes posts marked with a `noindex` robots meta tag from WordPress's internal search results, while keeping the noindex tag in place for search engines.

## Key Takeaways

- Single toggle, no nested options
- Removes noindexed posts from `?s=` (default search), WP_Query `s=` parameter, and search widgets
- Keeps the noindex meta tag intact (search engines still see it)
- Useful for staging content, low-quality pages, and internal-only content
- Affects only posts explicitly marked with a noindex meta tag

## What Is the Exclude Noindex from Search feature?

WordPress has two separate search systems:

1. **External search (Google, Bing, etc.)**: Uses the `noindex` meta tag in the page's `<head>`. When the tag is present, search engines exclude the page from their index.
2. **Internal search (the search box on your site)**: Uses WordPress's `WP_Query` with the `s` parameter. By default, this returns ALL matching posts, including those marked with `noindex`.

These can get out of sync. A page that's marked `noindex` (so Google ignores it) can still appear in your site's internal search results, where visitors can find and click it.

Exclude Noindex from Search bridges this gap. When a post has a `noindex` meta tag (set by your SEO plugin or by [Enable Nofollow for Post Types](core-nofollow-post-types.md)), the feature excludes it from internal search results. The `noindex` tag is preserved (search engines still see it), but the post is hidden from your site's own search.

## Why You Need It

Internal site search is often the user's first stop when they can't find something in the navigation. If the search returns noindexed posts (which the user might click only to be told "this page is not for you"), the experience is broken.

Common use cases for excluding noindexed posts from search:

- **Staging content**: Posts published for review but not meant for public consumption
- **Low-quality pages**: Tag pages, archive pages, or auto-generated content that you noindex but still exist
- **Internal-only content**: Documentation or knowledge-base posts that are noindex (for Google) but should still be findable internally
- **Sponsored content**: Posts that are noindex per Google's paid content guidelines but shouldn't appear in site search

The feature ensures internal search results are consistent with external search expectations.

---

## How to Use Exclude Noindex from Search in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Content Subtab

Click on the **Core** menu, then click the **Content** subtab.

### Step 3: Enable Exclude Noindex from Search

Scroll to the **SEO and Visibility** section and toggle on **Exclude Noindex Posts from Search Results**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Verify

Search for a noindexed post using your site's search box. The post should not appear in the results. Compare to the same search with the toggle off (the post should appear).

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Exclude Noindex Posts from Search Results** | Master toggle. | Off |

No nested options.

---

## How "Noindex" Is Detected

The feature uses WordPress's standard `wp_robots` filter to determine whether a post has a noindex directive. Posts with any of the following are considered noindexed and excluded from search:

| Source | Detection method |
|--------|-------------------|
| **Classic Monks** (Nofollow for Post Types feature) | Posts in selected post types are tagged with `noindex, nofollow` |
| **Yoast SEO** | Yoast sets the `noindex` meta based on post settings |
| **RankMath** | RankMath sets the `noindex` meta based on post settings |
| **AIOSEO** | AIOSEO sets the `noindex` meta based on post settings |
| **Manual `wp_robots` filter** | Custom code that filters `wp_robots` to add `noindex` |

The feature is SEO-plugin-agnostic. It uses the resulting `wp_robots` directive, not a specific plugin's custom meta key.

---

## What Gets Affected

| Search context | Affected? | Notes |
|----------------|-----------|-------|
| Default WordPress search (`?s=`) | Yes | Most common use case |
| Custom search plugins (SearchWP, Relevanssi) | Depends on plugin | The default WP_Query is affected; custom search engines may need their own integration |
| WP_Query with `s` parameter | Yes | Any code that runs a search via WP_Query |
| REST API search endpoint (`/wp-json/wp/v2/search`) | Yes | Same WP_Query under the hood |
| Block editor post search | No | Block editor searches are server-side admin queries; the filter is scoped to front-end searches |
| Admin post list search | No | Same as above; admin queries are not filtered |
| Search widget results | Yes | Uses the default search query |

---

## Developer Notes

This feature is a single toggle with no developer hooks currently exposed. The feature-specific logic is loaded conditionally when the toggle is enabled.

**Options used:**
| Option | Type | Default |
|--------|------|---------|
| Feature toggle | Boolean | `false` |
---

## Troubleshooting

### Noindexed posts are still appearing in search

**Cause:** The toggle is off, or the noindex detection isn't working for your specific SEO plugin.
**Fix:** Verify the toggle is on. View a noindexed post's page source and check that the `<meta name="robots">` tag contains `noindex`. If it doesn't, your SEO plugin isn't setting the noindex correctly. Use the `cm_is_post_noindexed` filter to add custom detection.

### Posts are being excluded from search when they shouldn't be

**Cause:** The noindex detection is over-aggressive. Some posts may be tagged noindex for external search but should still appear in internal search.
**Fix:** Use a custom post meta (`_exclude_from_search`) to control per-post inclusion. The `cm_is_post_noindexed` filter can be overridden to ignore the noindex tag for specific posts.

### The exclusion breaks the custom search plugin I'm using

**Cause:** The default WP_Query is filtered, but your custom search plugin (SearchWP, Relevanssi) has its own search engine.
**Fix:** Custom search plugins typically index the post content separately. They may have their own setting to exclude noindexed posts. Configure that in the search plugin's settings.

### Search widget results are not changing

**Cause:** The search widget uses a cached query or a custom search implementation that bypasses the default `pre_get_posts` filter.
**Fix:** Clear the widget cache (some caching plugins cache widget output). Check if the search widget is using a custom search engine (e.g., SearchWP) that needs its own configuration.

### The exclusion applies to admin search too

**Cause:** The default scope is all WP_Query searches, including admin. The exclusion is intentionally scoped to all searches to be safe.
**Fix:** If you need admin searches to include noindexed posts (e.g., for content audits), use the `cm_exclude_noindex_from_search_contexts` filter to limit the exclusion to front-end only.

---

## Related Articles

- [How to Add Nofollow to External Links in Classic Monks](core-nofollow-external-links.md)
- [How to Enable Nofollow for Post Types in Classic Monks](core-nofollow-post-types.md)
- [How to Disable Core Sitemaps in Classic Monks](core-disable-core-sitemaps.md)
- [How to Use Content Utilities in Classic Monks](core-content-utilities.md)
