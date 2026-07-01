---
title: "How to Apply Content Protection to Administrators in WordPress | CM"
slug: protection-for-admin
description: "Apply content protection (text selection, right-click, etc.) to administrators in WordPress via Classic Monks. By default, content protection excludes admins, but you can opt-in to apply it to admins too."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/protection-for-admin/
---

# How to Apply Content Protection to Administrators in WordPress

> Apply Content Protection to Administrators in Classic Monks turns on all content protection features (text selection, right-click, copy/paste, etc.) for administrators. By default, these features exclude admins, but you can opt-in.

## Key Takeaways

- Single toggle, no nested options
- Master switch for applying content protection to admins
- By default, admins bypass content protection (e.g., they can select text)
- Useful for shared admin environments or compliance requirements
- Affects all content protection features in Classic Monks

## What Is the Protection for Admin feature?

Most content protection features in Classic Monks (Disable Text Selection, Disable Right Click, Disable Copy/Paste, etc.) have a built-in "Apply to Administrators" sub-option. When that sub-option is on (the default), admins are exempt from the content protection.

The Protection for Admin feature is a master switch that overrides all the "Apply to Administrators" sub-options. When enabled, content protection applies to admins too.

## Why You Need It

The default behavior (admins bypass content protection) is correct for most sites. But there are cases where admins should also have the protection:

- **Shared admin environments**: Where multiple admins use the same device
- **Compliance requirements**: Some industries require content protection to apply to all users, including internal staff
- **Demo environments**: Where admins are showing the site to clients and want to demonstrate the protection
- **Standardization**: To ensure consistent behavior across all users

For most sites, the default (admins bypass) is correct. For the above cases, enabling this feature is useful.

## Trade-offs vs excluding admins

Applying content protection to admins has trade-offs:

- **Workflow**: Admins cannot easily copy text from the frontend to use in marketing, support responses, etc.
- **Development**: Devs working on the site cannot easily test the content without disabling the protection
- **Debugging**: Admins may have trouble reporting issues if they cannot see the same view as regular users

For most sites, the trade-offs favor excluding admins.

---

## How to Apply Content Protection to Administrators in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Content Protection** subtab.

### Step 3: Enable Apply to Administrators

Scroll to **Apply to Administrators** and toggle on. This is a master switch that turns on content protection for admins.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Log in as an admin. Visit the frontend. Try to select text, right-click, etc. These actions should now be disabled (if the corresponding content protection features are also enabled).

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Apply to Administrators** | Master toggle to apply content protection to admins. | Off |

No nested options. The toggle overrides the per-feature "Apply to Administrators" sub-options.

---

## What Gets Affected

- The content protection features: all apply to admins
- The admin's workflow: text selection, right-click, etc. are disabled
- The admin's debugging: harder to test the frontend without disabling protection
- The user experience: admins and regular users see the same behavior

## What Does NOT Get Affected

- The admin's own data: the admin can still access the wp-admin
- The admin's content editing: the editor is not affected (only the frontend)
- The content protection features themselves: still toggleable independently
- The "Apply to Administrators" sub-options: still work, but the master switch overrides them

---


## Troubleshooting

### The content protection is still not applying to admins

**Cause:** The toggle is off, or no content protection features are enabled.
**Fix:** Verify the toggle is on. Verify the individual content protection features (Disable Right Click, Disable Text Selection, etc.) are also enabled.

### The admin's workflow is too restricted

**Cause:** The protection is now applying to the admin.
**Fix:** Disable the toggle. Admins will again bypass content protection.

### The "Apply to Administrators" sub-option is not working

**Cause:** The master switch is overriding the per-feature sub-options.
**Fix:** This is by design. The master switch (Apply to Administrators in the master list) overrides the per-feature sub-options. Disable the master switch to use the per-feature sub-options.

### I want to apply protection to some admins but not others

**Cause:** The feature applies to all admins.
**Fix:** Use the `cm_protection_for_admin_enabled` filter to exclude specific admin user IDs. Or use a custom user role (not administrator) for the admins who should be exempt.

### The protection is still being bypassed

**Cause:** The admin is using a non-standard role or capability.
**Fix:** Check the user's role in Users > edit user. Use the `cm_protection_for_admin_roles` filter to add custom roles.

---

## Related Articles

- [How to Disable Right Click in WordPress](security-disable-right-click.md)
- [How to Disable Text Selection in WordPress](security-disable-text-selection.md)
- [How to Disable Copy/Cut/Paste in WordPress](security-disable-copy-paste.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
