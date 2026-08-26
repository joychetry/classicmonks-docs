---
title: "How to Show the Staging Environment Indicator in WordPress"
slug: staging-indicator
description: "Show a visible staging environment indicator in the WordPress admin. Reminds everyone working on a staging site that they're not on production, preventing accidental edits and user confusion."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/staging-indicator/
---

# How to Show the Staging Environment Indicator in WordPress

> Show Staging Environment Indicator in Classic Monks displays a visible banner in the WordPress admin when you're on a staging or development site. Reminds everyone that this is not the production site, preventing accidental edits and user confusion.

## Key Takeaways

- Single toggle, no nested options
- Visible banner in the WordPress admin
- Customizable banner text and color
- Shows on every admin page
- Pairs with [Staging Protection](security-staging-protection.md) for comprehensive staging safety

## What Is the Staging Environment Indicator feature?

Working on a staging site can be confusing, especially when the staging site looks identical to the production site. The Staging Environment Indicator feature adds a visible banner (e.g., a yellow bar at the top of the admin) that says "STAGING SITE" or similar, so everyone knows they're not on the production site.

This is a small but important safety feature. The most common staging site accident is: a team member thinks they're on the staging site, makes a change, but is actually on production. The indicator prevents this by making it visually obvious which environment they're in.

## Why You Need It

Staging site accidents are common and serious:

- **Wrong environment edits**: A change meant for staging goes to production (or vice versa)
- **User confusion**: Editors may not realize they're on staging, leading to confusion
- **Data leakage**: Test data on staging may be visible to editors
- **Email leakage**: Staging sites can send emails to real customers

The staging indicator is a low-cost, high-impact way to prevent these accidents.

---

## How to Show the Staging Environment Indicator in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Staging Protection** subtab.

### Step 3: Enable Show Staging Environment Indicator

Scroll to **Show Staging Environment Indicator** and toggle on. The indicator appears immediately in the admin.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Visit any admin page. The staging indicator should be visible (e.g., as a yellow bar at the top of the admin).

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Show Staging Environment Indicator** | Master toggle. | On |

The banner text and color are customizable via filters. The default banner is a yellow bar with the text "STAGING ENVIRONMENT".

---

## What Gets Affected

- The WordPress admin: the indicator is visible on every admin page
- The frontend: the indicator is NOT shown on the frontend (only admin)
- The user experience: editors see the indicator and know they're on staging
- The safety: fewer accidents from editing the wrong environment

## What Does NOT Get Affected

- The frontend: not affected
- The staging protection (HTTP auth, search engine block, etc.): not affected (this is a separate toggle)
- The user accounts: not affected
- The WordPress functionality: not affected

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `staging-protection.php`:

**Actions:**

- `wp_footer` calls `CM_Staging_Protection::add_staging_indicator()` (Renders staging environment indicator bar)

```php
// Hooked in staging-protection.php
add_action( 'wp_footer', 'CM_Staging_Protection::add_staging_indicator' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The indicator is not showing

**Cause:** The toggle is off, or a caching plugin is serving the old admin.
**Fix:** Verify the toggle is on. Clear any caching plugins. The indicator is rendered server-side, so caching can hide it.

### The indicator is showing on the frontend

**Cause:** A theme or plugin is rendering the indicator outside the admin.
**Fix:** The indicator is added via the `admin_notices` action or `admin_bar_menu` action, which only fires in the admin. If a theme is showing it on the frontend, check the theme's hooks.

### The indicator is too prominent

**Cause:** The default styling is intentionally prominent (yellow bar).
**Fix:** Use the `cm_staging_indicator_html` filter to customize the styling. Use a less prominent color (e.g., light gray) for less distraction.

### I want to show different text for different environments

**Cause:** The default text is the same for all staging sites.
**Fix:** Use the `cm_staging_indicator_environment_type` filter to detect the environment, then customize the text based on the environment.

### I want to show the indicator to admins only

**Cause:** The indicator is shown to all logged-in users.
**Fix:** Use the `cm_staging_indicator_enabled` filter to check the user's role. Show only to administrators and editors, hide from subscribers.

---

## Related Articles

- [How to Enable Staging Protection in WordPress](security-staging-protection.md)
- [How to Enable HTTP Authentication for Staging in WordPress](security-http-auth.md)
- [How to Block AI Crawlers in WordPress](security-ai-bot-blocking.md)
- [How to Use the Email Tab in Classic Monks: Feature Index](../email.md)
