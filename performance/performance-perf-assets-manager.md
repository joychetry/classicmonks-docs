---
title: "Disable Unused Scripts and Styles on WordPress Pages"
slug: perf-assets-manager
description: "Speed up WordPress by disabling unused CSS and JavaScript on specific pages with Classic Monks Assets Manager. Learn setup, testing, and rollback steps."
last_updated: 2026-08-03
author: Joy
reading_time: 10 min
canonical: https://classicmonks.com/docs/perf-assets-manager/
---

# How to disable unused scripts and styles in WordPress

> Use Classic Monks Assets Manager to stop unnecessary CSS and JavaScript from loading on pages that do not need it.

## Key Takeaways

- Assets Manager lets you review frontend assets from the current page and disable selected plugin, theme, and miscellaneous assets.
- You can disable an asset on the **Current URL**, **Everywhere**, or matching URLs with a **Regex** rule.
- Test changes while logged out because logged-in users can be excluded from Assets Manager optimizations.
- Check dependencies and interactive features before publishing a rule.
- Use the asset-level controls to roll back one change. Use **Reset** carefully because it clears the complete Assets Manager rule set.

## What does Assets Manager do?

Classic Monks Assets Manager reduces WordPress page weight by conditionally unloading selected CSS and JavaScript assets from the frontend. It can target assets provided by plugins, the active theme, WordPress, or other detected sources, then apply the rule to one URL, all URLs, or a URL pattern.

This is useful when a plugin loads its assets site-wide even though only a few pages use the plugin. For example, you can keep a contact-form script on the contact page while preventing it from loading on unrelated blog posts. You can also review an asset's file size, handle, dependencies, and load status before deciding whether to disable it.

Assets Manager does not delete files, uninstall plugins, or automatically determine whether an asset is safe to remove. It changes whether selected frontend assets load for the visitor context covered by your rule. A successful optimization can reduce requests and page weight, but the result depends on the assets you disable and the rest of the page.

## When should you disable unused scripts and styles?

Use page-level asset control when a plugin or theme component is needed only in specific places. Common examples include:

- WooCommerce assets on standard blog posts and marketing pages.
- Contact-form assets on pages that do not contain a form.
- Booking, membership, event, or directory assets outside their relevant workflows.
- Page-builder, slider, or large theme assets that are loaded globally but used on only a small section of the site.

Do not disable an asset only because its filename looks unfamiliar or because it appears large. Review its dependencies and test the page where it is used.

## Recommendations before enabling Assets Manager

1. **Use staging first.** Asset rules can affect menus, forms, checkout, login flows, analytics, consent banners, and page builders.
2. **Record a baseline.** Test an important page before changing it, including visible features, console errors, and performance results.
3. **Start with Current URL.** A page-specific rule is safer than disabling an asset everywhere.
4. **Keep logged-in bypass enabled while editing.** Then plan a logged-out test because visitors may receive a different asset set.
5. **Clear caching layers.** Purge page, CDN, and browser caches when an old asset list continues to appear.

## How to enable Assets Manager in WordPress

### Step 1: Open the Performance settings

In the WordPress admin area, open **Classic Monks** settings and select the **Performance** tab.

### Step 2: Open Assets Manager

Select the **Assets Manager** subtab.

### Step 3: Enable the feature

Turn on **Enable Assets Manager**.

The related settings appear below the main toggle:

| Setting | What it controls |
|---|---|
| **Disable WordPress Emoji** | Removes WordPress emoji resources through the Assets Manager workflow. |
| **Disable For Logged-In Users** | Prevents Assets Manager from unloading assets for logged-in users. Keep this enabled while editing and testing. |
| **Show Non-Loaded Assets** | Shows assets that are not currently loaded, instead of only detected loaded assets. |
| **Hide Admin Bar Control** | Removes the Assets Manager entry from the frontend admin bar. |
| **Show Frontend Icon** | Adds a floating Assets Manager icon for administrators on the frontend. |

### Step 4: Save the settings

Click **Save Changes**. With Assets Manager enabled, its frontend panel can collect the current page's assets and apply saved rules.

## How to open the frontend Assets Manager panel

Open the page you want to optimize while logged in as an administrator. Use the **Assets Manager** control in the WordPress admin bar. If the admin-bar control is hidden, enable **Show Frontend Icon** in the settings and use the floating administrator-only icon instead.

The panel displays the current URL and detected content type. Its main tabs are:

- **Plugins**: assets and plugin-level controls grouped by plugin.
- **Theme**: styles and scripts supplied by the active theme.
- **Misc**: other detected assets that do not belong to the plugin or theme groups.
- **Disabled Assets**: existing rules and their scopes.

## How to disable an asset on one WordPress page

Start with a page-specific rule when you are unsure whether an asset is safe to unload.

1. Open the target URL on the frontend.
2. Open the **Assets Manager** panel.
3. Select **Plugins**, **Theme**, or **Misc**.
4. Find the asset you want to test.
5. Review its **Type**, **Asset Info**, **Size**, and **Loaded** status.
6. Check the **Requires** and **Depended on by** information when it is available.
7. Turn off the asset's status toggle.
8. Under **Where to disable**, select **Current URL**.
9. Click **Save** in the Assets Manager panel.
10. Reload the page in a logged-out or private browser session.

The panel shows the filename and WordPress handle, which helps identify the rule for rollback.

## How to disable an asset everywhere

Choose **Everywhere** only when the asset is not needed on any public frontend page. This is appropriate for a genuinely unused plugin component or a resource that is replaced by another implementation.

