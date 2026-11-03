# Shark AI 🦈

A private AI assistant that runs fully on your device and works offline, on phones, tablets and computers.
**Developed by MeshCode.**

## What it does
- **Chat modes:** Chat, Write, Summarize, Translate (19 languages), Code, Explain, Brainstorm
- **7 offline models:** Shark Nano, Lite, Smart, Pro, Coder, Ultra, and Vision (sees images)
- **Voice input:** speech-to-text that works offline (Whisper)
- **Read aloud:** uses the device's built-in voices
- **Image reader:** describes photos and reads the text in them (Florence-2), on any device
- **Documents:** PDF, TXT, MD, CSV, JSON, HTML and code files. Scanned PDFs are read using OCR. Long documents are read in parts.
- **Chat history** stays on the device, with search, Markdown export, backup and restore
- **Installable app (PWA)** with an auto-adapting phone/desktop layout and dark/light themes

## Deploy (GitHub web + Netlify)
1. Create a new GitHub repo (e.g. `shark-ai`).
2. Click **Add file → Upload files** and drag in **everything inside this folder**, keeping the folders (`icons/`, `vendor/`). Commit.
3. In Netlify: **Add new site → Import from GitHub → pick the repo**.
   - Build command: *(leave empty)*
   - Publish directory: `/` (root)
4. Deploy. Open the Netlify URL on any device.

> It must be served over **https** (Netlify does this). It won't work by double-clicking `index.html`.

## First use on each device
1. Open the site → tap **Download** on the recommended model (Wi-Fi recommended).
2. Install it: Android/PC Chrome → **Install app**; iPhone → **Share → Add to Home Screen**.
3. Try the mic and an image once while online so those skills download too.
4. From then on it works with **no internet**.

## Device requirements
- **Chat models need WebGPU:** Chrome/Edge on Android, Windows, Mac or Linux, or Safari on iOS/iPadOS 26+.
- Phones: roughly 2021 or newer with 6 GB+ RAM works best (Shark Nano/Lite). Laptops: Shark Pro or above.
- Voice input and the image reader also run without WebGPU (slower, on the CPU).

## Updating
Change any file, then bump `VERSION` in `sw.js` (e.g. `shark-ai-v1.0.1`) so installed apps pick up the update.

## Files
| Path | Purpose |
|---|---|
| `index.html` | App layout |
| `styles.css` | Styling and the responsive phone/desktop layout |
| `app.js` | Main app logic |
| `llm-worker.js` | Runs the chat model off the main thread |
| `ai-worker.js` | Voice (Whisper) and image reading (Florence-2) |
| `sw.js` | Offline caching |
| `manifest.webmanifest` | Install settings |
| `_headers` | Netlify headers |
| `LICENSES.md` | Model and library licenses (keep this file when you sell) |
| `icons/` | Shark logo and app icons |
| `vendor/` | Bundled AI libraries (WebLLM, wllama, Transformers.js, PDF.js) |

## AI engines
- **Graphics chip (WebLLM):** fastest. Some phones (many Qualcomm/Snapdragon) can't run it.
- **Processor (wllama / llama.cpp):** works on almost every device. Available for Shark Nano, Lite, Smart and Coder.
- **Automatic (default):** picks the best one and switches to the processor if the graphics chip fails. Users can change this in Settings → AI engine.
