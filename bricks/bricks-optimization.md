---
title: "How to Optimize Bricks Builder Performance in WordPress"
slug: "bricks-optimization"
description: "Optimize Bricks Builder performance in Classic Monks. Disable Bricks frontend CSS and JS on non-Bricks pages and enable CSS minification for faster loading."
last_updated: 2026-08-04
author: Joy
reading_time: 5 min
canonical: "https://classicmonks.com/docs/bricks-optimization/"
---

# How to Optimize Bricks Builder Performance in WordPress

> If you use Bricks Builder for only some of your pages, its CSS and JavaScript still load on every page of your site. Classic Monks lets you disable Bricks frontend assets on non-Bricks pages and enable CSS minification so your site loads faster.

## Key Takeaways

- Disable Bricks frontend CSS and JavaScript on pages that do not use Bricks.
- Enable CSS minification for the Bricks styles that do load.
- Reduce page weight and HTTP requests on non-Bricks pages.
- Each option is an independent toggle in the **Optimization** subtab.

## What Is Bricks Optimization

Bricks Optimization is a group of options in the Classic Monks **Bricks** tab, **Optimization** subtab, that reduce the Bricks Builder frontend asset load. When you use Bricks for a landing page or a few templates but not the whole site, Bricks still enqueues its CSS and JavaScript on every page. These options stop that, so pages that do not use Bricks load lighter.

## Recommendations Before Enabling

- **Confirm which pages use Bricks.** These options disable Bricks assets on pages that do not use Bricks, so verify your Bricks pages still load their styles.
- **Test both Bricks and non-Bricks pages.** After enabling, check that Bricks pages look correct and non-Bricks pages load faster.
- **Enable one at a time.** Turn on each option and test, so you can isolate any issue.

## Optimize Bricks Asset Loading

### Step 1: Open the Bricks Tab

In your WordPress dashboard, go to **Classic Monks**, then open the **Bricks** tab.

### Step 2: Open the Optimization Subtab

Click the **Optimization** subtab.

### Step 3: Disable Bricks Frontend CSS

Toggle on **Disable Bricks frontend CSS on non-bricks pages**. This prevents the Bricks frontend stylesheet from loading on pages that do not use Bricks.

### Step 4: Disable Bricks Frontend JS

Toggle on **Disable Bricks frontend JS on non-bricks pages**. This prevents the Bricks frontend JavaScript from loading on pages that do not use Bricks.

### Step 5: Enable CSS Minification

Toggle on **Enable CSS minification for Bricks styles**. This minifies the Bricks CSS that does load, reducing its size.

### Step 6: Save and Test

Click **Save (⌘+S)**. Open both a Bricks page and a non-Bricks page to confirm the Bricks page still looks correct and the non-Bricks page loads without the extra assets.

## Verify It Works

After saving, verify the optimization:

- A Bricks page still renders its styles and layouts correctly.
- A non-Bricks page no longer loads the Bricks frontend CSS and JavaScript.
- The page size and HTTP requests on non-Bricks pages are reduced.

You can check the page source or use the browser's Network panel to confirm the Bricks assets are not enqueued on non-Bricks pages.

## Examples

### Example 1: Bricks Only on the Homepage

A site builds only its homepage with Bricks and uses another theme for the rest. Toggle on **Disable Bricks frontend CSS on non-bricks pages** and **Disable Bricks frontend JS on non-bricks pages**. Blog posts and other pages load without the Bricks assets, making them faster.

### Example 2: Minify Bricks Styles Site-Wide

A site uses Bricks throughout and wants the CSS smaller. Toggle on **Enable CSS minification for Bricks styles**. The Bricks CSS that loads is minified, reducing its transferred size.

### Example 3: A Mixed Bricks Site

A site uses Bricks for a few templates but not all pages. Toggle on all three optimization options. Bricks pages keep their styles, and non-Bricks pages load lighter and faster.

## Troubleshooting

### A Bricks page loses its styling

**Cause:** The frontend CSS is disabled on a page that actually uses Bricks.
**Fix:** Confirm the page uses Bricks, or keep the CSS disable off for that section. The option only targets non-Bricks pages.

### Non-Bricks pages still load Bricks assets

**Cause:** The option is off, or a caching plugin is serving the old page.
**Fix:** Confirm the toggle is on and clear the page cache.

### The minified CSS is not applied

**Cause:** The option is off, or Bricks is not using the minified style.
**Fix:** Confirm the toggle is on and clear the Bricks and page caches.

## Related Articles

- [How to Complete the Bricks Initial Setup in WordPress](bricks-setup.md)
- [How to Use Bricks Builder UI Improvements in WordPress](bricks-ui-improvements.md)
- [How to Check Bricks Builder Status in WordPress](bricks-status.md)

---

*Written by Joy. Last updated August 4, 2026. Tested with WordPress 6.x and Classic Monks 2.1.0.*

<!-- schema: Article, TechArticle -->
<!-- schema: BreadcrumbList -->