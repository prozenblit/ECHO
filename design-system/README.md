# Echo design system

Everything needed to build Echo screens that match the design exactly. Plain HTML + CSS (no framework): use the CSS as is, or port the markup to your framework.
Source: design file "Echo", "final (screens) + drafts (components)" (2026-11-16).

## What is inside
| File | Use |
|---|---|
| `tokens.css` / `tokens.json` | All colours, fonts, sizes, radii, spacing, shadows as named variables. `tokens.css` is the CSS version; `tokens.json` is for tooling. |
| `fonts.css` + `fonts/` | Manrope and Jura (bundled, offline). |
| `components.css` | Styles for every component and layout pattern, including the states the design draws. |
| `components.md` | Copy-paste HTML for every component, variant and state, plus behaviour notes and the four screen compositions. |
| `assets/` | Icons and logos (SVG) + `MANIFEST.md` (sizes, colours, how to use each). |
| `CLAUDE.md` | Rules for AI assistants (Claude Code reads it automatically). |
| `.claude/skills/echo-ui/` | Optional Claude Code skill: makes Claude use this system whenever you ask for UI. |

## Set up (3 steps)
1. Copy this folder into your project (e.g. `design-system/`).
2. Load the fonts and the files in your page / app entry, in this order:
```html
<link rel="stylesheet" href="design-system/fonts.css">
<link rel="stylesheet" href="design-system/tokens.css">
<link rel="stylesheet" href="design-system/components.css">
```
The fonts are Manrope (400, 500) and Jura (300, 500, 600). They are bundled in `fonts/` and declared in `fonts.css` (works offline; SIL Open Font License), so load `fonts.css` before the other two files. Keep `assets/` next to `components.css`: icon masks are resolved relative to the CSS file.
3. Open `components.md`, copy the markup of the component you need, keep the class names.

## Building by hand
- Use the CSS variables from `tokens.css` (`var(--…)`) for anything you style yourself. Do not add colours, sizes or radii that are not tokens.
- Icons: monochrome icons use the `.icon` mask classes; coloured logos and gradient icons use `<img src="assets/…">` (see `assets/MANIFEST.md`).
- States (`hover`, `active`/selected, on/off) work through real pseudo-classes and attributes; the `.is-*` classes force a state (useful for tests and docs). The design only draws a few states (CTA / outline hover, active nav, tab and sidebar item, toggle on/off); focus, disabled and error are not drawn and are not provided.
- The design is dark-only and drawn for a 1920 px wide desktop frame. Screen frames are fixed-size (1920x1080 / 1920x1293) and clip their content.
- Pipeline background: the Figma picture (`assets/pipeline-bg.jpeg`) is replaced by an interactive dot grid (extended row 41: `<canvas class="bg-grid">` inside `.bg-photo`; the drawing code is in the script at the end of `prototypes/general-information.html`). The picture file stays as the original design asset.
- Progress rings and the donut are static drawings in the design; a live version exists as extended row 25.

## Building with Claude Code
1. Copy this folder into your repo and copy `.claude/skills/echo-ui/` into the repo's `.claude/skills/` (or keep `CLAUDE.md` where Claude Code can see it, and add the line `Follow design-system/CLAUDE.md for all UI.` to your project's `CLAUDE.md`).
2. Ask in plain words, for example: "Build a confirmation modal with the text '…' and the buttons Cancel and Confirm." Claude will use `components.md` and `components.css` and will not invent styles (a modal is not in the design, so Claude will tell you it is derived and mark it EXTENDED).
3. If something looks off, ask Claude to check it against `CLAUDE.md`'s rules and the token values.

## "EXTENDED" items
The design does not draw every state or component. 42 items were added with ONLY existing tokens, approved one by one by the owner (2026-11-16 to 2026-11-18), and are marked `EXTENDED` in `components.css` (PART 3) and in the Extended table of `components.md`. The first 13: field focus, focus ring, typed-value colour, inactive tab hover, button pressed, disabled toggle/nav pill/rows, field error, textarea, Select open list, interactive row hover, tooltip, toast and scrollbar. Everything not marked `EXTENDED` comes directly from the design (including the hover/disabled states and the Modal the owner drew in Figma on 2026-11-16).

## Known design inconsistencies
See `CLAUDE.md` → "Known design inconsistencies and decisions". Highlights: the active gradient is drawn in two directions (canonical `--gradient-brand`, alternate `--alt-gradient-brand` on the Runs screens); the Outline button hover differs from the Outline + icon hover; the Overview sidebar label swap is not built; the Wallet step numerals read 1, 2, 2; typos in the design copy are kept verbatim.