After selecting **Everywhere**, check the available **Exceptions**. You can restore the asset for the **Current URL** or for supported content types. This is safer than creating multiple unrelated rules when one global rule covers most of the site.

Global rules deserve a wider test. Check the homepage, blog, search, forms, checkout, and page templates that use the component.

## How to disable assets on matching URLs with Regex

Choose **Regex** when one rule needs to cover several URL patterns. The panel provides this example:

```text
(^\/contact$|^\/about-us$)
```

This pattern matches `/contact` and `/about-us`. Adapt the pattern to your site structure and test every matching URL before publishing it.

Regex rules are easy to broaden accidentally. Use **Current URL** first, then move to Regex after the page-specific behavior works.

## How to disable a plugin on a specific page

Assets Manager also exposes plugin-level controls in the **Plugins** tab. When a plugin is disabled, choose one of these scopes:

- **Current URL**: disable the plugin's frontend behavior on the page being viewed.
- **Everywhere**: disable it across the frontend.
- **Regex**: disable it for matching URL patterns.

Use plugin-level rules cautiously because they can affect several resources at once. If you only need to unload one file, use the individual asset control.

## How to verify that an asset was disabled safely

Do not rely only on the Assets Manager toggle. Verify both the optimization and the page behavior:

1. Open the page in a private browser window or while logged out.
2. Confirm the intended asset no longer appears in the browser's Network panel and check the console for errors.
3. Test navigation menus, forms, login flows, WooCommerce cart and checkout, and other interactive elements used on the page.
4. Check the page at mobile and desktop breakpoints.
5. Compare the page before and after with PageSpeed Insights, Lighthouse, or another performance tool.
6. Clear relevant caches before judging the final result.

A better performance score is not guaranteed by disabling an asset. The rule is successful only if it reduces unnecessary work without removing required functionality.

## How to roll back an Assets Manager rule

To restore one asset, open the same page and return its status toggle to enabled. If the asset was disabled everywhere or with Regex, remove that broader rule or add the required exception. Click **Save** and test again as a logged-out visitor.

Use the panel's **Reset** control with care. The implementation treats Reset as a complete Assets Manager reset, not merely an undo for the current row. It clears the saved asset and plugin rules, so export or record important rules before using it on a production site.

If the page remains broken after restoring the asset, clear caches, check the console, and review whether another related asset was also disabled.

## Troubleshooting

### The panel does not appear

Check that **Enable Assets Manager** is on and that either the admin-bar control or frontend icon is enabled. The panel is available to administrators, not ordinary visitors. If you are using a page builder, open the page outside its preview when testing frontend assets.

### The asset still loads after I disabled it

Verify that you are testing the same URL and scope saved in the rule. If **Disable For Logged-In Users** is enabled, logged-in users can continue to receive the normal asset set. Test privately while logged out, then clear page, CDN, and browser caches.

### The asset is not listed

Enable **Show Non-Loaded Assets** and reload the page. Also check the **Plugins**, **Theme**, and **Misc** tabs. An asset that is not enqueued on the current request may not appear in the default loaded-assets view.

### Disabling the asset broke the page

Restore the asset immediately, save the rule, clear caches, and retest. Review **Requires** and **Depended on by** before trying again. If the asset supports a form, cart, menu, page builder, analytics tool, or consent system, leave it enabled on the relevant pages.

### A Regex rule affects the wrong pages

Switch the asset back to **Current URL**, then test the pattern separately. Anchor the expression to the intended paths and include exceptions for pages that must keep the asset.

## Frequently Asked Questions

### Does Assets Manager delete scripts or styles from WordPress?

No. Assets Manager changes where selected frontend assets load; it does not delete files, uninstall plugins, or remove theme resources from the server.

### Can I disable a plugin's scripts on one WordPress page?

Yes. Open the plugin in the **Plugins** tab, turn off its status, choose **Current URL**, and save the rule. Test the page and any related workflow before applying a broader scope.

### Should I disable unused CSS and JavaScript everywhere?

Only when the asset is genuinely unnecessary across the entire public frontend. Start with **Current URL** and use **Everywhere** only after testing the pages and content types that may depend on it.

### Why does the asset still load for me after I disable it?

Logged-in users can be excluded from Assets Manager optimizations when **Disable For Logged-In Users** is enabled. Test in a private window while logged out, then clear caching layers if needed.

### What should I do if disabling an asset breaks a page?

Restore the asset or remove its rule, save the change, clear caches, and retest. Review its dependencies before creating a narrower Current URL rule or an exception.

## Technical background

WordPress plugins and themes enqueue scripts and styles with unique handles and dependencies. Assets Manager uses that information to show the current page's resources and unload selected frontend assets. See the official [`wp_enqueue_script()`](https://developer.wordpress.org/reference/functions/wp_enqueue_script/), [`wp_enqueue_style()`](https://developer.wordpress.org/reference/functions/wp_enqueue_style/), [`wp_dequeue_script()`](https://developer.wordpress.org/reference/functions/wp_dequeue_script/), and [`wp_dequeue_style()`](https://developer.wordpress.org/reference/functions/wp_dequeue_style/) references for the underlying WordPress concepts.

## Related Articles

- [How to disable WordPress emoji assets per page](performance-perf-disable-emoji-assets.md)
- [How to show non-loaded assets in Assets Manager](performance-perf-show-non-loaded-assets.md)
- [How to lazy load elements in WordPress](performance-perf-lazy-loading.md)

**Tested versions:** Classic Monks 2.1.0; WordPress tested up to 7.0.

<!-- schema: Article, TechArticle -->
<!-- schema: BreadcrumbList -->
