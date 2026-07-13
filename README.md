# Flick Blast

A browser game where you **flick your fingers at the camera** to launch projectiles and smash targets. Hand tracking is powered by [MediaPipe Hands](https://developers.google.com/mediapipe) running entirely in your browser — no data leaves your machine.

## Play

The whole game is a single file: [`index.html`](index.html). The only external dependency is the MediaPipe CDN.

Camera access requires a **secure context**, so opening the file directly via `file://` won't work in most browsers. Serve it locally instead:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

or host it anywhere with HTTPS (GitHub Pages works great).

## How to play

1. Click **Enable Camera & Play** and allow camera access.
2. Hold your hand up, palm facing the camera (the view is mirrored, like a selfie).
3. Crosshairs track your **index** and **middle** fingertips.
4. **Flick** — snap a fingertip quickly toward a target — to launch a projectile in that direction. Faster flicks launch faster shots, and each fingertip fires independently.
5. Hit targets before their timer runs out. Every target that expires costs one of your **3 lives**.
6. Chain hits within 2.5 seconds to build a **combo multiplier** (up to ×5).

### Targets

| Target | Behavior | Points |
|---|---|---|
| 🔵 Cyan bullseye | Stationary | 10 |
| 🟡 Amber square | Orbits a point, spinning | 20 |
| 🩷 Pink bullseye | Bounces around the screen | 30 |

The game speeds up as you score: more targets, faster movement, smaller hit boxes, shorter timers.

## Features

- Real-time hand skeleton overlay with highlighted flick fingers and trajectory preview
- Particle bursts, combo popups, and synthesized sound effects (Web Audio, no assets)
- Pause/resume (<kbd>P</kbd> / <kbd>Esc</kbd>), auto-pause when your hand leaves the frame or the tab is hidden
- Settings panel: camera resolution, hand-model quality, flick sensitivity, camera overlay brightness, skeleton and sound toggles
- Local leaderboard (top 5, stored in `localStorage`)
- FPS + hand-tracking-rate counter

Works in current Chrome/Chromium, Edge, Firefox, and Safari on desktop, and Chrome on Android. Bright, even lighting gives the best tracking.
