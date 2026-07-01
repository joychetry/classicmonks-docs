---
title: "How to Disable XML-RPC in WordPress | CM"
slug: security/disable-xmlrpc
description: "Disable XML-RPC in WordPress via Classic Monks. Blocks brute force attacks, pingbacks, and other vulnerabilities that exploit the XML-RPC endpoint."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/security/disable-xmlrpc/
---

# How to Disable XML-RPC in WordPress

> Disable XML-RPC in Classic Monks blocks the WordPress XML-RPC endpoint. Stops pingback attacks, brute force amplification, and other exploits that target the legacy XML-RPC interface.

## Key Takeaways

- Single toggle, no nested options
- Blocks all access to `xmlrpc.php`
- Stops pingback spam and DDoS amplification
- Prevents brute force attacks via XML-RPC
- May break some plugins that use XML-RPC (e.g., Jetpack legacy, older mobile apps)

## What Is the Disable XML-RPC feature?

XML-RPC is a legacy WordPress API that predates the REST API. It uses XML over HTTP and allows remote clients to interact with WordPress. While it was deprecated in favor of the REST API, it's still enabled by default for backward compatibility.

The Disable XML-RPC feature blocks all access to `xmlrpc.php`, the endpoint that handles XML-RPC requests.

## Why You Need It

XML-RPC is a high-value attack surface:

- **Brute force amplification**: Attackers can use `system.multicall` to test many passwords in one request
- **Pingback DDoS**: Attackers can use your site to send pingbacks to target sites, hiding their origin
- **Pingback spam**: Spam blogs use XML-RPC pingbacks to create backlinks
- **Information disclosure**: XML-RPC errors can reveal usernames and other information

For most sites, XML-RPC is no longer needed (the REST API has replaced it). Disabling it eliminates these risks.

---

## How to Disable XML-RPC in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **WP Protection** subtab.

### Step 3: Enable Disable XML-RPC

Scroll to **Disable XML-RPC** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Try to access `https://yoursite.com/xmlrpc.php` in your browser. The response should be 403 Forbidden or 404 Not Found. The page should no longer respond to XML-RPC requests.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Disable XML-RPC** | Master toggle. | Off |

No nested options.

---

## What Gets Affected

- The XML-RPC endpoint: returns 403/404 for all requests
- The pingback functionality: disabled (other sites can't ping your posts)
- The trackback functionality: disabled
- The Jetpack legacy features: may break (if you use Jetpack)
- The mobile app connections: older apps may break

## What Does NOT Get Affected

- The REST API: still works
- The WordPress admin: not affected
- The frontend pages: not affected
- The plugin/theme update via WP-CLI: not affected

---

## Advanced Options (Developers)

This feature registers 2 WordPress hooks in `xmlrpc-pingbacks.php`:

**Filters:**

- `xmlrpc_enabled` calls `__return_false()` (Disables XML-RPC completely)
- `wp_headers` calls `cm_remove_x_pingback()` (Removes X-Pingback header)

```php
// Hooked in xmlrpc-pingbacks.php
add_filter( 'xmlrpc_enabled', '__return_false' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The site is broken after enabling

**Cause:** A plugin or app is using XML-RPC and is now broken.
**Fix:** Identify the plugin/app that uses XML-RPC. Either disable the feature or configure allowed methods in the plugin settings under Security > Disable XML-RPC.

### Jetpack is not working

**Cause:** Jetpack uses XML-RPC for some legacy features.
**Fix:** Jetpack's modern features work via the REST API. Disable the legacy XML-RPC features in Jetpack settings. Or adjust the XML-RPC settings in the plugin under Security > Disable XML-RPC.

### The pingback spam is still happening

**Cause:** The pingbacks may be coming from a different source.
**Fix:** Verify XML-RPC is actually disabled (try `xmlrpc.php` directly). The spam may be from trackbacks (which can be disabled separately in Settings > Discussion).

### Mobile apps can't connect

**Cause:** Older WordPress mobile apps used XML-RPC.
**Fix:** Update the mobile app to the latest version (the modern WordPress mobile app uses the REST API). Or use the web interface.

### I want to allow specific XML-RPC methods

**Cause:** The feature blocks all XML-RPC.
**Fix:** Configure allowed methods in the plugin settings under Security > Disable XML-RPC. For example, allow `pingback.ping` while blocking other methods.

---

## Related Articles

- [How to Disable .htaccess File Access in WordPress](security-disable-htaccess-file-access.md)
- [How to Remove REST API Links in WordPress](security-remove-rest-api-links.md)
- [How to Disable User Enumeration in WordPress](security-disable-user-enumeration.md)
- [How to Use the Email Tab in Classic Monks: Feature Index](../email.md)
