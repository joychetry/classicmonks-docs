---
title: "How to Use Bricks AI Builder in Classic Monks: HTML to Bricks | CM"
slug: bricks-ai-builder
description: Use Bricks AI Builder in Classic Monks to convert HTML into Bricks Builder elements. Generates sections, classes, components, and JavaScript from natural language.
last_updated: 2026-06-24
author: Joy
reading_time: 9 min
canonical: https://classicmonks.com/docs/bricks-ai-builder/
---

# How to Use Bricks AI Builder in WordPress

> Bricks AI Builder converts HTML into Bricks Builder elements directly inside the Live HTML to Bricks panel, generating structured sections, global classes, and components.

## Key Takeaways

- Requires Bricks Builder and the Live Code Sync & Import feature enabled
- Available in the Live HTML to Bricks panel as a dedicated mode
- Customizable system prompt for design standards and coding preferences
- Generates sections, classes, components, and vanilla JavaScript when needed

---

## What Is Bricks AI Builder?

Bricks AI Builder is the AI-powered mode inside Classic Monks' Live HTML to Bricks conversion flow. Instead of pasting HTML and manually mapping it to Bricks elements, you describe what you want in natural language and the AI generates a structured Bricks layout. The output uses Bricks sections, global classes, components, and variables, not raw HTML.

It runs in the same panel as the existing Live Code Sync & Import feature, so the workflow is familiar if you already use that tool.

## Why You Need It

Converting HTML mockups to Bricks layouts by hand is slow. You paste HTML, then rebuild every section, class, and component manually. For a typical landing page, that is hours of work even when the markup is clean.

Bricks AI Builder compresses that into minutes:

- **Describe the layout**: "Hero with logo top-left, headline, subhead, two CTA buttons" gets you a structured Bricks section with global classes ready for styling
- **Generate from scratch**: "Pricing page with 3 tiers and FAQ section below" produces a full page with proper Bricks structure
- **Iterate fast**: "Make the hero taller and add a video background" applies the change without manual rebuilding
- **Stay on-brand**: Set a system prompt with your design system, typography rules, and color palette to keep generated output consistent

---

## How to Enable Bricks AI Builder in Classic Monks

### Step 1: Enable Bricks Builder

