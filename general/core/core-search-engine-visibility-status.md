---
title: "How to Enable Search Engine Visibility Status in Classic Monks | CM"
slug: core/search-engine-visibility-status
description: "Show search engine indexing status in the WordPress admin bar in Classic Monks. Auto-discourage indexing on URLs that don't match your Live Site URL. Prevent accidental staging site indexing."
last_updated: 2026-06-24
author: Joy
reading_time: 5 min
canonical: https://classicmonks.com/docs/core/search-engine-visibility-status/
---

# How to Enable Search Engine Visibility Status in WordPress

> Search Engine Visibility Status adds an indicator to the WordPress admin bar showing the current site's search engine indexing status, and automatically discourages indexing on URLs that don't match your configured Live Site URL.

## Key Takeaways

- Adds an admin bar indicator showing the current indexing status
- Configurable Live Site URL (your production domain)
- When the current URL doesn't match the Live Site URL, the page is auto-set to `noindex, nofollow`
- Prevents accidental indexing of staging or development sites
- Shows a visible warning in the admin when indexing is discouraged

## What Is the Search Engine Visibility Status feature?

The feature has two parts:

1. **Admin bar indicator**: A small icon/label in the WordPress admin bar that shows the current site's search engine indexing status. Green when the current URL matches the Live Site URL (production); yellow when it doesn't (staging/development).

2. **Automatic noindex on non-production URLs**: When the current request URL doesn't match the configured Live Site URL, the feature adds a `<meta name="robots" content="noindex, nofollow">` tag to the page. This prevents search engines from indexing the staging or development site.

The combination of these two features addresses one of the most common SEO disasters: accidentally indexing a staging site, which causes Google to see duplicate content and can tank the production site's rankings.

## Why You Need It

The classic staging site SEO mistake:

1. Developer creates a staging site at `staging.yoursite.com` for testing
2. The staging site's robots.txt or `wp-config.php` has `noindex` directives removed (or never added)
3. The staging site is fully accessible to Google
4. Google indexes the staging site's pages
5. Google sees the same content at both `www.yoursite.com` and `staging.yoursite.com`
6. Google flags this as duplicate content and may de-rank the production site

Search Engine Visibility Status prevents this by:

- Forcing `noindex, nofollow` on any URL that doesn't match the production Live Site URL
- Showing a visible indicator in the admin so developers KNOW the site is set to discourage indexing

The feature is opt-in (you set the Live Site URL), so it only activates for sites you've explicitly configured.

---

## How to Use Search Engine Visibility Status in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Content Subtab

Click on the **Core** menu, then click the **Content** subtab.

### Step 3: Enable Search Engine Visibility Status

Scroll to the **SEO and Visibility** section and toggle on **Enable Search Engine Visibility Status**. Nested options expand below the toggle.

### Step 4: Set the Live Site URL

Enter your production domain in the **Live Site URL** field. Use the canonical URL of your production site, including the protocol:

- `https://www.yoursite.com` (most common)
- `https://yoursite.com` (without www)
- `https://yoursite.com` (with custom path if WordPress is in a subdirectory)

Be consistent: this URL should match what Google has indexed as your production site. If you have a `www.` redirect, use the `www.` version here (the one Google indexes, not the one users see).

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Test the Indicator

Visit any page on your admin (e.g., the WordPress dashboard). Look at the top admin bar. You should see a small icon or label indicating the indexing status. If you're on the production URL, it's green. If you're on a staging URL, it's yellow.

### Step 7: Verify the Auto-noindex

Visit a page on your staging site (e.g., `https://staging.yoursite.com/`). View the page source. The `<head>` should contain a `<meta name="robots" content="noindex, nofollow">` tag. This prevents Google from indexing the staging page.

Visit the same page on production (e.g., `https://www.yoursite.com/`). The meta tag should NOT be present. The production site is indexable.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Search Engine Visibility Status** | Master toggle. Enables both the admin bar indicator and the auto-noindex. | Off |
| **Live Site URL** | Your production domain. | Empty |

No nested options. The Live Site URL is the only configuration.

---

## How the Auto-noindex Works

On every page load, the feature checks the current request URL:

