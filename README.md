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

## Ink & Paper

Every tool shares the same two-color system: **ink** (the mark) and **paper** (the ground). Each panel has two swatches, a ⇄ swap button, and six preset duos (Print, Blueprint, Riso Red, Terminal, Butter, Midnight). Colors persist in the URL (`?ink=ff4b2e&paper=f7f1e1`) alongside `?variant=`, so a good combo is a bookmarkable link. New tools should copy the color block from any existing tool.

## Tools

- **kinetic-type** — text warped by stacked sine oscillators. 3 variants (`?variant=A|B|C`, arrow keys to cycle).
- **flow-field-ink** — particles drifting through a vector field, leaving ink trails. 3 fields (`?variant=A|B|C`): silk, vortex, turbulence. Click or `C` to wipe the ink; fade at 0 accumulates forever (poster mode).
- **halftone** — drop any image, get it rasterized by brightness. 3 renderers (`?variant=A|B|C`): dots, lines, ASCII. Sliders for cell size, contrast, angle; right-click the canvas to save the result.
- **reaction-diffusion** — Gray-Scott simulation, upscaled from a small buffer. 3 regimes (`?variant=A|B|C`): coral, mitosis, maze — switching sets the feed/kill sliders, then drift them yourself. Drag to paint chemical, `R` reseeds.
- **physics-type** — letters as verlet bodies you grab and throw. 3 setups (`?variant=A|B|C`): springs home, hanging chain, gravity pit. `R` resets the layout.
