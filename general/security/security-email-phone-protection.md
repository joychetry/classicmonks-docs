---
title: "How to Use Email and Phone Protection in WordPress | CM"
slug: security/email-phone-protection
description: "Protect email addresses and phone numbers from scrapers and bots in Classic Monks. Auto-detect or manual configuration, with cloaking methods to prevent automated harvesting."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/security/email-phone-protection/
---

# How to Use Email and Phone Protection in WordPress

> Email and Phone Protection in Classic Monks cloaks email addresses and phone numbers in your WordPress content to prevent automated scrapers from harvesting them. Auto-detect feature scans your content and applies protection without manual configuration.

## Key Takeaways

- Single toggle with 4 sub-options (auto-detect, scope, method, class)
- Cloaks email addresses and phone numbers from scrapers
- Auto-detect feature scans content automatically
- Configurable cloaking method (JavaScript, CSS, or text replacement)
- Works on posts, pages, custom post types, and comments
- Improves privacy and reduces spam

## What Is the Email and Phone Protection feature?

Email addresses and phone numbers in your WordPress content are vulnerable to automated harvesting. Bots scan pages, extract email addresses and phone numbers, and add them to spam lists or sell them to marketers.

The Email and Phone Protection feature cloaks these addresses in your content, making them invisible to bots but visible to real users. The feature works on all post types, pages, comments, and widgets.

## Why You Need It

Public email addresses and phone numbers are at constant risk:

- **Spam bots**: Scan the web for email addresses to add to spam lists
- **Robocallers**: Harvest phone numbers for telemarketing
- **Data brokers**: Compile databases of personal information
- **Phishing**: Use harvested emails to send targeted phishing attacks

Cloaking your contact information is a critical privacy measure.

---

## How to Use Email and Phone Protection in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **WP Protection** subtab.

### Step 3: Enable Email and Phone Protection

Scroll to **Email and Phone Protection** and toggle on. Nested options expand.

### Step 4: Enable Auto-Detect (Recommended)

Toggle on **Auto-Detect Phone Numbers** to automatically scan your content and apply protection to any email or phone number it finds.

### Step 5: Configure the Scope

Set the **Email Protection Scope**:

- **All Content**: Apply to posts, pages, custom post types, comments, widgets
- **Posts and Pages Only**: Apply only to post content (not comments or widgets)
- **Custom**: Use the filter to specify your own scope

### Step 6: Configure the Method

Set the **Email Protection Method**:

- **JavaScript Cloaking**: Render emails as JavaScript (most secure, slight rendering delay)
- **CSS Cloaking**: Use CSS to hide emails (works without JavaScript, less secure)
- **Text Replacement**: Replace `@` with `[at]` and `.` with `[dot]` (most compatible, looks ugly)

### Step 7: Configure the Class (Advanced)

If you want to add a custom CSS class to cloaked elements, set the **Email Protection Class** field. This is useful for theme-specific styling.

### Step 8: Save Changes

Click **Save Changes**.

### Step 9: Test

View a page or post that contains an email address. The email should be cloaked (visible to humans, not to bots).

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Email and Phone Protection** | Master toggle. | Off |
| **Auto-Detect Phone Numbers** | Automatically find and protect phone numbers. | Off |
| **Email Protection Scope** | Where to apply protection. | All Content |
| **Email Protection Method** | How to cloak the addresses. | JavaScript |
| **Email Protection Class** | Custom CSS class for cloaked elements. | (empty) |

---

## What Gets Affected

- The post content: emails and phone numbers are cloaked
- The page content: emails and phone numbers are cloaked
- The custom post type content: emails and phone numbers are cloaked
- The comments: emails are cloaked (if "All Content" scope)
- The widgets: emails are cloaked (if "All Content" scope)
- The rendered HTML: emails appear as cloaked elements to bots

## What Does NOT Get Affected

- The admin (the post editor still shows the original email)
- The user experience: real users see the email as normal (with JavaScript)
- The email functionality: clicking the email still opens the mail client
- The phone functionality: clicking the phone number on mobile still initiates a call
- Search engines: Google can still read the cloaked emails (uses JavaScript)

---

## Advanced Options (Developers)

This feature registers 4 WordPress hooks in `email-phone-protection.php`:

**Actions:**

- `template_redirect` calls `cm_email_protection_start_buffer()` (Starts output buffering for email filtering (priority 1))
- `wp_enqueue_scripts` calls `cm_email_protection_enqueue_assets()` (Enqueues email protection JS/CSS)
- `init` calls `cm_email_protection_init()` (Initializes email protection (priority 100))

**Filters:**

- `cm_email_protection_filter_hooks` calls `apply_filters()` (Customizable filter)

```php
// Hooked in email-phone-protection.php
add_action( 'template_redirect', 'cm_email_protection_start_buffer' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### Emails are still being harvested

**Cause:** The cloaking method is not working, or the auto-detect is missing some addresses.
**Fix:** Verify the toggle is on. Use a different cloaking method (JavaScript is most secure). Add custom patterns in the plugin settings under Security > Email & Phone Protection.

### The cloaked emails are not visible to users

**Cause:** The user's browser has JavaScript disabled, or the JavaScript is conflicting with another script.
**Fix:** Use a different cloaking method (CSS or text replacement). Test with JavaScript enabled and disabled.

### The cloaking breaks email click-to-open functionality

**Cause:** The cloaking method is replacing the mailto: link incorrectly.
**Fix:** Use the JavaScript cloaking method, which preserves the mailto: link. CSS and text replacement may break click-to-open.

### The cloaked emails are visible in the page source

**Cause:** The cloaking method is text replacement or CSS, not JavaScript.
**Fix:** Use JavaScript cloaking. With JavaScript, the actual email is not in the page source (it's generated by JS at render time).

### The auto-detect is missing some phone numbers

**Cause:** The default phone number patterns are limited (e.g., US format only).
**Fix:** Add custom phone patterns in the plugin settings under Security > Email & Phone Protection.

---

## Related Articles

- [How to Use a Custom Login URL in WordPress](security-custom-login-url.md)
- [How to Enable Spam Comment Protection in WordPress](security-spam-comment-protection.md)
- [How to Use the Email Tab in Classic Monks: Feature Index](../email.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
