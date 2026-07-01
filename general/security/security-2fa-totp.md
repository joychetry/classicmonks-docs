---
title: "How to Use TOTP Two-Factor Authentication in WordPress | CM"
slug: security/2fa-totp
description: "Add TOTP-based two-factor authentication to WordPress in Classic Monks. Users scan a QR code with their authenticator app for secure logins."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/security/2fa-totp/
---

# How to Use TOTP Two-Factor Authentication in WordPress

> TOTP 2FA in Classic Monks adds Time-based One-Time Password authentication to WordPress logins. Users scan a QR code with an authenticator app and enter a 6-digit code on each login.

## Key Takeaways

- Single toggle, no nested options
- Adds TOTP (Time-based One-Time Password) authentication
- Compatible with Google Authenticator, Authy, 1Password, and other authenticator apps
- Required for all user roles (configurable via filter)
- Pairs with [Email OTP 2FA](security-2fa-email.md) and [Trusted Devices](security-2fa-trusted-devices.md)

## What Is the TOTP 2FA feature?

TOTP (Time-based One-Time Password) is an industry-standard 2FA method. The user:

1. Enters username and password (first factor)
2. Scans a QR code with an authenticator app (sets up the 2FA)
3. Enters the 6-digit code from the app on each login (second factor)

The code changes every 30 seconds, so even if an attacker captures the code, they can only use it within a short window.

## Why You Need It

Passwords alone are no longer sufficient:

- **Password reuse**: 65% of people reuse passwords across sites
- **Phishing**: Phishing kits can capture passwords in real-time
- **Data breaches**: Massive password dumps are sold on the dark web
- **Brute force**: Automated attacks can test thousands of passwords

2FA adds a second factor that the attacker doesn't have (the user's authenticator app), making stolen passwords useless.

---

## How to Use TOTP 2FA in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Two-Factor Auth** subtab.

### Step 3: Enable TOTP Authentication

Scroll to **Enable TOTP Authentication** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Set Up TOTP for Your Account

Log out. Log in with your username and password. After the password is verified, you'll be prompted to set up TOTP:

1. Scan the QR code with your authenticator app (Google Authenticator, Authy, 1Password, etc.)
2. Enter the 6-digit code shown in the app
3. Save the recovery codes shown after setup (in case you lose access to the app)

### Step 6: Test

Log out. Log in. You'll be prompted for the 6-digit code from your authenticator app after entering your password.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable TOTP Authentication** | Master toggle. | Off |

The TOTP app is configured by each user individually. Admins can require 2FA for specific roles from the plugin settings under Security > 2FA.

---

## What Gets Affected

- The login flow: after password, users are prompted for a 6-digit code
- The user profile: each user has a TOTP setup and recovery codes
- The WordPress admin: requires 2FA for users with TOTP enabled
- The REST API: 2FA can be required for API access via the `cm_2fa_required_for_api` filter

## What Does NOT Get Affected

- The user experience (after setup): only 1 extra click per login
- The frontend: not affected (only admin/editor logins are typically 2FA-protected)
- The password reset flow: separate flow, not affected
- The application passwords: separate authentication method

---

## Advanced Options (Developers)

This feature registers 6 WordPress hooks in `2fa/two-factor-auth.php`:

**Actions:**

- `wp_login` calls `CM_Two_Factor_Auth::wp_login()` (Triggers 2FA after successful password auth (priority 10))
- `show_user_profile` calls `CM_Two_Factor_Auth::user_profile_fields()` (Adds 2FA fields to user profile)
- `personal_options_update` calls `CM_Two_Factor_Auth::user_profile_update()` (Saves 2FA settings on profile update)
- `login_enqueue_scripts` calls `CM_Two_Factor_Auth::enqueue_scripts()` (Enqueues 2FA verification page scripts)

**Filters:**

- `authenticate` calls `CM_Two_Factor_Auth::authenticate()` (Intercepts authentication for 2FA flow (priority 99))
- `cm_2fa_rate_limit_enabled` calls `apply_filters()` (Customizable filter)

```php
// Hooked in 2fa/two-factor-auth.php
add_filter( 'authenticate', 'CM_Two_Factor_Auth::authenticate' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The user is locked out of their account

**Cause:** The user lost access to their authenticator app and didn't save recovery codes.
**Fix:** An admin can reset the user's 2FA from the user profile page (Users > edit user > "Reset 2FA" button). Or the user can use a recovery code.

### The 6-digit code is rejected

**Cause:** Time sync issue between the server and the user's device.
**Fix:** Ensure the server's time is synced (use NTP). The TOTP code is time-based, so any significant time drift will cause failures.

### The QR code is not scanning

**Cause:** The QR code is too small or the user is using an app that doesn't support QR scanning.
**Fix:** Most authenticator apps support QR scanning. If the user is using a manual entry, the secret key is shown below the QR code and can be entered manually.

### The 2FA is not required for my user role

**Cause:** The 2FA toggle is on, but the user role is not in the required roles.
**Fix:** Add the user role in the plugin settings under Security > 2FA. Or have the user enable 2FA manually from their profile page.

### I want to use TOTP with my team's authenticator app (e.g., 1Password, Authy)

**Cause:** Different apps have different QR code scanning behaviors.
**Fix:** TOTP is an open standard. All major authenticator apps (Google Authenticator, Authy, 1Password, Bitwarden, etc.) support it. The user can use any compatible app.

---

## Related Articles

- [How to Use Email OTP 2FA in WordPress](security-2fa-email.md)
- [How to Allow Trusted Devices in WordPress](security-2fa-trusted-devices.md)
- [How to Enable 2FA Rate Limiting in WordPress](security-2fa-rate-limiting.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
