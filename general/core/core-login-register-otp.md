---
title: "How to Add Login & Register Forms With OTP in Classic Monks | CM"
slug: login-register-otp
description: "Add OTP-based login and registration forms in Classic Monks. Phone and email OTP with Twilio, Firebase, or custom SMS provider. Shortcodes, WooCommerce integration, and wp-login replacement."
last_updated: 2026-07-23
author: Joy
reading_time: 8 min
canonical: https://classicmonks.com/docs/login-register-otp/
---

# How to Add Login & Register Forms With OTP in WordPress

> Classic Monks includes a complete login and registration system with one-time password (OTP) verification via phone or email, replacing the default WordPress login with inline shortcode-based forms.

## Key Takeaways

- Add login, register, and lost-password forms anywhere with `[cm_login_form]` shortcode
- OTP verification works with Phone (Twilio, Firebase, or Custom SMS provider) and Email (WordPress or WooCommerce template)
- Replace the default wp-login.php and WooCommerce my-account login with OTP-powered forms
- Full style customization: colors, fonts, borders, header image, and custom CSS
- Supports password + OTP dual authentication and automatic login after registration

---

## What Is Login & Register Forms With OTP?

Login and Register Forms With OTP is a complete authentication system in Classic Monks. It adds a dedicated submenu under **Classic Monks > Login** where you configure every aspect of the inline forms, OTP delivery, and integration options.

The system generates frontend login, registration, and password-reset forms that can be placed anywhere via shortcode, or configured to replace the default WordPress `wp-login.php` and WooCommerce my-account login. OTP codes are delivered by phone (via Twilio, Firebase Authentication, or a custom SMS endpoint) or email (using the WordPress or WooCommerce email template engine).

---

## Why You Need It

The default WordPress login screen works for basic sites but falls short for modern use cases:

- **Passwordless login** -- Users prefer a one-time code sent to their phone or email over remembering complex passwords
- **Registration verification** -- OTP ensures the phone number or email is real before creating an account, reducing spam registrations
- **WooCommerce checkout** -- Verify a customer's phone during checkout for delivery confirmation and fraud prevention
- **Custom branding** -- Match the login experience to your site's look and feel instead of the standard WordPress login page

With Classic Monks, you get all of this in one feature with no third-party plugin dependencies beyond the OTP provider itself.

---

## How to Enable Login & Register Forms With OTP in Classic Monks

### Step 1: Navigate to Classic Monks Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Core Tab

Click on the **Core** menu.

### Step 3: Open the Users Subtab

Click the **Users** subtab in the left sub-navigation.

### Step 4: Enable the Feature

Toggle on **Login & Register Forms With OTP**. The toggle has a submenu indicator (the `«` icon) that signals it adds a new submenu to the admin sidebar.

![Login & Register Forms With OTP toggle in Core > Users subtab](../../images/core/users/login-register-otp-toggle.jpg)

### Step 5: Save and Reload

Click **Save Changes**, then reload the page. A new **Login** submenu appears under **Classic Monks** in the admin sidebar.

### Step 6: Open the Login Settings

Click **Classic Monks > Login** to open the settings page. Six tabs are available:

1. **General** -- Form behavior, registration role, password reset method, surfaces
2. **Fields** -- Form field labels and placeholder text
3. **OTP** -- OTP methods, phone number format, email OTP, checkout OTP
4. **Providers** -- SMS provider configuration (Twilio, Firebase, Custom)
5. **Style** -- Form appearance, colors, header image, custom CSS
6. **Shortcodes** -- Shortcode reference and copy-to-clipboard helper

![Classic Monks > Login settings page showing the six configuration tabs](../../images/core/login/login-settings-page.jpg)

---

## Configuration Options

### General Tab

The General tab has five subtabs:

**Forms:**

