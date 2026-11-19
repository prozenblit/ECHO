# Asset manifest — Echo

Source: Figma file `<figma-file-key>`. Every SVG is the raw `exportAsync({format:'SVG_STRING'})` output written byte-for-byte; nothing redrawn, cleaned or edited. `.currentColor.svg` = same file with the colour literal replaced by `currentColor` (mono assets only; produced by `svg-postprocess.mjs`).
Hash = FNV-1a 32 of the SVG text as returned by Figma. All 14 files were re-hashed (3 of them, the status-check icons, were later replaced by CSS and deleted: 11 remain) locally after writing and all equal the Figma hash (the table values). 5 assets (logo, status-check-done, building, exclamation, status-check-pending) were also re-exported from Figma later: identical hash.
Canonical pages: `final` 78:1750 (roots 78:2486 Pipeline, 78:1751 Runs/Ownership, 78:2225 Runs/Overview, 78:2600 Wallet Check) and component masters on `drafts` 3:10845. Counts = visible instances of the asset on the 4 canonical screens (nodes inside component instances included).

## Files

"Node box" = Figma node width x height; "svg box" = exported viewBox. Where they differ the reason is in the Notes column.

| file | Figma name | node id (exported) | node box / svg box | original colour(s) | hash | currentColor copy | used where (count) | recommended CSS |
|---|---|---|---|---|---|---|---|---|
| logo.svg | Group 1 (inside Frame 7 78:2489, header Frame 8) | 78:2490 (Pipeline). Same logo: 78:1754, 78:2228, 78:2603 | 85x20 / 85x20 | #53B2ED -> #7BE697 gradient wordmark "ECHO" (4 vectors in Union 78:2491, 70x20) + three vertical lines stroke #59BCFA at opacity 0.75 / 0.5 / 0.25, width 1.5 | 63d3eddd | no (gradient) | header of every screen: Pipeline 1, Ownership 1, Overview 1, Wallet 1 = 4 | `<img src="assets/logo.svg" width="85" height="20" alt="Echo">` only |
| select-chevron-down-disabled.svg | flat Grey 300 copy of the Select chevron for the DRAWN disabled state | 101:116, 101:117, 101:118 | 16x16 | stroke #62666D (2nd path opacity 0.5) | - | no | Added 2026-11-16 |
| search-disabled.svg | Search icon, flat Grey 300 stroke, no blue ellipse, DRAWN disabled state | 101:120, 101:121 | 16x16 | stroke #62666D | - | no | Added 2026-11-16 |
| arrow-down.svg | arrow down (owner-drawn, Figma 2026-11-17) | 128:1049 | 16x16 / 16x16 | stroke #A6ACB6 (Grey 100) | - | arrow-down.currentColor.svg | row caret, open state (field rows) | mask icon 16x16 (`.icon--arrow-down`). Exception to byte-for-byte: the export's `<rect fill="#F5F5F5">` background (frame fill) was removed; the path is unchanged |
| arrow-right.svg | arrow right (owner-drawn, Figma 2026-11-17) | 128:1050 | 16x16 / 16x16 | stroke #A6ACB6 (Grey 100) | - | arrow-right.currentColor.svg | row caret, closed state (field rows) | mask icon 16x16 (`.icon--arrow-right`). Same background-rect exception as arrow-down |
| calendar.svg | lucide/calendar, gradient (Figma `183:1127`, Date Picker default/hover) | 183:1127 | 16x16 / 16x16 | gradient stroke (Gradient main) | - | no | date field icon (`.datefield__icon`) | `<img>` 16x16; added 2026-11-18 |
| calendar-grey.svg | lucide/calendar, grey (Figma `183:1148`, Date Picker Variant3) | 183:1148 | 16x16 / 16x16 | stroke Grey 300 | - | no | not used yet (the Variant3 state) | added 2026-11-18 |
| select-chevron-down.svg | Frame 11 (children `arrow-down` x2: 18:310 12x6, 18:311 6x3 opacity 0.5) | 18:308 (component master `Select` 10:170). Instances: I78:2510;18:308, I78:1774;18:308, I78:2248;18:308, I78:2623;18:308 | 16x16 / 16x16 | stroke gradient #7BE697 -> #53B2ED; second chevron opacity 0.5 | 15bfbe09 | no (gradient) | every Select: Pipeline 1, Ownership 1, Overview 1, Wallet 1 = 4 | `<img>` 16x16, or `background: url(...) center/16px no-repeat` |
| search.svg | Frame 11 (Vector 73:1672 12x12 + circle) | 73:1665 (component master `Search` 73:1680). Instance: I78:2635;73:1665 | 16x16 / 16x16 | stroke gradient #7BE697 -> #53B2ED; circle fill #59BCFA at 0.15 | 29037fed | no (gradient) | Search input: Wallet Check 1 (Ownership/Overview/Pipeline: not found, only Wallet Check instance exists in canonical screens) | `<img>` 16x16 |
| download-default.svg | Vector (variant `Property 1=Default` 18:289) | 18:287 (component master `Outline Button + icon` 18:290). Instances: I78:1807;18:287, I78:2281;18:287 | 10x12 / 11x13 (stroke 1 extends the box) | stroke #DCE1E9 (was #8A8F98 until 2026-11-17: owner changed the Outline button colour to White; only the stroke attribute changed, hash no longer matches) | 522ce64e | download-default.currentColor.svg | Outline Button + icon: Ownership 1, Overview 1 = 2 | `.icon{width:11px;height:13px;background-color:currentColor;-webkit-mask:url(assets/download-default.currentColor.svg) center/contain no-repeat;mask:...}` colour #DCE1E9 |
| download-variant2.svg | Vector (variant `Property 1=Variant2` 18:291) | 18:292 (master `Outline Button + icon` 18:290) | 10x12 / 11x13 | stroke gradient #53B2ED -> #7BE697 (note: direction reversed relative to select-chevron-down / search which run #7BE697 -> #53B2ED) | 9963424a | no (gradient) | not seen on canonical screens (master only; presumably the hover/active variant, unconfirmed) | `<img>` 11x13 |
| lucide-circle-exclamation-point.svg | lucide/circle-exclamation-point | 78:2537 (also 78:2560) | 12x12 / 12x12 | stroke #F3AB52 | 3959cf00 | lucide-circle-exclamation-point.currentColor.svg | Pipeline error/warning rows: 2 | mask icon 12x12, `color:#F3AB52` (design colour). Frame fill is SOLID #FFFFFF (frame background fill, not exported) |
| lucide-building.svg | lucide/building | 78:2001 (also 78:2011, 78:2024, 78:2037) | 16x16 / 16x16 | fill #59BCFA at fill-opacity 0.5 | a5d09f28 | lucide-building.currentColor.svg | Runs/Ownership: 4 | mask icon 16x16, `color:#59BCFA; opacity:.5` (the 0.5 is inside the SVG as fill-opacity, kept in the .currentColor copy; do not apply opacity twice) |
| lucide-circle-user-round.svg | lucide/circle-user-round | 78:2050 (also 78:2064) | 16x16 / 16x16 | stroke #59BCFA at stroke-opacity 0.5 | b6d8611f | lucide-circle-user-round.currentColor.svg | Runs/Ownership: 2 | as lucide-building |
| progress-ring-72-short.svg | Group 2 (Ellipse 1 track 72x72 + Ellipse 2 arc VECTOR 33.84x64.05, gradient stroke 4, drop shadow dx-2 dy2 blur 3 black 0.48) | 78:2549 (Pipeline) | 72x72 / 76x81 (shadow + arc stroke) | track #08090A, arc gradient #53B2ED -> #7BE697 | dc4918bd | no | Pipeline: 1 | `<img>`; DATA-DRIVEN arc length (progress); a real UI must draw the arc dynamically (SVG stroke-dasharray) rather than ship this static file |
| progress-ring-72-long.svg | Group 2 (arc VECTOR 57x68) | 78:2572 (Pipeline) | 72x72 / 76x84 | as above | 3914170c | no | Pipeline: 1 | as above |
| progress-ring-140.svg | Group 2 (Ellipse 1 140x140 + arc VECTOR 111.18x131.76, stroke 8; the ring's text "62%" / "60 out of 116" is in sibling Frame 4 78:1797, NOT in this svg) | 78:1800 (Ownership). Overview ring 78:2270 > Group 2 not separately exported (its Group 3 hash differs from Ownership's by 4 chars of text/arc; arc not compared) | 140x140 / 145x152 | track #111213, arc gradient #53B2ED -> #7BE697, drop shadow as above | 6c1723da | no | Ownership 1, Overview 1 = 2 | as above |

