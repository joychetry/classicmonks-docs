---
title: "How to Customize the Login Page in WordPress | CM"
slug: wl-login-customization
description: "Customize the WordPress login page in Classic Monks. Change the logo, background, form styling, video settings, and more."
last_updated: 2026-07-28
author: Joy
reading_time: 4 min
canonical: https://classicmonks.com/docs/wl-login-customization/
merged_docs: "How to Loop the Login Video in WordPress, How to Mute the Login Video in WordPress"
---

# How to Customize the Login Page in WordPress

> Customize the WordPress login page in Classic Monks. Change the logo, background, form styling, video settings, and more.

## Key Takeaways

- Customize login page background with colors, images, or videos
- Control video behavior (loop, mute) for dynamic backgrounds
- Quick admin customization with one click
- Does not affect frontend functionality
- Reversible (disable to restore default)

## Why You Need It

The default WordPress login page is plain and unbranded. Customizing it creates a professional first impression for clients.

---

## How to Enable this Feature

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings, then the **White Label** tab.

### Step 2: Enable the Feature

Toggle on **Login Page Customization**.

### Step 3: Configure Video Settings (Optional)

If using a video background:

- **Login Video Loop**: Toggle on to make the background video play continuously instead of stopping after one cycle.
- **Login Video Muted**: Toggle on to prevent the background video from playing audio. This ensures a silent, professional experience.

### Step 4: Save and Test

Click **Save Changes**. Check the login page to verify the customization appears correctly.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Login Page Customization** | Master toggle. Enables custom login page styling. | Off |
| **Login Video Loop** | Makes the background video play continuously. | Off |
| **Login Video Muted** | Prevents the background video from playing audio. | Off |

---

## Common Use Cases

### Client white-labeling

For agencies that build WordPress sites for clients, white-labeling the admin creates a branded experience. The client sees your agency's branding instead of WordPress.

### Brand consistency

For companies that use WordPress as their CMS, white-labeling ensures the admin matches the company's brand guidelines.

### Multi-site management

For companies managing multiple WordPress sites, consistent white-labeling across all sites creates a unified admin experience.

### Dynamic video backgrounds

For companies that want a modern, dynamic login page, video backgrounds with looping and muted settings create a professional first impression without audio distraction.

---

## Troubleshooting

### The feature is not taking effect

**Cause:** The toggle is off, or a caching plugin is serving the old page.
**Fix:** Verify the toggle is on. Clear the admin page cache.

### The feature breaks the admin

**Cause:** The white-label feature may conflict with another admin customization plugin.
**Fix:** Disable other admin customization plugins to find the conflict.

### The video background is not playing

**Cause:** The video file path is incorrect, or the browser blocks autoplay.
**Fix:** Verify the video URL is correct. Ensure the video is muted (browsers block autoplay with audio). Enable the Login Video Muted toggle.

### The video plays with audio

**Cause:** The Login Video Muted toggle is off.
**Fix:** Enable the Login Video Muted toggle to prevent audio playback.

---

## Related Articles

- [How to Use Content Management in WordPress](../core/core-content-management.md)
- [How to Use the Admin Menu Manager in WordPress](white-label-wl-admin-menu-manager.md)
- [How to Add a Custom Login Logo in WordPress](white-label-wl-login-logo.md)

---

## Developer Notes

This feature registers hooks in `custom-login-page.php`:

**Actions:**

- `login_enqueue_scripts` calls `cm_custom_login_page_style()` (injects CSS for login page background, form, navigation; priority 10)
- `login_footer` calls `cm_custom_login_video()` (adds video background to login page; priority 10)
- `login_message` calls `cm_custom_login_message()` (displays custom message on login page; priority 10)

```php
// Hooked in custom-login-page.php
add_action( 'login_enqueue_scripts', 'cm_custom_login_page_style' );
```

The feature modifies WordPress admin output by registering hooks. Disabling it reverses those changes.

### Before you enable this feature

White-label features modify the WordPress admin. Consider:

1. **Client expectations** (white-labeling hides WordPress branding, which may confuse clients)
2. **Brand guidelines** (match the customizations to your brand)
3. **Testing on all admin pages** (some customizations may look wrong on certain pages)
4. **Documentation** (record which customizations are enabled for future reference)

White-label features are designed to be safe, but they modify the admin HTML output. Test on all admin pages before enabling on production.
