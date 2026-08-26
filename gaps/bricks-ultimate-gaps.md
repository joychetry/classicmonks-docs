---
type: comparison-alternative
status: draft
primary_keyword: "Classic Monks vs Bricks Ultimate"
secondary_keywords:
  - "Bricks Ultimate alternative"
  - "What Bricks Ultimate doesn't have"
  - "Bricks Ultimate vs Classic Monks"
  - "WordPress plugin for Bricks Builder"
  - "Bricks addon comparison"
seo_title: "Classic Monks vs Bricks Ultimate: What Bricks Ultimate Lacks"
meta_description: "Bricks Ultimate owns Bricks storefront layout. Classic Monks adds site-wide performance, security, store operations, and white label beyond Bricks elements."
slug: classic-monks-vs-bricks-ultimate-what-bricks-ultimate-does-not-have
date: 2026-08-17
last_updated: 2026-08-17
author: "Joy Chetry"
recommended_schema:
  - BlogPosting
  - FAQPage
internal_links:
  - "/best-all-in-one-wordpress-plugins/"
  - "/pricing/"
  - "/features/"
  - "/demo/"
  - "/bricks-builder-elements/"
  - "/docs/classic-monks-vs-bricks-ultimate/"
---

# Classic Monks vs Bricks Ultimate: What Bricks Ultimate Doesn't Have

This **Classic Monks vs Bricks Ultimate** comparison looks at what Classic Monks adds beyond Bricks Ultimate, including site-wide performance, security, WooCommerce operations, white label, AI, admin tools, and builder-agnostic coverage.

We compared the official Bricks Ultimate feature and pricing pages with the live Classic Monks feature and pricing pages, the current Classic Monks changelog, and the local feature references used to verify implementation scope. The comparison reflects the August 17, 2026 feature set.

**How we selected the differences:** We included a category when the current Bricks Ultimate feature list does not represent a comparable workflow and Classic Monks has a documented, implemented capability. We kept material limitations visible where Bricks Ultimate still owns a workflow or where the products take different approaches.

The better question is: **What can Classic Monks add to a WordPress site that is outside Bricks Ultimate's current feature set?**

Bricks Ultimate (official name BricksUltimate, at bricksultimate.com) is a premium add-on that only works with Bricks Builder, and it is heavily focused on WooCommerce storefront elements: 35 general elements, 32 WooCommerce elements, 28 Query Loop Providers, and a large dynamic tag set. Classic Monks is a WordPress-wide stack with 162 features for Bricks Builder plus security, performance, WooCommerce operations, admin tools, media, AI, and white label. The official Classic Monks features library currently lists **393+ features**.

Bricks Ultimate remains a strong Bricks-only storefront tool, and its element catalog is its reason to exist. This post focuses on the other side of the decision: the capabilities you gain when Classic Monks becomes your core WordPress stack.

