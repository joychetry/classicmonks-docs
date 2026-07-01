---
title: "How to Allow Duplicate Comments in Classic Monks | CM"
slug: allow-duplicate-comments
description: "Allow the same user to comment multiple times on a single post in Classic Monks. Overrides WordPress's default duplicate comment block."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/allow-duplicate-comments/
---

# How to Allow Duplicate Comments in WordPress

> Allow Duplicate Comments lets a single user post multiple comments on the same post, overriding WordPress's default behavior of blocking the second comment from the same author and email.

## Key Takeaways

- Single toggle, no nested options
- Allows the same name+email combo to comment multiple times
- Useful for discussion threads, polls, and multi-part Q&A
- Spam risk: easier for spammers to flood a thread; consider combining with moderation

## What Is the Allow Duplicate Comments feature?

WordPress by default blocks the second comment from a user with the same name and email on the same post. This prevents accidental double-posts and reduces trivial spam. Allow Duplicate Comments disables that check, so the same user can comment as many times as they want on a single post.

## Why You Need It

The default duplicate block is correct for most blogs, but some use cases call for multiple comments from the same user:

- **Discussion threads**: A user wants to reply to multiple comments, not just one
- **Polls or surveys**: The same user voting multiple times (not recommended for actual surveys, but works for casual polls)
- **Multi-part Q&A**: A user asking follow-up questions, each as a separate comment
- **Forums and discussion-heavy sites**: Where conversation flow is more important than duplicate prevention

The toggle is the only setting. The risk is increased spam; combine with comment moderation or Akismet if you enable this on a public site.

---

## How to Use Allow Duplicate Comments in Classic Monks

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Content Subtab

Click on the **Core** menu, then click the **Content** subtab.

### Step 3: Enable Allow Duplicate Comments

Scroll to the **Comment System Overrides** section and toggle on **Allow Duplicate Comments**.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Open any post on the front-end. Submit a comment with a name and email. Then submit a second comment with the same name and email. Both should appear (rather than the second one being blocked with the default "duplicate comment detected" message).

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Allow Duplicate Comments** | Master toggle. Disables WordPress's duplicate check. | Off |

No nested options.

---

## Developer Notes

Allow Duplicate Comments permits the same user to comment multiple times on the same post. No developer hooks are currently exposed.

**Options used:**
| Option | Type | Default |
|--------|------|---------|
| `allow_duplicate_comments` | Boolean | `false` |
---

## Troubleshooting

### Comments are still being blocked as duplicates

**Cause:** The toggle is off, or another plugin is enforcing the duplicate check independently.
**Fix:** Verify the toggle is on. Disable comment-related plugins (Akismet, anti-spam) to see if they have their own duplicate check. Check if a custom theme function is filtering `preprocess_comment`.

### Spam is dramatically increasing after enabling

**Cause:** Bots can now post multiple comments with the same name+email without being blocked, which makes comment spam easier.
**Fix:** Enable comment moderation (Settings > Discussion > "Comment must be manually approved"), install Akismet, or add a CAPTCHA. The duplicate check was a small barrier; replace it with proper moderation.

### Existing comments are still being marked as duplicates in the database

**Cause:** The toggle affects future comments, not past ones. Comments already in the database have their duplicate flag set.
**Fix:** No action needed for past comments. They are displayed normally. The toggle only changes the behavior for new comment submissions.

### I want to allow duplicates only for specific posts

**Cause:** The toggle is global, but you want per-post control.
**Fix:** Use the `cm_allow_duplicate_comments_post_ids` filter to specify a list of post IDs that should allow duplicates. Combine with a default-allow or default-deny filter for the rest.

---

## Related Articles

- [How to Configure Comments in Classic Monks](core-comments.md)
- [How to Disable Comments in Classic Monks](core-disable-comments.md)
