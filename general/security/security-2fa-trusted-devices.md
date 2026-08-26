---
title: "How to Allow Trusted Devices in WordPress"
slug: 2fa-trusted-devices
description: "Allow users to mark devices as trusted in Classic Monks. Avoid 2FA prompts for a configurable period (default 30 days) on devices the user has used before."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/2fa-trusted-devices/
---

# How to Allow Trusted Devices in WordPress

> Trusted Devices in Classic Monks lets users mark a device as trusted after a successful 2FA login. The user is not prompted for 2FA on the same device for a configurable period (default 30 days).

## Key Takeaways

- Single toggle with 1 sub-option (trusted period in days)
- Users can mark a device as trusted after 2FA login
- No 2FA prompts on trusted devices for the configured period
- Each user manages their own trusted devices
- Optional browser fingerprinting for additional security

## What Is the Allow Trusted Devices feature?

2FA improves security but adds friction. Every login requires an extra step. The Allow Trusted Devices feature lets users skip 2FA on devices they've used before.

The user logs in with 2FA once, then checks "Trust this device for X days." Subsequent logins from the same device don't require 2FA until the trust period expires.

## Why You Need It

2FA friction is real:

- **Daily logins**: For users who log in multiple times per day, 2FA adds 30+ seconds per login
- **Multiple devices**: Users with desktop + laptop + tablet need 2FA on each
- **Lost productivity**: For teams that need to log in frequently, 2FA slows them down
- **Support burden**: Lockouts from 2FA (lost device, expired code) create support tickets

Trusted devices reduce friction while maintaining security.

## Trade-offs vs strict 2FA

Trusted devices reduce 2FA's protection:

- **Stolen device**: An attacker with the trusted device can log in without 2FA
- **Compromised browser**: A compromised browser session can persist across logins
- **Cookie theft**: If the auth cookie is stolen, the attacker can bypass 2FA

For high-security sites, don't enable trusted devices. For most sites, the trade-off is acceptable.

---

## How to Allow Trusted Devices in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Two-Factor Auth** subtab.

### Step 3: Enable Allow Trusted Devices

Scroll to **Allow Trusted Devices** and toggle on. Nested options expand.

### Step 4: Set the Trusted Period

Set the **Trusted Period** in days. Common values:

- **7 days**: For high-security sites
- **30 days**: Default, good balance
- **60 days**: For low-risk internal sites
- **90 days**: For very low-risk sites

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Test

Log in with 2FA. After successful login, you should see a "Trust this device for X days" option. Check the box. On subsequent logins from the same device, the 2FA prompt is skipped.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Allow Trusted Devices** | Master toggle. | Off |
| **Trusted Period** | Number of days the device is trusted. | 30 |

---

## What Gets Affected

- The login flow: after 2FA, users can mark the device as trusted
- The 2FA prompts: skipped on trusted devices until the period expires
- The user profile: each user sees a list of their trusted devices
- The auth cookie: includes a "trusted device" flag

## What Does NOT Get Affected

- The first login on a new device: still requires 2FA
- The 2FA setup: still required initially
- The recovery codes: still generated and usable
- The application passwords: separate authentication method

---

## Advanced Options (Developers)

This feature registers 1 WordPress hook in `2fa/two-factor-auth.php`:

**Actions:**

- `wp_login` calls `CM_Two_Factor_Auth::wp_login()` (Manages trusted device cookie after 2FA verification)

```php
// Hooked in 2fa/two-factor-auth.php
add_action( 'wp_login', 'CM_Two_Factor_Auth::wp_login' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The "Trust this device" option is not showing

**Cause:** The toggle is off, or the user is using a device that the system has marked as already trusted.
**Fix:** Verify the toggle is on. Try logging in with a different browser or incognito mode to see the option.

### The trust period is too short

**Cause:** The configured trusted period is short.
**Fix:** Increase the trusted period in the settings. Or adjust the trusted period in the plugin settings under Security > 2FA > Trusted Devices.

### The trust is not being remembered

**Cause:** Cookies are being cleared by browser settings or privacy extensions.
**Fix:** Check browser settings (e.g., "Clear cookies on exit" should be off). Some incognito modes don't persist cookies.

### The user wants to revoke trust for a specific device

**Cause:** The user has a list of trusted devices in their profile.
**Fix:** Go to Users > Profile > "Trusted Devices" section. Click "Revoke" next to the device to remove it from the trusted list.

### Trusted devices are a security risk in my context

**Cause:** The feature is opt-in, but you may want to require all users to use 2FA every time.
**Fix:** Disable the "Allow Trusted Devices" toggle. All logins will require 2FA, with no exception.

---

## Related Articles

- [How to Use TOTP Two-Factor Authentication in WordPress](security-2fa-totp.md)
- [How to Use Email OTP 2FA in WordPress](security-2fa-email.md)
- [How to Enable 2FA Rate Limiting in WordPress](security-2fa-rate-limiting.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
