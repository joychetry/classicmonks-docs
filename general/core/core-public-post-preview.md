---
title: "How to Use Public Post Preview in Classic Monks | CM"
slug: public-post-preview
description: "Share unpublished posts with clients or reviewers via a secure, temporary URL in Classic Monks. Optional password protection, configurable expiry, no login required."
last_updated: 2026-06-24
author: Joy
reading_time: 6 min
canonical: https://classicmonks.com/docs/public-post-preview/
---

# How to Use Public Post Preview in WordPress

> Public Post Preview generates a secure, temporary URL that lets external collaborators view unpublished posts without a WordPress login. Optional password protection and configurable expiry add control over who can see what, and for how long.

## Key Takeaways

- Secure, hard-to-guess preview URLs for unpublished content
- Optional global password protects all previews site-wide
- Configurable expiry (1-30 days) prevents stale links from working forever
- Per-post-type mode (only-on, except-on, or all-post-types)
- No WordPress account required for the reviewer (just the URL + optional password)

## What Is Public Post Preview?

Public Post Preview is a Classic Monks feature that adds a "Public Preview" link to the post edit screen's Publish meta box. Clicking the link generates a unique, signed URL that anyone can use to view the post, even if the post is in draft, pending review, or scheduled for the future. The URL contains a cryptographic token tied to the specific post, so it's hard to guess or share accidentally.

## Why You Need It

WordPress's default workflow for sharing unpublished content is awkward:

- **Create a user account** for the reviewer (security risk, account management overhead)
- **Make the post public** temporarily (exposes it to the public at large)
- **Use a staging site** (extra infrastructure, copy the post manually)
- **Email screenshots** (no interactivity, can't see draft autosaves)

Public Post Preview solves this by generating a secure, time-limited URL that anyone with the link can use. The reviewer sees the post exactly as it would appear when published, with full interactivity (links, forms, etc.), but no one else can find the URL.

---

## How to Use Public Post Preview in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Content Subtab

Click on the **Core** menu, then click the **Content** subtab.

### Step 3: Enable Public Post Preview

Scroll to the **Editorial Workflow** section and toggle on **Public Post Preview**. Nested options expand below the toggle.

### Step 4: Choose a Mode

Pick the **Mode** from the dropdown:

- **Enable only on selected**: Public Preview is available only on checked post types
- **Enable except on selected**: Public Preview is available on all post types except checked ones
- **Enable on all post types**: Public Preview is available on every public post type

### Step 5: Select the Post Types

A list of every public post type appears. Check the ones you want to enable Public Preview for. Uncheck the ones that should never be shareable as previews (e.g., WooCommerce orders, private post types).

### Step 6: (Optional) Enable Global Password Protection

Toggle on **Enable Global Password Protection** if you want to require a single password for ALL public previews on the site. This is useful when sharing drafts with multiple clients and you want a single password that's easy to communicate.

### Step 7: (If Enabled) Set the Global Password

Enter a strong password in the **Global Preview Password** field. Share this password with reviewers via a separate channel (not in the same email as the preview URL).

### Step 8: Set the Link Expiry

Enter the number of days (1-30) in the **Preview Link Expiry** field. The default is 3 days. The link stops working after this period, so reviewers who bookmark it will be locked out, set this to a value that matches your typical review cycle.

### Step 9: Save Changes

Click **Save Changes**.

### Step 10: Generate a Preview Link for a Post

Open any post edit screen. In the right sidebar's Publish meta box, find the new **Public Preview** section. Click the link/button to copy the preview URL to your clipboard.

The URL is a long string that includes the post ID and a cryptographic token. Share this URL (and the global password, if enabled) with the reviewer.

### Step 11: Reviewer Accesses the Preview

The reviewer opens the URL in any browser. They see the post exactly as it will appear when published, with all your content, formatting, custom fields, and dynamic data. If global password is enabled, they're prompted for the password before seeing the content.

The URL works until the expiry date. After that, accessing the URL shows a "Preview link expired" message.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Public Post Preview** | Master toggle. Enables the preview link. | Off |
| **Mode** | `only-on`, `except-on`, or `all-post-types`. | `only-on` |
| **Post Type Checkboxes** | Per-post-type control. | None checked |
| **Enable Global Password Protection** | Require a password for all previews. | Off |
| **Global Preview Password** | The password reviewers must enter. | Empty |
| **Preview Link Expiry** | Days until the link stops working (1-30). | 3 |

---

## Security Model

The preview URL contains three components:

1. **The post ID** (so the server knows which post to render)
2. **A cryptographic token** (so the server can verify the URL is authentic)
3. **An expiry timestamp** (so the server can reject expired links)

The token is generated using WordPress's `wp_generate_password()` and stored in the post meta. When a request hits the preview URL, the server validates the token against the stored value and the expiry timestamp. If either fails, the request is rejected with a generic "Preview link expired or invalid" message (no information leak about which check failed).

Even if a reviewer shares the URL, the token is unique per post. Reusing a token for a different post fails. Brute-forcing tokens is computationally infeasible (the token space is 32+ characters of random data).

---

## Developer Notes

Public Post Preview generates a secure, time-limited URL for unpublished posts. No developer hooks are currently exposed.

**Options used:**
| Option | Type | Default |
|--------|------|---------|
| `enable_public_post_preview` | Boolean | `false` |

The preview logic is in `functions/core/content/public-preview.php`.
---

## Troubleshooting

### The preview URL returns "Preview link expired or invalid"

**Cause:** The expiry date has passed, the token was regenerated (e.g., if the post was updated significantly and the token was refreshed), or the URL was truncated when shared.
**Fix:** Generate a new preview URL from the post edit screen. Verify the full URL was shared (no line breaks, no truncation by email clients). If the issue persists, the token store may be corrupted; deactivating and reactivating Classic Monks rebuilds the preview meta.

### The reviewer can see the post but some dynamic data is missing

**Cause:** Some plugins render content via AJAX or shortcodes that don't fully execute in preview mode (e.g., a contact form's submission handler).
**Fix:** This is expected. Preview URLs render the post content but may not trigger server-side actions like form submissions. The reviewer can see the form's appearance, but submitting the form may not work. Use a staging site for fully interactive previews.

### The global password is being asked for but the reviewer doesn't know it

**Cause:** The password was shared through a different channel than the URL, or the reviewer is using a different password manager.
**Fix:** Re-share the password. Use a password manager with shared vaults (1Password, Bitwarden) for client sharing.

### The preview works for some posts but not others

**Cause:** The post type may not be in the enabled list, or the preview meta was never created for older posts.
**Fix:** Verify the post type is enabled in the mode dropdown. For older posts, open the post and click the Public Preview button once to generate the token. The token is created on first use, not on post save.

### The preview URL is being flagged as suspicious by email providers

**Cause:** The long token in the URL triggers spam filters in some email clients (e.g., Gmail sometimes flags URLs with long random strings).
**Fix:** Share the URL via a non-email channel (Slack, a shared doc, a private repo). Or use a URL shortener (though this adds a third-party dependency).

---

## Related Articles

- [How to Use Content Management in Classic Monks](core-content-management.md)
- [How to Use Content Duplication in Classic Monks](core-content-duplication.md)
- [How to Add Code Snippets in WordPress (PHP, CSS, JS)](../code-manager.md)
