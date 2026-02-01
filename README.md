# EMOVISION — Real-Time Neural Emotion Decoding

🚀 **Deployed Link:** [Add your deployed link here](#)

---

A real-time AI-powered emotion analyzer that uses your webcam to detect and classify your facial expressions. Built as a single-file web application using TensorFlow.js and face-api.js — no backend or server required.

![Demo Preview](https://i.imgur.com/placeholder.png)

---

## How It Works

Emovision uses a pipeline of pre-trained neural networks to analyze your face in real time:

1. **Face Detection** — The TinyFaceDetector model locates your face in the webcam feed and draws a bounding box around it.
2. **Landmark Extraction** — The FaceLandmark68 model identifies 68 key points on your face to understand its geometry.
3. **Expression Classification** — The FaceExpression model scores your face against 7 emotion categories every 200ms during a 10-second analysis window.
4. **Aggregation** — All per-frame scores are averaged together to produce a final confidence-weighted result, making it robust against momentary blips.

The detected emotions are: **Happy**, **Sad**, **Angry**, **Fearful**, **Disgusted**, **Surprised**, and **Neutral**.

---

## Features

- **Real-time face detection** with a live green bounding box and a face-detected indicator
- **10-second emotion sampling** that analyzes dozens of frames for an accurate average
- **Confidence scoring** reported as a percentage based on the number of frames captured
- **Full emotion breakdown** showing scores for all 7 categories, sorted by relevance
- **Animated matrix background** and a scanning-line effect for a sci-fi aesthetic
- **Zero dependencies on a backend** — all AI models are loaded from a CDN at runtime
- **Responsive layout** that works on desktop and mobile browsers

---

## Tech Stack

| Technology | Purpose |
|---|---|
| **TensorFlow.js** | Runtime for running ML models in the browser |
| **face-api.js** | Pre-trained face detection and expression recognition models |
| **HTML / CSS / JS** | Single-file frontend, no build step needed |
| **Google Fonts** | `Inter` for body text, `Fira Code` for the monospace UI elements |

---

## Getting Started

Because Emovision is a single HTML file with no build step, setup is straightforward.

**Option A — Open locally:**  
Download `Emovision1.html` and open it directly in a modern browser (Chrome, Firefox, Edge, or Safari). When prompted, allow camera access.

**Option B — Deploy to a host:**  
Upload the file to any static hosting service (Vercel, Netlify, GitHub Pages, etc.) and access it via the generated URL. Camera access requires the page to be served over **HTTPS** — `localhost` is also allowed by browsers.

> **Note:** On first load, the app downloads roughly 5–10 MB of AI model weights from a CDN. Make sure you have a stable internet connection.

---

## Browser Requirements

- A modern browser with support for the **WebGL** API (required by TensorFlow.js)
- A functioning webcam with permission granted to the page
- An **HTTPS** origin (or `localhost`) — the GetUseredia API will not work over plain HTTP

---

## Project Structure

```
Emovision1.html
│
├── <head>
│   ├── TensorFlow.js CDN script
│   ├── face-api.js CDN script
│   └── Embedded CSS (glassmorphism UI, animations, matrix background)
│
└── <body>
    ├── Matrix rain canvas (background)
    ├── Header (title + tagline)
    ├── Main container
    │   ├── Loading screen (spinner while models download)
    │   ├── Instructions panel
    │   ├── Video feed + overlay canvas (face box drawing)
    │   ├── Progress overlay (countdown + progress bar)
    │   ├── Analysis controls (Analyze button)
    │   └── Results panel (emoji, dominant emotion, breakdown table)
    └── Inline JavaScript
        ├── Model loading (tinyFaceDetector, faceLandmark68, faceExpression)
        ├── Camera initialization
        ├── Continuous face detection loop
        ├── 10-second analysis loop (samples every 200ms)
        ├── Score aggregation & result rendering
        └── Matrix background animation
```

---

## Possible Improvements

- Add support for **multiple simultaneous faces**
- Integrate a **emotion history chart** to track mood over time
- Add a **snapshot/screenshot** button to save the result
- Swap in a custom-trained model for higher accuracy or additional emotion categories
- Add a **dark/light theme toggle**

---

## License

This project is open source. Feel free to use, modify, and distribute it as you see fit.