1. Get the current request's host (e.g., `staging.yoursite.com`)
2. Get the configured Live Site URL's host (e.g., `www.yoursite.com`)
3. If they match exactly (after normalizing www vs non-www), the page is indexable (no meta tag added)
4. If they don't match, add a `<meta name="robots" content="noindex, nofollow">` tag to the `<head>`

The comparison is strict: any difference (subdomain, path, protocol) is treated as "not production" and triggers the noindex. (Replace this with a colon rather than em dash.) This is intentional, better to over-noindex than to accidentally let a staging URL get indexed.

### Edge Cases

- **Local development** (e.g., `localhost`, `127.0.0.1`, `*.local`): Always noindexed unless you set the Live Site URL to a local URL (rare but possible)
- **Preview URLs** (e.g., `staging.yoursite.com`): Noindexed
- **Production with www** (`www.yoursite.com`): Indexable if Live Site URL is `www.yoursite.com`
- **Production without www** (`yoursite.com`): Indexable if Live Site URL is `yoursite.com`
- **Mixed www/non-www**: The comparison normalizes both, so `www.yoursite.com` and `yoursite.com` are treated as the same

---

## What Does NOT Get Discouraged

- **External links from noindexed pages**: Search engines don't follow links from noindexed pages anyway
- **Comments on noindexed pages**: Comments are still allowed; the page just isn't indexed
- **The auto-noindex on staging doesn't affect the production site's robots.txt**: The production site is fully indexable unless you separately set it to discourage

---

## Developer Notes

This feature is a single toggle with no developer hooks currently exposed. The feature-specific logic is loaded conditionally when the toggle is enabled.

**Options used:**
| Option | Type | Default |
|--------|------|---------|
| Feature toggle | Boolean | `false` |
---

## Troubleshooting

### The admin bar indicator is not showing

**Cause:** The toggle is off, the user role doesn't have admin bar access, or a custom admin bar plugin is hiding it.
**Fix:** Verify the toggle is on. Verify the user has admin bar enabled (Users > Profile > Show Admin Bar). Disable other admin bar customizations to find the conflict.

### The Live Site URL field is not validating

**Cause:** The field accepts any string. There's no URL validation; what you enter is what it uses.
**Fix:** Use the canonical URL of your production site. Include the protocol (https://). If you're not sure, check Google Search Console > Settings > Verified Sites for the canonical URL.

### The auto-noindex is appearing on production

**Cause:** The Live Site URL doesn't match the production URL. For example, you set `yoursite.com` but Google indexes `www.yoursite.com`.
**Fix:** Verify the Live Site URL exactly matches the production URL that Google has indexed. Check the URL bar on production to see what the canonical form is.

### The auto-noindex is not appearing on staging

**Cause:** The Live Site URL is set incorrectly (matches staging), or a different plugin is removing the noindex meta tag.
**Fix:** Verify the Live Site URL is set to the production URL. Check for other plugins that filter `wp_robots` to remove the noindex.

### The staging site is being indexed by Google anyway

**Cause:** The auto-noindex is server-side (only applies to requests served by WordPress). If a search engine accessed the staging site before the feature was enabled, the page is already indexed. The noindex prevents future indexing, not retroactively.
**Fix:** Remove the staging URLs from Google Search Console (URL Removal tool). Verify the noindex is now present on staging. Submit a reconsideration request if needed.

### I have multiple staging environments (dev, staging, qa)

**Cause:** The feature only knows about one Live Site URL. If you have multiple non-production environments, all of them should auto-noindex (which they will, since none of them match the Live Site URL).
**Fix:** This is working as designed. If you want one of the non-production environments (e.g., `qa.yoursite.com`) to be indexable for testing, set the Live Site URL to the qa environment instead. But this is rare and risky.

---

## Related Articles

- [How to Add Nofollow to External Links in Classic Monks](core-nofollow-external-links.md)
- [How to Enable Nofollow for Post Types in Classic Monks](core-nofollow-post-types.md)
- [How to Disable Core Sitemaps in Classic Monks](core-disable-core-sitemaps.md)
- [How to Exclude Noindex Posts from Search Results in Classic Monks](core-exclude-noindex-from-search.md)
- [How to Use Content Utilities in Classic Monks](core-content-utilities.md)
