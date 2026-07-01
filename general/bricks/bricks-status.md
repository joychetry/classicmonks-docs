---
title: "How to Check Bricks Builder Status in WordPress | CM"
slug: bricks-status
description: "Check the Bricks Builder integration status in Classic Monks. Verifies theme activation, plugin compatibility, and system requirements."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/bricks-status/
---

# How to Check Bricks Builder Status in WordPress

> The Bricks Status panel in Classic Monks shows the current integration status. Verify that Bricks Builder is installed, activated, and compatible with Classic Monks.

## Key Takeaways

- Read-only diagnostic panel (no toggles)
- Shows Bricks theme activation status
- Shows PHP and WordPress version compatibility
- Shows Classic Monks integration status
- Useful for troubleshooting before enabling features

## What Is the Bricks Status Panel?

The Bricks Status panel is a diagnostic tool in the Bricks Builder tab that shows the current integration status. It verifies:

- Bricks Builder is installed and activated
- The Bricks theme is active
- PHP version meets requirements
- WordPress version meets requirements
- Classic Monks is properly integrated with Bricks

The panel is read-only. It provides information only; it doesn't change any settings.

## Why You Need It

Before enabling any Bricks-related features, you should verify that:

1. **Bricks Builder is installed**: Some features require the Bricks Builder plugin
2. **The theme is active**: The Bricks theme must be active for most features to work
3. **Compatibility**: PHP and WordPress versions must meet the minimum requirements
4. **Integration status**: Classic Monks must be properly integrated with Bricks

The Status panel shows all of this at a glance.

---

## How to Check Bricks Status

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Bricks Tab

Click on the **Bricks** menu. The first subtab is **Bricks Status**.

### Step 3: Review the Status

The Status panel shows:
- Bricks theme: Active / Inactive
- Bricks Builder plugin: Active / Inactive
- PHP version: [version] (minimum 7.4)
- WordPress version: [version] (minimum 6.0)
- Classic Monks integration: Active / Inactive

### Step 4: Fix Any Issues

If any status shows "Inactive" or a version warning, resolve the issue before enabling Bricks features.

---

## Troubleshooting

### Bricks theme shows "Inactive"

**Cause:** The Bricks theme is not the active theme.
**Fix:** Go to Appearance > Themes and activate the Bricks theme.

### Bricks Builder plugin is not installed

**Cause:** The Bricks Builder plugin is not installed or not activated.
**Fix:** Install and activate the Bricks Builder plugin from the WordPress plugin directory or the Bricks website.

### PHP version warning

**Cause:** The server is running an old PHP version.
**Fix:** Update PHP to 7.4 or later. Most hosting providers offer PHP version management in their control panel.

### WordPress version warning

**Cause:** The site is running an old WordPress version.
**Fix:** Update WordPress to 6.0 or later. Use WordPress Updates to update to the latest version.

---

## Related Articles

- [How to Use Bricks AI Builder in WordPress](bricks-ai-builder.md)
- [How to Use Live HTML to Bricks in WordPress](bricks-live-html.md)
- [How to Use Bricks Builder UI Improvements in WordPress](bricks-ui-improvements.md)


### Developer integration

The Bricks status module checks system requirements.

**Utility function:**

- `cm_is_bricks_theme()` checks if the Bricks theme is active
- `cm_bricks_should_enqueue()` checks if Bricks assets should load

**Hooks used:**

- `admin_notices` displays status notices when Bricks is not detected
- `pre_cm_update_option_enable_bricks_setup` toggle function for setup feature

The status check runs on admin_init and compares PHP version, Bricks version, and theme activation state.