> **Quick verdict:** Choose Classic Monks when you manage client sites and want one plugin to cover Bricks features plus site-wide performance, security, store operations, admin cleanup, AI, and white label. Keep Bricks Ultimate, or run both during migration, when you depend on its specific elements, such as the checkout builder, mini cart builder, order bumps, form stylers, or ACF and Metabox loop providers.
>
> **Context:** This deep-dive is one spoke of the [Best All-in-One WordPress Plugins in 2026](https://classicmonks.com/best-all-in-one-wordpress-plugins/) hub, which compares Classic Monks and Bricks Ultimate alongside ASE, WP Extended, Jetpack, and Perfmatters.
>
> **Low-risk next step:** Explore the full stack in the [zero-install Classic Monks demo](https://classicmonks.com/demo/), then compare the [current pricing](https://classicmonks.com/pricing/) once you know which categories matter to your sites.

## What does Classic Monks have that Bricks Ultimate does not?

The clearest difference is scope. Bricks Ultimate is an element pack for one builder. Classic Monks includes a builder layer, then extends into the rest of the WordPress stack.

| Capability area | Classic Monks | Bricks Ultimate's current feature list | Why it matters |
| --- | --- | --- | --- |
| Site-wide performance | Performance tab: Assets Manager, CDN Rewrite, lazy loading, preloading, image conversion, and Bricks CSS minification | Not in scope; element and storefront tools only | The performance layer is separate with Bricks Ultimate |
| Security | Full security tab: login lockdown, 2FA, CAPTCHA, content protection, and Staging Protection | No security features | No hardening in an element pack |
| WooCommerce operations | Store tab: swatches, checkout controls, coupons, BOGO deals, order tools, redirects, and email controls | Storefront layout elements: checkout builder, mini cart builder, order bumps, applied coupons | Bricks Ultimate builds store layout; Classic Monks runs the store |
| White label | Enterprise plan: rebrand the plugin, hide it from the plugins list, priority support | Only on the $699 Unlimited tier, and only for the add-on itself | White label below the top tier requires Classic Monks |
| AI inside WordPress | AI Agent, AI Tools, Bricks AI Builder, image generation and editing, alt-text generation | No AI feature category listed | No AI workflow is represented in Bricks Ultimate |
| Admin and media | Admin menu, toolbar, notices, columns, dashboard cleanup, Folder Manager, image conversion | Not in scope | Outside an element pack |
| New-site setup and staging | Quick WordPress Setup, Bricks setup workflow, Staging Protection | No setup or staging tools | Client onboarding and staging access are outside Bricks Ultimate |
| Works without Bricks | Builder-agnostic; modules stay active on Gutenberg, Elementor, Breakdance, or plain WordPress | Requires Bricks Builder to function at all | One plugin can serve non-Bricks client sites too |

The table is a category comparison, not a claim that every individual Bricks Ultimate element has a Classic Monks equivalent. For the module-by-module parity review, see the [full Classic Monks vs Bricks Ultimate comparison](https://classicmonks.com/docs/classic-monks-vs-bricks-ultimate/).

## Does Classic Monks offer site-wide performance that Bricks Ultimate does not?

Bricks Ultimate is not a performance plugin. It optimizes elements inside the builder, but it does not manage site-wide loading behavior.

Classic Monks includes a Performance tab with asset and loading controls:

* Assets Manager for conditionally disabling scripts and styles
* CDN Rewrite for selected site directories
* Lazy loading for images, iframes, background images, videos, and YouTube embeds
* Critical-image preloading and intelligent page preloading based on navigation behavior
* Image conversion to WebP and AVIF
* Bricks asset disabling and CSS minification
* Controls for emojis, Dashicons, Google Fonts, embeds, jQuery Migrate, RSS, and other WordPress output

This is not a claim that Classic Monks replaces every caching product. It does not provide full-page caching, and you should keep a proper caching or hosting layer where the site needs one. For a Bricks agency, Classic Monks covers the optimization layer around the builder instead of assembling a separate performance stack.

See the [Classic Monks Assets Manager documentation](https://classicmonks.com/docs/perf-assets-manager/).

## Does Classic Monks include security features that Bricks Ultimate does not?

Yes. Bricks Ultimate ships no security features, because security is outside an element pack's job.

Classic Monks includes a full security tab with 39 per-feature docs:

* Custom login URL, login lockdown with extended lockout, Cloudflare Turnstile, and math CAPTCHA
* 2FA with TOTP authenticator app and email OTP, trusted devices, and 2FA rate limiting
* Auto logout, user-enumeration blocking, REST API and XML-RPC controls, and file-modification controls
* Email and phone protection, site-wide password protection, and AI crawler blocking
* Content protection for copying, selection, printing, and inspection
* Staging Protection with access tokens, HTTP authentication, and IP allowlists

Read the [WordPress security documentation](https://classicmonks.com/docs/security/) for the current list.

## What does Classic Monks add for WooCommerce beyond Bricks Ultimate's elements?

This is where the two products differ most clearly. Bricks Ultimate builds storefront layout inside Bricks: checkout builder, mini cart builder, order bumps, applied coupons, cart counter, thank you page, and swatches for loop. Those are display and offer elements.

Classic Monks runs the store on top of the layout:

* Product swatches for colors, images, and labels
* Checkout field cleanup, placeholders, inline validation, and custom order headings
* Direct checkout links and a checkout product selector
* URL coupons, automatic coupon application, BOGO deals, and role-based restrictions
* Custom order statuses, order-table columns, and product price history
* Redirects for cart, login, logout, and My Account workflows
* WooCommerce script and style controls on non-store pages, plus cart-fragmentation controls
* Store email controls

A Bricks store typically needs both layers: layout elements and store operations. Bricks Ultimate covers the first. Classic Monks covers the second and adds the builder layer of its own. Read the [WooCommerce documentation](https://classicmonks.com/docs/woocommerce/) for the current store feature set.

## Is white label available below Bricks Ultimate's top tier?

Only on the $699 Unlimited tier, and it applies to the add-on itself. The $49, $79, $109, $149, and $249 tiers do not include white label, and the separate WooCommerce plugins (Buy X Get Y Pro, Bought Together, Product Add-Ons) are included only on the Unlimited tier.

Classic Monks includes white-label plugin capability on the Enterprise plan, with rebranding, plugin hiding, client license expiry controls, 6-hour priority support, and priority feature requests. For an agency that wants a branded client-facing stack, the ordering flips: Classic Monks Enterprise LTD is $599 one-time for unlimited sites with white label, while Bricks Ultimate Unlimited is $699 one-time for the add-on plus a required Bricks license.

The white-label plugin capability should not be treated as included in every Classic Monks plan. It is an Enterprise benefit.

## Does Classic Monks work without Bricks Builder?

Yes. Classic Monks is builder-agnostic. Its Bricks features activate only when Bricks is installed, and its admin, security, performance, WooCommerce, media, and setup modules stay active on Gutenberg, Elementor, Breakdance, or plain WordPress sites.

Bricks Ultimate does nothing outside Bricks. It requires the Bricks Builder theme, WordPress 6.0+, and PHP 8.0.x+, per its official site.

That matters for an agency with a mixed portfolio. One Classic Monks license can serve Bricks projects and non-Bricks projects, while a Bricks Ultimate license only helps the Bricks sites.

## What else does Classic Monks add for agencies?

Beyond the categories above, Classic Monks bundles tools that have no counterpart in an element pack:

* AI inside WordPress: AI Agent chat overlay, AI content and management workflows, alt-text generation, image generation and editing, and Bricks AI Builder for HTML-to-Bricks conversion
* Admin tools: Admin Menu Manager, Top Toolbar Manager, Admin Notices Manager, dashboard cleanup, content duplication, post type and taxonomy switchers, and Form Desk
* Media: Image Converter for WebP and AVIF, watermarks, media replacement, folder management, and bulk downloads
* Setup: Quick WordPress Setup for fresh sites and a separate Bricks setup workflow
* Code Manager with PHP, JavaScript, CSS, and HTML support, syntax validation, safe mode, and fatal-error recovery
* Email controls, staging protection, settings export and import, and Multisite support

Read the [Classic Monks AI feature guide](https://classicmonks.com/docs/ai-features-master/) and the [Bricks Builder documentation](https://classicmonks.com/docs/bricks/) for the current builder feature set.

## What does Bricks Ultimate still own that Classic Monks does not?

This is where the comparison stays honest. Bricks Ultimate is the deeper Bricks-native storefront tool, and its element catalog is its reason to exist.

* **WooCommerce storefront elements.** Checkout Builder, Mini Cart Builder, Order Bumps, Applied Coupons, Cart Counter, Cart Content, My Account Navigation, Thank You Page builder, Free Shipping Notice, Purchasable badges, Linked Variations, and Swatches for Loop. Classic Monks has WooCommerce elements and store operations, but not a visual checkout builder, mini cart builder, or order bump element.
* **Query Loop Providers.** 28 providers covering ACF checkboxes, galleries, and post objects, Metabox galleries, relationships, and checkboxes, custom WP queries, product lists (best selling, featured, on sale, top rated, related, cross-sells, upsells, recently viewed), customer orders, wishlist items, and compare items. Classic Monks has query elements for comments, reviews, product gallery, menu, recently viewed, and wishlist, but not this provider list.
* **Form stylers.** Dedicated styling elements for Contact Form 7, Gravity Forms, Fluent Forms, Piotnet Forms, WPForms, WS Forms, and WPGB Facets. Classic Monks manages form submissions through Form Desk, but does not style third-party form plugins.
* **General elements Classic Monks does not ship.** AJAX Popup Builder, Off Canvas, Sliding Menu, Accordion Menu, Business Hours, Highlighted Heading, Dual Color Text, Reading Progress Bar, Flex Gallery, and Slim Gallery. Classic Monks ships an overlapping set, but not these specific elements.
* **WooCommerce dynamic tags.** Bricks Ultimate lists roughly 95 WooCommerce dynamic tags plus 34 general tags. Classic Monks covers WordPress, media, taxonomy, menu, comments, reviews, and WooCommerce tags, but not this full WooCommerce tag list.
* **Themes and pricing entry.** Bricks Ultimate ships a Bricks child theme (Brucart) for WooCommerce, and its 1-domain license at $49 one-time is a cheap entry for a Bricks-only shop.

The cleanest way to read it: if a site needs a specific Bricks Ultimate element, Bricks Ultimate is the tool that has it.

## Should you switch from Bricks Ultimate to Classic Monks?

Use this decision rule:

* **Choose Classic Monks** if you manage client sites and want one license to cover Bricks features plus site-wide performance, security, store operations, admin tools, AI, and white label.
* **Keep Bricks Ultimate** if you run Bricks-only sites and need its specific elements: checkout builder, mini cart builder, order bumps, form stylers, or the ACF and Metabox loop providers.
* **Use both during migration** if Classic Monks is the operating stack and Bricks Ultimate's specific elements earn their keep. These two coexist more easily than most add-on pairs, because their overlap is element-level rather than global settings.

Migration is partial in both directions, so do it on staging:

1. List every Bricks Ultimate element and provider used in your templates, per template.
2. Map each to a Classic Monks feature where one exists: swatches, BOGO deals, wishlist, recently viewed, tables, image compare, countdown, star ratings, breadcrumbs, back to top, buy now, reviews, and comments and product queries.
3. List the elements with no Classic Monks counterpart: checkout builder, mini cart builder, order bumps, applied coupons, form stylers, AJAX popup, off canvas, accordion menu, sliding menu, business hours, and the ACF and Metabox loop providers.
4. Decide per gap: keep Bricks Ultimate for the gaps, or rebuild those templates with Bricks elements plus Classic Monks conditions and dynamic data.
5. Test on staging: builder editing, front-end output, WooCommerce checkout, wishlist and compare behavior, and forms.
6. Remove Bricks Ultimate elements from templates only after Classic Monks coverage verifies in the builder.
7. Keep Bricks Ultimate active until the soak period passes on live sites.

Classic Monks pricing currently includes Yearly plans from **$39 for one site** to **$299 for unlimited sites**, plus Lifetime plans at **$299 for 100 sites** and **$599 for unlimited sites**. Bricks Ultimate is a one-time purchase by domain count: **$49 for 1 domain**, **$79 for 10**, **$109 for 20**, **$149 for 50**, **$249 for 100**, and **$699 for unlimited** with lifetime updates and support, with white label and its WooCommerce plugins included only on the Unlimited tier. Bricks Ultimate also requires a Bricks license to function. All Classic Monks plans include the core feature library. Enterprise-only white-label and priority-support benefits remain plan-specific. Check the [current Classic Monks pricing](https://classicmonks.com/pricing/) before buying because pricing and plan contents can change.

## Final verdict

Bricks Ultimate is a strong Bricks-only storefront add-on, and its element catalog is genuinely deep. Classic Monks covers much of the builder territory, but its larger advantage is what sits outside the Bricks Ultimate model: site-wide performance, security, WooCommerce operations, AI, admin tools, media, setup, staging, and white label.

If those are the tools you need, Classic Monks is not just a Bricks Ultimate alternative. It is a broader core stack that can replace several categories of plugins around Bricks Ultimate's original job.

Start with the elements your templates actually use, test on staging, and move the site to Classic Monks when the real workflows pass. Keep Bricks Ultimate for the elements Classic Monks does not ship.

[Try the Classic Monks demo](https://classicmonks.com/demo/)  
 [Browse the Classic Monks feature library](https://classicmonks.com/features/)  
 [Check Classic Monks pricing](https://classicmonks.com/pricing/)  
 [Read the full Classic Monks vs Bricks Ultimate comparison](https://classicmonks.com/docs/classic-monks-vs-bricks-ultimate/)  
 [Read the best all-in-one WordPress plugins guide](https://classicmonks.com/best-all-in-one-wordpress-plugins/)

## Frequently Asked Questions

### Is Classic Monks better than Bricks Ultimate?

Classic Monks is better for agencies that want Bricks features plus site-wide performance, security, store operations, admin tools, AI, and white label in one plugin. Bricks Ultimate is better for Bricks-only storefront layout, especially checkout builder, mini cart builder, order bumps, form stylers, and ACF or Metabox loop providers.

### Can Classic Monks replace Bricks Ultimate?

Partially. Classic Monks covers many common Bricks element needs, WooCommerce swatches and BOGO deals, wishlist and recently viewed queries, and adds the WordPress stack beyond the builder. It does not ship checkout builder, mini cart builder, order bumps, form stylers, AJAX popup, off canvas, or the ACF and Metabox loop providers. Keep Bricks Ultimate where those matter.

### Does Bricks Ultimate include white label?

Only on the $699 Unlimited tier, and it applies to the add-on itself. Classic Monks includes white label on Enterprise (yearly or LTD), along with hiding the plugin from the plugins list, client license expiry controls, priority support, and priority feature requests.

### Does Classic Monks work without Bricks Builder?

Yes. Classic Monks is builder-agnostic and works with Gutenberg, Elementor, Breakdance, and plain WordPress. Bricks features activate only when Bricks is installed. Bricks Ultimate requires the Bricks Builder theme and does nothing outside Bricks.

### Can I use Classic Monks and Bricks Ultimate together?

Yes. They are different layers of Bricks and do not conflict. Avoid using both for the same job: pick one owner for swatches, wishlist, compare, countdowns, tables, image compare, and BOGO tools.

### Which is better for a WooCommerce store built in Bricks?

Bricks Ultimate for storefront layout: checkout builder, mini cart, order bumps, applied coupons, cart counter, and swatches for loop. Classic Monks for store operations on top of that: coupons, BOGO deals, checkout fields, order tools, redirects, plus security and performance around the store.

### Is Bricks Ultimate cheaper than Classic Monks?

For a Bricks-only shop, Bricks Ultimate starts at $49 one-time for one domain. For an agency at the top end, the order flips: Bricks Ultimate Unlimited is $699 one-time plus a required Bricks license, while Classic Monks Enterprise LTD is $599 one-time for unlimited sites with white label and the whole stack.

## Recommended schema

Implement `BlogPosting` (headline, dates, author, publisher) and `FAQPage` (the FAQ Q&A pairs as `mainEntity`). Google retired the FAQ rich result in May 2026, so FAQPage will not produce a Google SERP feature, but it still helps Bing, Perplexity, and RAG crawlers when the publishing layer emits it. Validate in Google Rich Results Test after publishing. JSON-LD draft below.

*Note: when the author page from 06-author-page.md is published, set `author.url` in the JSON-LD to that page. The interim value points at the live /about-us/ page.*

## Internal links

- Best All-in-One WordPress Plugins in 2026: [/best-all-in-one-wordpress-plugins/](https://classicmonks.com/best-all-in-one-wordpress-plugins/)
- Classic Monks pricing: [/pricing/](https://classicmonks.com/pricing/)
- Classic Monks features: [/features/](https://classicmonks.com/features/)
- Try the demo: [/demo/](https://classicmonks.com/demo/)
- Bricks Builder elements (live): [/bricks-builder-elements/](https://classicmonks.com/bricks-builder-elements/)
- Full comparison (publish-order dependency, not live yet): [/docs/classic-monks-vs-bricks-ultimate/](https://classicmonks.com/docs/classic-monks-vs-bricks-ultimate/)

## Source verification

- Bricks Ultimate site (bricksultimate.com), verified 2026-08-17: 35 general elements, 32 WooCommerce elements, 28 Query Loop Providers, 34 general and roughly 95 WooCommerce dynamic tags, conditions, interactions, Brucart child theme, requires Bricks Builder with WordPress 6.0+ and PHP 8.0.x+.
- Bricks Ultimate pricing on the official site, verified 2026-08-17: one-time $49 (1 domain), $79 (10), $109 (20), $149 (50), $249 (100), $699 (unlimited, includes Buy X Get Y Pro, Bought Together, Product Add-Ons, White Label). 7-day refunds, PayPal, client sites allowed.
- Classic Monks pricing page (classicmonks.com/pricing), verified 2026-08-17: yearly $39 / $119 / $199 / $299; LTD $299 (100 sites) / $599 (unlimited).
- Classic Monks features page (classicmonks.com/features) for the 393+ features and 162 Bricks Builder features, verified 2026-08-17.
- Classic Monks bricks-builder-elements page, verified live 2026-08-17: 30+ elements, 7 categories.
- Classic Monks security, WooCommerce, Bricks, AI, and performance docs, verified live 2026-08-17.
- Classic Monks feature inventory (docs/features-docs/cm-features-parent.md) for feature names in the Bricks Builder, Security, WooCommerce, Performance, and White Label tabs.

Last updated: August 17, 2026.

## JSON-LD (ready to paste into the page head or body via the SEO plugin)

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "BlogPosting",
      "headline": "Classic Monks vs Bricks Ultimate: What Bricks Ultimate Doesn't Have",
      "description": "Bricks Ultimate owns Bricks storefront layout. Classic Monks adds site-wide performance, security, store operations, and white label beyond Bricks elements.",
      "datePublished": "2026-08-17",
      "dateModified": "2026-08-17",
      "author": {
        "@type": "Person",
        "name": "Joy Chetry",
        "url": "https://classicmonks.com/about-us/"
      },
      "publisher": {
        "@type": "Organization",
        "name": "Classic Monks",
        "url": "https://classicmonks.com/",
        "logo": {
          "@type": "ImageObject",
          "url": "https://classicmonks.com/wp-content/uploads/2025/05/classicmonks-logo.svg"
        }
      },
      "mainEntityOfPage": "https://classicmonks.com/docs/classic-monks-vs-bricks-ultimate-what-bricks-ultimate-does-not-have/"
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        {
          "@type": "Question",
          "name": "Is Classic Monks better than Bricks Ultimate?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "Classic Monks is better for agencies that want Bricks features plus site-wide performance, security, store operations, admin tools, AI, and white label in one plugin. Bricks Ultimate is better for Bricks-only storefront layout, especially checkout builder, mini cart builder, order bumps, form stylers, and ACF or Metabox loop providers."
          }
        },
        {
          "@type": "Question",
          "name": "Can Classic Monks replace Bricks Ultimate?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "Partially. Classic Monks covers many common Bricks element needs, WooCommerce swatches and BOGO deals, wishlist and recently viewed queries, and adds the WordPress stack beyond the builder. It does not ship checkout builder, mini cart builder, order bumps, form stylers, AJAX popup, off canvas, or the ACF and Metabox loop providers. Keep Bricks Ultimate where those matter."
          }
        },
        {
          "@type": "Question",
          "name": "Does Bricks Ultimate include white label?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "Only on the $699 Unlimited tier, and it applies to the add-on itself. Classic Monks includes white label on Enterprise (yearly or LTD), along with hiding the plugin from the plugins list, client license expiry controls, priority support, and priority feature requests."
          }
        },
        {
          "@type": "Question",
          "name": "Does Classic Monks work without Bricks Builder?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "Yes. Classic Monks is builder-agnostic and works with Gutenberg, Elementor, Breakdance, and plain WordPress. Bricks features activate only when Bricks is installed. Bricks Ultimate requires the Bricks Builder theme and does nothing outside Bricks."
          }
        },
        {
          "@type": "Question",
          "name": "Can I use Classic Monks and Bricks Ultimate together?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "Yes. They are different layers of Bricks and do not conflict. Avoid using both for the same job: pick one owner for swatches, wishlist, compare, countdowns, tables, image compare, and BOGO tools."
          }
        },
        {
          "@type": "Question",
          "name": "Which is better for a WooCommerce store built in Bricks?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "Bricks Ultimate for storefront layout: checkout builder, mini cart, order bumps, applied coupons, cart counter, and swatches for loop. Classic Monks for store operations on top of that: coupons, BOGO deals, checkout fields, order tools, redirects, plus security and performance around the store."
          }
        },
        {
          "@type": "Question",
          "name": "Is Bricks Ultimate cheaper than Classic Monks?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "For a Bricks-only shop, Bricks Ultimate starts at $49 one-time for one domain. For an agency at the top end, the order flips: Bricks Ultimate Unlimited is $699 one-time plus a required Bricks license, while Classic Monks Enterprise LTD is $599 one-time for unlimited sites with white label and the whole stack."
          }
        }
      ]
    }
  ]
}
```

## Update history

- **2026-08-17:** first draft of the negative-space conversion page (A6bn). Prices and feature scope verified against official Bricks Ultimate and Classic Monks pages on the same date.