## Special assets

- Logo: gradient + 3 translucent lines -> `<img>` only, never mask.
- IMAGE fills: exactly one in the canonical roots: `78:2487` "unsplash:jZRGh3IuVb8", RECTANGLE 2165x2706, scaleMode FILL, visible, inside Pipeline 78:2486 (background photo). NOT exported (owner did not ask). No IMAGE fills on Runs/Ownership, Runs/Overview, Wallet Check or in the component masters.
- Gradient divider lines (decorative, not exported, not icons): `Line 4, 11, 12, 13, 14, 15` 136x0 gradient stroke 2 (e.g. 78:1838-78:1843, same in Overview); `Line 16/17/18` 129x0 / 102x0 / 74x0 solid stroke ~#1C1E1F-ish, weight 1 (78:2078-78:2080). These are bars/rules, best rebuilt as CSS borders/gradients; listed because they are VECTOR/LINE nodes.
- lucide/check 24x24 (78:1868, 78:1874) is a sub-part of the status icons, not exported on its own.

## Could not export / not available

- Individual vectors inside the logo Boolean (78:2492..78:2495) and the three logo `Line` nodes: `exportAsync` fails when called on them directly (ERR); the whole Group 1 export (78:2490) already contains them. No loss.
- Hidden nodes: no hidden icon nodes were encountered among the exported candidates (exports succeeded). Hidden state of every vector in the canonical roots was not separately audited beyond those exports.