| Option | Description | Default |
|--------|-------------|---------|
| Form Pattern | Display login and register as separate forms or a single combined form | Separate |
| Navigation Pattern | Tab bar, text links, or no navigation between forms | Tabs |
| Enable Registration | Allow new users to register via the form | On |
| Default Role | Role assigned to new registrations | Subscriber (Customer if WooCommerce active) |
| Auto Login After Registration | Log the user in automatically after sign-up | On |
| Enable Password Login | Show the password field alongside OTP option | On |
| Reset Password Method | Email reset link (WordPress default) or email verification code | Link |

**Texts:** Customize every button label and form heading -- Login tab, Sign-up tab, Sign in button, Sign Up button, Email Reset Link button, Continue button, and the intro text for each form.

**Redirects:** Set custom redirect URLs after login, registration, and logout. Leave empty to redirect to the homepage.

**Integrations:** Control where the forms appear -- replace `wp-login.php`, show in WooCommerce my-account, show at WooCommerce checkout.

**Debug:** Enable debug mode to log OTP events for troubleshooting. Accessible only to administrators.

### OTP Tab

| Subtab | Options |
|--------|---------|
| Methods | Enable phone OTP, enable email OTP, OTP digit count (4-8), OTP expiry (seconds), resend limit, incorrect attempt limit, ban duration, resend cooldown |
| Rules | Dual operator routing -- send phone OTP via an alternate provider for specific countries |
| Phone | Country code display (select box or input), default country (geolocation or custom), allowed countries, strip leading zero |
| Email | Email OTP subject, body, sender name/email, template engine (WordPress or WooCommerce), optional branding with logo and footer |
| Checkout | Enable checkout OTP verification, checkout priority, billing phone behavior, always verify at checkout |

### Providers Tab

| Subtab | Purpose |
|--------|---------|
| Twilio | Account SID, Auth Token, and From number for Twilio SMS |
| Firebase | Firebase API Key and Firebase config (JSON) for Firebase Authentication |
| Custom | Custom SMS endpoint URL, HTTP method (POST/GET), request format (form or JSON), phone format, default country code, custom request body, and auth type (none/bearer/basic) |
| Routing | (See Dual Operator in OTP > Rules) |
| Test | Send a test OTP to verify your provider configuration is working |

### Style Tab

| Subtab | Options |
|--------|---------|
| Header | Header image, image width, alignment |
| Form | Background color, accent color, border radius, border color, padding, max width, shadow toggle, background mode color |
| Fields | Input height, background color, text color, border, border width, focus colors, field bottom margin, label color, icon color, placeholder color, OTP button colors, required indicator |
| Custom | Custom CSS for advanced styling |

---

## Shortcodes Tab

The **Shortcodes** tab provides a visual shortcode builder with copy-to-clipboard functionality.

![Shortcodes tab showing the shortcode preview, copy button, and quick examples](../../images/core/login/shortcodes-tab.jpg)

### How to Use the Shortcode Builder

### Step 1: Choose Which Forms to Include

Under **Include forms**, check the boxes for the forms you want in this shortcode instance:

- **Login** (checked by default)
- **Register**
- **Lost password**

### Step 2: Configure Display Options

Override the global form layout for this shortcode only:

- **Default form**: Which form is active on load (Login, Register, or Lost password)
- **Form pattern**: Separate forms or single field (email first)
- **Navigation style**: Tabs, footer links, or disable navigation

Leave any option set to **Global setting** to inherit from the General tab.

### Step 3: Set Per-Shortcode Redirects

Set custom redirect URLs after login or registration:

- **Login redirect**: Same page or a custom URL
- **Register redirect**: Same page or a custom URL

### Step 4: Copy the Shortcode

Click **Copy shortcode** to copy the generated shortcode to your clipboard. Paste it into any page, post, or widget area.

The generated shortcode looks like:

```markdown
[cm_login_form forms="login,register" active="login"]
```

### Quick Examples

The tab also provides common starting points:

| Example | Shortcode |
|---------|-----------|
| Basic form | `[cm_login_form]` |
| Login only | `[cm_login_form active="login" forms="login"]` |
| Login and register | `[cm_login_form active="register" forms="login,register"]` |
| Lost password | `[cm_login_form active="lostpw" forms="lostpw"]` |

---

