---
title: "How to Use the Email Tab in Classic Monks: Feature Index | CM"
slug: email
description: "Index of all Email tab features in Classic Monks. Per-feature guides for email logging, SMTP settings, comment reply notifications, and WooCommerce email control."
last_updated: 2026-06-24
author: Joy
reading_time: 2 min
canonical: https://classicmonks.com/docs/email/
---

# How to Use the Email Tab in Classic Monks

> The Email tab in Classic Monks groups 12 independent features for managing WordPress email behavior, including logging, SMTP configuration, comment reply notifications, password change suppression, and WooCommerce transactional email control.

## About This Index

This page is a directory of all Email tab features. Each has its own dedicated guide with configuration, troubleshooting, and developer filters.

The Email tab has 3 subtabs:

- **Email Settings**: Core email infrastructure (logging, SMTP)
- **Notifications**: Disable various WordPress admin email notifications
- **WooCommerce**: WooCommerce-specific transactional email control

## Email Settings

| Feature | Description | Guide |
|---------|-------------|-------|
| **Enable Email Logging** | Track and log every email WordPress sends. View history, resend failed emails, audit communications. | [View guide](email/email-logging.md) |
| **Enable SMTP Settings** | Replace WordPress's default `mail()` with authenticated SMTP for reliable email delivery. | [View guide](email/email-smtp-settings.md) |

## Notifications

| Feature | Description | Guide |
|---------|-------------|-------|
| **Enable Comment Reply Email** | Send notification emails to commenters when someone replies to their comment. Configurable notification type. | [View guide](email/email-comment-reply-email.md) |
| **Disable Password Change Email** | Stop the "your password was changed" notification when users change their password. | [View guide](email/email-disable-password-change-email.md) |
| **Disable New User Email** | Stop the admin notification when new users register. | [View guide](email/email-disable-new-user-email.md) |
| **Disable Admin Email Change** | Remove the verification step when admin email is changed. | [View guide](email/email-disable-admin-email-change.md) |
| **Disable Auto Update Emails (Core)** | Stop the post-update email for WordPress core. | [View guide](email/email-disable-auto-update-core.md) |
| **Disable Auto Update Emails (Plugins)** | Stop the post-update email for plugins. | [View guide](email/email-disable-auto-update-plugins.md) |
| **Disable Auto Update Emails (Themes)** | Stop the post-update email for themes. | [View guide](email/email-disable-auto-update-themes.md) |

See the [Notifications index](email/email-notifications.md) for a full overview.

## WooCommerce

| Feature | Description | Guide |
|---------|-------------|-------|
| **Disable WooCommerce Emails** | Suppress all WooCommerce transactional emails. | [View guide](woocommerce/woocommerce-disable-woocommerce-emails.md) |
| **Only Allow Reset Password Email** | Allow only the customer reset password email; suppress everything else. | [View guide](woocommerce/woocommerce-allow-reset-password-email.md) |

## Common Combinations

For a **typical blog**:
- Enable Email Logging: ON (audit trail)
- Enable SMTP Settings: ON (reliable delivery)
- All other features: defaults

For a **high-traffic membership site**:
- Enable Email Logging: ON
- Enable SMTP Settings: ON
- All "Disable" notifications: ON (less admin noise)
- Disable WooCommerce Emails: depends on whether customers want order emails

For a **privacy-focused site** (GDPR-conscious):
- Enable SMTP Settings: ON (authenticated sending)
- All "Disable" notifications: ON (minimize data flow)
- Only Allow Reset Password Email: ON (account recovery without other emails)

For a **managed WordPress site** (agency-hosted):
- Enable Email Logging: ON (client reporting)
- Enable SMTP Settings: ON
- Disable Admin Email Change: ON (no verification for trusted admins)

## Related Articles

- [How to Use Content Management in WordPress](core/core-content-management.md)
- [How to Configure SMTP Settings in WordPress](email/email-smtp-settings.md)
- [How to Use Logs in WordPress](core/core-logs.md)