## Not present anywhere in the design (searched)

Searched all VECTOR / BOOLEAN_OPERATION / STAR / LINE / POLYGON nodes (findAll, incl. hidden) in the 4 canonical roots and in the 10 component nodes (10:170, 73:1680, 73:1679, 18:242, 18:248, 21:384, 21:401, 18:290, 21:32, 21:55), plus every node with an IMAGE fill. Nothing else exists, therefore NOT present: close/x, plus, minus, plain arrow-right/left/up, chevron-up/right/left, standalone check (only inside status icons), calendar, filter, user avatar images, flags, illustrations, favicon/brand mark separate from the wordmark. Tabs (21:384, 21:401), toggles (21:32, 21:55), Input (73:1679), Outline/CTA Buttons (18:242, 18:248) contain no vector nodes.
Alternate draft screens (4:15408, 63:712, 22:2621, 73:1531) were NOT listed for assets (only final + drafts components, per owner decision); NOT checked for extra icons. `old echo` 0:1 and `styling examples` 2:600 skipped per owner.

## Inconsistencies in the design

1. Gradient direction differs: logo, download-variant2, progress rings and orange status run #53B2ED -> #7BE697 / #F3892D -> #ECE040 ("from-left"), while select-chevron-down, search and status-check-done run #7BE697 -> #53B2ED. The same brand gradient is drawn in both directions.
2. Status icons: 40x40 frames hold a 42x42 Union (overflow), so export is 42x42; "pending" (78:1872) has no Union (circle r=20 stroke 2 centred on 40 box, exported 42x42 with 1px overflow too). The three status frames are named "Frame 11"/"Frame 13" (unnamed); search and chevron are also both named "Frame 11" 16x16. Component-instance icon `Frame 11` is the same name for four different icons.
3. Icon set is mixed: lucide-named icons (circle-exclamation-point, building, circle-user-round, check) vs custom unnamed vectors (arrow-down, search, download). lucide icons are drawn at 12 and 16 with fill-opacity/stroke-opacity 0.5 baked in; the 12x12 exclamation icon uses a 1px stroke at 12px grid (lucide native is 24px/2px).
4. Logo: the Pipeline copy (78:2490) differs from the other three copies (78:1754, 78:2228, 78:2603) by sub-0.0001 path-coordinate rounding (28.1319 vs 28.1318 ...), file size 4409 vs 4397 bytes (three copies are identical to each other after gradient-id normalisation). The Pipeline copy was used.
5. Exported hashes of the "same" icon differ across screens only because Figma embeds node ids in gradient/clip ids (e.g. `paint0_linear_78_1846`); after normalising ids all instances compared equal (chevron x4, done x6, progress x2, building x4, user x2, exclamation x2, download x2).
6. Component name typo/odd labels kept: layer names `Union`, `Ellipse 2` (a VECTOR arc named like an ellipse), `Frame 11`, `Frame 13`, `lucide/circle-exclamation-point` (lucide's actual name is `circle-alert`).

## Palette seen on icons (raw colours read from the SVGs)

| colour | role |
|---|---|
| #59BCFA | line/tick accent: logo ticks (opacity .75/.5/.25), building, circle-user-round (0.5), search fill (0.15) |
| #53B2ED -> #7BE697 (either direction) | brand accent gradient: logo wordmark, chevron, search, download-variant2, status done, ring arc |
| #F3AB52 | warning icon (circle-exclamation-point) |
| #F3892D -> #ECE040 | in-progress status gradient |
| #8A8F98 | neutral/disabled icon stroke (download-default) |
| #1C1E1F | pending status circle stroke |
| #62666D | pending status check stroke |
| #08090A / #111213 | ring track colour (72px / 140px rings) |
| black 0.48 alpha | ring arc drop-shadow (offset -2,2 blur 3) |

Counts: 13 SVG files (8 icon/logo + 3 ring illustrations + 2 disabled-state copies; the 3 status-check icons are now CSS), 4 .currentColor copies, 1 IMAGE fill (not exported), 0 hidden/unexportable assets.


## Removed 2026-11-16
status-check-done.svg, status-check-progress.svg, status-check-pending.svg were replaced by a pure-CSS step icon (`.step__icon--done|--current|--pending` in components.css). The CSS was compared against the original SVGs at 4x zoom (identical; the current ring angles were measured from the exported vector). 11 SVG assets remain.