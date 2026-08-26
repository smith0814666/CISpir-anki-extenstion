# Privacy Policy for CISpir

**Last updated: August 2026**

CISpir does not run a backend or collect user data on its own servers. This page describes exactly what the extension stores and sends.

## What stays on your device

- **Subtitle text, audio clips, and video metadata** are sent only to your local Anki via AnkiConnect (`localhost:8765`). They never leave your computer.
- **Settings and preferences** — including the Anki deck name, active tab ID, donation state, and AI result cache — are stored locally with Chrome's `storage.local` API.
- **API keys** are encrypted (AES-GCM) before being stored in `storage.local`.

## What is sent to AI providers

When you use the AI features (translation, grammar analysis, word lookup, or video summary), the subtitle text or selected sentence is sent **directly from your browser** to the AI provider you configured (OpenAI, Anthropic, Google AI, or DeepSeek). CISpir has no server in between; your API key authorizes these requests. If you do not configure a key or do not use these features, nothing is sent.

## Anonymous usage telemetry (optional, off by default)

The extension contains an optional, anonymous usage counter (Google Analytics 4). It is **disabled by default** and only activates if the publisher configures a measurement ID. When active, it sends only aggregate, non-personal events — such as install/update, daily active, and feature usage — using a randomly generated identifier with no fingerprinting, and never your subtitle text or account information.

## Remote code

CISpir does not load or execute any remotely hosted code. All extension code — the background service worker, side panel, settings page, and content scripts — is bundled inside the extension and runs locally on your device. Network requests only fetch data (text/JSON) from the AI provider you configure and, if enabled, the optional usage counter; that data is never executed as code.

## Third-party services

CISpir does not integrate with any advertising or tracking services.

## Contact

For questions, open an issue at [github.com/smith0814666/CISpir-anki-extenstion](https://github.com/smith0814666/CISpir-anki-extenstion).
