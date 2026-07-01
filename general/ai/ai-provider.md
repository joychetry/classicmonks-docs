---
title: "AI Provider Setup in Classic Monks: 8 Providers | CM"
slug: ai/ai-provider
description: Configure the AI Provider in Classic Monks to connect with OpenRouter, OpenAI, Anthropic, Gemini, NVIDIA, Zhipu, OpenAI-compatible, or custom endpoints.
last_updated: 2026-06-24
author: Joy
reading_time: 7 min
canonical: https://classicmonks.com/docs/ai/ai-provider/
---

# How to Configure the AI Provider in WordPress

> The AI Provider connects Classic Monks to your chosen model API, from OpenRouter and OpenAI to Anthropic, Gemini, NVIDIA, Zhipu, OpenAI-compatible endpoints, and fully custom URLs.

## Key Takeaways

- 8 supported providers: OpenRouter, OpenAI, Anthropic, Gemini, NVIDIA, Zhipu, OpenAI Compatible, Custom Endpoint
- Each provider has the same 3 fields: API key, optional endpoint URL, model name with Fetch Models helper
- API keys are stored in the WordPress database; HTTPS is required for the admin
- OpenRouter is recommended for getting started because one key unlocks 200+ models

---

## What Is the AI Provider?

The AI Provider is the connection between Classic Monks and a model API. Every AI feature in the plugin (the AI Agent, AI Tools, Bricks AI Builder, Vision / Image workflows) routes through whichever provider you select here. You pick one provider as the main text provider, optionally add a separate Vision / Image provider for image-aware tasks, and Classic Monks handles the request shaping, retries, and history for you.

## Why You Need It

Without an AI Provider configured, every AI feature in Classic Monks is non-functional. The provider is the bridge between your WordPress admin and the language models that power content generation, image analysis, code review, and chat assistance.

Picking the right provider matters for:

- **Cost**: Some providers (Gemini Flash, Zhipu GLM) are dramatically cheaper than others for the same task
- **Capability**: Different models excel at different things (Claude for reasoning, Gemini for multimodal, GPT for general tasks)
- **Compliance**: Some providers offer data residency, regional hosting, or self-hosted options
- **Resilience**: OpenRouter aggregates 200+ models behind one key, so a single provider outage does not take you down

---

## How to Configure the AI Provider in Classic Monks

### Step 1: Enable AI Features

The AI Provider configuration is hidden until you turn on **Enable AI Features** in the General subtab. See [How to Enable AI Features in Classic Monks](ai-features-master.md).

### Step 2: Open the General Subtab

In the AI tab, stay on the **General** subtab. Scroll to the **AI Provider** section below the AI Agent and Bricks AI Builder toggles.

![AI tab General subtab with the AI Provider dropdown expanded showing all 8 supported providers](../../images/ai/ai-provider/general-subtab.png)

### Step 3: Choose a Provider

Click the **AI Provider** dropdown and select one of the 8 supported options. The provider-specific fields appear below the dropdown as soon as you change the selection.

### Step 4: Enter Your API Key

Each provider has an **API Key** password field. The field stores the key when you save. If a key is already saved, the field shows "Saved API key. Leave blank to keep it unchanged." and the actual value is not rendered to the page.

Get keys from the provider's dashboard:

