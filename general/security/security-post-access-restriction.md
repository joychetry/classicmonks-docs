---
title: "How to Restrict Editor Access to Specific Posts in WordPress | CM"
slug: post-access-restriction
description: "Restrict editor access to specific posts in Classic Monks. Editors can only edit posts they authored or are explicitly granted access to, useful for multi-author sites."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/post-access-restriction/
---

# How to Restrict Editor Access to Specific Posts in WordPress

> Restrict Editor Access in Classic Monks limits editors to viewing and editing only their own posts (or posts explicitly granted to them). Useful for multi-author sites where editors should not see other editors' drafts.

## Key Takeaways

- Single toggle, no nested options
- Editors can only see/edit their own posts
- Admins retain full access to all posts
- Compatible with the WordPress block editor
- Works for posts, pages, and custom post types

## What Is the Restrict Editor Access feature?

By default, WordPress editors can view and edit all posts, regardless of who authored them. The Restrict Editor Access feature limits editors to their own posts (and posts they are explicitly granted access to).

This is useful for multi-author sites where:

- Editors should not see other editors' drafts
- Sensitive content should only be accessible to specific editors
- Workflow separation is needed (e.g., one editor per topic)

## Why You Need It

The default WordPress behavior has issues for multi-author sites:

- **Privacy**: Editors can see all drafts, including private or unfinished posts
- **Workflow confusion**: An editor may edit a post that another editor is working on
- **Information disclosure**: Internal posts (e.g., company news) are visible to all editors
- **Access control**: No way to limit an editor to specific posts

The Restrict Editor Access feature provides per-editor post access control.

---

## How to Restrict Editor Access to Specific Posts in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Content Protection** subtab.

### Step 3: Enable Restrict Editor Access

Scroll to **Restrict Editor Access to Specific Posts** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Log in as an editor (not admin). Go to Posts. You should see only the posts you authored. To edit a post by another author, you need to be granted access.

### Step 6: Grant Access to Specific Posts (Optional)

To allow an editor to access a specific post by another author:

1. Go to the post edit screen (as admin)
2. In the "Post Access" meta box (added by the feature), check the editors who should have access
3. Save the post

The selected editors can now view and edit the post.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Restrict Editor Access to Specific Posts** | Master toggle. | Off |

The Post Access meta box on the post edit screen is where you grant access to specific editors.

---

## What Gets Affected

- The post list: editors see only their own posts (plus posts they're granted)
- The post edit: editors can only edit their own posts (plus posts they're granted)
- The "All Posts" view: not available to editors
- The admin: full access to all posts
- The author filter on the post list: still available (for the editor's own posts)

## What Does NOT Get Affected

- The admin: full access to all posts
- The author profile pages: not affected
- The post author: still the original author
- The post publication: not affected
- The post types: works for posts, pages, and custom post types

---

## Advanced Options (Developers)

This feature registers 5 WordPress hooks in `post-access-restriction.php`:

**Actions:**

- `add_meta_boxes` calls `CM_Post_Access_Restriction::add_access_restriction_meta_box()` (Adds access restriction metabox to posts)
- `save_post` calls `CM_Post_Access_Restriction::save_access_restriction_meta()` (Saves access restriction settings)
- `load-post.php` calls `CM_Post_Access_Restriction::check_post_access()` (Checks access when editing a post)

**Filters:**

- `parse_query` calls `CM_Post_Access_Restriction::filter_posts_for_editors()` (Filters post query for restricted editors)
- `rest_dispatch_request` calls `CM_Post_Access_Restriction::restrict_rest_api_access()` (Restricts REST API access (priority 10))

```php
// Hooked in post-access-restriction.php
add_action( 'add_meta_boxes', 'CM_Post_Access_Restriction::add_access_restriction_meta_box' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The editor can still see all posts

**Cause:** The toggle is off, or the editor is also an admin (admins have full access).
**Fix:** Verify the toggle is on. Verify the editor role is not also an admin. Check the user's role in Users > edit user.

### The editor can't see any posts (including their own)

**Cause:** A role or capability conflict.
**Fix:** Verify the editor role has the `read` capability. Check for plugins that modify editor capabilities. Use the `cm_restrict_editor_access_roles` filter to adjust the restricted roles.

### The "Post Access" meta box is not showing

**Cause:** A plugin conflict or the toggle is off.
**Fix:** Verify the toggle is on. Check the screen options (top right of the post edit screen) to enable the meta box.

### The editor can see the post but can't edit it

**Cause:** The Post Access meta box is granted for view but not edit.
**Fix:** The feature grants both view and edit when an editor is added to the Post Access list. If the editor can only view, there may be a custom role with limited capabilities. Check the user's role and capabilities.

### I want to restrict access to specific pages, not all posts

**Cause:** The feature is global.
**Fix:** Use the `cm_restrict_editor_access_post_types` filter to specify which post types are restricted. For example, restrict only `page` and not `post`.

---

## Related Articles

- [How to Use Site-Wide Password Protection in WordPress](security-site-wide-password.md)
- [How to Enable Spam Comment Protection in WordPress](security-spam-comment-protection.md)
- [How to Manage Users in WordPress](../core/core-users.md)
- [How to Use Content Management in WordPress](../core/core-content-management.md)
