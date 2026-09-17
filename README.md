# 🤟 OmniSign — by Team HackTitan

### **Sign Every Word — Real-time ASL to Speech in Your Browser**

**OmniSign** translates **American Sign Language (ASL)** into live speech using just your webcam — **no backend, no installs, and complete privacy**. It also helps non-signers **learn ASL interactively** through a built-in learning library.

> 🏆 Built in 24 hours at **kalpAIthon 2.0** — a 24-hour open-innovation AI hackathon at **Kalpataru Institute of Technology (KIT), Tiptur** (23–24 April 2026).

🔗 **Live Demo:** https://omnisign-gules.vercel.app/
🏅 **Hackathon:** https://www.kalpaithon.com/

---

## 💡 The Problem

Communication between ASL signers and people who don't know sign language often requires an interpreter or text — slow, impersonal, and not always available. OmniSign removes that barrier: sign to your webcam, and your words are spoken aloud instantly. The same app teaches ASL to non-signers, working both directions of the conversation.

---

## ✨ Features

| Feature                    | Description                                                            |
| -------------------------- | ---------------------------------------------------------------------- |
| 🎥 Live ASL Detection      | MediaPipe Hands at up to 60 FPS, supports **2 hands simultaneously** — right hand signs alphabets, left hand signs numbers |
| ⚡ Stable Sign Transitions | Adjustable latency/stability buffer to avoid false mid-sign detections |
| 🗣️ Text to Speech         | Converts detected signs into real-time voice output (Web Speech API)   |
| 🧱 Phrase Builder          | Stack words into full sentences, then speak them; includes quick words & preset phrases |
| 📚 Learn ASL               | Interactive library: alphabet, numbers, greetings, and common signs — with tips & difficulty ratings |
| ↔️ Bidirectional           | Learn + communicate using the same system                              |
| 🔒 100% Private            | Runs entirely in-browser — your camera feed never leaves your device   |

---

## 🚀 Getting Started

No build step, no dependencies to install — it's a static site.

### Option 1: Use the live demo (easiest)

👉 https://omnisign-gules.vercel.app/

### Option 2: Run locally

```bash
git clone https://github.com/coding-shetty/HackTitan.git
cd HackTitan

# Either open index.html directly in your browser, or serve it:
python3 -m http.server 8000
# then visit http://localhost:8000
```

> ⚠️ **Camera access is required.** Allow webcam permission when prompted. Works best in Chrome / Edge.

---

## 🗂️ Project Structure

```
HackTitan/
├── index.html       # The entire app — self-contained UI + logic (CDN-loaded MediaPipe & Fingerpose)
├── classifier.js    # ES-module refactor: landmark-geometry ASL classifier + stabilizer
├── mediapipe.js     # ES-module refactor: camera + MediaPipe Hands setup
├── phrase.js        # ES-module refactor: phrase builder (word stack, quick words, presets)
├── speech.js        # ES-module refactor: Web Speech API wrapper
├── learn-data.js    # ES-module refactor: ASL sign library data for Learn mode
└── README.md
```

> ℹ️ `index.html` is fully self-contained and is what runs the app (and what the Vercel demo serves). The root `.js` files are a modular ES-module refactor of the same core logic — useful for ongoing development, but **not required to run the app**.

---

## 🧠 How It Works

```
Webcam Input
    ↓
MediaPipe Hands (21 hand landmarks, up to 2 hands)
    ↓
Custom landmark-geometry classifier (finger extension / curl scores)
    ↓
Confidence filtering + rolling-window stability system
    ↓
Detected sign (alphabet / number / word)
    ↓
Phrase Builder → Web Speech API → 🔊 Spoken output
```

### 🎯 Stability System

Instead of trusting every frame, OmniSign uses a **rolling prediction window** with majority voting, ensuring:

- smoother transitions between signs
- fewer false detections
- better real-world usability (a slider tunes the latency in the UI)

---

## 🔧 Tech Stack

- **MediaPipe Hands** (CDN) — real-time hand landmark tracking
- **Fingerpose** (CDN) — gesture estimation
- **Web Speech API** — text-to-speech output
- **Vanilla JavaScript** — no frameworks, no build step
- **HTML + CSS** — glassmorphism dark UI
- **Vercel** — static hosting for the live demo

---

## 📸 Demo Video

https://github.com/user-attachments/assets/7ab56ea9-ca8b-440c-a5b4-fb3c08c80ce4

- 🔤 Letters → Speech
- 🔢 Numbers → Speech
- ✋ Dual-Hand Detection
- 📚 Learn Mode

> 🎧 Note: the demo video is muted, but on the real website detected signs are spoken aloud via text-to-speech.

---

## 🗺️ Roadmap

- [ ] Integrate Fingerpose fully for better accuracy
- [ ] Add an ML model (TFLite / ONNX) for the full ASL vocabulary
- [ ] Speech → Sign (reverse communication)
- [ ] Animated sign tutorials
- [ ] Convert to a PWA (mobile support)
- [ ] Multi-language speech output

---

## 👥 Team HackTitan

**Team Lead:** Diganth N

**Members:**

- Yashas A
- Vijeth H J
- Diganth A R

⏱️ Built in 24 hours at **kalpAIthon 2.0** (23–24 April 2026), organized by the Department of Artificial Intelligence & Machine Learning, Kalpataru Institute of Technology, Tiptur.

---

## 🌍 Vision

> Breaking communication barriers between signers and non-signers using AI.

---

## 📄 License

MIT License — free to use, modify, and build upon. See [LICENSE](LICENSE).
