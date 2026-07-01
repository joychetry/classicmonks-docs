---
title: "How to Enable Spam Comment and Review Protection in WordPress | CM"
slug: spam-comment-protection
description: "Enable spam comment and review protection in Classic Monks. Stops spam bots from submitting comments or reviews with multiple layers of protection."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/spam-comment-protection/
---

# How to Enable Spam Comment and Review Protection in WordPress

> Spam Comment and Review Protection in Classic Monks stops spam bots from submitting WordPress comments and WooCommerce reviews. Uses multiple techniques (honeypots, time-traps, content analysis) to identify and block spam.

## Key Takeaways

- Single toggle, no nested options
- Multiple spam detection techniques (no single point of failure)
- Works for both WordPress comments and WooCommerce reviews
- Compatible with Akismet (can run alongside it)
- Configurable via filters for advanced users

## What Is the Spam Comment Protection feature?

Spam comments and reviews are a constant problem for public WordPress sites. Bots scan the web for comment forms and submit spam links, often at scale. The Spam Comment Protection feature uses multiple techniques to identify and block spam:

- **Honeypot fields**: Hidden form fields that bots fill but humans don't
- **Time-trap**: Submissions faster than 3 seconds are flagged as spam
- **Content analysis**: Links, BBCode, and other spam indicators are detected
- **User-agent analysis**: Known bad user agents are blocked
- **Rate limiting**: Too many submissions in a short time are blocked

## Why You Need It

Spam is more than an annoyance:

- **Time waste**: Moderating spam comments is a daily chore
- **SEO damage**: Spam comments with bad links can hurt your search rankings
- **User trust**: A blog full of spam comments looks unmaintained
- **Server load**: Spam bots can hit your site thousands of times per minute
- **Database bloat**: Spam comments fill up your WordPress database

The Spam Comment Protection feature eliminates most spam before it reaches your moderation queue.

## How It Works

The Spam Comment Protection feature works by adding invisible checks to the comment form:

1. **Honeypot field**: A hidden `email` field. Bots fill it; humans don't. If filled, the comment is flagged.
2. **Time-trap**: The form records the time it was rendered. Submissions faster than 3 seconds are flagged (humans need at least 3 seconds to read and write a comment).
3. **Content analysis**: The comment text is checked for known spam indicators (multiple links, certain keywords, BBCode, etc.).
4. **User-agent check**: Known bad user agents (e.g., scrapers, bots) are blocked.
5. **Rate limiting**: Too many submissions from the same IP in a short time are throttled.

If any of these checks fail, the comment is marked as spam or rejected outright.

---

## How to Enable Spam Comment Protection in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Content Protection** subtab.

### Step 3: Enable Spam Comment Protection

Scroll to **Enable Spam Comment and Review Protection** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Test

Submit a test comment on a post. The comment should appear in the moderation queue. Submit another comment within 3 seconds (time-trap). The second comment should be marked as spam.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Spam Comment and Review Protection** | Master toggle. | Off |

No nested options. The detection techniques are configured via filters (see Advanced Options).

---

## What Gets Affected

- The WordPress comment form: protected by the spam detection techniques
- The WooCommerce review form: also protected
- The comment moderation queue: receives less spam
- The comment submission: legitimate comments are unaffected (low false positive rate)
- The Akismet integration: works alongside (Akismet is the final filter)

## What Does NOT Get Affected

- The comment form fields: not changed (the hidden honeypot is added, not visible)
- The user experience: legitimate users don't notice anything
- The comment display: not affected
- The Akismet integration: still works (runs after the spam protection)
- The discussion settings: not changed (still works the same way)

---

## Advanced Options (Developers)

This feature registers 4 WordPress hooks in `spam-comment-protection.php`:

**Actions:**

- `wp_footer` calls `cm_forget_spam_comment_add_action_url()` (Injects action URL via JS (priority 99))
- `init` calls `cm_forget_spam_comment_validate_submission()` (Validates comment submission (priority 1))
- `woocommerce_before_single_product` calls `cm_forget_spam_review_remove_action_url()` (Removes action URL from review form)

**Filters:**

- `comment_form_defaults` calls `cm_forget_spam_comment_remove_action_url()` (Removes action URL from comment form)

```php
// Hooked in spam-comment-protection.php
add_filter( 'comment_form_defaults', 'cm_forget_spam_comment_remove_action_url' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### Legitimate comments are being flagged as spam

**Cause:** The time-trap is too aggressive, or the comment content triggers a pattern.
**Fix:** The time trap is a built-in anti-spam measure. If legitimate comments are being blocked, check that the comment submission isn't being cached. Disable page caching on comment forms.

### Spam is still getting through

**Cause:** The bot is sophisticated and bypasses the spam detection.
**Fix:** Configure spam detection patterns in the plugin settings under Security > Spam Protection. Combine with Akismet for additional protection.

### The honeypot field is being filled by humans

**Cause:** A browser extension is auto-filling all form fields.
**Fix:** This is rare. The feature can detect auto-fillers via the time-trap (submissions faster than 3 seconds are still flagged).

### I want to see what spam is being detected

**Cause:** There's no built-in log.
**Fix:** Check the WordPress comment moderation queue. Comments marked as spam are there. Configure the spam action in the plugin settings under Security > Spam Protection.

### Akismet is conflicting

**Cause:** Akismet runs after the spam protection, but both may flag the same comment.
**Fix:** This is not a conflict. Both run; the spam protection runs first (cheaper), then Akismet. The comment is marked as spam if either detects it.

---

## Related Articles

- [How to Block AI Crawlers in WordPress](security-ai-bot-blocking.md)
- [How to Use a Custom Login URL in WordPress](security-custom-login-url.md)
- [How to Use Math Captcha in WordPress](security-math-captcha.md)
- [How to Configure SMTP Settings in WordPress](../email/email-smtp-settings.md)
