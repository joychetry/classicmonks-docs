# Classic Monks Documentation Style Guide

This guide defines how every Classic Monks documentation article should be written, structured, and formatted. Follow it for consistency across all docs.

---

## Article Structure

Every article MUST follow this template:

```
# [Descriptive H1 Title]

> [One-line summary — the "TL;DR" for skimmers]

## Key Takeaways
- Bullet 1: What the feature does
- Bullet 2: Why it matters (performance/UX/business benefit)
- Bullet 3: Key requirement or caveat

## What Is [Feature Name]?
[2-3 sentences explaining the concept. No jargon. Write for someone who
has heard the term but doesn't know how it works in WordPress.]

## Why You Need It
[Real-world problem this solves. Cite a metric, a warning from PageSpeed
Insights, or a common pain point. Make the reader feel the problem before
offering the solution.]

## How to Enable [Feature] in Classic Monks
### Step 1: Navigate to Settings
### Step 2: Configure Options
### Step 3: Save and Verify

## Configuration Options
[Table or bullet list of every toggle/field with a one-line explanation]

## Advanced Options (Developers)
[Filters, hooks, PHP snippets. Only for features that have them.]

## Troubleshooting
[Common issues and fixes — max 3-5 items]

## Related Articles
[Links to 2-3 related Classic Monks docs]
```

---

## Title Conventions

- **Format:** `How to [Action] in WordPress` (brand in SEO title, not in H1)
- **Examples:**
  - "How to Add Code Snippets in WordPress (PHP, CSS, JS)"
  - "How to Set Up the AI Agent in WordPress"
  - "How to Create Short Links with Click Tracking"
- **Do NOT** use vague titles like "Code Manager" or "Overview"
- **Do** include the feature name + action + context

---

## Tone of Voice

| Do | Don't |
|----|-------|
| "Click on **Code Manager**." | "The user should proceed to click on the Code Manager option." |
| "This saves hours of manual work." | "This feature is very useful and can help you." |
| "You'll see a list of your snippets." | "One will observe a listing of code fragments." |
| "Works with Bricks Builder." | "This is compatible with Bricks Builder." |

**Rules:**
1. **Second person** — always "you" and "your"
2. **Active voice** — "Enable the toggle" not "The toggle should be enabled"
3. **Concise** — cut every word that doesn't earn its place
4. **Confident** — state facts, don't hedge ("might", "perhaps", "it depends")
5. **No corporate jargon** — no "leverage", "utilize", "streamline", "seamlessly"
6. **No em dashes (—)** — use commas, periods, colons, or restructure the sentence

---

## Formatting Rules

### Bold
- Use for **UI elements** (button names, menu paths, toggle labels)
- Use for **key terms** on first mention
- Do NOT bold entire sentences

### Code
- Use `inline code` for file names, function names, CSS classes, shortcodes
- Use fenced code blocks for PHP snippets, CSS, HTML
- Always specify the language: ```php, ```css, ```html

### Lists
- **Numbered** for sequential steps
- **Bulleted** for features, options, non-sequential items
- Keep list items to 1-2 sentences max

### Images and Screenshots

Place a screenshot after **every step** in the how-to section. This is how Perfmatters does it, and it works because users can visually confirm they're in the right place.

**Pattern:**

```markdown
### Step 1: Navigate to Settings

Click into the **Classic Monks** plugin settings in your WordPress dashboard.

![Classic Monks plugin settings page](../images/code-manager/settings-page.png)

### Step 2: Go to the Core Tab

Click on the **Core** menu.

![Core tab location in Classic Monks](../images/code-manager/core-tab.png)
```

**Rules:**

1. **One screenshot per step** — show the exact UI state the user should see after following the instruction
2. **Descriptive alt text** — every image must describe what it shows (e.g., "Code Manager settings page with Add New button highlighted"), not just "screenshot1.png"
3. **Image path:** Save images in `docs/images/[feature-name]/` using kebab-case filenames
4. **Format:** PNG for UI screenshots, SVG for diagrams. Compress PNGs to under 200KB
5. **Width:** Screenshots should be 1200px wide (retina-ready at 2x for 600px display)
6. **No screenshots for code blocks** — only for UI navigation steps
7. **Highlight when useful** — if a specific button or toggle is hard to find, note it in the step text (e.g., "Toggle on **Code Manager** under the Setup section")

**Image file naming convention:**

```
docs/images/
├── code-manager/
│   ├── settings-page.png
│   ├── core-tab.png
│   ├── enable-code-manager.png
│   └── add-new-snippet.png
├── ai-agent/
│   ├── ai-tab.png
│   ├── provider-selection.png
│   └── chat-panel.png
└── short-links/
    ├── enable-short-links.png
    ├── create-new-link.png
    └── analytics-dashboard.png
```

**When to skip screenshots:**
- Configuration Options tables (no UI to show)
- Advanced Options / code snippets (code blocks replace screenshots)
- Troubleshooting section (text-only problem/fix pairs)
- Opening summary, Key Takeaways, Related Articles

### Links
- Link to related Classic Monks docs using relative paths
- Link to external resources (WordPress.org, PageSpeed Insights) with full URLs
- Never leave raw URLs in body text

---

## Content Guidelines

### Opening Summary
Every article starts with a blockquote summary (1 line). This appears in search results and social previews.

**Example:**
> The Code Manager lets you add PHP, CSS, and JavaScript snippets directly from the WordPress admin without editing theme files.

### Key Takeaways
3-5 bullet points. Written for someone scanning. Each should stand alone as a complete thought.

### "What Is" Section
- Define the feature in plain language
- Explain the WordPress context (why this matters in WP specifically)
- Mention the Classic Monks advantage over alternatives

### "Why You Need It"
- Lead with the **pain point** (e.g., "PageSpeed Insights flags unused CSS...")
- Quantify when possible ("reduces requests by 40%")
- Connect to a real metric (Core Web Vitals, load time, admin efficiency)

### Step-by-Step Instructions
- Number every step
- Bold the UI element you're clicking
- Include the full navigation path on Step 1
- Mention saving/refreshing when relevant
- Add screenshots descriptions if the feature is visual

### Troubleshooting
- Frame as: **Problem** → **Cause** → **Fix**
- Keep to the 3-5 most common issues
- Link to support/contact for edge cases

---

## SEO Considerations

- **H1:** Must include the primary keyword (feature name + "WordPress")
- **H2s:** Include secondary keywords naturally
- **First paragraph:** Must contain the feature name and "Classic Monks"
- **Alt text:** Every image description should include the feature name
- **Internal links:** At least 2-3 links to other Classic Monks docs per article
- **Meta description:** Derived from the opening blockquote summary

---

## Article Length

- **Minimum:** 800 words
- **Target:** 1200-1800 words
- **Maximum:** 2500 words (only for comprehensive guides like "Settings & Recommendations")
- If an article exceeds 2500 words, split it into sub-articles

---

## Checklist Before Publishing

- [ ] Title follows "How to [Action] in Classic Monks" format
- [ ] Opening blockquote summary is present
- [ ] Key Takeaways section has 3-5 bullets
- [ ] Every step has a numbered instruction
- [ ] UI elements are bolded
- [ ] Code blocks have language tags
- [ ] At least 2 internal links to other docs
- [ ] Troubleshooting section covers top 3 issues
- [ ] No em dashes (—) anywhere in the article
- [ ] No corporate jargon
- [ ] Readability: can a non-developer understand 80% of it?
