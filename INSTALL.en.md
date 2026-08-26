# CISpir — Installation & Usage Guide

**CISpir** is a Chrome extension that turns YouTube subtitles into Anki flashcards — with audio, AI translation, and grammar analysis — saved straight to your local Anki.

## 🚀 Quick start

1. Install [Anki desktop](https://apps.ankiweb.net/) (the desktop app, not web/mobile)
2. Install the **AnkiConnect** add-on in Anki (code `2055492159`)
3. Install **CISpir** (load the `dist` folder)
4. (Optional) Add an **AI API key** in settings
5. Open a YouTube video → click the CISpir icon → load captions → click ☆ to save to Anki

## Requirements

- Windows / macOS / Linux
- A Chromium browser: Chrome 114+, Edge, Brave, or Arc
- Anki desktop app
- (Optional) An AI API key

## 1. Install Anki (desktop)

- Download: https://apps.ankiweb.net/
- **Desktop app required.** AnkiWeb and the mobile apps do not support AnkiConnect.

## 2. Install AnkiConnect

1. Open Anki.
2. Tools → Add-ons → Get Add-ons…
3. Enter `2055492159` → OK.
4. Restart Anki.
5. Verify: open `http://localhost:8765` — you should see `{"result": null, "error": "must be a POST request"}`.

## 3. Install CISpir

**Method A — Chrome Web Store** (coming soon): search "CISpir" → Add to Chrome.

**Method B — Load unpacked (recommended now):**

1. Download the latest release ZIP from `github.com/smith0814666/CISpir-anki-extenstion/releases`.
2. Unzip it.
3. Go to `chrome://extensions/` → turn on **Developer mode**.
4. Click **Load unpacked** → select the `dist` folder.

📌 Pin the icon: puzzle icon → CISpir → 📌.

## 4. Configure AI (optional)

Choose one provider and paste the key in CISpir settings (gear icon → Save).

| Provider | Key URL | Default model |
|---|---|---|
| Google AI | aistudio.google.com/apikey | gemini-2.0-flash (free tier) |
| DeepSeek | platform.deepseek.com/api_keys | deepseek-chat |
| OpenAI | platform.openai.com/api-keys | gpt-4o-mini |
| Anthropic | console.anthropic.com/keys | claude-sonnet-5-20251001 |

🔒 Keys are encrypted (AES-GCM) and stored only in your browser.

## 5. Use it

1. Open a YouTube video with captions.
2. Make sure Anki is running — the sidebar shows 🟢 Anki ✓.
3. Click the CISpir icon to open the side panel.
4. Pick the caption language and target language → **Load Captions**.
5. Click a sentence to play it; select a word to translate it.
6. Click **☆** to save to Anki — it grabs the audio clip, translation, grammar, and video link automatically.

### Controls

| Action | How |
|---|---|
| Play a sentence | Click it |
| Prev / next | ⏮ ⏭ or ← → keys |
| Loop one sentence | 🔄 |
| Playback speed | 0.5× – 2× |
| Look up a word | Select (highlight) it |

### AI features

| Feature | Button | What it does |
|---|---|---|
| Translate all | 🌐 | Batch-translate the subtitles |
| Grammar analysis | 📖 | Break down grammar, add readings |
| Extract chunks | 🔤 | Pull out learnable words & phrases, then save them to Anki |
| Video summary | 📄 | Summary, key vocab, difficulty |

## Anki card fields

Text · Translation · Reading · Audio · TargetWord · WordReading · Definition · Explanation · Source

## 💝 Donate

CISpir is completely free — every feature works without paying. If it helps you, you can voluntarily support its ongoing maintenance. **Donating never unlocks or restricts any feature.**

Click **Support CISpir** in the side panel or settings to donate. Three channels are supported:

| WeChat | Alipay |
|:---:|:---:|
| <img src="./assets/donation/wechat-qr.jpg" alt="WeChat donation QR code" width="200"> | <img src="./assets/donation/alipay-qr.jpg" alt="Alipay donation QR code" width="200"> |

> **PayPay**: send to ID `milesmissyou` in PayPay (no QR code).

Payment happens in the selected app. CISpir cannot read payment information and does not upload device data.

## FAQ

- **Anki ✗?** Is Anki running? AnkiConnect installed? Restarted Anki? Check `http://localhost:8765`.
- **No captions?** Refresh the page; some videos block third-party access.
- **No API key?** Captions, audio, and saving still work. Translation / grammar / chunks / summary don't.
- **Browsers?** Chrome / Edge / Brave / Arc ✅ · Firefox / Safari ❌.

## Support

github.com/smith0814666/CISpir-anki-extenstion
