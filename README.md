# Ma — The Space Between Things

An interactive web essay about *ma* (間) — the Japanese concept of purposeful empty space — built as three watercolor koi ponds sunk into a paper-textured page, with two koi swimming freely between them through an underwater tunnel.

**[Live demo →](https://saimalshafi.github.io/ma-koi-pond/)**

## What it is

The page reads as a single flat wash of paper, with three rectangular ponds cut into it like windows onto moving water. Two koi swim continuously through all three ponds, diving under the paper between them and resurfacing on the other side — the water itself is a live WebGL ripple simulation, not a video or a sprite loop. A sakura branch casts a soft shadow across the whole page, its silhouette rippling where it falls across the water. Click anywhere in a pond to drop food; the koi will notice and swim over to eat it. The essay text about *ma* sits around the ponds and gently makes way for the koi's trailing wake as they pass through it.

Everything — the paper texture, the pond water, the koi bodies, the lily pads, the sakura branch — is a still image or a handful of images, generated in Gemini and composited together, then brought to life entirely in code: no video, no pre-rendered animation, no external animation libraries.

## How it was built

- **Water**: a real-time WebGL fluid/ripple shader reacts to the koi moving through it and to clicks, so the surface distorts continuously rather than looping.
- **Koi movement**: each koi is a chain of connected segments (an inverse-kinematics-style spine) driven by a steering/wander behavior, with the body mesh-warped frame by frame onto that spine so it bends and undulates like a real fish rather than rotating as a rigid sprite.
- **The tunnel**: koi are re-routed off the visible canvas and back through a shared "tunnel" pool between ponds, with the pond edges dissolving them in and out at the paper's edge rather than a hard cut.
- **The shadow**: a single SVG/raster sakura branch, animated with a slow parallax sway, is also sampled into the water's shader so its shadow visibly ripples wherever it crosses a pond.
- **Layout**: a fixed-proportion "stage" is scaled uniformly to fit any window size (with a cap so it doesn't blow up on ultrawide monitors), while the paper background keeps extending to fill the viewport behind it.
- **Everything else** — text, koi art, lily pads, the paper wash — is a static image or handful of images generated in Gemini and composited by hand, then laid out and animated with plain HTML, CSS and JavaScript on a `<canvas>`.

No frameworks, no build step: it's a single self-contained HTML file.

## Sound

A short looping ambient/water track, also generated in Gemini, plays softly in the background and can be muted from the toggle in the corner.

## Credits

Design, development, and image/audio direction by [Saim Al Shafi](https://saimalshafi.com). Imagery and music generated with Gemini.

## License

MIT — see [LICENSE](LICENSE).
