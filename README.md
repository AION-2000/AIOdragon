<div align="center">

# 🐉 AIOdragon

### Rule the skies. Command the fire.

**A cinematic 3D dragon-flight and aerial-combat experience, powered by the browser and packaged for Android.**

[![Release](https://img.shields.io/badge/Release-v1.0.1-ef6c35?style=for-the-badge)](#release-status)
[![Three.js](https://img.shields.io/badge/Three.js-WebGL2-111827?style=for-the-badge&logo=threedotjs)](#technology)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES%20Modules-303b59?style=for-the-badge&logo=javascript)](#technology)
[![Android](https://img.shields.io/badge/Android-Capacitor-267d65?style=for-the-badge&logo=android)](#android-build)

**[Overview](#overview) · [Features](#the-experience) · [Architecture](#architecture) · [Quick start](#quick-start) · [Android](#android-build) · [Credits](#credits--provenance)**

</div>

---

## Overview

**AIOdragon** takes players high above a cloud sea into a stylized fantasy world of dragon flight, elemental combat, airborne encounters, and boss battles. Its WebGL2 game is built with JavaScript and Three.js, with an Android release candidate packaged through Capacitor.

The project is a **patched and repackaged derivative** of the supplied *Skyfire: Riders of the Cloud Sea / Skyfire-Touch* reference game. AIOdragon's work includes mobile-input and lifecycle improvements, diagnostics, quality-control helpers, updated branding, web bundling, Android packaging, and release checks. **The original gameplay systems, models, and much of the artwork remain inherited reference work.**

> [!IMPORTANT]
> **Repository status:** This GitHub repository is currently **documentation-only**. The complete, buildable project exists in the separate **AIOdragon Android Release Kit** and has not yet been imported here. The instructions below apply **after** the game source, Android project, tests, and assets have been added. A README alone is not the game.

## The experience

| System | Experience |
| :-- | :-- |
| 🐉 **Dragon flight** | Banking, hovering, dives, boosts, and evasive maneuvers |
| 🔥 **Elemental combat** | Fire breath, charged attacks, target engagement, and effects |
| ⚔️ **Encounters** | Airborne enemies and a Cloud Titan boss encounter |
| 🌪️ **Survival** | Escalating waves and locally saved records |
| 🌄 **World & atmosphere** | Terrain, waterways, stylized clouds, vegetation, and atmospheric rendering |
| 🎥 **Camera & presentation** | Chase camera, rider perspective, and photo mode |
| 🎮 **Controls** | Keyboard, mouse, touch, and gamepad input paths |
| 🎵 **Audio** | Procedural music and sound using Web Audio |

*These systems are present in the inherited reference and documented patches. This does not certify native-device performance or a completed campaign playthrough.*

## Technology

| Layer | Technologies |
| :-- | :-- |
| Game runtime | JavaScript ES Modules, Three.js, WebGL2 |
| 3D content | GLB models, terrain data, textures, effects |
| Architecture | Fixed-step simulation, system registry, events, quality and diagnostics |
| Interface | HTML, CSS, HUD, touch and device input |
| Android | Capacitor 8, Gradle, Android Studio |
| Tooling | Node.js, npm, esbuild |
| Quality | Node test runner, jsdom, Playwright |

## Architecture

The full release kit has the following layout:

\`\`\`text
AIOdragon/
├── game/
│   ├── src/
│   │   ├── core/          # Simulation, events, input and diagnostics
│   │   ├── actors/        # Dragons, riders, enemies, progression
│   │   ├── combat/        # Weapons and combat effects
│   │   ├── world/         # Terrain, clouds, sky, vegetation and water
│   │   ├── render/        # Atmosphere, pipeline, materials
│   │   ├── camera/        # Camera systems
│   │   ├── audio/         # Sound and music
│   │   ├── ui/            # Menus, HUD and touch controls
│   │   └── vfx/           # Visual effects
│   ├── assets/            # GLB models and textures
│   ├── vendor/            # Bundled third-party modules
│   └── index.html
├── android/                # Capacitor / Gradle project
├── scripts/                # Web and Android build scripts
├── qa/                     # Core, touch, browser and static QA
├── store/                  # Graphics, screenshots and store guidance
├── package.json
├── capacitor.config.json
└── SOURCE-ATTRIBUTION.md
\`\`\`

## Quick start

**Prerequisites:** Node.js **22+**, npm, and a modern browser supporting **WebGL2**.

Once the source has been imported:

\`\`\`bash
git clone https://github.com/AION-2000/AIOdragon.git
cd AIOdragon
npm ci
npm start
\`\`\`

Open the local URL printed by the server. The game must be served over HTTP; opening \`game/index.html\` through \`file://\` is not supported for ES modules and local assets.

### Developer commands

| Command | Action |
| :-- | :-- |
| \`npm start\` | Start the local game server |
| \`npm test\` | Run Node unit tests |
| \`npm run build\` | Build the production web bundle |
| \`npm run test:browser\` | Run Playwright browser QA |
| \`npm run android:sync\` | Build and sync assets to Android |
| \`npm run android:open\` | Open the native project in Android Studio |

For browser QA, run \`npx playwright install chromium\` after installing dependencies.

## Android build

The Android release wraps the browser game through **Capacitor**, with landscape orientation, immersive fullscreen, wake-lock integration, and lifecycle/input cleanup.

| Setting | Value |
| :-- | :-- |
| App ID | \`com.aioverse.aiodragon\` |
| Release candidate | \`1.0.1\` |
| Version code | \`2\` |
| Minimum Android | Android 8 · API 26 |
| Target SDK | API 36 |
| Orientation | Landscape |

**Toolchain:** JDK **21**, Android SDK Platform **36**, Build Tools **36.0.0**, Android Studio.

\`\`\`bash
npm ci
npm run android:sync
npm run android:open
\`\`\`

### Signed release

Restore the **existing private signing backup** outside the repository, then:

\`\`\`bash
node scripts/configure-signing.mjs /path/to/PRIVATE-SIGNING-BACKUP
npm run android:release
\`\`\`

Expected outputs:

- \`android/app/build/outputs/apk/release/app-release.apk\` — sideload / direct installation
- \`android/app/build/outputs/bundle/release/app-release.aab\` — Google Play submission

**Never commit signing keys, signing passwords, private backup ZIPs, \`keystore.properties\`, or generated APK/AAB binaries.** The original signing identity is required for compatible app updates.

## Quality & testing

The prepared **1.0.1 release candidate** passed reported Android build, signature, package-identity, and watermark-removal checks. The release kit also contains browser-emulated screenshot evidence.

**Not yet validated:** complete gameplay on a physical Android device, sustained frame rate and memory use, long-session battery/thermal behavior, audio routing, background/resume reliability, and end-to-end campaign completion.

Browser-emulated screenshots are not evidence of physical-device FPS or compatibility. The release kit includes QA notes, test reports, and release verification artifacts.

## Release status

**v1.0.1 — Android release candidate; not a Google Play production release.**

- Configured the app identity as AIOdragon.
- Removed the unwanted reference watermark from the bundled game.
- Retained the signing identity required for an update.
- Added Android build and package verification.
- Prepared store material and checklists.
- Documented remaining acceptance work explicitly.

A public privacy-policy URL, monitored support address, physical-device checks, and Google Play review are still outstanding.

## Privacy & security

This candidate has no game accounts, advertising SDK, analytics SDK, or in-app purchases. Settings and records are stored locally. Before publication, review the release kit's data-safety guidance and actual store requirements.

## Roadmap

- [ ] Import the audited source, Android project, assets, and screenshots into GitHub.
- [ ] Validate launch, touch controls, rendering, and audio on physical Android devices.
- [ ] Measure sustained FPS, memory use, battery and temperature.
- [ ] Add automated CI for web builds and tests.
- [ ] Finish support/privacy URLs and store compliance.
- [ ] Publish an approved release once acceptance is complete.

## Credits & provenance

**AIOdragon · AIOVerse**, maintained by **Shihab Shahriar Aion**.

AIOdragon builds on the supplied **Skyfire-Touch / Skyfire: Riders of the Cloud Sea** reference. Inherited gameplay, art, assets, and vendor libraries are not claimed as entirely new AIOVerse creations.

The source kit includes **SOURCE-ATTRIBUTION.md** and **THIRD-PARTY-LICENSES.txt**, which describe the authorship boundary and bundled MIT-licensed vendor code, including Three.js and meshoptimizer. **Do not assume that the complete derivative, including reference gameplay and artwork, is open-source or freely redistributable.** No blanket license is granted by this README.

---

<div align="center">

### Built for the sky. Engineered for the next flight.

**AIOVerse** · [GitHub profile](https://github.com/AION-2000) · [Issues](https://github.com/AION-2000/AIOdragon/issues)

</div>