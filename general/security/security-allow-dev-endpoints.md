---
title: "How to Allow Development Endpoints in WordPress"
slug: allow-dev-endpoints
description: "Allow access to WordPress development endpoints (WP_DEBUG, error logs, debug info) on staging sites. Useful for development and debugging while keeping the rest of the staging protection active."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/allow-dev-endpoints/
---

# How to Allow Development Endpoints in WordPress

> Allow Development Endpoints in Classic Monks whitelists development and debugging endpoints on staging sites. Allows access to WP_DEBUG, error logs, and other dev tools while keeping the rest of the staging protection active.

## Key Takeaways

- Single toggle, no nested options
- Whitelists WordPress development endpoints
- Allows access to WP_DEBUG, error logs, debug info
- Configurable per-endpoint via filter
- Pairs with [Staging Protection](security-staging-protection.md)

## What Is the Allow Development Endpoints feature?

When [Staging Protection](security-staging-protection.md) is enabled, the staging site is locked down. This includes development endpoints like:

- `wp-admin/admin-ajax.php?action=debug_info`
- `wp-content/debug.log`
- `wp-includes/version.php` (WordPress version info)
- `readme.html` (WordPress readme)

These endpoints are useful for development but can leak information to attackers. The Allow Development Endpoints feature selectively allows access to these endpoints while keeping the rest of the staging protection active.

## Why You Need It

Development endpoints are useful for:

- **Debugging**: Access to error logs and debug info is essential for development
- **Performance testing**: Some tools need to access internal endpoints
- **Migration tools**: Some migration plugins use internal endpoints
- **API testing**: Some API testing tools need access to internal endpoints

For most staging sites, you'll need some development endpoints accessible.

---

## How to Allow Development Endpoints in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Staging Protection** subtab.

### Step 3: Enable Allow Development Endpoints

Scroll to **Allow Development Endpoints** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Try to access a development endpoint (e.g., `wp-content/debug.log`). The endpoint should be accessible.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Allow Development Endpoints** | Master toggle. | Off |

The whitelisted endpoints are maintained by Classic Monks. To customize, add the endpoints to your server configuration.

---

## What Gets Affected

- The staging protection: allows access to whitelisted dev endpoints
- The development: developers can access debug info
- The user experience: dev tools work as expected

## What Does NOT Get Affected

- The HTTP authentication: still applies to non-whitelisted requests
- The search engine blocking: still applies
- The staging indicator: still shows
- The regular visitors: still need authentication

---


## Common Use Cases

### API Development

When developing APIs that need to be tested, allowing dev endpoints enables direct testing without bypassing staging protection.

### Migration Testing

Migration plugins often need internal endpoints to work. Allowing dev endpoints during migration is essential.

### Performance Profiling

Tools like Query Monitor need dev endpoints to display database queries and PHP errors. Allow these for performance work.

## Troubleshooting

### The dev endpoint is still blocked

**Cause:** The endpoint is not in the whitelist.
**Fix:** Add the endpoint to your server configuration.

### The endpoint is accessible but returns 404

**Cause:** The endpoint path is wrong, or the file doesn't exist.
**Fix:** Verify the endpoint path is correct. For example, `wp-content/debug.log` only works if `WP_DEBUG_LOG` is enabled and the log file exists.

### The dev endpoint is accessible to anyone

**Cause:** The dev endpoint is whitelisted for all visitors.
**Fix:** Use the `cm_staging_protection_dev_endpoint_behavior` filter to set the behavior to "authenticated" for sensitive endpoints.

### The dev endpoint is being accessed suspiciously

**Cause:** The dev endpoints can be discovered by attackers.
**Fix:** Use the `cm_staging_protection_dev_endpoint_accessed` action to log access. Monitor the logs for suspicious activity.

---

## Related Articles

- [How to Enable Staging Protection in WordPress](security-staging-protection.md)
- [How to Enable HTTP Authentication for Staging in WordPress](security-http-auth.md)
- [How to Allow Performance Testing Tools in WordPress](security-allow-performance-tools.md)
- [How to Use the Email Tab in Classic Monks: Feature Index](../email.md)
