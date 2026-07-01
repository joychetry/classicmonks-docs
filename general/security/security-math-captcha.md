---
title: "How to Use Math Captcha in WordPress | CM"
slug: math-captcha
description: "Add math-based captcha challenges to WordPress, WooCommerce, and comment forms in Classic Monks. Privacy-friendly alternative to image-based captchas that doesn't depend on third-party services."
last_updated: 2026-06-24
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/math-captcha/
---

# How to Use Math Captcha in WordPress

> Add math-based captcha challenges to WordPress, WooCommerce, and comment forms in Classic Monks. A privacy-friendly alternative to image-based captchas that doesn't require third-party services.

## Key Takeaways

- Single toggle with 4 sub-options (form scope)
- Adds a simple math problem to forms ("What is 3 + 5?")
- Privacy-friendly: no third-party service, no tracking
- Self-contained: doesn't depend on external APIs
- Configurable per form type (WP, WC, comments, frontend)

## What Is the Math Captcha feature?

The Math Captcha feature adds a simple math problem to your forms. Users see a question like "What is 3 + 5?" and must enter the correct answer. This is a self-contained captcha that doesn't depend on Google, Cloudflare, or any third-party service.

## Why You Need It

Traditional captchas have trade-offs:

- **Image captchas**: Bad for accessibility, can be bypassed by OCR
- **Google reCAPTCHA**: Tracks users across the web, requires Google account
- **Cloudflare Turnstile**: Requires Cloudflare account, can be rate-limited
- **hCaptcha**: Better than reCAPTCHA but still some tracking

Math captcha is different:

- **No external service**: Self-contained, no third-party API calls
- **No tracking**: Doesn't follow users across the web
- **Accessibility-friendly**: Doesn't require identifying objects in images
- **Language-independent**: Numbers are universal

For most basic spam protection, math captcha is sufficient.

---

## How to Use Math Captcha in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **WP Protection** subtab.

### Step 3: Enable Math Captcha

Scroll to **Enable Math Captcha** and toggle on. Nested options expand.

### Step 4: Configure Form Scope

Select which forms get the math captcha:

- **WordPress Login Forms**: Login, registration, password reset
- **WooCommerce Forms**: Login, registration, checkout
- **Comment Forms**: Standard WordPress comments
- **Frontend Post Submission**: Frontend post submission plugins

### Step 5: Save Changes

Click **Save Changes**.

### Step 6: Test

Visit the login form (or whatever form you enabled). The math captcha should appear.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Math Captcha** | Master toggle. | Off |
| **WordPress Login Forms** | Apply to WP login forms. | On |
| **WooCommerce Forms** | Apply to WC forms. | On |
| **Comment Forms** | Apply to comments. | On |
| **Frontend Post Submission** | Apply to frontend submission forms. | On |

The math problem is randomly generated for each form load. The numbers are between 1 and 10 by default.

---

## What Gets Affected

- The login form: shows a math captcha
- The registration form: shows a math captcha
- The password reset form: shows a math captcha
- WooCommerce forms: shows a math captcha
- The comment form: shows a math captcha
- Form submission: requires the correct answer to succeed

## What Does NOT Get Affected

- The admin (after login): not affected
- The form fields: only the captcha is added
- The user experience: math problems are quick (1-2 seconds)
- The form data: submitted normally once captcha passes

---

## Advanced Options (Developers)

This feature registers 6 WordPress hooks in `math-captcha.php`:

**Actions:**

- `login_form` calls `CM_Math_Captcha::render_captcha()` (Renders captcha on login form)
- `register_form` calls `CM_Math_Captcha::render_captcha()` (Renders captcha on registration form)
- `woocommerce_login_form` calls `CM_Math_Captcha::render_captcha()` (Renders captcha on WooCommerce login)

**Filters:**

- `authenticate` calls `CM_Math_Captcha::validate_login_captcha()` (Validates captcha during login (priority 30))
- `comment_form_field_comment` calls `CM_Math_Captcha::add_captcha_to_comment_form()` (Adds captcha to comment form)
- `preprocess_comment` calls `CM_Math_Captcha::validate_comment_captcha()` (Validates captcha for comments)

```php
// Hooked in math-captcha.php
add_action( 'login_form', 'CM_Math_Captcha::render_captcha' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### Math captcha is not showing

**Cause:** The toggle is off, or the form scope doesn't include the form you're testing.
**Fix:** Verify the toggle is on. Verify the form scope includes the form (e.g., WP Login Forms for the login form).

### Math captcha is showing but the form rejects correct answers

**Cause:** A JavaScript error or theme conflict is preventing the form from submitting.
**Fix:** Check the browser console for errors. Disable other form-related plugins to find the conflict. Test with a default theme.

### The math problem is too easy

**Cause:** The default range is 1-10 with addition only.
**Fix:** The captcha uses simple addition and subtraction by default. If you need harder questions, consider using the Cloudflare Turnstile feature instead.

### The math problem is too hard for some users

**Cause:** The math may be challenging for users with cognitive disabilities or non-native speakers.
**Fix:** Use a smaller number range. Consider adding an audio captcha option. Some sites provide both math and image captcha options.

### The captcha is bypassed by automated bots

**Cause:** Sophisticated bots can solve math captchas.
**Fix:** For high-value forms (login, registration), use Cloudflare Turnstile instead. For low-value forms (comments), math captcha is usually sufficient. Consider adding Login Lockdown to complement.

---

## Related Articles

- [How to Use Cloudflare Turnstile in WordPress](security-cloudflare-turnstile.md)
- [How to Use a Custom Login URL in WordPress](security-custom-login-url.md)
- [How to Enable Login Lockdown in WordPress](security-login-lockdown.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
