# Design Tools

Self-built generative design toys, inspired by [rohan newman's custom-tools experiments](https://www.instagram.com/p/DVxYR8Hidd4/): prompt an AI for a sketch, run it live in the browser, play with the parameters, keep what feels good.

## Run

No build step, no dependencies. Either:

- double-click `index.html` (gallery) or any `tools/<name>/index.html`, or
- `python3 -m http.server` in this folder → http://localhost:8000

## Structure

```
index.html            gallery — links to every tool
tools/<name>/index.html   one self-contained tool per folder
```

**Rule of the playground:** every tool stays a single dependency-free HTML file. That keeps the barrier to starting (and abandoning) a toy at zero.

## Adding a tool

1. Copy an existing tool folder as a starting point (`tools/kinetic-type/` has the canvas + slider + variant-switcher harness).
2. Describe the effect you want to an AI the way rohan does — name the geometry (grid / stripes / slices), the oscillators, the blend mode, and which parameters get sliders.
3. Add one `<li>` to the gallery in `index.html`.

## Tools

- **kinetic-type** — text warped by stacked sine oscillators. 4 variants (`?variant=A|B|C|D`, arrow keys to cycle). Variant D's `warpField()` is intentionally left as a stub — write your own oscillator mix there.
