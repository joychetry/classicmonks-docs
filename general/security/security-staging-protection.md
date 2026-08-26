---
title: "How to Enable Staging Protection in WordPress"
slug: staging-protection
description: "Enable staging protection in Classic Monks. Locks down staging and development sites with HTTP authentication, blocks indexing, and shows a visible staging indicator."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/staging-protection/
---

# How to Enable Staging Protection in WordPress

> Staging Protection in Classic Monks locks down staging and development sites. Combines HTTP authentication, search engine blocking, and a visible staging indicator to prevent accidental access or indexing.

## Key Takeaways

- Single toggle, no nested options
- Adds HTTP authentication to the staging site
- Disables search engine indexing
- Shows a visible staging indicator
- Blocks development endpoints (e.g., WP_DEBUG, error log)
- Pairs with [Site-Wide Password Protection](security-site-wide-password.md) for additional security

## What Is the Staging Protection feature?

Staging and development sites are private copies of your site used for testing. They have the same content, same URLs, and same functionality as the production site. This creates a risk: if a staging site is accidentally indexed by search engines, it can compete with (or replace) the production site in search results.

The Staging Protection feature in Classic Monks combines several techniques to prevent this:

- **HTTP Authentication**: Browser-level password prompt before any content loads
- **Search engine blocking**: robots.txt and meta tags to prevent indexing
- **Staging indicator**: A visible banner in the admin to remind everyone this is a staging site
- **Development endpoint blocking**: Block access to common dev endpoints (e.g., `/wp-admin/admin-ajax.php?action=debug`)

## Why You Need It

Staging site accidents are common and serious:

- **Search engine indexing**: A staging site indexed by Google can permanently damage your SEO
- **User confusion**: Customers may end up on the staging site and not realize it
- **Data leakage**: Staging sites often have test data that shouldn't be public
- **Cross-contamination**: Form submissions on staging may go to production
- **Email leakage**: Staging sites can send emails to real customers

For any non-production site, Staging Protection is essential.

---

## How to Enable Staging Protection in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Staging Protection** subtab.

### Step 3: Enable Staging Protection

Scroll to **Enable Staging Protection** and toggle on. The feature activates all the related protections.

### Step 4: (Optional) Configure Sub-Options

The related sub-options include:

- **Enable HTTP Authentication**: Browser-level password prompt
- **Allow Performance Testing Tools**: Whitelist GTmetrix, Pingdom, etc.
- **Allow Development Endpoints**: Allow WP_DEBUG, error log access
- **Show Staging Environment Indicator**: Visible banner in admin

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Test

Visit the site in a new browser. You should be prompted for HTTP authentication (if enabled). Check the source for the staging indicator and robots.txt for noindex directives.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Staging Protection** | Master toggle. | Off |
| **Enable HTTP Authentication** | Browser-level password prompt. | Off |
| **Allow Performance Testing Tools** | Whitelist for performance tools. | Off |
| **Allow Development Endpoints** | Allow dev endpoints (WP_DEBUG, etc.). | Off |
| **Show Staging Environment Indicator** | Visible banner in admin. | On |

---

## What Gets Affected

- The frontend: HTTP authentication prompt (if enabled)
- The admin: staging indicator banner (if enabled)
- The search engines: blocked from indexing (via robots.txt + meta tags)
- The development endpoints: blocked (if Allow Dev Endpoints is off)
- The performance tools: blocked (if Allow Performance Tools is off)

## What Does NOT Get Affected

- The WordPress functionality: works the same after authentication
- The database: not affected
- The users: still work after authentication
- The plugins: still work after authentication

---

## Advanced Options (Developers)

This feature registers 5 WordPress hooks in `staging-protection.php`:

**Actions:**

- `wp` calls `CM_Staging_Protection::initialize_protection()` (Initializes staging protection logic)
- `admin_notices` calls `CM_Staging_Protection::admin_notice()` (Shows staging protection admin notice)
- `wp_footer` calls `CM_Staging_Protection::add_staging_indicator()` (Renders staging indicator on frontend)
- `admin_bar_menu` calls `CM_Staging_Protection::add_admin_bar_menu()` (Adds staging indicator to admin bar (priority 100))
- `rest_api_init` calls `CM_Staging_Protection::register_token_endpoint()` (Registers REST API token endpoint)

```php
// Hooked in staging-protection.php
add_action( 'wp', 'CM_Staging_Protection::initialize_protection' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The staging site is still being indexed

**Cause:** The search engines have already indexed the staging site. Removing the indexing doesn't remove existing pages.
**Fix:** Use Google Search Console to remove the indexed URLs. Use the URL removal tool to deindex individual pages.

### The HTTP authentication is not working

**Cause:** The sub-option is off, or the server doesn't support .htaccess authentication.
**Fix:** Verify the sub-option is on. For Nginx, the .htaccess-based auth doesn't work; configure HTTP auth at the Nginx level.

### The performance tools can't access the site

**Cause:** The "Allow Performance Testing Tools" sub-option is off.
**Fix:** Enable the sub-option. Add the user agent string of your performance tool to the allow list.

### The development endpoints are not accessible

**Cause:** The "Allow Development Endpoints" sub-option is off.
**Fix:** Enable the sub-option if you need access to dev endpoints (e.g., for testing).

### I forgot the HTTP auth password

**Cause:** The password is in the Classic Monks settings or the .htaccess file.
**Fix:** Reset the password via the Classic Monks settings. Or remove the .htaccess authentication temporarily to regain access.

---

## Related Articles

- [How to Use Site-Wide Password Protection in WordPress](security-site-wide-password.md)
- [How to Block AI Crawlers in WordPress](security-ai-bot-blocking.md)
- [How to Use a Custom Login URL in WordPress](security-custom-login-url.md)
- [How to Use the Email Tab in Classic Monks: Feature Index](../email.md)
