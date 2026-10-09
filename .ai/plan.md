# Active Feature Plan: Web Audio Harness & Engine Baseline

* **Current Milestone:** Milestone 1 — Interactive Web Testing Harness
* **Primary Objective:** Build a browser-based testing harness with UI sliders (G-Force & Speed) to validate the Tone.js audio graph before flashing to mobile hardware.

---

## Technical Strategy

### Phase 1: Core Audio Engine (Tone.js)
1. Initialize `Tone.Transport` and load 3 synchronized stem loops (Bass, Drums, Synth) at a fixed BPM.
2. Route stem players into individual `Tone.Gain` nodes, then into a master `Tone.Filter` (Low-Pass Filter).
3. Expose reactive methods in `AudioEngineService` to modulate cutoff frequency and stem gain levels.

### Phase 2: Web Testing Harness (Angular UI)
1. Build `HarnessComponent` using Angular Standalone + Signals.
2. Provide interactive sliders for `G-Force (0.0g - 2.0g)` and `Speed (0 - 120 km/h)`.
3. Bind slider signals directly to `AudioEngineService` methods using Angular `effect()` or direct signal triggers.

### Phase 3: Hardware Integration (Capacitor)
1. Create `MotionService` using `@capacitor/motion` with Exponential Moving Average (EMA) signal smoothing.
2. Create `SpeedService` using `@capacitor/geolocation`.
3. Swap harness slider feeds for live native device sensors.

---

## Success Criteria
- [ ] Stems play completely in sync without drifting over time.
- [ ] Sweeping the G-Force slider produces instant, smooth low-pass filter transitions without audio popping or JS main thread stutter.
- [ ] Speed thresholds clean-mute and unmute drum/synth stems gracefully on measure beats.