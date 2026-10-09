# G-Beat

**Real-time motion-reactive audio engine driven by mobile telemetry and Web Audio DSP.**

Inspired by Mercedes-AMG and WILL.I.AM's *MBUX SOUND DRIVE*, **G-Beat** is an experimental hybrid mobile application built with **Angular**, **Capacitor**, and **Tone.js**. It transforms physical vehicle dynamics, instantaneous acceleration, braking G-forces, and baseline velocity into dynamic multitrack music transitions in real time.

## The Problem & Solution

* **The Problem:** Standard GPS-based speed tracking has a 1–3 second latency and jitter. Changing song pitch/tempo strictly by speed leads to unnatural audio stretching and laggy feedback.
* **The Solution:** G-Beat uses a **hybrid sensor fusion** approach:
  * **Accelerometer & Gyroscope (60Hz):** Drives zero-latency Digital Signal Processing (DSP) filter sweeps (e.g., Low-Pass Filter cutoff) the millisecond acceleration happens.
  * **GPS Geolocation (1Hz):** Anchors baseline speed tiers to dynamically mute/unmute synchronized audio stems (Drums, Bass, Synth) on beat measures.

## Architecture Overview

<img width="1194" height="1324" alt="image" src="https://github.com/user-attachments/assets/f75cf2bd-63f8-4bdf-bbc2-2940d8d59941" />


1. **Motion Service:** Captures raw IMU G-force data and applies exponential moving average (EMA) smoothing.
2. **Speed Service:** Monitors vehicle velocity in km/h for threshold-based stem switching.
3. **Audio Engine:** Manages sample-accurate stem synchronization, gain nodes, and low-pass filter sweeps.

## Tech Stack

* **Framework:** Angular (Standalone Components, Signals for state)
* **Mobile Bridge:** Capacitor (`@capacitor/motion`, `@capacitor/geolocation`)
* **Audio DSP:** Tone.js / Web Audio API
* **Language:** TypeScript


## 🚀 Getting Started (Web Harness)

Test the audio engine directly in your browser using interactive UI sliders for G-Force and Speed before flashing to mobile hardware:

```bash
# Clone the repository
git clone [https://github.com/your-username/g-beat.git](https://github.com/your-username/g-beat.git)
cd g-beat

# Install dependencies
npm install

# Start local dev server
npm start
Open http://localhost:4200 to access the Web Testing Harness.
```
