# GLass Museum

Six rooms of creative coding in **one HTML file**. No dependencies, no build step,
no external requests — open the file and it runs.

**→ [hoshinonaiginga.github.io/glass-museum/](https://hoshinonaiginga.github.io/glass-museum/)**

## The rooms

| Room | What it is |
|---|---|
| **Ray Tracer** | A software ray tracer on the CPU — spheres, a checker floor, shadows, mirrors. No WebGL. It sketches while you drag; let go and the plate develops at full resolution, 8 samples a pixel. |
| **Slime Mold** | Physarum reduced to one rule. Up to 120,000 particles on a grid, Jones' sensor angles. Drag to feed it. |
| **Synth** | Raw Web Audio: oscillator → filter → envelope, a feedback delay, a sequencer and a keyboard. Redraw the sequence while it plays. |
| **Mandelbulb** | Raymarched in a WebGL fragment shader. One ray per pixel, palette from a single cosine. |
| **Ink** | 4,000 particles reading a field of drifting sines. Touch and your finger becomes a vortex. |
| **Glasshouse** | The room that holds the museum's own source. Press `source`, edit, `run` — it rebuilds itself. |

## One file, zero dependencies

That is the constraint the whole thing is built around, not a side effect. No npm, no
bundler, no CDN, no web fonts, no service worker, no manifest. The comments are the
wall labels: the concept is that you are standing inside the source, so every room
opens with a note explaining what it does and why it does it that way.

Editing a room and pressing `run` produces a remix. It travels in the URL — `#r=` holds
a compressed JSON diff of only what you changed, usually about a kilobyte. Opening
someone's remix link runs it in a sandboxed iframe with an opaque origin, never on the
site's own origin, which on GitHub Pages is shared with every other project on the account.

<!-- GIFs to add, one per room. The ray tracer developing after you let go is the
     most convincing one. -->

## Tested on

Chrome on Android (the real audience — portrait phone) and Chromium via Playwright at
412×915 @2x: every room starts, no page errors, Slime Mold and Ink held for 60 s without
collapsing. **Safari on iOS has never been tested.** The riskiest part there is the
self-rebuild, which uses `document.write()` inside the sandboxed iframe.

## How it was made

Written with GLM — hence *GLass Museum* — then reviewed line by line with Claude and
tested on real devices. The name of the museum in the interface stays `GLASSHOUSE`.
