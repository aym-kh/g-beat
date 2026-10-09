# Project Context: G-Beat

## 🎯 Overview
**G-Beat** is an experimental motion-reactive audio application inspired by Mercedes-AMG & will.i.am's *MBUX SOUND DRIVE*. It converts vehicle dynamics (accelerometer G-force and GPS velocity) into dynamic audio transitions in real time.

## Architecture & Core Mechanics
- **Sensor Fusion Strategy:**
  - **IMU Accelerometer (60Hz):** Drives low-latency DSP Low-Pass Filter (LPF) cutoff sweeps (300Hz ↔ 10,000Hz) mapped to real-time G-force.
  - **GPS Velocity (1Hz):** Drives threshold-based stem switching (muting/unmuting Drums, Bass, Synth layers on time measures).
- **Audio Engine:** Multitrack stem synchronization and DSP signal graph powered by **Tone.js** and the native **Web Audio API**.

## Stack & Conventions
- **Framework:** Angular 18+ (Standalone Components, Signals for state management).
- **Mobile Bridge:** Capacitor (`@capacitor/motion`, `@capacitor/geolocation`).
- **Audio:** Tone.js / Web Audio API.
- **Backend (Optional Future):** NestJS + Supabase (Stem storage & preset profiles).

## Strict Rules for AI Assistants
1. **State Management:** Use Angular **Signals** (`signal()`, `computed()`) for high-frequency (60Hz) sensor feeds. Do NOT trigger global Change Detection or use `zone.js` global events for sensor loops.
2. **Components:** Use **Standalone Components** exclusively. Do NOT suggest `NgModule` structures.
3. **Control Flow:** Use modern `@if` and `@for` template syntax.
4. **Audio Processing:** 
   - Never pitch-shift or time-stretch mixed full tracks. Stick to stem layering and filter cutoff sweeps.
   - Always apply volume/parameter ramping ($50\text{ms} - 500\text{ms}$) to prevent digital audio popping.
5. **Documentation:** Architectural decisions belong in `docs/rfcs/` or `docs/`. Task progress is tracked in `.ai/todo.md`.