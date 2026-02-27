# Chainsaw

An interactive browser artwork. The user drags across a photograph to make chainsaw cuts — the image tears open to reveal a seething dark red interior, with jagged edges, embedded splinters, flying debris particles, and looping chainsaw audio.

Live at: https://alanblackwell.github.io/chainsaw/

## What it does

- **Background**: Animated dark red "seething" layer — 9 radial gradient blobs drifting slowly, pulsing in intensity
- **Image layer**: `source.png` scaled to fill the viewport, rendered to an offscreen canvas; wound areas erased with `destination-out` compositing to reveal the seething layer beneath
- **Cuts**: User drag (mouse or touch) creates a cut path. Each path point carries stable per-point noise values for edge jaggedness and splinter placement
- **Chainsaw kerf**: A jagged polygon (30px base width, ±10px tooth amplitude) is erased along the cut path, with vibration animated each frame
- **Wound edges**: Dark red jagged edge lines + outward splinter spikes drawn along both sides of the kerf
- **Wound glow**: Pulsing red glow along the cut using `screen` blend mode
- **Debris flakes**: Elliptical particles (splinters and chunks) thrown from the cut, with gravity and drag, fading out
- **Audio**: `chainsaw.mp3` (a real recording) played in a looping Web Audio source with random start offset, slight pitch variation, and a two-tap dungeon echo effect. Fades in on mousedown, fades out (2.5s) on mouseup
- **Healing**: Completed cuts fade over 200 frames; up to 5 cuts retained at once

## Files

| File | Role |
|------|------|
| `index.html` | Entire application — single self-contained HTML/JS file |
| `source.png` | Background photograph |
| `chainsaw.mp3` | Chainsaw audio recording (looped during cuts) |

## Key constants (in index.html)

| Constant | Value | Meaning |
|----------|-------|---------|
| `KERF` | 30px | Base chainsaw cut width |
| `TEETH` | 10px | Jagged edge amplitude |
| `CUT_LIFE` | 200 frames | How long a completed cut takes to heal |
| `MAX_CUTS` | 5 | Maximum simultaneous cuts retained |

## Deployment

GitHub Pages, served directly from the `main` branch root.
No build step — edit `index.html` and push to deploy.
