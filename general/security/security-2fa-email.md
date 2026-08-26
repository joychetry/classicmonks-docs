---
title: "How to Use Email OTP Two-Factor Authentication in WordPress"
slug: 2fa-email
description: "Add email-based one-time password authentication to WordPress in Classic Monks. Users receive a 6-digit code via email as the second login factor."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/2fa-email/
---

# How to Use Email OTP Two-Factor Authentication in WordPress

> Email OTP 2FA in Classic Monks adds email-based one-time password authentication. Users receive a 6-digit code via email after entering their password.

## Key Takeaways

- Single toggle, no nested options
- Adds email-based 2FA (no authenticator app required)
- Better for users without smartphones or who don't want to install apps
- Requires reliable email delivery (use [SMTP Settings](../email/email-smtp-settings.md))
- Less secure than TOTP (email can be intercepted) but better than nothing

## What Is the Email OTP 2FA feature?

Email OTP 2FA uses the user's email address as the second factor. After entering the password, the user receives a 6-digit code via email and must enter it to complete the login.

This is a fallback for users who don't want to use an authenticator app, or for sites where email is the most reliable channel.

## Why You Need It

TOTP 2FA requires an authenticator app, which has barriers:

- **No smartphone**: Some users don't have a smartphone
- **App installation friction**: Users don't want to install yet another app
- **Lost device**: If the user loses their phone, they're locked out
- **Email is universal**: Almost everyone has email and can receive codes

Email OTP 2FA is a good middle ground: better than password-only, more accessible than TOTP.

## Trade-offs vs TOTP

Email OTP is less secure than TOTP because:

- **Email interception**: If the user's email is compromised, the attacker can get the OTP
- **Email delays**: Email delivery can be slow (1-5 minutes), causing login friction
- **Phishing**: Sophisticated phishing kits can intercept emails in real-time

For high-security sites, prefer TOTP. For accessibility, use Email OTP.

---

## How to Use Email OTP 2FA in WordPress

### Step 1: Configure SMTP

Before enabling Email OTP 2FA, configure [SMTP Settings](../email/email-smtp-settings.md) to ensure reliable email delivery. 2FA codes that don't arrive lock users out.

### Step 2: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 3: Go to the Security Tab

Click on the **Security** menu, then click the **Two-Factor Auth** subtab.

### Step 4: Enable Email OTP

Scroll to **Enable Email OTP** and toggle on.

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Enable Email OTP for Your Account

Go to Users > Profile. In the "Two-Factor Authentication" section, enable Email OTP. Click "Send Test Code" to verify it works.

### Step 7: Test

Log out. Log in with your username and password. After the password is verified, a 6-digit code is sent to your email. Enter the code to complete the login.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Email OTP** | Master toggle. | Off |

Each user enables Email OTP individually from their profile. Admins can require it for specific roles from the plugin settings under Security > 2FA.

---

## What Gets Affected

- The login flow: after password, a 6-digit code is sent via email
- The user profile: each user can enable Email OTP
- The WordPress admin: requires 2FA for users with Email OTP enabled
- The email deliverability: must be reliable (use SMTP)

## What Does NOT Get Affected

- The user experience: only 1 extra click per login (after the code is received)
- The TOTP 2FA: still works independently
- The frontend: not affected
- The application passwords: separate authentication method

---

## Advanced Options (Developers)

This feature registers 3 WordPress hooks in `2fa/two-factor-auth.php`:

**Actions:**

- `wp_ajax_nopriv_cm_resend_2fa_email` calls `cm_resend_2fa_email()` (AJAX handler for resending OTP email)

**Filters:**

- `authenticate` calls `CM_Two_Factor_Auth::authenticate()` (Intercepts authentication for email OTP flow (priority 99))
- `cm_2fa_rate_limit_enabled` calls `apply_filters()` (Customizable filter)

```php
// Hooked in 2fa/two-factor-auth.php
add_filter( 'authenticate', 'CM_Two_Factor_Auth::authenticate' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The OTP code is not being sent

**Cause:** Email deliverability issue or the toggle is off.
**Fix:** Verify the toggle is on. Test email delivery (use a plugin like Check Email). Configure [SMTP Settings](../email/email-smtp-settings.md) to use a reliable email service (Gmail SMTP, SendGrid, Mailgun, etc.).

### The OTP code is rejected

**Cause:** The code has expired (default: 10 minutes).
**Fix:** Request a new code. If the issue persists, check the server's time sync (the OTP is time-based).

### The user is locked out of their account

**Cause:** The user can't access their email.
**Fix:** An admin can disable Email OTP for the user from the user profile page. Or the user can use the recovery code (if TOTP is also enabled).

### The OTP code arrives slowly

**Cause:** Email delivery delay (especially with shared hosting).
**Fix:** Use a reliable SMTP service (Gmail SMTP, SendGrid, etc.). Increase the OTP expiration time in the plugin settings under Security > 2FA.

### I want to require Email OTP for specific user roles

**Cause:** Email OTP is opt-in by default.
**Fix:** Require 2FA (TOTP or Email OTP) for specific user roles from the plugin settings under Security > 2FA. Users in those roles will be forced to enable one of the 2FA methods.

---

## Related Articles

- [How to Use TOTP Two-Factor Authentication in WordPress](security-2fa-totp.md)
- [How to Allow Trusted Devices in WordPress](security-2fa-trusted-devices.md)
- [How to Enable 2FA Rate Limiting in WordPress](security-2fa-rate-limiting.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
