---
title: "How to Use the Performance Tab in Classic Monks: Feature Index | CM"
slug: performance
description: "Index of the Performance tab operational guides in Classic Monks. Covers WordPress optimizations, media, CDN, assets, lazy loading, intelligent preloading, and selective media preload."
last_updated: 2026-07-28
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/performance/
---

# How to Use the Performance Tab in Classic Monks: Feature Index

> The Performance tab groups operational guides for WordPress optimizations, media handling, CDN rewriting, asset control, lazy loading, intelligent preloading, and selective media preload.

## Key Takeaways

- Guides are grouped by the seven Performance subtabs
- Lazy Loading is one operational guide covering all of its controls
- Intelligent Preloading and Selective Media Preload are separate workflows
- Each guide includes setup, verification, troubleshooting, and developer notes
- Test performance changes while logged out and record before/after results

## WP Optimizations

The WP Optimizations subtab disables unnecessary WordPress features. 18 features.

| Feature | Description | Guide |
|---------|-------------|-------|
| Force HTTPS Links | Rewrite all internal links to HTTPS. | [View guide](performance/performance-perf-force-https.md) |
| Disable All Updates | Block all WordPress/plugin/theme updates. | [View guide](performance/performance-perf-disable-all-updates.md) |
| Disable Search Functionality | Remove the WordPress search feature. | [View guide](performance/performance-perf-disable-search.md) |
| Disable Google Fonts | Remove Google Fonts from the frontend. | [View guide](performance/performance-perf-disable-google-fonts.md) |
| Disable WordPress Font Library | Remove the WP 6.5+ font manager. | [View guide](performance/performance-perf-disable-font-library.md) |
| Disable Emojis | Remove the emoji script. | [View guide](performance/performance-perf-disable-emojis.md) |
| Disable Dashicons | Remove Dashicons from the frontend. | [View guide](performance/performance-perf-disable-dashicons.md) |
| Disable Embeds | Remove oEmbed functionality. | [View guide](performance/performance-perf-disable-embeds.md) |
| Remove jQuery Migrate | Remove the legacy jQuery compatibility script. | [View guide](performance/performance-perf-remove-jquery-migrate.md) |
| Disable WP Responsive Images | Disable WordPress responsive image handling. | [View guide](performance/performance-perf-disable-responsive-images.md) |
| Disable Google Maps | Remove Google Maps JavaScript. | [View guide](performance/performance-perf-disable-google-maps.md) |
| Remove RSD Link | Remove the RSD link from the head. | [View guide](performance/performance-perf-remove-rsd-link.md) |
| Remove Shortlink | Remove the WP shortlink from the head. | [View guide](performance/performance-perf-remove-shortlink.md) |
| Disable RSS Feeds | Disable RSS/Atom feed generation. | [View guide](performance/performance-perf-disable-rss-feeds.md) |
| Remove RSS Feed Links | Remove RSS feed link tags from the head. | [View guide](performance/performance-perf-remove-rss-feed-links.md) |
| Disable Self Pingbacks | Prevent self-pingbacks on self-links. | [View guide](performance/performance-perf-disable-self-pingbacks.md) |
| Disable Year/Month Folders | Flatten media upload directory structure. | [View guide](performance/performance-perf-disable-year-month-folders.md) |
| Enable Classic Widgets | Revert to the classic widget interface. | [View guide](performance/performance-perf-enable-classic-widgets.md) |

## Media Enhancements

The Media Enhancements subtab adds media management features. 19 features.

| Feature | Description | Guide |
|---------|-------------|-------|
| Secure Downloads | Signed, time-limited download links. | [View guide](performance/performance-perf-secure-downloads.md) |
| Image Converter | Convert between WebP, AVIF, JPEG, PNG. | [View guide](performance/performance-perf-image-converter.md) |
| Unused Media Checker | Find unused files in the Media Library. | [View guide](performance/performance-perf-unused-media.md) |
| Missing Media Checker | Find broken media references. | [View guide](performance/performance-perf-missing-media.md) |
| Media Trash | Trash deleted media (30-day recovery). | [View guide](performance/performance-perf-media-trash.md) |
| Delete Images by Dimensions | Remove specific image sizes. | [View guide](performance/performance-perf-delete-image-sizes.md) |
| Media Replacement | Replace files without breaking references. | [View guide](performance/performance-perf-media-replace.md) |
| SVG Support | Enable SVG uploads. | [View guide](performance/performance-perf-svg-support.md) |
| SVG Security Sanitization | Sanitize SVGs on upload. | [View guide](performance/performance-perf-svg-sanitization.md) |
| Bulk Media Download | Download multiple files as ZIP. | [View guide](performance/performance-perf-bulk-media-download.md) |
| Auto Resize Images | Resize uploaded images to max dimension. | [View guide](performance/performance-perf-auto-resize-images.md) |
| Skip Smaller Images | Don't upscale small images. | [View guide](performance/performance-perf-skip-smaller-images.md) |
| Media File Renaming | Rename files with auto-reference update. | [View guide](performance/performance-perf-media-file-renaming.md) |
| Media Duplicator | Duplicate files in the Media Library. | [View guide](performance/performance-perf-media-duplicator.md) |
| Media Library Infinite Scrolling | Infinite scroll in the Media Library. | [View guide](performance/performance-perf-media-infinite-scroll.md) |
| Media List View Default | Default to list view in Media Library. | [View guide](performance/performance-perf-media-list-view.md) |
| Clean Image Filenames | Auto-clean uploaded file names. | [View guide](performance/performance-perf-clean-filenames.md) |
| Disable Unnecessary Image Sizes | Disable specific image sizes. | [View guide](performance/performance-perf-disable-image-sizes.md) |
| Disable Big Image Size Threshold | Prevent WordPress from downsizing images. | [View guide](performance/performance-perf-disable-big-image-threshold.md) |