- **OpenRouter**: [openrouter.ai/keys](https://openrouter.ai/keys)
- **OpenAI**: [platform.openai.com/api-keys](https://platform.openai.com/api-keys)
- **Anthropic**: [console.anthropic.com/settings/keys](https://console.anthropic.com/settings/keys)
- **Google Gemini**: [aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)
- **NVIDIA Build / Integrate**: NVIDIA dashboard
- **Zhipu AI (GLM)**: [z.ai/manage-apikey/apikey-list](https://z.ai/manage-apikey/apikey-list)
- **OpenAI Compatible**: Your self-hosted or third-party endpoint dashboard
- **Custom Endpoint**: Whatever service you are connecting to

### Step 5: (Optional) Override the Endpoint

Every provider except OpenAI Compatible and Custom Endpoint has a default endpoint URL pre-filled as a placeholder. Leave it blank to use the provider's default. Override it only if you are proxying through a gateway or running a self-hosted mirror.

### Step 6: Choose a Model

Each provider has a model field with two controls:

- A searchable select dropdown that lists models fetched from the provider
- A free-text input for the exact model identifier
- A **Fetch Models** button that calls the provider's API and populates the dropdown

Click **Fetch Models** after entering your API key to populate the dropdown with models your account has access to. Pick a model from the list, or paste a model ID manually if you know it.

### Step 7: Save Changes

Click **Save Changes**. Classic Monks validates the provider, model, and API key on the next AI request.

---

## Supported Providers

| Provider | Default Model | Best For | Endpoint Override |
|----------|---------------|----------|-------------------|
| **OpenRouter (Recommended)** | `anthropic/claude-4.5-sonnet` | Access to 200+ models with one key | Yes |
| **OpenAI** | `gpt-4o` | GPT-5, o-series, and legacy chat models. Auto-routes between Chat Completions and Responses API | Yes |
| **Anthropic** | `claude-3-5-sonnet-latest` | Claude reasoning and coding strength | Yes |
| **Google Gemini** | `gemini-3-flash` | Multimodal tasks, fast inference, generous free tier | Yes (supports `{model}` placeholder) |
| **NVIDIA Build / Integrate** | `z-ai/glm5` | GPU-accelerated OpenAI-compatible chat models | Yes |
| **Zhipu AI (GLM)** | `GLM-4.7` | Chinese and bilingual content | Yes |
| **OpenAI Compatible** | (none, must specify) | LM Studio, Ollama, Together AI, any OpenAI-format API | Yes (required, base URL) |
| **Custom Endpoint** | (none, must specify) | Any AI API with separate URL, key, and model | Yes (required) |

---

## Configuration Options

| Option | Description | Default |
|--------|-------------|---------|
| **AI Provider** | Selects which provider powers all AI features. | OpenRouter |
| **API Key** | Provider-specific key. Stored in WordPress options. | Empty |
| **API Endpoint** | Optional override of the provider's default endpoint URL. | Provider default |
| **Model Name** | The exact model identifier passed in every AI request. | Provider default |
| **Fetch Models** | Calls the provider's model-list API and populates the model dropdown. | Button |

---

## Switching Providers

Switching is non-destructive. When you change the **AI Provider** dropdown:

1. The new provider's fields appear
2. Your old provider's API key, endpoint, and model stay saved in the background
3. Switching back to the old provider restores its saved values

You can keep multiple providers configured and switch between them as needed. This is useful for testing model quality, comparing costs, or routing specific workflows to specialized providers (via the Vision / Image Provider).

## Security Notice

A warning notice appears at the bottom of the AI Provider section:

> API keys are stored in your WordPress database. Ensure your site uses HTTPS and keep regular backups.

Classic Monks stores API keys as WordPress options. They are not encrypted at rest. If your database is compromised, the keys are exposed. Mitigations:

- Use HTTPS on the entire admin
- Restrict database access
- Use the [Custom Endpoint](#) provider to point at a proxy that holds the real key
- Rotate keys if you suspect a leak

---

## Developer Notes

Provider configuration is managed through WordPress options. The active provider and model are determined by:

| Option | Type | Description |
|--------|------|-------------|
| `cm_ai_providers` | Array | List of enabled providers |
| `cm_ai_provider` | String | Active provider slug |
| `cm_ai_model` | String | Active model identifier |

The function `cm_get_ai_provider()` returns the active provider slug, and `cm_get_ai_provider_model()` returns the active model identifier.

Provider-specific API keys are stored as individual options (e.g., `cm_ai_openai_api_key`, `cm_ai_anthropic_api_key`).
---

## Troubleshooting

### "API Key Invalid" Error

**Cause:** The key is wrong, expired, revoked, or belongs to a different provider than the one selected.
**Fix:** Verify the key works in the provider's own dashboard. Confirm the **AI Provider** dropdown matches where the key was issued.

### Fetch Models Returns Empty

**Cause:** Provider API is down, the key has no model-list permission, or the endpoint override is wrong.
**Fix:** Disable any custom endpoint URL temporarily. If it still fails, the provider API is likely the issue. Try again in a few minutes.

### Custom Endpoint Provider Returns 404

**Cause:** The endpoint URL is the chat completions path, but the plugin needs the base URL plus the chat path.
**Fix:** For OpenAI Compatible, enter the base URL only (e.g. `https://api.example.com/v1`). For Custom Endpoint, enter the full chat completions URL.

### Provider Defaults Don't Match the Documentation

**Cause:** Default model values change as providers release new versions. The plugin tracks the latest stable model at release time.
**Fix:** Use **Fetch Models** to see what your account has access to, then pick a model explicitly. The default is just a fallback.

---

## Frequently Asked Questions

### Which AI provider should I choose?

For most users, OpenRouter is the best starting point. One API key unlocks 200+ models including Claude, GPT, Gemini, and Llama, and you can switch models without changing providers. If you have a direct relationship with one provider (e.g., an OpenAI enterprise account), use that provider directly to keep billing consolidated.

### How does Fetch Models work?

The **Fetch Models** button calls the provider's API with your API key and populates the model dropdown with the models your account has access to. If the API call fails (wrong key, network issue, provider outage), the dropdown stays empty and you can paste a model ID manually.

### Should I use the OpenAI Compatible or Custom Endpoint option?

Use **OpenAI Compatible** when connecting to any service that follows the OpenAI API format (LM Studio, Ollama with the OpenAI shim, Together AI, Anyscale, etc.). Use **Custom Endpoint** when the service has a different URL structure, requires custom headers, or is a proprietary AI service.

### Where are my API keys stored?

API keys are stored as WordPress options in the database (encrypted at the database level by your host, not by the plugin). HTTPS is required for the admin to prevent interception. For maximum security, use a custom endpoint that proxies to your real provider, keeping the actual key off the WordPress server.

### Can I switch providers without losing my configuration?

Yes. When you change the **AI Provider** dropdown, your old provider's API key, endpoint, and model stay saved in the background. Switching back to the old provider restores its saved values. This makes it easy to test multiple providers.

## Related Articles

- [How to Enable AI Features in Classic Monks](ai-features-master.md)
- [How to Configure the Vision / Image Provider in Classic Monks](vision-image-provider.md)
- [How to Use the AI Agent in Classic Monks](ai-agent.md)
- [How to Use AI Tools in Classic Monks](ai-tools.md)
- [How to Configure AI Advanced Settings in Classic Monks](ai-advanced.md)
