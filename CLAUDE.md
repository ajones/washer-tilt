# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

A static single-page web app (no build step) that monitors mobile device tilt via the DeviceOrientation API and triggers animations and sounds in response.

## Running

Open `index.html` directly in a browser, or serve locally:

```
npx serve .
# or
python3 -m http.server
```

DeviceOrientation requires HTTPS on most mobile browsers. For local testing on device, use something like:

```
npx serve . --ssl-cert ... --ssl-key ...
# or tunnel via ngrok / Tailscale
```

## Architecture

- **Single-page, no framework, no build step** — plain HTML/CSS/JS.
- `DeviceOrientationEvent` provides `alpha` (z-axis), `beta` (x-axis, front-back tilt), and `gamma` (y-axis, left-right tilt) in degrees.
- iOS 13+ requires a user gesture to call `DeviceOrientationEvent.requestPermission()` before orientation events fire.
- Sounds should be created with the Web Audio API (`AudioContext`) rather than `<audio>` elements to avoid mobile autoplay restrictions and allow procedural generation.
- Animations should be driven by `requestAnimationFrame`, reading the latest orientation values each frame rather than triggering on every event.
