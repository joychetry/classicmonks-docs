---
title: "How to Configure Comments in Classic Monks: Feature Index | CM"
slug: comments
description: "Index of comment system overrides in Classic Monks. Each comment feature has its own dedicated guide with configuration, troubleshooting, and developer filters."
last_updated: 2026-06-24
author: Joy
reading_time: 2 min
canonical: https://classicmonks.com/docs/comments/
---

# How to Configure Comments in WordPress

> The Comment System Overrides section in Classic Monks Core groups five independent toggles that control how comments behave on your site. Each feature has its own dedicated guide.

## About This Index

This page is a directory of all comment system overrides in Classic Monks. Each feature is a toggle in the **Core > Content > Comment System Overrides** section, but each has its own documentation because the configuration, troubleshooting, and edge cases are different.

## Comment System Overrides

| Feature | Description | Guide |
|---------|-------------|-------|
| **Disable Comments** | Globally turn off the WordPress comment system on all post types. Hides comment forms and prevents new submissions. | [View guide](core-disable-comments.md) |
| **Allow Duplicate Comments** | Let the same user post multiple comments on the same post. Overrides WordPress's default duplicate block. | [View guide](core-allow-duplicate-comments.md) |
| **Disable Link in Comment and Disable Auto-linking** | Strip auto-linking and rendered link tags from comment text. | [View guide](core-disable-link-in-comments.md) |
| **Remove Comment URLs** | Remove the Website URL field from the comment form and strip the website link from comment meta. | [View guide](core-remove-comment-urls.md) |
| **HTML5 Comment Support** | Add HTML5 input types and validation attributes to the comment form. | [View guide](core-html5-comment-support.md) |

## Common Combinations

For a typical blog, the recommended comment setup is:

- **Disable Link in Comment**: ON (reduces comment spam)
- **Remove Comment URLs**: ON (eliminates the website field)
- **Disable Comments**: OFF (comments are enabled)
- **Allow Duplicate Comments**: OFF (default behavior)
- **HTML5 Comment Support**: ON (better mobile UX)

For a business site, the typical setup is:

- **Disable Comments**: ON (no public discussion)
- All other comment settings: irrelevant when comments are disabled

For a forum-style discussion site:

- **Allow Duplicate Comments**: ON (users reply to multiple comments)
- All other settings: defaults

## Related Articles

- [How to Manage Content in Classic Monks](core-content-management.md)
- [How to Use Logs in Classic Monks](core-logs.md)
- [How to Configure AI Advanced Settings in Classic Monks](../ai/ai-advanced.md)
