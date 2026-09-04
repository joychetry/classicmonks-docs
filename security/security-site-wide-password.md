---
title: "How to Use Site-Wide Password Protection in WordPress"
slug: site-wide-password
description: "Add site-wide password protection in Classic Monks. Visitors must enter a password to access any content. Useful for staging sites, member-only sites, and pre-launch sites."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/site-wide-password/
---

# How to Use Site-Wide Password Protection in WordPress

> Site-Wide Password Protection in Classic Monks requires a password for any visitor to access your site. Useful for staging environments, pre-launch sites, and member-only content.

## Key Takeaways

- Single toggle with 1 sub-option (IP whitelist)
- Requires a password for any visitor (not logged in)
- Optional IP whitelist for admin access
- Hides all content from search engines while active
- Pairs with [Staging Protection](security-staging-protection.md) for staging sites

## What Is the Site-Wide Password Protection feature?

Site-Wide Password Protection requires a password to access any content on your WordPress site. Visitors see a password prompt before they can view any page, post, or media.

This is different from [Custom Login URL](security-custom-login-url.md) (which changes the URL) or [Login Lockdown](security-login-lockdown.md) (which limits failed attempts). Site-Wide Password Protection is a wall in front of the entire site.

## Why You Need It

Site-Wide Password Protection is useful for:

- **Staging sites**: Hide a work-in-progress site from public access
- **Pre-launch sites**: Keep the site private until launch
- **Member-only sites**: Require a password to view any content
- **Temporary sites**: Quick way to make a site private (e.g., for a contest)
- **Beta sites**: Get feedback from a limited audience before public launch

For most production sites, this is too restrictive. For staging or pre-launch, it's essential.

---

## How to Use Site-Wide Password Protection in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Content Protection** subtab.

### Step 3: Enable Site-Wide Password Protection

Scroll to **Enable Site-Wide Password Protection** and toggle on. Nested options expand.

### Step 4: Configure the IP Whitelist (Optional)

Add trusted IPs to the **IP Whitelist** field (one per line). These IPs bypass the password requirement:

- Office IP addresses
- Your home IP (for development)
- Search engine bots (if you want them to index the site)

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Test

Log out (or open a private browsing window). Visit any page. You should see a password prompt. Enter the correct password to access the site.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Site-Wide Password Protection** | Master toggle. | Off |
| **IP Whitelist** | IPs that bypass the password requirement. | (empty) |

The password itself is configured in the WordPress settings (Settings > Reading > "Password protect this site"). The Classic Monks feature enhances this built-in WordPress feature with the IP whitelist and other options.

---

## What Gets Affected

- The frontend: all pages require the password
- The admin: still works for logged-in admins
- The search engines: the password page may not be indexable (no content to index)
- The media files: typically not protected (they're served directly)

## What Does NOT Get Affected

- The admin (after login): full access
- The REST API: not protected (use a separate security plugin if needed)
- The cron jobs: not affected
- The IP-whitelisted visitors: full access without password

---

## Advanced Options (Developers)

This feature registers 5 WordPress hooks in `password-protection.php`:

**Actions:**

- `template_redirect` calls `CM_Password_Protection::maybe_show_login_form()` (Shows password form for protected content)
- `init` calls `CM_Password_Protection::maybe_process_login()` (Processes password form submission)
- `wp_before_admin_bar_render` calls `CM_Password_Protection::add_password_protection_admin_bar_item()` (Adds admin bar indicator)

**Filters:**

- `cm_password_protection_error_messages` calls `apply_filters()` (Customizable filter)
- `cm_password_protection_login_head` calls `apply_filters()` (Customizable filter)

```php
// Hooked in password-protection.php
add_action( 'template_redirect', 'CM_Password_Protection::maybe_show_login_form' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### I'm locked out of the site

**Cause:** You forgot the password or your IP changed.
**Fix:** Access the database directly (`wp_options` table, look for the `blog_public` option). Set it to 1 to disable WordPress's built-in password protection. Or add your IP to the whitelist.

### The admin shows the password prompt

**Cause:** The admin is not logged in, or a cookie was cleared.
**Fix:** Log in to the admin (the password prompt does not appear for logged-in admins). Clear cookies and try again.

### Search engines are indexing the password page

**Cause:** The password page has a meta description and title.
**Fix:** Use the `cm_site_wide_password_meta_robots` filter to add `noindex, nofollow` to the password page. Or use the password protection as a signal to set the site to "Discourage search engines" in Settings > Reading.

### The password is not being remembered

**Cause:** Cookie is being cleared by browser settings.
**Fix:** Check browser settings. The password is stored in a cookie, so "Clear cookies on exit" will require re-entering the password.

### I want to require a password only for specific pages

**Cause:** The feature is site-wide.
**Fix:** For per-page protection, use WordPress's built-in "Password protect this post" option on the post edit screen. For per-section protection, use a membership plugin.

---

## Related Articles

- [How to Use a Custom Login URL in WordPress](security-custom-login-url.md)
- [How to Use Staging Protection in WordPress](security-staging-protection.md)
- [How to Enable Stay Logged In in WordPress](security-stay-logged-in.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
