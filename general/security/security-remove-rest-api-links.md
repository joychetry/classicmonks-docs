---
title: "How to Remove REST API Links in WordPress | CM"
slug: security/remove-rest-api-links
description: "Remove REST API links from the WordPress head to prevent users enumeration. Disables the link tag that exposes the API endpoint and other version information."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/security/remove-rest-api-links/
---

# How to Remove REST API Links in WordPress

> Remove REST API Links in Classic Monks strips the REST API link tag from your WordPress head. Prevents users enumeration and reduces the information exposed to potential attackers.

## Key Takeaways

- Single toggle, no nested options
- Removes the `<link rel="https://api.w.org/">` tag from the page head
- Prevents users enumeration (via the `/wp-json/wp/v2/users` endpoint)
- Reduces the information exposed to potential attackers
- Doesn't disable the REST API itself (only the discovery link)

## What Is the Remove REST API Links feature?

WordPress's REST API is enabled by default, and WordPress automatically adds a `<link>` tag to the page head that points to the API endpoint:

```html
<link rel="https://api.w.org/" href="https://example.com/wp-json/" />
```

This link makes it easy for tools and apps to discover the API. But it also tells attackers:

- That the site is WordPress
- The exact API endpoint URL
- That the API is enabled and accepting requests

The Remove REST API Links feature strips this discovery link. The REST API itself is not disabled (apps that know the URL can still use it), but the auto-discovery is removed.

## Why You Need It

The default REST API link tag is a small but real security risk:

- **Users enumeration**: Attackers can hit `/wp-json/wp/v2/users` to list all users
- **Plugin enumeration**: The API exposes which plugins are installed
- **Version disclosure**: The API may include the WordPress version
- **Reconnaissance**: Attackers can use the API to gather information about your site

Removing the discovery link is a quick, low-risk hardening step.

---

## How to Remove REST API Links in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **WP Protection** subtab.

### Step 3: Enable Remove REST API Links

Scroll to **Remove REST API Links** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

View the page source of any page on your site. The `<link rel="https://api.w.org/">` tag should not be present. The REST API itself should still work (test by visiting `/wp-json/` directly).

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Remove REST API Links** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- The page head: the REST API discovery link is removed
- The page source: the link tag is no longer visible
- Browser auto-discovery: tools that use the link tag to find the API will need the URL

## What Does NOT Get Affected

- The REST API itself: still accessible at `/wp-json/`
- The Gutenberg editor: still uses the REST API
- Apps that already know the API URL: still work
- The WordPress admin: not affected

---

## Advanced Options (Developers)

This feature registers 2 WordPress hooks in `rest-api.php`:

**Actions:**

- `init` calls `cm_disable_rest_api()` (Conditionally restricts REST API access)

**Filters:**

- `rest_authentication_errors` calls `cm_restrict_rest_api()` (Returns error for unauthorized REST requests)

```php
// Hooked in rest-api.php
add_action( 'init', 'cm_disable_rest_api' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The Gutenberg editor is broken

**Cause:** The Gutenberg editor requires the REST API. Removing the discovery link doesn't disable the API, but a theme or plugin may be using the link tag.
**Fix:** The Remove REST API Links feature should not break Gutenberg. If it does, check the browser console for errors and disable other API-related plugins.

### The link is still in the page source

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the toggle is on. Clear all caching layers.

### The REST API is completely disabled

**Cause:** Another plugin is disabling the REST API entirely, not just the discovery link.
**Fix:** The Remove REST API Links feature only removes the link tag, not the API itself. If the API is disabled, check other plugins like "Disable REST API".

### Users can still be enumerated

**Cause:** The REST API is still enabled, just the discovery link is removed.
**Fix:** To fully block users enumeration, use the `cm_rest_api_users_response` filter (see Advanced Options) or use a dedicated security plugin.

---

## Related Articles

- [How to Disable User Enumeration in WordPress](security-disable-user-enumeration.md)
- [How to Use a Custom Login URL in WordPress](security-custom-login-url.md)
- [How to Enable Login Lockdown in WordPress](security-login-lockdown.md)
- [How to Use the Email Tab in Classic Monks: Feature Index](../email.md)
