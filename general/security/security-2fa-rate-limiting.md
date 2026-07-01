---
title: "How to Enable 2FA Rate Limiting in WordPress | CM"
slug: 2fa-rate-limiting
description: "Add rate limiting to 2FA verification in Classic Monks. Locks out users after too many failed 2FA attempts to prevent brute force attacks on the second factor."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/2fa-rate-limiting/
---

# How to Enable 2FA Rate Limiting in WordPress

> 2FA Rate Limiting in Classic Monks locks out users after too many failed 2FA attempts. Prevents brute force attacks on the 6-digit code (which has only 1M possible values).

## Key Takeaways

- Single toggle with 3 sub-options (max attempts, window, lockout duration)
- Protects against brute force attacks on 2FA codes
- Configurable per user or per IP
- Pairs with [Login Lockdown](security-login-lockdown.md) for defense in depth
- Returns 403 or shows an error after the threshold

## What Is the 2FA Rate Limiting feature?

2FA codes (TOTP or Email OTP) are 6 digits, which means 1 million possible values. An attacker who knows a username can try 1 million codes to find the right one. At 100 attempts per second, that's ~3 hours to brute force.

The 2FA Rate Limiting feature prevents this by locking out the user (or IP) after a configurable number of failed attempts.

## Why You Need It

2FA without rate limiting is a weak 2FA:

- **Brute force feasible**: 1M codes is large but not infinite
- **Real-time phishing**: Attackers can phish a code in real-time
- **Code reuse**: If the same code is captured, the attacker has 30 seconds to use it
- **Knowledge of username**: Combined with username enumeration, the attack is targeted

Rate limiting eliminates the brute force vector.

---

## How to Enable 2FA Rate Limiting in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Two-Factor Auth** subtab.

### Step 3: Enable 2FA Rate Limiting

Scroll to **Enable 2FA Rate Limiting** and toggle on. Nested options expand.

### Step 4: Configure the Threshold

Set the **Max Attempts**. Common values:

- **3**: Aggressive (locks out quickly, may lock out legitimate users who mistype)
- **5**: Default, good balance
- **10**: Permissive (only locks out persistent attackers)

### Step 5: Configure the Window

Set the **Time Window** in minutes. The counter resets after this window with no failed attempts. Common values:

- **5 minutes**: Aggressive
- **15 minutes**: Default
- **30 minutes**: Permissive

### Step 6: Configure the Lockout

Set the **Lockout Duration** in minutes. How long the user is locked out after exceeding the threshold:

- **5 minutes**: Quick recovery
- **30 minutes**: Default
- **60 minutes**: Stronger protection

### Step 7: Save Changes

Click **Save Changes**.

### Step 8: Test

Log in with a username and password. Enter wrong 2FA codes 3 times. The 4th attempt should be locked out.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable 2FA Rate Limiting** | Master toggle. | Off |
| **Max Attempts** | Number of failed attempts before lockout. | 3 |
| **Time Window** | Reset window in minutes. | 15 |
| **Lockout Duration** | Lockout duration in minutes. | 30 |

---

## What Gets Affected

- The 2FA verification: tracks failed attempts
- The user: locked out after the threshold
- The login flow: returns 403 or error after lockout
- The auth cookie: not affected (only 2FA is rate-limited)

## What Does NOT Get Affected

- The password login: not rate-limited (use [Login Lockdown](security-login-lockdown.md) for that)
- The REST API: not affected
- The TOTP 2FA: still works (just rate-limited)
- The Email OTP 2FA: still works (just rate-limited)
- The recovery codes: still work (but also rate-limited)

---

## Advanced Options (Developers)

This feature registers 2 WordPress hooks in `2fa/two-factor-auth.php`:

**Filters:**

- `authenticate` calls `CM_Two_Factor_Auth::authenticate()` (Checks rate limit during 2FA verification)
- `cm_2fa_rate_limit_enabled` calls `apply_filters()` (Customizable filter)

```php
// Hooked in 2fa/two-factor-auth.php
add_filter( 'authenticate', 'CM_Two_Factor_Auth::authenticate' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The user is locked out

**Cause:** The user exceeded the max attempts.
**Fix:** Wait for the lockout duration. An admin can reset the rate limit for the user from the user profile.

### The lockout is too aggressive

**Cause:** The max attempts is too low.
**Fix:** Increase the max attempts. Or use the `cm_2fa_rate_limit_max_attempts` filter to customize per user role.

### Legitimate users are being locked out

**Cause:** The threshold is too low for typical user behavior (e.g., users who retry the code after a clock drift).
**Fix:** Increase the max attempts or the time window. Educate users to wait for the code to refresh before retrying.

### The rate limit is not triggering

**Cause:** The toggle is off, or a caching plugin is bypassing the 2FA check.
**Fix:** Verify the toggle is on. The 2FA check happens after the password, so caching should not be an issue unless the entire 2FA flow is cached (which is unusual).

### I want to log rate limit hits

**Cause:** There's no built-in logging.
**Fix:** Use the `cm_2fa_rate_limit_triggered` action to log to your own system. Or use a security plugin that integrates with the WordPress activity log.

---

## Related Articles

- [How to Use TOTP Two-Factor Authentication in WordPress](security-2fa-totp.md)
- [How to Use Email OTP 2FA in WordPress](security-2fa-email.md)
- [How to Allow Trusted Devices in WordPress](security-2fa-trusted-devices.md)
- [How to Enable Login Lockdown in WordPress](security-login-lockdown.md)
