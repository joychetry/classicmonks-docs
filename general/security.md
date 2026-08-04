---
title: "How to Use the Security Tab in Classic Monks: Feature Index | CM"
slug: security
description: "Index of all Security tab features in Classic Monks. 39 per-feature guides covering WP protection, 2FA, content protection, stay logged in, and staging protection."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/security
---

# How to Use the Security Tab in Classic Monks: Feature Index

> The Security tab in Classic Monks adds 39 features across 5 subtabs. This index links to every per-feature guide, organized by subtab for fast navigation.

## Key Takeaways

- 39 per-feature docs covering the full Security tab
- 5 subtabs: WP Protection, Two-Factor Auth, Content Protection, Stay Logged In, Staging Protection
- Each feature has its own dedicated guide with frontmatter, FAQ, and advanced developer options
- Defense-in-depth: features are designed to be combined (e.g., Custom Login URL + Login Lockdown + Turnstile)

## WP Protection

The WP Protection subtab is the broadest, covering login security, captcha, and server hardening. 13 features.

| Feature | Description | Guide |
|---------|-------------|-------|
| **Use a Custom Login URL** | Change `/wp-login.php` to a custom slug. 3 sub-options. | [View guide](security/security-custom-login-url.md) |
| **Enable Login Lockdown** | Lock out users after failed attempts. 9 sub-options including extended lockout. | [View guide](security/security-login-lockdown.md) |
| **Use Cloudflare Turnstile** | Add privacy-first captcha. 6 sub-options. | [View guide](security/security-cloudflare-turnstile.md) |
| **Use Math Captcha** | Add self-contained math captcha. 4 sub-options. | [View guide](security/security-math-captcha.md) |
| **Use Auto Logout** | Auto-logout after configurable idle time. 1 sub-option. | [View guide](security/security-auto-logout.md) |
| **Email and Phone Protection** | Cloak emails and phone numbers from scrapers. 4 sub-options. | [View guide](security/security-email-phone-protection.md) |
| **Remove REST API Links** | Remove the API discovery link tag. | [View guide](security/security-remove-rest-api-links.md) |
| **Disable User Enumeration** | Block user enumeration attacks. | [View guide](security/security-disable-user-enumeration.md) |
| **Hide Remember Me Checkbox** | Force session expiry at browser close. | [View guide](security/security-hide-remember-me.md) |
| **Disable .htaccess File Access** | Block HTTP access to .htaccess. | [View guide](security/security-disable-htaccess-file-access.md) |
| **Disallow File Modifications** | Disable file edits via admin. | [View guide](security/security-disallow-file-mods.md) |
| **Disable XML-RPC** | Block the legacy XML-RPC endpoint. | [View guide](security/security-disable-xmlrpc.md) |

## Two-Factor Auth

The Two-Factor Auth subtab adds TOTP and Email OTP support. 4 features.

| Feature | Description | Guide |
|---------|-------------|-------|
| **TOTP 2FA** | Time-based One-Time Password via authenticator app. | [View guide](security/security-2fa-totp.md) |
| **Email OTP 2FA** | Email-based one-time password. | [View guide](security/security-2fa-email.md) |
| **Allow Trusted Devices** | Skip 2FA on trusted devices for a configurable period. | [View guide](security/security-2fa-trusted-devices.md) |
| **Enable 2FA Rate Limiting** | Lock out users after failed 2FA attempts. 3 sub-options. | [View guide](security/security-2fa-rate-limiting.md) |

## Content Protection

The Content Protection subtab protects content from unauthorized access and casual copying. 15 features.

