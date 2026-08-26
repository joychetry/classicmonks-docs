---
title: "How to Allow Performance Testing Tools in WordPress"
slug: allow-performance-tools
description: "Whitelist performance testing tools (GTmetrix, Pingdom, Lighthouse, etc.) in Classic Monks. Allows them to bypass staging protection for performance audits."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/allow-performance-tools/
---

# How to Allow Performance Testing Tools in WordPress

> Allow Performance Testing Tools in Classic Monks whitelists performance testing services (GTmetrix, Pingdom, Lighthouse, etc.) so they can bypass the staging protection. Run real performance audits on your staging site without disabling security.

## Key Takeaways

- Single toggle, no nested options
- Whitelists major performance testing tools
- Allows audits on staging sites without disabling protection
- Configurable user agent list via filter
- Pairs with [Staging Protection](security-staging-protection.md) and [HTTP Authentication](security-http-auth.md)

## What Is the Allow Performance Testing Tools feature?

When [Staging Protection](security-staging-protection.md) is enabled, the staging site is locked down: HTTP authentication, search engine blocking, etc. This is great for security, but it also blocks legitimate use cases like performance testing.

The Allow Performance Testing Tools feature whitelists the user agents of major performance testing services, so they can access the staging site without authentication.

## Why You Need It

Performance audits are essential, even for staging sites:

- **Pre-launch audits**: Catch performance issues before the site goes live
- **Comparison testing**: Compare staging vs production performance
- **Continuous monitoring**: Set up automated performance monitoring on staging
- **Client demos**: Show clients the performance metrics before launch

Without this feature, you'd need to disable staging protection to run performance tests, which is risky.

---

## How to Allow Performance Testing Tools in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Staging Protection** subtab.

### Step 3: Enable Allow Performance Testing Tools

Scroll to **Allow Performance Testing Tools** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Run a performance test on the staging site using a major tool (e.g., GTmetrix). The tool should be able to access the site without authentication.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Allow Performance Testing Tools** | Master toggle. | Off |

The whitelisted user agents are maintained by Classic Monks and updated as new tools emerge. To add custom user agents, add them to your server configuration.

---

## What Gets Affected

- The staging protection: allows the whitelisted tools to bypass
- The performance testing: works on staging sites
- The user experience: performance tools can access the site

## What Does NOT Get Affected

- The HTTP authentication: still applies to non-whitelisted users
- The search engine blocking: still applies
- The staging indicator: still shows
- The regular visitors: still need authentication

---


## Troubleshooting

### The performance tool is still blocked

**Cause:** The tool's user agent is not in the whitelist.
**Fix:** Check the tool's user agent (in the browser's developer tools or in the tool's documentation). Add it to your server configuration.

### The tool passes but the test fails

**Cause:** The tool is bypassing the HTTP auth but not the search engine block (or vice versa).
**Fix:** Use the `cm_staging_protection_bypass_behavior` filter to customize which protections are bypassed.

### The user agent is being spoofed

**Cause:** Some performance tools allow user agent spoofing, which can be used maliciously.
**Fix:** Verify the user agent with a reverse DNS lookup. Use IP-based whitelisting in your server configuration (more secure than user agent matching).

### A new tool is not in the whitelist

**Cause:** The whitelist is maintained by Classic Monks.
**Fix:** Add the new tool's user agent to your server configuration. The plugin will be updated in a future release to include it.

---

## Related Articles

- [How to Enable Staging Protection in WordPress](security-staging-protection.md)
- [How to Enable HTTP Authentication for Staging in WordPress](security-http-auth.md)
- [How to Block AI Crawlers in WordPress](security-ai-bot-blocking.md)
- [How to Use the Email Tab in Classic Monks: Feature Index](../email.md)
