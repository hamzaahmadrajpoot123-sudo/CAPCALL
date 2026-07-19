# CapsCall

**Talk in your language. They'll read theirs.**

CapsCall is a real-time, peer-to-peer voice and video calling website for two people, with live translated captions. Each person picks the language they speak — what they say is transcribed, translated, and shown as a caption (and optionally spoken aloud) in the other person's chosen language.

## Live demo

Open `index.html` in a browser (Chrome or Edge recommended), or host it with GitHub Pages — see below.

## How it works

1. Both people open the site and enter their name, phone number (for display only — not verified), and the language they'll be speaking.
2. One person clicks **Start a new call** and gets a short room code (e.g. `CAP-AB12CD`).
3. They send that code to the other person (WhatsApp, SMS, etc.).
4. The other person clicks **Join with a code**, enters it, and the call connects.
5. While talking, each person's speech is recognized, translated into the other person's language, and shown as a live caption. A "Translated voice (TTS)" toggle can read the translated text aloud.

## Tech stack

- **WebRTC** (via [PeerJS](https://peerjs.com/), using PeerJS's free public signaling/broker server) for real peer-to-peer audio/video over the internet — no backend server required.
- **Web Speech API** (`SpeechRecognition` / `SpeechSynthesis`) for live transcription and text-to-speech, built into Chrome/Edge.
- **MyMemory Translation API** (free, no key required) for live text translation between languages.
- Plain HTML/CSS/JS — no build step, no framework.

## Deploying with GitHub Pages

1. Push this repo to GitHub (already done if you're reading this from the repo).
2. Go to **Settings → Pages** in the repository.
3. Under "Build and deployment", set **Source** to `Deploy from a branch`, branch `main`, folder `/ (root)`.
4. Save. Your site will be live at `https://<username>.github.io/CAPCALL/` within a minute or two.

## Known limitations

- **Two people only.** Group calling (3+ people) isn't supported in this version.
- **Phone numbers are not verified.** There's no SMS/OTP backend — the number is just a display label. Adding real OTP verification requires a backend and an SMS provider (e.g. Twilio).
- **Speech recognition browser support.** `SpeechRecognition` is well supported in Chrome and Edge, but not in Safari or Firefox.
- **Translation quality.** MyMemory is a free API with rate limits and machine-translation quality. For production use, consider a paid provider (Google Cloud Translation, Azure Translator, DeepL) with your own API key.
- **Signaling reliability.** This uses PeerJS's free public broker server for connection setup. It's fine for testing and light use, but for production-grade reliability you'd want to run your own PeerJS/signaling server and TURN server (for users behind restrictive NATs/firewalls).

## License

MIT
