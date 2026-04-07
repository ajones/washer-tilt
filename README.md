# washer-tilt

A mobile web app that watches your washing machine door using your phone's tilt sensor and yells at you if you leave it open.

Mount your phone on the washing machine door. When the door is closed (vertical), the app is happy — two eyes appear and look around. When the door swings open past the threshold, the eyes go concerned and the app starts reading out passive-aggressive one-liners every 20 seconds until you close it.

## How it works

- Uses the DeviceOrientation API to measure tilt in real time
- Happy when the device is within ±3° of vertical (door closed)
- Unhappy when outside that range (door open) — stays awake and nags until corrected
- Eyes close and go dark after a random idle period when the door is closed
- Fullscreen on tap

## Settings

- **Threshold slider** — adjusts how many degrees off vertical triggers the unhappy state
- **Voice panel** — choose a speech synthesis voice, adjust rate and pitch

## Running locally

```
npx serve .
```

DeviceOrientation requires HTTPS on mobile. Use ngrok or Tailscale to tunnel a local server, or just use the GitHub Pages deployment.

## Android voice setup

The built-in Android TTS voices all sound the same. To get better ones:

Settings → General Management → Language & Input → Text-to-speech → Google Text-to-Speech → Install voice data → English (UK)

Then reload the page — the new voices appear in the voice panel marked `network`.
