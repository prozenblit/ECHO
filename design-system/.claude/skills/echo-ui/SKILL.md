---
name: echo-ui
description: Use whenever building, changing or reviewing user interface for Echo (pages, screens, components, modals, forms, tables, buttons, layout, styling). Loads the Echo design system so every UI follows the exact design tokens and component markup and nothing is invented.
---
# Echo UI

You build Echo UI strictly from its design system. Do not invent colours, fonts, sizes, radii, shadows or components.

## Find the design system
The design-system folder is the one that contains `tokens.css`, `components.css`, `components.md`, `CLAUDE.md` (usually `design-system/` at the repo root). If it is not there, search the repo for `components.md` next to `tokens.json`. Everything below is relative to that folder.

## Workflow for any UI request
1. Read `CLAUDE.md` once per task (rules, tokens, non-negotiables, what NOT to do).
2. Find each needed component in `components.md` and copy its markup and class names exactly (use the variant snippet that matches the request: size, colour family, state).
3. Make sure the page loads `tokens.css` then `components.css` (and the fonts Manrope 400/500 and Jura 300/500/600 described in `README.md`).
4. Layout: use the layout patterns in `components.md` (screen frame, header, panels, tables, stepper, detail cards, the four screen compositions) before writing any custom layout CSS. For anything custom use only `var(--…)` tokens from `tokens.css`.
5. Icons: only files from `assets/` (see `assets/MANIFEST.md`) — never draw or hand-write SVG paths.
6. Text and labels: use the exact copy the user gives; do not rewrite it.
7. If the request needs something that is not in `components.md` (for example a checkbox, avatar, date picker or pagination): first check the Extended table (13 approved items: focus, error, textarea, select open list, tooltip, toast, scrollbar ...; the Modal is drawn); then build it ONLY from existing tokens and the closest component, tell the user plainly that it is not part of the design ("not in the design — derived from <components/tokens>"), and mark it with an `EXTENDED` comment. Never present it as designed.
8. Frameworks: if the project uses a framework, port the markup 1:1 (same classes, same structure) and keep `components.css` as the style source.

## Echo specifics
- Dark theme only, desktop frame 1920 wide; primary text is #DCE1E9 (token `--color-text-primary`), never pure white.
- Brand gradient: `--gradient-brand` (canonical); the Runs screens use `--alt-gradient-brand` through `.nav-pill--alt` / `.is-active` variants — do not mix them by hand.
- Outline buttons need the label inside `<span class="btn__label">`.
- Progress rings are static assets; the Pipeline photo layer has no image (set `--bg-photo-image` yourself).

## Before finishing
- No raw hex/px values that are not tokens (grep your change for `#` colours).
- Every class you used exists in `components.css`.
- States shown in the request (hover/disabled/focus/error) use the documented classes/pseudo-classes; undrawn states are labelled EXTENDED (focus, error, pressed, row hover, disabled toggle/nav pill/rows); hover and disabled of buttons, tabs and fields are drawn.