| Feature | Description | Guide |
|---------|-------------|-------|
| **Site-Wide Password Protection** | Require a password for any visitor. 1 sub-option (IP whitelist). | [View guide](security/security-site-wide-password.md) |
| **Block AI Crawlers** | Block 10+ major AI training crawlers. | [View guide](security/security-ai-bot-blocking.md) |
| **Spam Comment and Review Protection** | Multi-layer spam detection for comments and reviews. | [View guide](security/security-spam-comment-protection.md) |
| **Restrict Editor Access** | Limit editors to their own posts. | [View guide](security/security-post-access-restriction.md) |
| **Disable Text Selection** | Prevent text selection on the frontend. 4 sub-options. | [View guide](security/security-disable-text-selection.md) |
| **Disable Right Click** | Disable the right-click context menu. | [View guide](security/security-disable-right-click.md) |
| **Disable View Source** | Block the CTRL+U shortcut. | [View guide](security/security-disable-view-source.md) |
| **Disable Inspect Element** | Block the F12 shortcut. | [View guide](security/security-disable-inspect-element.md) |
| **Disable Copy/Cut/Paste** | Block CTRL+C/X/V shortcuts. | [View guide](security/security-disable-copy-paste.md) |
| **Disable Select All** | Block the CTRL+A shortcut. | [View guide](security/security-disable-select-all.md) |
| **Disable Save** | Block the CTRL+S shortcut. | [View guide](security/security-disable-save.md) |
| **Disable Print** | Block the CTRL+P shortcut. | [View guide](security/security-disable-print.md) |
| **Disable Image Drag** | Prevent dragging images to the desktop. | [View guide](security/security-disable-image-drag.md) |
| **Disable Safari Reader Mode** | Prevent Safari from offering Reader Mode. | [View guide](security/security-disable-safari-reader.md) |
| **Apply to Administrators** | Master switch to apply content protection to admins. | [View guide](security/security-protection-for-admin.md) |

## Stay Logged In

The Stay Logged In subtab extends auth cookie duration. 2 features.

| Feature | Description | Guide |
|---------|-------------|-------|
| **Enable Stay Logged In** | Extend auth cookie to 30 days. | [View guide](security/security-stay-logged-in.md) |
| **Auto-check Remember Me** | Pre-check the Remember Me checkbox. | [View guide](security/security-auto-check-remember-me.md) |

## Staging Protection

The Staging Protection subtab locks down staging and development sites. 5 features.

| Feature | Description | Guide |
|---------|-------------|-------|
| **Enable Staging Protection** | Master toggle for staging safety. | [View guide](security/security-staging-protection.md) |
| **Enable HTTP Authentication** | Browser-level password prompt. | [View guide](security/security-http-auth.md) |
| **Allow Performance Testing Tools** | Whitelist for GTmetrix, Pingdom, etc. | [View guide](security/security-allow-performance-tools.md) |
| **Allow Development Endpoints** | Allow access to dev endpoints (WP_DEBUG, etc.). | [View guide](security/security-allow-dev-endpoints.md) |
| **Show Staging Environment Indicator** | Visible banner in admin. | [View guide](security/security-staging-indicator.md) |

## Common Combinations

- **Maximum login security**: Custom Login URL + Login Lockdown + Cloudflare Turnstile + Hide Remember Me
- **Mandatory 2FA for admins**: TOTP 2FA + Trusted Devices + Rate Limiting (require for admin role)
- **Staging site lockdown**: Staging Protection + HTTP Authentication + Staging Indicator
- **Premium content protection**: Site-Wide Password + Text Selection + Disable Copy/Paste
- **Spam-free blog**: Spam Comment Protection + Math Captcha + Disable User Enumeration

## Subtab Index

- [WP Protection](security/security-custom-login-url.md) (12 features)
- [Two-Factor Auth](security/security-2fa-totp.md) (4 features)
- [Content Protection](security/security-site-wide-password.md) (15 features)
- [Stay Logged In](security/security-stay-logged-in.md) (2 features)
- [Staging Protection](security/security-staging-protection.md) (5 features)

## Related Articles

- [How to Use the Email Tab in Classic Monks: Feature Index](email.md)
- [How to Use the WooCommerce Tab in Classic Monks: Feature Index](woocommerce.md)
- [How to Use the Interface Tab in Classic Monks: Feature Index](interface.md)
- [How to Configure SMTP Settings in WordPress](email/email-smtp-settings.md)
