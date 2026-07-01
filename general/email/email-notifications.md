---
title: "How to Configure Email Notifications in WordPress | CM"
slug: email/notifications
description: "Index of email notification features in WordPress via Classic Monks. Per-feature guides for comment reply, password change, new user, admin email, and auto-update emails."
last_updated: 2026-06-24
author: Joy
reading_time: 2 min
canonical: https://classicmonks.com/docs/email/notifications/
---

# How to Configure Email Notifications in WordPress

> The Notifications subtab in Classic Monks Email groups 7 independent toggles that suppress various WordPress admin email notifications. Each has its own dedicated guide.

## About This Index

This page is a directory of all email notification features in Classic Monks. Each feature is a toggle in the **Classic Monks > Email > Notifications** section, with its own dedicated documentation.

## Email Notifications

| Feature | Description | Guide |
|---------|-------------|-------|
| **Enable Comment Reply Email** | Send notification emails to commenters when someone replies to their comment. Configurable notification type. | [View guide](email-comment-reply-email.md) |
| **Disable Password Change Email** | Stop the "your password has been changed" notification when users change their password. | [View guide](email-disable-password-change-email.md) |
| **Disable New User Email** | Stop the admin notification when new users register on the site. | [View guide](email-disable-new-user-email.md) |
| **Disable Admin Email Change** | Remove the verification step when the site admin email address is changed. | [View guide](email-disable-admin-email-change.md) |
| **Disable Auto Update Notification Emails for Core** | Stop the post-update email when WordPress core auto-updates. | [View guide](email-disable-auto-update-core.md) |
| **Disable Auto Update Notification Emails for Plugins** | Stop the post-update email when plugins auto-update. | [View guide](email-disable-auto-update-plugins.md) |
| **Disable Auto Update Notification Emails for Themes** | Stop the post-update email when themes auto-update. | [View guide](email-disable-auto-update-themes.md) |

## Common Combinations

For a **typical blog** with low admin activity:
- Disable Password Change Email: ON (reduces inbox clutter)
- Disable New User Email: OFF (you want to know about new registrations)
- All Auto Update Emails: ON (routinely updated, lots of noise)
- All others: defaults

For a **high-traffic membership site**:
- All "Disable" toggles: ON (admin doesn't need any of these notifications)
- Comment Reply Email: ON with Opt-in Checked (engagement driver)

For a **managed WordPress site** (agency-hosted, multi-admin):
- Disable Admin Email Change: ON (no verification needed for trusted admins)
- All others: defaults

For a **privacy-focused site** (GDPR-conscious):
- All "Disable" toggles: ON (minimize data flow)
- Comment Reply Email: ON with Opt-in Unchecked (explicit consent required)

## Related Articles

- [How to Configure SMTP Settings in WordPress](email-smtp-settings.md)
- [How to Log WordPress Emails in Classic Monks](email-logging.md)
- [How to Manage Content in WordPress](../core/core-content-management.md)
