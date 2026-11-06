# 💨 Meme Disintegration Effect (1200×1200 WebGL VFX)

> A high-fidelity, real-time procedural disintegration VFX tool inspired by the legendary **"Sad emoji getting disintegrated into dust"** meme.

[![WebGL](https://img.shields.io/badge/WebGL-1.0%20%2F%20GLSL-orange.svg)]()
[![Performance](https://img.shields.io/badge/Performance-60%2B%20FPS%20(1200x1200)-brightgreen.svg)]()
[![Zero Dependencies](https://img.shields.io/badge/Dependencies-Zero%20(Vanilla%20JS)-blue.svg)]()
[![Telegram Ready](https://img.shields.io/badge/Export-Silent%20MP4%20(Telegram%20GIF)-2CA5E0.svg)]()

Unlike typical lazy approximations (which slice images into uniform square grids or blow everything up at once), this project achieves authentic, cinematic ash dissolution powered by **custom GLSL fragment shaders** and an **optimized TypedArray particle engine**.

---

## ✨ Key Features

* **No Premature Grid Slicing:** The source image remains continuous and pristine. Particles separate *strictly* along the dynamic tear front.
* **Two-Stage Wave Mechanics:**
  1. **Diagonal Charring Wave:** Moves from bottom-right to top-left, smoothly burning only opaque pixels into deep charcoal black while leaving the background untouched.
  2. **The 0.35s "Charred Pause":** Material stays stably black before the trailing dissolve front rips it into flying ash.
* **Organic Ash & Dust Atlas:** Zero square pixels! Employs a procedural 16-tile ash atlas generating micro-soot specks, torn polygonal flakes, and porous carbon chunks with internal voids and rotation.
* **DaVinci Resolve Retime Curve:** Simulation speed is driven by a non-linear S-curve (starts at 100% speed, then dynamically accelerates up to 380%), giving the disintegration explosive punch and momentum.
* **Event-Driven MP4 Export (Telegram GIF Ready):**
  * One-click recording directly from the Canvas stream at 60 FPS.
  * **Completely audio-free:** Telegram automatically interprets and loops the file as an animated GIF.
  * **Adaptive Duration:** Automatically stops recording the exact frame the last ash particle dissipates into thin air (`partCount === 0`).
* **Custom PNG Support:** Drag-and-drop or upload any transparent PNG to disintegrate custom art, logos, or avatars.
* **Zero Dependencies:** Pure vanilla HTML5, WebGL 1.0, and JavaScript in a single self-contained file.

---

## 🚀 Quick Start

No installations, build tools, or local servers required.

1. Clone or download this repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/meme-disintegrator.git
   ```
2. Double-click `index.html` to open it directly in any modern browser (Chrome, Edge, Firefox, Safari).
3. Hit **▶ Запустити розпад** to watch the animation, or **🎬 Експортувати в MP4** to generate your GIF.

---

## 🎛️ Interactive Controls

| Control | Description |
| :--- | :--- |
| **Play / Pause / Reset** | Full playback control over the disintegration sequence. |
| **Dispersal Angle Slider** | Adjusts the wind impulse direction into the upper-left quadrant (default: `-120°`). |
| **Wave Duration** | Scales the base speed of the dissolution wave (from 1.5s to 6.0s). |
| **Ash Density** | Adjusts emission volume from light wisps to a dense blizzard of debris. |
| **Background Color** | Clean white by default, with dark, slate, and custom color pickers. |
| **Custom PNG Dropzone** | Replace the default procedural 3D sad meme emoji with your own artwork. |

---

## 🛠️ Architecture & Performance

To guarantee a locked **60–165 FPS at full 1200×1200 px resolution**:
* **Body Dissolution Quad:** Evaluated via a single GLSL fragment shader utilizing multi-octave 2D Simplex Fractal Brownian Motion (`fbm`) noise.
* **Particle System:** Memory is managed using contiguous flat buffers (`Float32Array` pools up to 40,000 particles) with zero garbage collection allocations inside the animation loop.
* **Particle Rendering:** Hardware-instanced WebGL point sprites with UV atlas sampling and per-particle rotation/opacity attenuation.

---

## 📱 Telegram Video Sticker / GIF Compatibility

Videos exported via the built-in exporter have **no audio stream**. When sent to Telegram on desktop or mobile, they are automatically categorized as inline looping GIFs (`animation`), making it effortless to build custom reaction memes for group chats.
