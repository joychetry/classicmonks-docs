---
title: "How to Block AI Crawlers in WordPress | CM"
slug: security/ai-bot-blocking
description: "Block AI crawlers (GPTBot, ClaudeBot, CCBot, etc.) in Classic Monks. Prevents your content from being used to train AI models without your consent."
last_updated: 2026-06-24
author: Joy
reading_time: 3 min
canonical: https://classicmonks.com/docs/security/ai-bot-blocking/
---

# How to Block AI Crawlers in WordPress

> Block AI Crawlers in Classic Monks blocks the major AI training crawlers (GPTBot, ClaudeBot, CCBot, etc.) from accessing your site. Prevents your content from being used to train AI models without your consent.

## Key Takeaways

- Single toggle, no nested options
- Blocks 10+ major AI crawlers
- Updates the robots.txt automatically
- Logs blocked requests for verification
- Optional user-agent whitelist for whitelisted crawlers

## What Is the Block AI Crawlers feature?

AI companies train their models on web content. To collect this content, they use crawlers (bots) that scan websites and ingest the content. The major AI companies have identified crawlers:

- **OpenAI**: GPTBot, ChatGPT-User, OAI-SearchBot
- **Anthropic**: ClaudeBot, Claude-User, Claude-SearchBot
- **Google**: Google-Extended
- **Common Crawl**: CCBot
- **Meta**: Meta-ExternalAgent, Meta-ExternalFetcher
- **Perplexity**: PerplexityBot
- **Apple**: Applebot-Extended
- **Bytespider**: Bytespider (TikTok)
- **Amazon**: Amazonbot
- **Cohere**: cohere-ai

The Block AI Crawlers feature blocks all of these from accessing your site.

## Why You Need It

AI training has become a contentious issue:

- **Consent**: Your content may be used to train AI models that compete with you
- **Attribution**: AI models may use your content without credit
- **Server load**: AI crawlers are aggressive and can strain your server
- **Bandwidth**: AI crawlers can consume significant bandwidth
- **Terms of service**: Some users explicitly want their content excluded from AI training

The Block AI Crawlers feature is for users who want to opt out of AI training.

## Trade-offs vs allowing AI crawlers

Blocking AI crawlers has trade-offs:

- **Reduced AI search visibility**: Google's AI Overviews and other AI search features may not include your content
- **Future AI features**: As AI becomes more integrated into search, blocked sites may be disadvantaged
- **No clear opt-out from major AI companies**: Some companies (notably OpenAI) have stated they respect robots.txt; others have not

For most sites, the trade-off is acceptable. The content you publish is yours to control.

---

## How to Block AI Crawlers in WordPress

### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

### Step 2: Go to the Security Tab

Click on the **Security** menu, then click the **Content Protection** subtab.

### Step 3: Enable Block AI Crawlers

Scroll to **Block AI Crawlers** and toggle on.

### Step 4: Save Changes

Click **Save Changes**.

### Step 5: Verify

Visit `https://yoursite.com/robots.txt`. You should see entries like:

```
User-agent: GPTBot
Disallow: /

User-agent: ClaudeBot
Disallow: /

User-agent: CCBot
Disallow: /
```

### Step 6: Test

Use a tool like [OpenAI's GPTBot verification](https://platform.openai.com/docs/gptbot) or your server logs to verify that the AI crawlers are being blocked.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Block AI Crawlers** | Master toggle. | Off |

No nested options. The blocked crawlers list is maintained by Classic Monks and updated as new crawlers emerge.

---

## What Gets Affected

- The robots.txt: updated to disallow AI crawlers
- The AI crawler requests: blocked at the server level
- The AI search visibility: AI search engines may not include your content
- The server load: reduced (AI crawlers are aggressive)

## What Does NOT Get Affected

- The regular search engines: Google, Bing, etc. are not blocked
- The human visitors: not affected
- The WordPress admin: not affected
- The API access: not affected (only the crawlers are blocked)

---

## Advanced Options (Developers)

This feature registers 2 WordPress hooks in `ai-bot-blocker.php`:

**Actions:**

- `wp_loaded` calls `CM_AI_Bot_Blocker::block_ai_user_agents()` (Blocks known AI bot user agents)

**Filters:**

- `robots_txt` calls `CM_AI_Bot_Blocker::modify_robots_txt()` (Adds AI bot disallow rules to robots.txt (priority 10))

```php
// Hooked in ai-bot-blocker.php
add_action( 'wp_loaded', 'CM_AI_Bot_Blocker::block_ai_user_agents' );
```

The feature modifies WordPress behavior by registering or removing hooks. Disabling it reverses those changes and WordPress returns to its default behavior.

## Troubleshooting

### The AI crawlers are still accessing the site

**Cause:** The robots.txt is updated, but some AI crawlers ignore robots.txt.
**Fix:** Add blocking rules to your server configuration (Apache .htaccess or Nginx config) to return 403 for known AI crawlers. This is more reliable than robots.txt alone.

### The robots.txt doesn't show the AI crawlers

**Cause:** A caching plugin is serving the old robots.txt, or another plugin is overriding it.
**Fix:** Clear all caching layers. Check that no other plugin is modifying the robots.txt.

### I want to allow specific AI crawlers

**Cause:** The block list is comprehensive.
**Fix:** If a legitimate bot is being blocked, you can whitelist it by adding its user agent to your server configuration (Apache .htaccess or Nginx config).

### A new AI crawler is not in the block list

**Cause:** The AI crawler was added after the plugin was released.
**Fix:** The plugin will be updated in a future release to include new crawlers. In the meantime, you can add blocking rules to your server configuration.

### The AI search engines still show my content

**Cause:** Some AI search engines use the regular search engine index, not their own crawler.
**Fix:** Disabling AI crawlers doesn't remove content from existing search indexes. The content will fade over time as the search indexes are updated. For immediate removal, contact the AI search engine directly.

---

## Related Articles

- [How to Use Site-Wide Password Protection in WordPress](security-site-wide-password.md)
- [How to Use Staging Protection in WordPress](security-staging-protection.md)
- [How to Disable XML-RPC in WordPress](security-disable-xmlrpc.md)
- [How to Use the Email Tab in Classic Monks: Feature Index](../email.md)