Bricks AI Builder requires the Bricks Builder theme. Install and activate Bricks from [bricksbuilder.io](https://bricksbuilder.io).

### Step 2: Enable Live Code Sync & Import

In the Classic Monks settings, open the **Bricks Builder** tab. Toggle on **Live Code Sync & Import**. Bricks AI Builder depends on this feature; it will not work without it.

### Step 3: Enable AI Features

Open the **AI** tab. In the **General** subtab, toggle on **Enable AI Features**. See [How to Enable AI Features in Classic Monks](../ai/ai-features-master.md).

### Step 4: Enable Bricks AI Builder

Still in the **General** subtab, toggle on **Enable Bricks AI Builder**. A status message confirms whether the dependency on Live Code Sync is satisfied.

If a yellow warning appears saying "Live Code Sync & Import must be enabled in the Bricks Builder tab for Bricks Ai Builder to work", go back to Step 2 and enable it.

### Step 5: Configure Your AI Provider

Bricks AI Builder uses the main AI Provider. Configure it in the **AI Provider** section. See [How to Configure the AI Provider in Classic Monks](../ai/ai-provider.md).

### Step 6: Set a Bricks AI Builder System Prompt (Optional)

Switch to the **Ai Agent** subtab and edit the **Bricks AI Builder System Prompt** field. This prompt guides the conversion behavior, including coding standards, design preferences, and how to handle edge cases.

### Step 7: Open the Live HTML to Bricks Panel

In the Bricks Builder editor, open the **Live HTML to Bricks** panel from the toolbar. Switch to the **AI** mode.

> **Note:** The Live HTML to Bricks panel is part of the Bricks Builder toolbar, accessible only on pages being edited with Bricks. The AI mode toggle appears at the top of the panel.

### Step 8: Save Changes

Click **Save Changes** in the Classic Monks settings to persist the toggle and prompt.

---

## Using Bricks AI Builder

### Generating from a Description

1. Open the Live HTML to Bricks panel
2. Switch to **AI** mode
3. Type a description: "Pricing page with 3 tiers (Starter, Pro, Agency) and a comparison table below"
4. Press Enter or click **Generate**
5. Review the generated Bricks structure in the preview
6. Click **Insert** to apply it to the current page or save as a component

### Converting Existing HTML

1. Open the Live HTML to Bricks panel
2. Switch to **AI** mode
3. Paste your HTML in the input
4. Add a natural-language instruction: "Convert this HTML into a Bricks section using the brand colors from the global palette"
5. Press Enter or click **Generate**
6. Review the conversion and click **Insert**

### Iterating on Generated Output

After the AI generates a layout, you can refine it conversationally:

- "Add a video background to the hero"
- "Make the spacing tighter on the pricing cards"
- "Replace the icons with the Iconify set"
- "Convert this to a reusable component"

Each refinement preserves the Bricks structure (global classes, sections, variables) so styling stays consistent.

### Vanilla JavaScript Generation

When a generated component needs interactivity (tabs, accordions, sliders, dropdowns), Bricks AI Builder emits the required vanilla JavaScript along with the Bricks elements. You do not need to write JS by hand. The script uses Bricks' existing event system where possible and falls back to standard DOM listeners.

### Confirmation Prompts

For destructive operations (replacing a section root or the entire page), Bricks AI Builder shows a confirmation prompt before applying the change. The prompt names the elements that will be replaced and asks for explicit approval.

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **Enable Bricks AI Builder** | Activates the AI mode in the Live HTML to Bricks panel. | Off |
| **Live Code Sync & Import** | Required dependency. Bricks AI Builder refuses to run without it. | Off (must be on) |
| **Bricks AI Builder System Prompt** | Custom instructions guiding conversion behavior, coding standards, and design preferences. | Default conversion |
| **AI Provider** | Powers the AI generation. Uses the same provider configured in the AI Provider section. | OpenRouter |

---

## Image Attachments

When you attach an image in the Bricks AI chat (for reference or "match this design"), the attachment is routed to the **Vision / Image Provider** if configured, or the main AI Provider if it supports images. A status message under the **Enable Bricks AI Builder** toggle tells you which path is active.

**To attach an image:**

1. Click the attachment icon in the Bricks AI chat
2. Pick an image from the Media Library
3. Add a text instruction: "Match this design's color palette and typography"
4. Generate

Vision-capable models can analyze the image and produce Bricks output that closely mirrors the reference. For best results, configure a dedicated Vision / Image Provider. See [How to Configure the Vision / Image Provider in Classic Monks](../ai/vision-image-provider.md).

---

## System Prompt Tips

A well-tuned system prompt dramatically improves output quality. Include:

- **Design system rules**: spacing scale, typography, color palette
- **Component preferences**: "Use Bricks' Tabs element for tabbed sections", "Always wrap feature lists in the Bricks Icon List element"
- **Coding standards**: "Use BEM-style class names with the `cm-` prefix", "Avoid inline styles"
- **Edge case handling**: "When the HTML uses a carousel, generate a Bricks Accordion instead"
- **Branding**: "Always reference the global color variables, not raw hex values"

**Example system prompt:**

```
You convert HTML into Bricks Builder layouts.

Rules:
- Use Bricks sections for all top-level layout blocks
- Apply global CSS classes from the site palette
- Use Bricks' native elements (Icon List, Accordion, Slider) instead of raw HTML
- Wrap repeating items in Bricks' Loop element
- Use the brand's color variables (var(--color-primary), var(--color-accent))
- Spacing follows the 8px scale: 8, 16, 24, 32, 48, 64
- Typography uses Inter for body, Space Grotesk for headings
- Add JavaScript only when no native Bricks element supports the behavior
```

---

## Advanced Options (Developers)

The Bricks AI Builder uses standard WordPress hooks for initialization and asset loading.

**Hooks used:**

- `wp_enqueue_scripts` enqueues AI builder assets conditionally via `cm_bricks_should_enqueue()`
- `admin_notices` displays notices when dependencies are missing

The AI generation process uses server-side API calls to the configured provider. The prompt and element restrictions are configured through the plugin settings, not via WordPress filters.


## Troubleshooting

### "Live Code Sync & Import Must Be Enabled" Warning

**Cause:** The Bricks AI Builder toggle is on, but Live Code Sync is off.
**Fix:** Open the Bricks Builder tab in Classic Monks settings and toggle on **Live Code Sync & Import**.

### Bricks AI Mode Not Visible in the Live HTML to Bricks Panel

**Cause:** One of the dependencies is missing (Bricks theme not active, Live Code Sync off, AI Features off, Bricks AI Builder off).
**Fix:** Verify all four: Bricks active, Live Code Sync on, AI Features on, Bricks AI Builder on.

### Generated Output Is Generic HTML, Not Bricks Structure

**Cause:** The AI model is not following the conversion instructions, or the system prompt is empty.
**Fix:** Set a detailed system prompt with explicit Bricks element preferences. Switch to a more capable model (Claude Sonnet, GPT-4o) for complex conversions.

### Image Attachments Return Errors

**Cause:** No Vision / Image Provider is configured and the main provider's model does not support images.
**Fix:** Configure the Vision / Image Provider. See [How to Configure the Vision / Image Provider in Classic Monks](../ai/vision-image-provider.md).

### Component Replacements Need Confirmation Every Time

**Cause:** The plugin prompts for confirmation on destructive operations (section root, page root replacement) by design.
**Fix:** This is intentional safety behavior. To avoid prompts, instruct the AI to make additive changes ("add a new section below") instead of replacements ("replace the hero section with...").

---

## Frequently Asked Questions

### Does Bricks AI Builder work without the Bricks theme?

No. Bricks AI Builder runs inside the Live HTML to Bricks panel in the Bricks editor. Without the Bricks theme active, the panel doesn't exist and the AI mode is unreachable. Install and activate Bricks first.

### Does Bricks AI Builder need Live Code Sync & Import?

Yes. The AI mode in the Live HTML to Bricks panel depends on Live Code Sync being enabled in the Bricks Builder tab of Classic Monks. If Live Code Sync is off, the AI toggle is disabled with a warning. Enable Live Code Sync, reload the page, then access the AI mode.

### Can Bricks AI Builder work without an AI Provider?

No. The AI mode sends your description or HTML to the main AI Provider configured in Classic Monks. Without a working provider, the Generate button fails. Configure at least one provider (OpenRouter, OpenAI, Anthropic, etc.) in AI > General before using Bricks AI Builder.

### What does Bricks AI Builder output?

Structured Bricks Builder elements: sections with global classes, components, dynamic data tags, and vanilla JavaScript when the converted layout needs interactivity (tabs, accordions, sliders). The output is editable in the Bricks editor, not locked HTML.

### Will Bricks AI Builder overwrite my existing page?

The AI mode is destructive on confirmation. The Live HTML to Bricks panel shows a confirmation prompt before replacing a section root or the entire page root. Additive changes ("add a new section below this") do not need confirmation. The plugin never overwrites without explicit user approval.

## Related Articles

- [How to Enable AI Features in Classic Monks](../ai/ai-features-master.md)
- [How to Configure the AI Provider in Classic Monks](../ai/ai-provider.md)
- [How to Configure the Vision / Image Provider in Classic Monks](../ai/vision-image-provider.md)
- [How to Configure AI Advanced Settings in Classic Monks](../ai/ai-advanced.md)
- [How to Use the AI Agent in Classic Monks](../ai/ai-agent.md)