## CDN

The CDN subtab handles CDN configuration. 2 features.

| Feature | Description | Guide |
|---------|-------------|-------|
| CDN Rewrite | Rewrite media URLs to use CDN. | [View guide](performance/performance-perf-cdn-rewrite.md) |
| Disable CDN for Admin | Don't rewrite URLs for admins. | [View guide](performance/performance-perf-cdn-disable-admin.md) |

## Assets Manager

The Assets Manager subtab controls CSS and JS loading. 6 features.

| Feature | Description | Guide |
|---------|-------------|-------|
| Assets Manager | Control CSS/JS per page. | [View guide](performance/performance-perf-assets-manager.md) |
| Disable WordPress Emoji | Page-level emoji control. | [View guide](performance/performance-perf-disable-emoji-assets.md) |
| Disable for Admin | Don't disable assets for admins. | [View guide](performance/performance-perf-assets-manager-admin.md) |
| Show Non-Loaded Assets | Display disabled assets in admin bar. | [View guide](performance/performance-perf-show-non-loaded-assets.md) |
| Hide Admin Bar Panel | Hide the manager from admin bar. | [View guide](performance/performance-perf-hide-assets-manager-panel.md) |
| Show Frontend Icon | Show manager icon on frontend. | [View guide](performance/performance-perf-show-frontend-icon.md) |

## Lazy Loading

The Lazy Loading subtab contains one operational guide covering lazy loading, critical image protection, lazy rendering, negative loading, and off-screen unloading.

| Guide | Covers |
|---|---|
| [How to Enable Lazy Loading](performance/performance-perf-lazy-loading.md) | Images, iFrames, backgrounds, HTML5 videos, YouTube, native loading, thresholds, exclusions, critical images, fade-in, lazy rendering, negative loading, and unload controls |

## Monks Preloading

The Preloading subtab contains two separate operational workflows.

| Guide | Covers |
|---|---|
| [How to Enable Intelligent Preloading](performance/performance-perf-monks-preload.md) | Triggers, delays, request limits, ignore paths, mobile and slow connections, errors, memory, and bandwidth testing |
| [How to Use Selective Media Preload](performance/performance-perf-selective-media-preload.md) | Post-type scope, Media Preload Settings metabox, selected media, custom URLs, LCP testing, and preload limits |

## Common Combinations

- **Maximum performance**: WP Optimizations (all 18) + Lazy Loading (images + iFrames) + Assets Manager (disable unnecessary CSS/JS)
- **E-commerce performance**: CDN + Lazy Load Images + Preload Critical Images + Assets Manager
- **Blog performance**: Disable Emojis + Disable Dashicons + Lazy Load YouTube + Intelligent Preloading

## Subtab Index

- [WP Optimizations](performance/performance-perf-force-https.md) (18 features)
- [Media Enhancements](performance/performance-perf-secure-downloads.md) (19 features)
- [CDN](performance/performance-perf-cdn-rewrite.md) (2 features)
- [Assets Manager](performance/performance-perf-assets-manager.md) (6 features)
- [Lazy Loading](performance/performance-perf-lazy-loading.md) (one operational guide covering 17 feature controls)
- [Intelligent Preloading](performance/performance-perf-monks-preload.md)
- [Selective Media Preload](performance/performance-perf-selective-media-preload.md)

## Related Articles

- [How to Use the Security Tab in Classic Monks: Feature Index](security.md)
- [How to Use the Interface Tab in Classic Monks: Feature Index](interface.md)
- [How to Use the WooCommerce Tab in Classic Monks: Feature Index](woocommerce.md)
- [How to Use the Email Tab in Classic Monks: Feature Index](email.md)
