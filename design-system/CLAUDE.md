# Echo — Design System
**For Claude agents building or modifying this platform**

Load this file at the start of any session working on Echo. All design decisions must follow these rules. Do not invent, substitute, or "improve" values.

## Companion files — load these too
- `components.css` — full CSS for all components and patterns, all drawn states
- `components.md` — copy-paste HTML for every component with behaviour notes + the Extended table
- `tokens.css` — all tokens as CSS custom properties · `tokens.json` — same tokens as JSON
- `fonts.css` + `fonts/` — bundled Manrope and Jura (offline)
- `assets/` — exported icons/logos + `MANIFEST.md` (use only these; never redraw icons)
- `README.md` — human-readable setup and usage guide; `.claude/skills/echo-ui/` — optional skill that loads this system automatically

**When implementing any UI:** check `components.md` first. If the component exists, use that exact HTML + CSS class. Do not write new CSS for something already in the library.

## What the platform is
Echo is a desktop web application for running client KYC (know-your-customer) checks: a Pipeline of runs that need attention, a Runs view with ownership structure / UBOs / directors / required actions, and a Wallet Check form that links a crypto wallet to a client (spec: the four screens `78:2486`, `78:1751`, `78:2225`, `78:2600`). The design is dark-only (screen background `Black 900` #08090A) and drawn at a fixed 1920 px frame width; no responsive variants, breakpoints or mobile layouts exist in the design. Layout is a 66 px header (logo, five nav pills, an environment Select) above a centred content area.

## Source of truth
- Design file `Echo` · screens page "final" (`78:1750`, four frames: Pipeline `78:2486`, Runs / Ownership `78:1751`, Runs / Overview `78:2225`, Wallet Check `78:2600`) · component definitions page "drafts" (`3:10845`; the only place they exist). Extracted 2026-11-16. The extracted spec files are in `../figma-spec/`.
- Owner decisions (defaults applied because the open questions were not answered): (1) the Pipeline background photo is replaced by the interactive dot grid (extended row 41, owner 2026-11-17); (2) the active-gradient direction canonical = "Gradient main oposite" for nav pill and tabs, the other direction kept as `--alt-*`; (3) the Overview sidebar label swap is treated as an inconsistency and not built (Ownership is the reference); (4) Outline-button hover built as drawn per component (3-stop vs 2-stop), difference kept; (5) progress rings and donut are static drawn assets; (6) unused definitions (Outline Button, Tabs 32, toggle) are kept; Wallet step numerals "1, 2, 2" and nav "Runs" Medium weight kept verbatim; (7) gradient notation `#7BE697@0 -> #53B2ED@1` means stop POSITION.
- Not canonical / ignored: pages "old echo" (captures of an older built app) and "styling examples" (inspiration captures); the older copies of the four screens on "drafts" (identical or superseded; final wins).

## Non-negotiables
- Dark theme only: screen fill `Black 900` #08090A, primary text `White` #DCE1E9 (the style is named "White" but its value is #DCE1E9, never #FFFFFF). (spec: `78:2486`, `78:2501`)
- Font: Manrope Regular 400 and Medium 500 for all UI text; Jura Light 300 / Medium 500 / SemiBold 600 for numerals only. Base text is Manrope Regular 12. Letter-spacing 0 everywhere. No bold, italic, uppercase transforms or tracking. (spec: foundations §2, `78:2501`)
- Brand colour is a gradient between Blue-ish `#53B2ED` and Green `#7BE697`; the canonical direction is `--gradient-brand` (`#53B2ED -> #7BE697`). Accent text colour is Blue `#59BCFA`. (spec: `78:2500`, `18:249`, `21:379`)
- Radii by role: 4 pills/tags, 8 controls/buttons/tabs/row cards/notices/active nav pill, 16 KPI cards/panels/large cards, 24 inactive nav pills, toggle track, step chip. (spec: `78:1974`, `10:170`, `78:2516`, `78:2502`)
- Control height 32 (24 for Tabs 24 and the step chip); toggle 32x16. Only one button height exists. (spec: `10:170`, `21:401`, `21:31`)
- Borders are hairlines: 1 px Grey 400 on panels/controls/rows/tables, 0.5 px for active nav / warning outlines. (spec: `78:2516`, `78:2500`, `78:1970`)
- The only shadow is a drop shadow on the gradient ring/donut arcs, baked into the static assets. No other shadows, blurs or scrims exist. (spec: `78:2551`)
- Icons come only from `assets/`; monochrome ones as masks, gradient/logo ones as `<img>`. (spec: assets manifest)
- Plain HTML + CSS, no framework; developers port the markup 1:1.

## Tokens
### Named design colours
Exact design paint-style names (30). CSS var = `--color-<kebab name>`. Alpha entries are `rgba()` in CSS.
| Token (CSS var) | Design name | Value | Use |
|---|---|---|---|
| `--color-black-900` | Black 900 | #08090A | screen background, KPI card, text on bright fills |
| `--color-grey-500` | Grey 500 | #111213 | control fill, row card, filled panel, header border |
| `--color-grey-400` | Grey 400 | #1C1E1F | hairline borders, tab track, step chip |
| `--color-grey-300` | Grey 300 | #62666D | muted text, placeholders |
| `--color-grey-200` | Grey 200 | #8A8F98 | secondary text (the outline button is White since 2026-11-17) |
| `--color-grey-100` | Grey 100 | #A6ACB6 | label text, form labels, toggle OFF track and label |
| `--color-white` | White | #DCE1E9 | primary text, CTA fill |
| `--color-blue` | Blue | #59BCFA | accent text (percentages, links, numerals) |
| `--color-blue-75` / `-50` / `-25` / `-15` | Blue 75% / 50% / 25% / 15% | #59BCFA at .75 / .5 / .25 / .15 | logo lines, person-tag fill (15%) |
| `--color-green` | Green | #7BE697 | success, approved, status dot |
| `--color-green-75` / `-50` / `-15` | Green 75% / 50% / 15% | #7BE697 at .75 / .5 / .15 | defined, not applied on the screens |
| `--color-green-25` | Green 25% | #7BE697 at .25 | success pill fill |
| `--color-orange` | Orange | #F3AB52 | warning / missing text, dot, warning outline |
| `--color-red` | Red | #F35352 | conflict / problem text, dot |
| `--color-red-25` | Red 25% | #F35352 at .25 | problem pill fill, critical notice fill |
| `--color-red-50` | Red 50% | #F35352 at .5 | defined, not applied on the screens |
| `--color-purple` | Purple | #9081E4 | role / "Main check" text, info |
| `--color-purple-15` | Purple 15% | #9081E4 at .15 | role pill, info notice fill |
| `--color-purple-50` | Purple 50% | #9081E4 at .5 | defined, not applied on the screens |
| `--color-gradient-main-oposite` | Gradient main oposite (sic) | #53B2ED@0 -> #7BE697@1 | canonical brand gradient (nav pill, tabs, CTA hover, logo) |
| `--color-gradient-main` | Gradient main | #7BE697@0 -> #53B2ED@1 | the alternate direction (Runs screens, chevrons, step numerals) |
| `--color-gradient-green` / `-green-opposite` | Gradient green / opposite | #5DE7CB -> #66D74A / reversed | toggle ON track ONLY (not the stepper ring: that shows Gradient main); opposite not applied |
| `--color-gradient-orange` | Gradient orange | #F3892D@0 -> #ECE040@1 | current-step circle |
| `--color-bg-gradient` | bg gradient | #111213 (alpha 0.1)@0 -> #161718@1 | large panel fill |
Gradient CSS angles are derived arithmetically from the design transforms (88.23deg for the brand/green/orange styles, 85.08deg for bg gradient); exact transforms are in each token comment in `tokens.css`.
### Semantic aliases
| Token | → | Use |
|---|---|---|
| `--color-text-primary` | White | headings, nav, titles |
| `--color-text-label` / `-secondary` / `-muted` | Grey 100 / 200 / 300 | labels / secondary / captions + placeholders |
| `--color-text-inverse` | Black 900 | label on CTA / active tab |
| `--color-text-accent` / `-danger` / `-warning` / `-success` / `-info` | Blue / Red / Orange / Green / Purple | data-driven text colours |
| `--color-surface-base` / `-field` / `-raised` / `-cta` / `-card-gradient` | Black 900 / Grey 500 / Grey 400 / White / bg gradient | surfaces |
| `--color-border-hairline` / `-header` / `-outline` / `-warning` / `-active` / `-active-alt` | Grey 400 / Grey 500 / White / Orange / brand gradient / alt gradient | borders |
| `--color-brand-gradient`, `-gradient-alt`, `-accent`, `-logo-wordmark` | brand gradient, alt gradient, Blue, raw wordmark | brand |
| `--color-action-*` (19) | cta, outline, toggle, tab, field roles | control parts (see `tokens.css`) |
| `--color-status-*` (19) | dot, pill, notice roles | status parts (see `tokens.css`) |
| `--gradient-brand` / `--alt-gradient-brand` | canonical / alternate brand gradient | use these for gradient fills and strokes |
### Raw (unbound in the design)
| Token | Value | Use |
|---|---|---|
| `--color-raw-logo-wordmark` | #4DFFCD | logo wordmark glyph vectors (inside the logo asset) — raw in design (no style bound) |
| `--color-raw-ring-arc-gradient` | #53B2ED -> #7BE697 (142.16deg) | progress arc of ring/donut (inside the static assets) |
| `--color-raw-ring-arc-gradient-short` | #53B2ED -> #7BE697 (153.67deg) | Pipeline 72 px short ring arc |
| `--color-gradient-progress` | #54B3E9 -> #F3892D | stepper line done -> current. Name "Gradient progress" chosen by Claude (unnamed raw paint in Figma; create a style with this name there to match) |
| `--color-raw-outline-hover-stroke` | #53B2ED / #4CCED4 @0.5 / #45EABB | Outline Button hover stroke (3 stops) |

## Typography
Font families: `--font-primary` Manrope, `--font-numeric` Jura (not monospace; the design has no monospace). Every real tuple (weight / size / line-height / letter-spacing 0) has a class and a `--type-*` token:
| Role | Tuple | Class |
|---|---|---|
| pill | Manrope Regular 10 (Figma 8; owner override) | `.type-pill-10` |
| person tag | Manrope Medium 10 (Figma 8; owner override) | `.type-tag-10` |
| field-small (table headers, "Single Source" pill, counts) | Manrope Regular 10 | `.type-field-10` (Select/Search/Input text is now Regular 12 = `.type-body-12`, Figma change 2026-11-16) |
| label | Manrope Medium 10 | `.type-label-10` |
| paragraph | Manrope Medium 10 / 16px | `.type-paragraph-10` (only the long Overview paragraph `78:2434` has a fixed line-height) |
| paragraph 12 (EXTENDED #27) | Manrope Medium 12 / 20px | `.type-paragraph-12` (owner: readable notice paragraph) |
| body | Manrope Regular 12 | `.type-body-12` |
| title | Manrope Medium 12 | `.type-title-12` |
| heading 14 / 16 | Manrope Medium 14 / 16 | `.type-heading-14` / `.type-heading-16` |
| numerals | Jura Medium 38 / 20 / 14, SemiBold 12 (+ Light for the `%` glyph) | `.type-numeral-38/20/14/12`, `.numeral-light` |
Sizes used: 8, 10, 12, 14, 16, 20, 38. Weights used: 300 (Jura `%` only), 400, 500, 600 (Jura caption only). Do not use any other size/weight/family. Design line-height "auto" = CSS `normal`.

## Spacing, sizing and controls
- Spacing values (`--space-1 … --space-64`: 1 2 4 6 8 10 12 13 16 20 24 32 36 38 40 48 64) are OBSERVED paddings and gaps; the design defines no spacing tokens or variables.
- Control heights: 32 (Select, Search, Input, buttons, Tabs 32, nav pill), 24 (Tabs 24, step chip, section head), 16 (toggle). Pills 15 high (18 for the one "Single Source" pill).
- Strokes: INSIDE strokes are CSS borders with the same padding; centre strokes on outline buttons are inset shadows; the 0.5 OUTSIDE stroke of the warning pill is a box-shadow; gradient strokes are masked `::before` rings (documented in each rule).
- Hug widths may differ 0.1–5 px between the design and a browser because of font metrics; do not "fix" with magic numbers.
- Effects: one drop shadow (rings only). Opacity: 0.7 on person-tag text, issue lines, notice suffix; 0.5 inside two icon assets; 0.2 photo.
- Motion: the design defines no durations, easings or transitions. Motion that exists (drawer, hover easing, dot grid, toasts) is EXTENDED and approved by the owner; do not add other animations as "design".

## Components
Everything below is **Design-defined** unless marked EXTENDED (42 approved extensions, listed in the Extended section). Details and markup in `components.md`.
### Button — CTA — Design-defined (spec: `18:142`, hover `18:249`)
`.btn.btn--cta`; White fill, Black 900 label, 32 high, radius 8, padding 0/24; hover (`:hover` / `.is-hover`) = brand gradient fill.
### Button — Outline — Design-defined (spec: `18:227`, hover `18:253`)
`.btn.btn--outline` + `<span class="btn__label">`; 0.5 px White stroke and White label (owner changed from 1 px Grey 200, 2026-11-17; hover ring 0.5 px, disabled keeps 1 px); hover = 3-stop gradient stroke + gradient label. Defined in the design but not used on a screen.
### Button — Outline + icon — Design-defined (spec: `18:289`, hover `18:291` "Variant2")
`.btn.btn--outline.btn--has-icon` + `.icon.icon--download`; padding 0/20/0/16, gap 12; hover = 2-stop stroke, gradient label, icon swaps to `download-variant2.svg`.
### Select — Design-defined (spec: `10:170`)
`.select` (+ `.select__label`, `--value`, `.select__chevron`); 32 high, Grey 500 fill, 1 px Grey 400 border, radius 8. Trigger only; no open list drawn.
### Search / Input — Design-defined (spec: `73:1680`, `73:1679`)
`.search` (+ `.search__icon`, `.search__input`, `--fill`), `.input` (+ `--fill`, `--narrow`); 120x32 fixed or FILL; placeholder Grey 300. Typed-text colour not drawn.
### Tabs — Design-defined (spec: `21:384` Tabs 32, `21:401` Tabs 24)
`.tabs` / `.tabs.tabs--sm` + `.tab` + `.is-active` (`aria-selected`); track Grey 400, active = brand gradient with Black 900 label.
### Toggle / toggle with text — Design-defined (spec: `21:32`, `21:55`)
`.toggle` (+ `.is-on`, `aria-checked`), `.toggle-field` (+ `.is-on`); OFF Grey 100 track and label, ON "Gradient green" track.
### Status pill / person tag — Design-defined, pattern (spec: `78:1974`, `78:2007`, `78:2018`, `78:2046`, `78:2056`, `78:2108`)
`.pill` + `--tag | --warning | --danger | --success | --role | --lg`.
### Status dot, KPI card, panel, row card, notice, step chip, nav pill — Design-defined, patterns
`.dot`, `.kpi`, `.panel` (+ `--filled`, `--gradient`, `--side`), `.row-card` (+ `--run`, `--dark`, `--fill`, `--top`, `.is-active`), `.notice` (+ `--critical | --warning | --info`), `.step-chip`, `.nav-pill` (+ `.is-active`, `--alt`, `--medium`) (spec: `78:2583`, `78:2516`, `78:2528`, `78:2531`, `78:1957`, `78:2632`, `78:2500`).
### Hover / disabled states drawn after the first build, and the Modal — Design-defined (Figma 2026-11-16)
Select/Search/Input hover (Grey 300 border) and disabled (Grey 400 fill, Grey 300 border/text); CTA, Outline, Outline+icon and Tabs disabled (colour swaps, no opacity); Modal (`.modal-scrim` + `.modal`: Black 900 at 25% scrim with blur 12, Grey 400 dialog radius 8 padding 24). Classes in `components.md`.
### Layout patterns — Design-defined
Screen frames and header, Pipeline photo layer (pattern, no image), section head, data tables (UBOs / Directors), ownership tree, stepper, progress ring and donut, filter list, action list, summary card, detail cards, and the four screen compositions.

## Layout and shell geometry
- Frames: Pipeline and Wallet Check 1920x1080; Runs / Ownership and Overview 1920x1293 (fixed height, content shorter than the frame). Frames clip their content; no scroll regions are drawn. (spec: `78:2486`, `78:2600`, `78:1751`, `78:2225`)
- Header: 1920x66 = padding 16/40, 33 high nav, 1 px bottom border Grey 500, space-between; logo box 162x32 (85x20 logo), nav 643 wide, Select 148x32 at the right. (spec: `78:2488`)
- Content: Pipeline column 642 wide at y 106; Wallet 984 wide (form 658 + gap 38 + side panel 288) at y 106; Runs 1500 wide at y 90 (side panel 288 + gap 16 + main 1196; main = summary card 307 + gap 13 + sidebar 218 + gap 1 + card 977). Content is centred horizontally. (spec: `78:2511`, `78:2624`, `78:1775`)
- Z-order = DOM order: photo layer, header, content. No overlays, modals, drawers or scrims exist.
- Tokens: `--layout-*` in `tokens.css`.

## Icons
Present in the design (all in `assets/`, see `assets/MANIFEST.md`): download (mask, 11x13), circle-exclamation-point (mask, 12), building (mask, 16), circle-user-round (mask, 16), select chevron (img, 16), search (img, 16), logo (img, 85x20), three step-status icons (img, 42), three progress-ring files (img, static), download-variant2 (hover asset). Mask pattern: `.icon` + `.icon--<name>`.
Added by the owner 2026-11-17: arrow-down and arrow-right (`assets/arrow-*.svg`). NOT in the design (searched): close, plus, minus, other arrows/chevrons, checkbox/radio glyphs, standalone check, calendar, filter, avatars, flags, illustrations. Do not draw or invent them.

## Known design inconsistencies and decisions
| Topic | Variant A | Variant B | Decision | Where kept |
|---|---|---|---|---|
| Active gradient direction | "Gradient main oposite" `#53B2ED -> #7BE697`: nav pill on Pipeline/Wallet, Tabs, CTA hover, Outline+icon hover | "Gradient main" `#7BE697 -> #53B2ED`: nav pill, sidebar active item and active run card on the Runs screens, chevron, step numerals | canonical = oposite (`--gradient-brand`); Runs usage built with the alternate | `--alt-gradient-brand`, `.nav-pill--alt`, `.row-card.is-active`, `.filter-item.is-active` |
| Outline hover recipe | Outline Button: raw 3-stop stroke `#53B2ED / #4CCED4@.5 / #45EABB` (`18:253`) | Outline + icon "Variant2": 2-stop stroke "Gradient main oposite" (`18:291`) | each reproduced as drawn, nothing unified | `--gradient-outline-hover` vs `--gradient-brand` |
| Overview sidebar | Ownership screen: active item "Ownership" gets the gradient border and Medium White label | Overview screen: gradient border on "Overview" but its label stays Regular Grey 100, while "Ownership" (not active) keeps the Medium White label | label swap NOT built; Ownership is the reference, `.is-active` styles the current item | `.filter-item.is-active` |
| Progress ring / donut | static drawn arc; label "62%" with caption "60 out of 116" (arc length not equal to the number) | Pipeline: 41% short arc, 62% long arc | kept static; no dynamic arcs (would be an extension) | `assets/progress-ring-*.svg` |
| Wallet step numerals | drawn "1, 2, 2" | "1, 2, 3" | OWNER DECISION 2026-11-18: 1, 2, 3 (Figma still says 2) | `components.md` Wallet screen |
| Nav "Runs" label | Manrope Medium 12 on all four screens | the other four labels are Regular 12 | kept | `.nav-pill--medium` |
| Paint style "White" | name suggests #FFFFFF | value is #DCE1E9 | value kept, name kept | `--color-white`, `--color-text-primary` |
| Typos | "oposite" in two style names; "Need You"; "Show Confidential Details"; missing "(" in "12.86% of the client)"; "Company  LTD" (two spaces); "(+56)" vs "(+11 )" spacing | — | kept verbatim in copy and token names | tokens, `components.md` |
| Logo path | one Pipeline logo copy differs from the other three by sub-0.0001 path-coordinate rounding | — | the Pipeline copy is shipped | `assets/logo.svg` |
| Hug-width differences | design widths (e.g. CTA 134, Select 110, header nav 643) | browser widths differ ≤ 1.5 px (≤ 2.4 px for tree rows) because of font metrics | recorded, no magic numbers | — |
| Select / field text colour | component default Grey 300 | all instances override to White; typed-text colour of Search/Input not drawn | both documented; typed text = placeholder colour | `.select__label--value` |
| Pill label size | Figma: all pills Regular 8 / 15 high | "Single Source" Regular 10 / 18 high | OWNER OVERRIDE 2026-11-16: every pill and tag is now 10 / 18 high (Figma still 8 / 15: update it) | `.pill` |
| Tabs 24 padding | design padding 8 top/bottom | does not fit 24 high | label centred, height 24 | `.tabs--sm` |
| Toggle naming | variant "Default" is the ON state | "off" is OFF | ON = `.is-on` | `.toggle` |
| Overview paragraph | `78:2434` is one text node with hard line breaks | — | reproduced with `<br>` (7 lines, the 5th wraps by itself = 8 line boxes, 128 high) | `components.md` Notice |
| Unused definitions | Outline Button, Tabs 32, toggle, hover variants exist in the file | not used on any final screen | built (owner default 6) | `components.css` |

## How to build UI with this system
1. Find the component in `components.md`; copy its markup and class names exactly (pick the variant snippet that matches the request).
2. Load `tokens.css` then `components.css` (preceded by `fonts.css`, the bundled Manrope 400/500 and Jura 300/500/600).
3. Layout: use the documented layout patterns first (screen frame, header, panels, tables, stepper, detail cards); for anything custom use only `var(--…)` tokens.
4. Icons: only files from `assets/`. Never draw SVG paths.
5. Use the exact copy the user gives. If something is missing from the system: check the Extended table (42 approved items); otherwise derive it only from existing tokens, say so, and mark it `EXTENDED` (CSS comment `EXTENDED — not in design: <derivation>` + a row in the Extended table of `components.md`).

## Extended (not in the design)
42 approved extensions (rows 1-14 approved 2026-11-16, rows 15-28 on 2026-11-17: expandable field rows with owner-drawn arrow icons, clickable pills, source chips, neutral pill, right drawer, radio, long ownership tree, text actions, revealed personal data, dynamic ring/donut, clamped text, 12 px notice paragraph, figure tables, score meter, documents-to-request list, risk-factor checklist, tally list, activity timeline, chart card, horizontal bars, SVG charts, checkbox, date picker, avatar chip, sticky header, interactive Pipeline dot grid (row 41: replaces the background picture), softer run-card hover (row 42);  all marked `EXTENDED — not in design` in `components.css` PART 3; tokens `--…-ext-…` / group `extended`): (1) field focus = gradient border (click, typing, Select open); (2) focus ring on buttons / tabs / nav pill / toggle = 1 px gradient ring 3 px outside; (3) typed value White; (4) inactive tab hover White; (5) button pressed = hover; (6) disabled for toggle / nav pill / rows = opacity 0.5; (7) field error = Red border + Red helper; (8) textarea; (9) Select open list (as wide as the trigger); (10) interactive row hover Grey 400; (11) tooltip (Grey 400, no border, Grey 100 text); (12) toast (top-right, four colours); (13, row 14) scrollbar `.scroll` (thin 6px, thumb Grey 300 at 50% opacity). Markup in the Extended table of `components.md`.
Still NOT drawn and not provided: checkbox, avatar, calendar/date/time pickers, pagination/sort arrows, breadcrumbs, empty states, loading spinner/skeleton, icon-only button, motion, responsive breakpoints. If one is needed: derive only from existing tokens (same-family recipe, then sibling, then a generic rule), label it `EXTENDED`, and ask the owner when no existing token fits.

## What NOT to do
- No colours, radii, fonts, weights or sizes outside the tokens; no raw hex in component rules.
- No generic UI-kit components (no Bootstrap/Material look-alikes) and no invented states presented as designed: focus, error, pressed and the disabled toggle/nav pill/rows are NOT drawn (they are the labelled EXTENDED items); hover/disabled of buttons, tabs and fields and the Modal ARE drawn.
- Dynamic ring/donut arcs are an approved EXTENDED row (25); the Pipeline background is the approved interactive dot grid (extended row 41); do not add other background art or animation and call it design.
- Do not redraw or re-colour icons; do not add icons the design does not have; do not apply opacity twice on the building / user-round icons (0.5 is inside the file).
- Do not "fix" the design inconsistencies above (typos, "1, 2, 2", Medium "Runs", two gradient directions); keep the copy the user gives you.
- Do not use bold, uppercase, letter-spacing, or pure white (#FFFFFF) / pure black text.
- Do not nest a hover gradient label without `.btn__label` on outline buttons (the gradient text will not render).
- The design is desktop-only at 1920 wide; do not claim responsive behaviour.
