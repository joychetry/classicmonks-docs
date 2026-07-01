---
title: "How to Optimize Bricks Builder Performance in WordPress | CM"
slug: bricks-optimization
description: "Optimize Bricks Builder performance in Classic Monks. Disable frontend CSS/JS, enable CSS minification, and reduce page load times."
last_updated: 2026-06-24
author: Joy
reading_time: 5 min
canonical: https://classicmonks.com/docs/bricks-optimization/
---

# How to Optimize Bricks Builder Performance in WordPress

> Bricks Optimization in Classic Monks reduces Bricks Builder's frontend asset loading. Disable CSS/JS on non-Bricks pages, enable CSS minification, and improve page speed.

## Key Takeaways

- Category overview of Bricks Builder features
- Multiple features can be enabled independently
- Each feature is a standalone toggle
- Features appear in the Bricks editor after enabling

## What Is This Category?

Bricks Optimization in Classic Monks reduces Bricks Builder's frontend asset loading. Disable CSS/JS on non-Bricks pages, enable CSS minification, and improve page speed. This is a category overview of all features in this group.

---

## Optimization Options

The Optimization subtab has 3 features:

1. **Disable Bricks Frontend CSS**: Prevents Bricks CSS from loading on non-Bricks pages
2. **Disable Bricks Frontend JS**: Prevents Bricks JavaScript from loading on non-Bricks pages
3. **Enable Bricks CSS Minification**: Minifies Bricks CSS output for faster loading

These features are critical for sites that use Bricks Builder for specific pages but not site-wide. Without them, Bricks CSS and JS load on every page, including blog posts and other non-Bricks content.

## How to optimize

Enable each optimization feature and test your site:

1. **Disable Bricks Frontend CSS**: Safe to enable if you don't use Bricks styling on non-Bricks pages
2. **Disable Bricks Frontend JS**: Safe to enable if you don't use Bricks JavaScript on non-Bricks pages
3. **Enable Bricks CSS Minification**: Safe to enable on any site with Bricks

After enabling, test both Bricks pages (to verify they still look correct) and non-Bricks pages (to verify they load faster).

## Performance impact

Disabling Bricks CSS/JS on non-Bricks pages can significantly reduce page load time:

- **CSS savings**: 50-200KB of unused CSS removed per page
- **JS savings**: 30-100KB of unused JavaScript removed per page
- **HTTP requests**: 2-4 fewer requests per page
- **PageSpeed impact**: 5-15 point improvement on PageSpeed Insights

These savings are significant for sites where only a few pages use Bricks Builder.

## Related Articles

- [How to Set Up the Bricks Integration in WordPress](bricks-setup.md)
- [How to Use Bricks Builder UI Improvements in WordPress](bricks-ui-improvements.md)
- [How to Check Bricks Builder Status in WordPress](bricks-status.md)


### Developer integration

The Bricks optimization module conditionally loads assets.

**Utility function:**

- `cm_bricks_should_enqueue()` returns true only on pages using Bricks Builder

**Hooks used:**

- `wp_enqueue_scripts` conditionally dequeues Bricks assets on non-Bricks pages
- `init` enables CSS minification via `bricks/assets/minify_css` filter (conditional)
- `wp_sitemaps_post_types` excludes Bricks templates from sitemaps (conditional)
- `wp_head` and `admin_head` inject inline CSS for builder modifications