## Shortcode Attributes

Use the `[cm_login_form]` shortcode to place forms anywhere on your site.

```markdown
[cm_login_form active="login" forms="login,register,lostpw"]
```

**Attributes:**

| Attribute | Values | Default | Description |
|-----------|--------|---------|-------------|
| `active` | `login`, `register`, `lostpw` | `login` | Which form is active on load |
| `forms` | Comma-separated: `login,register,lostpw` | All enabled | Which forms to show |
| `pattern` | `separate`, `single` | Global setting | Override the form pattern |
| `navstyle` | `tabs`, `links`, `disable` | Global setting | Override the navigation style |
| `login_redirect` | URL | Global setting | Redirect after login |
| `register_redirect` | URL | Global setting | Redirect after registration |

**Examples:**

```markdown
<!-- Login form only -->
[cm_login_form active="login" forms="login"]

<!-- Login and register with tabs -->
[cm_login_form active="register" forms="login,register"]

<!-- Lost password form -->
[cm_login_form active="lostpw" forms="lostpw"]

<!-- Full set with custom redirects -->
[cm_login_form active="login" forms="login,register,lostpw" login_redirect="/dashboard" register_redirect="/welcome"]
```

---

## WooCommerce Integration

When WooCommerce is active, the feature integrates with:

- **My Account Page** -- Replace the default WooCommerce login form with the OTP form
- **Checkout** -- Add phone verification during checkout. Customers can verify their phone number and the phone is saved to the order's billing info
- **Registration Default Role** -- Automatically switches to `customer` role instead of `subscriber` when WooCommerce is detected

Configure these under **General > Integrations** and **OTP > Checkout**.

---

## wp-login.php Replacement

Enable **Replace Default WordPress Login** under **General > Surfaces** to redirect `wp-login.php` to the inline form. When enabled:

- Visitors to `wp-login.php` see the custom form instead of the default WordPress login
- The password reset flow uses the feature's email-based reset (link or code)
- Administrators can still access `wp-login.php?action=login` directly by appending the query parameter

---

## Troubleshooting

### OTP Not Being Sent

**Cause:** The SMS provider is not configured correctly or the provider credentials are invalid.
**Fix:** Go to **Classic Monks > Login > Providers**, verify your Twilio SID/Auth Token or Firebase API key, and use the **Test** tab to send a test OTP. Check the debug log if enabled.

### OTP Email Not Arriving

**Cause:** The email is being blocked by the server or going to spam.
**Fix:** Check your server's email delivery logs. Configure a dedicated SMTP provider using the Classic Monks Email tab to improve deliverability. Verify the email OTP template under **OTP > Email**.

### Phone Number Format Not Accepted

**Cause:** The country code is missing or the format does not match the provider's expectations.
**Fix:** Ensure the country code select box is showing. If using a Custom provider, verify the phone format under **OTP > Phone > Country Code Display** and **Providers > Custom > Phone Format**.

### Form Not Showing on the Frontend

**Cause:** The shortcode is misspelled or the feature is enabled but the page was not reloaded.
**Fix:** Verify the shortcode is `[cm_login_form]` (with underscores). Reload the admin page after enabling the feature. Check that the user has the correct role to view the form.

### WooCommerce Checkout Phone Verification Not Working

**Cause:** Checkout OTP is disabled or the billing phone field is conflicting with the OTP phone field.
**Fix:** Enable **OTP at Checkout** under **OTP > Checkout**. Set the billing phone behavior to merge the OTP phone with the billing address or keep them separate.

### User Cannot Register

**Cause:** Registration is disabled in the General settings or WordPress itself.
**Fix:** Check **General > Main > Enable Registration** is on. Also verify that **Settings > General > Membership > Anyone can register** is enabled in WordPress.

---

## Related Articles

- [How to Manage Users in Classic Monks (WordPress)](../core/core-users.md)
- [How to Enable Two-Factor Authentication in Classic Monks](../security/security-2fa-totp.md)
- [How to Set Up Email Logging and SMTP in Classic Monks](../email/email-logging.md)
