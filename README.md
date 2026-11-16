<div align="center">

# AIOdragon

**Take flight. Bring the fire.**

A 3D dragon-riding aerial combat game set above a vast cloud sea.

**JavaScript · Three.js · WebGL2 · Capacitor**

</div>

## About

AIOdragon combines dragon flight, elemental combat and a stylized fantasy world in a shared JavaScript codebase. Fly across mountain valleys, rivers and villages, face airborne enemies, and challenge the Cloud Titan.

The project is developed under AIOVerse by [Shihab Shahriar Aion](https://github.com/AION-2000). It builds on a supplied Skyfire reference game, with documented integration, input, diagnostics, branding and Android packaging changes.

> **Repository status:** Documentation has been initialized. The complete game source, Android project, screenshots and release artifacts have not yet been imported into this repository. The prepared Android release candidate is **1.0.1**, which removes the reference watermark. A buildable GitHub checkout will be available after the source import.

## Game experience

- **Dragon flight:** wing-driven movement, banking, hovering, dives, boosts and evasive maneuvers.
- **Aerial combat:** fire breath, charged fireballs, target locking and elemental progression.
- **Enemies and encounters:** Shade Riders, drake flocks and the Cloud Titan boss.
- **Survival mode:** escalating waves and locally saved records.
- **A world above the clouds:** toon shading, terrain, water, vegetation and volumetric clouds.
- **Multiple perspectives:** chase camera, rider view and photo mode.
- **Flexible controls:** touch, keyboard, mouse and gamepad input paths.
- **Procedural audio:** synthesized effects and music through WebAudio.

These features originate in the reference implementation and its documented patches; their presence is not a claim that every feature has passed native-device acceptance.

## Platform status

| Target | Current status |
| --- | --- |
| Android | Signed APK and AAB release candidate prepared with Capacitor |
| Browser | WebGL2 game served through a local HTTP server |
| iOS | Intended target; no native iOS release has been produced |
| Windows | Browser launchers available; no new native Windows installer in this release |

### Android release identity

| Setting | Value |
| --- | --- |
| Application ID | `com.aioverse.aiodragon` |
| Version | `1.0.1` |
| Version code | `2` |
| Minimum Android version | Android 8 / API 26 |
| Target SDK | API 36 |
| WebView requirement | Android System WebView 100+ with WebGL2 |
| Orientation | Landscape |
| Local app origin | `https://localhost` |

The Android build bundles ES modules with esbuild and includes immersive fullscreen, keep-awake and background input-release integration.

## Architecture

A system-based game core coordinates rendering, input and simulation. Feature systems expose lifecycle hooks for initialization, fixed updates and frame updates.

| Layer | Responsibility |
| --- | --- |
| Core | Fixed-step simulation, system registry, events, quality and diagnostics |
| Actors and combat | Dragon physics, riders, enemies, weapons and boss encounters |
| World and rendering | Terrain, water, sky, clouds, materials and post-processing |
| UI and input | Menus, HUD, settings, touch controls and device input |
| Audio and effects | Procedural sound, particles and combat feedback |
| Platform integration | Web bundling and Capacitor Android packaging |

## Run the prepared source package

The commands below apply to the complete release kit, **not the documentation-only checkout currently in this repository**.

### Browser development

Install Node.js 22 or newer, extract the release kit, and open a terminal in the project directory:

```sh
npm ci
npm start
```

Open the local URL printed by the server. Serve the game over HTTP; do not open `index.html` with `file://`.

### Android build

Install a full JDK 21, Android SDK Platform 36 and Build Tools 36.0.0. Configure `JAVA_HOME` and `ANDROID_HOME`, accept SDK licenses, and restore the private signing backup outside the project directory.

```sh
npm ci
node scripts/configure-signing.mjs /absolute/path/to/private-signing-backup
npm run android:release
```

Build outputs:

- `android/app/build/outputs/apk/release/app-release.apk`
- `android/app/build/outputs/bundle/release/app-release.aab`

Use the APK for direct installation and the AAB for Google Play submissions. Keep the same signing identity and increase the version code for subsequent updates.

### Checks

```sh
npm test
npx playwright install chromium
npm run test:browser
```

## Release validation

The prepared 1.0.1 candidate passed Android build and signature verification. Packaged HTML and JavaScript were checked against the web bundle, and the watermark image and overlay were confirmed absent. Updated mobile-emulated browser captures completed without recorded browser errors.

The preceding 1.0.0 baseline passed 14 core/input tests. Native-phone installation, sustained frame rate, audio and background/resume behavior, ten-minute memory stability, and a complete campaign playthrough still require acceptance testing. Browser emulation is not a substitute for real-device testing.

## Privacy and storage

The current release has no accounts, ads, analytics or in-app purchases. Settings and records are stored locally. The release kit includes a privacy policy and Data Safety guidance. A public privacy-policy URL and a monitored support email must be configured before store submission.

## Source provenance and asset rights

AIOdragon is a patched derivative of the supplied **Skyfire: Riders of the Cloud Sea** reference. Original gameplay systems, models, textures and bundled vendor code are retained where documented. The 1.0.1 update removes the on-screen reference watermark; it does not change underlying asset ownership or licensing.

The complete release kit includes `SOURCE-ATTRIBUTION.md` and `THIRD-PARTY-LICENSES.txt`. No blanket open-source license is granted to third-party assets by this README.

## Signing security

Private keystores, signing passwords, `keystore.properties` and private backup archives must never be committed. Public application source and store artwork are separate from signing credentials.

## Maintainer

**Shihab Shahriar Aion · AIOVerse**

[GitHub](https://github.com/AION-2000) · [Report an issue](https://github.com/AION-2000/AIOdragon/issues)
