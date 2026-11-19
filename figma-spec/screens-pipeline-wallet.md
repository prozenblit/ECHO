# echo — Screens group-a: Pipeline + Wallet Check (harvested from design file `<figma-file-key>`)

Scope: page "final " (`78:1750`, trailing space) › "Pipeline" (`78:2486`, 1920x1080) and "Wallet Check" (`78:2600`, 1920x1080). Harvested 2026-11-16 by `figma-harvester` (screens:group-a), read-only via the Plugin API.
Owner decisions applied (from `_intake.md`): screens from `final` (drafts copies `22:2621`, `73:1531` NOT re-walked here; foundations found 0 differences, and I saw nothing that contradicts that); components/variants are defined on `drafts` page (`10:170`, `73:1680`, `73:1679`, `18:248`) and only their instances are described here; `old echo` / `styling examples` skipped.

Legend: `id` = Figma node id. `(visual estimate)` = not from node data. Counts = visible nodes incl. nodes inside instances. `x,y` parent-relative (Plugin API `x`/`y`; for GROUP children these are relative to the nearest frame ancestor). "T" = text node. Style names are paint-style names (verbatim) read via `fillStyleId/strokeStyleId`. `AL` = auto-layout: dir, gap, padding T/R/B/L, main-axis align / cross-axis align. `sz` = layoutSizing horizontal/vertical (FIXED/HUG/FILL). Colours resolved from styles: White = #DCE1E9, Black 900 = #08090A, Grey 500 = #111213, Grey 400 = #1C1E1F, Grey 300 = #62666D, Grey 200 = #8A8F98, Grey 100 = #A6ACB6, Blue = #59BCFA, Red = #F35352, Orange = #F3AB52, Purple = #9081E4, Green = #7BE697 (full hex tables: `foundations.md` 1.1).

Dump method: custom compact variant of `figma-dump-subtree.js` (same reads, adds parent-relative x/y, constraints, absolute-positioning, fill/stroke style names, mixed-text segments; one line per node) run on `78:2486` and `78:2600` with depth 9 = complete subtrees, 0 hidden nodes (HIDDEN flag never printed). Visible node counts: Pipeline 119, Wallet 74 (match foundations).

---

## 0. Scope and provenance
| Item | Value |
|---|---|
| Canonical node(s) | `78:2486` Pipeline FRAME 1920x1080 @page(0,0); `78:2600` Wallet Check FRAME 1920x1080 @page(6000,0). Both: fill Black 900 #08090A (style), clipsContent true, layoutMode NONE (children absolutely positioned), no stroke, no radius, no effects. Wallet root constraints MIN/MIN. |
| Alternates seen | Drafts copies `22:2621` (Pipeline), `73:1531` (Wallet): per foundations 0.0 node-for-node differences; not re-diffed. Final wins (owner). |
| Hidden nodes in scope | 0 in both frames (dump returns every node, none hidden). |
| Extraction scripts used | compact variant of `figma-dump-subtree.js` PAGE_ID `78:1750`, TARGETS `['78:2486']` / `['78:2600']`, DEPTH 9; plus small ad-hoc reads (absoluteBoundingBox/absoluteRenderBounds of `78:2487`, styled text segments of `78:2646`, full text strings); `node.screenshot()` of each frame for orientation (visual only). |
| Not covered by this file | Group-b screens (`78:1751`, `78:2225`); component-internal structure (components harvester: Select `10:170`, Search `73:1680`, Input `73:1679`, CTA Button `18:248`); SVG export (assets harvester; see `design-system/assets/MANIFEST.md`: logo.svg, select-chevron-down.svg, search.svg, lucide-circle-exclamation-point.svg, progress-ring-72-short.svg / progress-ring-72-long.svg). |

---

## 1. Pipeline `78:2486` (1920x1080)

### 1.1 Frame and top-level children (z-order bottom -> top = child index 0 -> 2)
| z | Id | Name | Type | x,y | w x h | Fill / stroke / radius | Layout | Notes |
|---|---|---|---|---|---|---|---|---|
| root | `78:2486` | Pipeline | FRAME | page 0,0 | 1920x1080 | fill Black 900 #08090A; clip | NONE | |
| 0 (bottom) | `78:2487` | unsplash:jZRGh3IuVb8 | RECTANGLE | 1991,2165 | 2165x2706 | IMAGE fill, scaleMode FILL, paint opacity 0.2, image filters all 0 (exposure/contrast/saturation/temperature/tint/highlights/shadows = 0); node opacity 1; rotation 90 (relativeTransform `[[-4.37e-8,-1,1991],[-1,4.37e-8,2165]]`); no stroke/effect | none | constraints MIN/MIN. See 1.2: the photo IS visible. |
| 1 | `78:2488` | Frame 8 (header) | FRAME | 0,0 | 1920x66 | no fill; stroke Grey 500 #111213 (style "Grey 500") 1px INSIDE, bottom only (T0/R0/B1/L0) | H g108 pad 16/40/16/40, main SPACE_BETWEEN, cross CENTER; sz FIXED/HUG | constraints MIN/MIN; height 66 = 16+33+16+1 (stroke in layout) |
| 2 (top) | `78:2511` | Frame 85 (content column) | FRAME | 639,106 | 642x718 | no fill/stroke | V g24 pad 0, main MIN, cross MIN; sz HUG/HUG | constraints CENTER/MIN. 639 = (1920-642)/2; 106 = 66 + 40; bottom of content y=824, leaving 256 empty below |

Gutters (arithmetic): left margin 639, right margin 1920-639-642 = 639; header-to-content gap 106-66 = 40.

### 1.2 Background photo `78:2487` (correction to foundations 6.2)
| Item | Value | Source |
|---|---|---|
| Rotated bounding box (absoluteBoundingBox) | x -715 .. 1991 (w 2706), y 0 .. 2165 (h 2165) | `78:2487` read |
| Visible part (absoluteRenderBounds, clipped by frame) | 0,0,1920x1080 = whole frame | `78:2487` read |
| Conclusion | The photo is NOT outside the canvas: foundations stated its box lay at y 2165..4330 (wrong; the rotated box spans y 0..2165). It is the bottom-most child and covers the whole 1920x1080 frame, painted at 0.2 opacity under header and content. A screenshot shows a dark dotted/dot-matrix arc ("planet horizon" curve) rising from the bottom, brightest around x 480-1480 (screenshot, visual estimate). | node bounds + `78:2486` screenshot |
| Rebuild consequence | Needs a background image asset (cropped as FILL, rotated 90deg: image displayed rotated; box 2706 wide x 2165 high after rotation) with opacity 0.2. Image bytes not exported by this harvester (owner said not unless asked). | |
Wallet Check has no photo (its children are only header + content).

### 1.3 Header `78:2488` (identical to Wallet `78:2601`; see 3.1 for shared-shell comparison)
| Node | Id | x,y | w x h | Props |
|---|---|---|---|---|
| Logo box "Frame 7" | `78:2489` | 40,16.5 | 162x32 | V g10 pad 0, main CENTER cross MIN; FIXED/FIXED |
| Group 1 | `78:2490` | 0,6 | 85x20 | GROUP; asset logo.svg |
| Union (wordmark boolean) | `78:2491` | 15,6 | 70x20 | BOOLEAN_OPERATION, fill Gradient main oposite (#53B2ED@0 -> #7BE697@1); contains 4 vectors |
| Vector | `78:2492` | 68.46,6 | 16.54x20 | fill #4DFFCD (raw) |
| Vector | `78:2493` | 49.37,6 | 16.54x20 | fill #4DFFCD (raw) |
| Vector | `78:2494` | 31.55,6 | 15.27x20 | fill #4DFFCD (raw) |
| Vector | `78:2495` | 15,6 | 14x20 | fill #4DFFCD (raw) |
| Line 1 | `78:2496` | 10,6 | 20x0, rot -90 | stroke Blue 75% (#59BCFA@0.75) w1.5 CENTER |
| Line 2 | `78:2497` | 5,6 | 20x0, rot -90 | stroke Blue 50% w1.5 CENTER |
| Line 3 | `78:2498` | 0,6 | 20x0, rot -90 | stroke Blue 25% w1.5 CENTER |
| Nav "Frame 1" | `78:2499` | 645.5,16 | 643x33 | H g0 pad 0, main MIN cross CENTER; HUG/HUG. 645.5 = 40+162+(1840-162-643-148)/2 = 40+162+443.5 (space-between free space) |
| Nav pill ACTIVE "Frame 3" (Pipeline) | `78:2500` | 0,0 | 109x33 | stroke Gradient main oposite (#53B2ED -> #7BE697) 0.5 INSIDE; radius 8; AL H g0 pad 8/32/8/32 CENTER/CENTER; HUG/HUG; no fill |
| T "Pipeline" | `78:2501` | 32.5,8.5 | 44x16 | Manrope Regular 12, lh auto, center, fill White |
| Nav pill "Frame 2" | `78:2502` | 109,0.5 | 93x32 | radius 24; same AL; no fill/stroke |
| T "Runs" | `78:2503` | 32,8 | 29x16 | Manrope **Medium** 12 center White (others Regular; inconsistency already noted in foundations) |
| Nav pill "Frame 4" | `78:2504` | 202,0.5 | 135x32 | radius 24 |
| T "Wallet check" | `78:2505` | 32,8 | 71x16 | Manrope Regular 12 White |
| Nav pill "Frame 5" | `78:2506` | 337,0.5 | 144x32 | radius 24 |
| T "System health" | `78:2507` | 32,8 | 80x16 | Manrope Regular 12 White |
| Nav pill "Frame 6" | `78:2508` | 481,0.5 | 162x32 | radius 24 |
| T "Admin Dashboard" | `78:2509` | 32,8 | 98x16 | Manrope Regular 12 White |
| Select instance | `78:2510` | 1732,16.5 | 148x32 | see 1.5 |
| Select T "Local Developer" | `I78:2510;9:137` | 13,9 | 74x14 | Manrope Regular 10 center, fill White #DCE1E9 (style "White") |
| Select icon wrapper "Frame 11" | `I78:2510;18:308` | 119,8 | 16x16 | contains 2 vectors |
| arrow-down | `I78:2510;18:310` | 3,6 | 12x6 | stroke Gradient main (#7BE697 -> #53B2ED) w1 CENTER, radius 0.5, constraints CENTER/CENTER |
| arrow-down (small) | `I78:2510;18:311` | 6,6 | 6x3 | same stroke, node opacity 0.5 |
Right gutter: 1732+148 = 1880 = 1920-40 (padding right 40). Nav inactive pills sit at y 0.5 (32 high) vs active y 0 (33 high, 0.5px stroke counted in layout); pill x: 0/109/202/337/481, widths 109/93/135/144/162 = 643.

### 1.4 Content column `78:2511` (642x718, V g24)
| Row | Id | x,y in `78:2511` | w x h | Layout |
|---|---|---|---|---|
| Greeting row "Frame 79" | `78:2512` | 0,0 | 642x32 | H g211 pad 0, main SPACE_BETWEEN cross CENTER; sz FIXED/HUG |
| KPI row "Frame 84" | `78:2515` | 0,56 (32+24) | 642x106 | H g24, main MIN cross CENTER; FIXED/HUG |
| "Frame 58" (Needs-you panel) | `78:2528` | 0,186 (56+106+24) | 642x312 | V g16 pad 16 (all), stroke Grey 400 #1C1E1F 1px INSIDE (strokes included in layout), radius 16, no fill; FIXED/HUG |
| "Frame 85" (Clients panel) | `78:2575` | 0,522 (186+312+24) | 642x196 | V g16 pad 16, fill Grey 500 #111213, stroke Grey 400 1 INSIDE, radius 16; FIXED/HUG. 522+196 = 718 = content height |

#### 1.4.1 Greeting row
| Node | Id | x,y | w x h | Props |
|---|---|---|---|---|
| T heading | `78:2513` | 0,5 | 508x22 | Manrope Medium 16, auto lh, left, fill White; sz FILL/HUG; text `Good afternoon, Alex. One run needs you.` (verbatim, includes name "Alex") |
| CTA Button instance | `78:2514` | 508,0 | 134x32 | main `CTA Button / Property 1=Default` (`18:142`, set `18:248`); fill White #DCE1E9; radius 8; AL H g10 pad 8/24/8/24 CENTER/CENTER; HUG/HUG |
| CTA label T | `I78:2514;10:169` | 24,8 | 86x16 | override text `Run KYC Check` (component default "Button"); Manrope Medium 12 center, fill Black 900 |

#### 1.4.2 KPI cards (4x, "Frame 80..83"; 142.5x106; 4*142.5 + 3*24 = 642)
Each: fill Black 900 (style), stroke Grey 400 1 INSIDE, radius 16, AL V g16 pad 24/24/24/24 main MIN cross MIN, sz FILL/HUG. Children: numeral T (Jura Medium 38, auto lh, left) at 25,25 (92.5x24; the last card hugs: 25x24), label T (Manrope Regular 12, Grey 300) at 25,65 (92.5x16).
| Card | Id | x,y | Numeral T id / text / colour | Label T id / text |
|---|---|---|---|---|
| Frame 80 | `78:2516` | 0,0 | `78:2517` "2" Blue (#59BCFA) | `78:2518` "Active" |
| Frame 81 | `78:2519` | 166.5,0 | `78:2520` "1" Red (#F35352) | `78:2521` "Need You" |
| Frame 82 | `78:2522` | 333,0 | `78:2523` "0" Purple (#9081E4) | `78:2524` "ECHO Working" |
| Frame 83 | `78:2525` | 499.5,0 | `78:2526` "0" Green (#7BE697), sz HUG/HUG | `78:2527` "Awaiting 4-eyes" (sz HUG/HUG, 89x16) |
Card 4 text nodes are HUG/HUG while cards 1-3 are FILL/HUG (inconsistent sizing, same look). Card x: 0 / 166.5 / 333 / 499.5 (step 166.5 = 142.5 + 24).

#### 1.4.3 Panel "Needs you / With the team" `78:2528` (642x312)
Inner content frames at x=17 (1px stroke + 16 padding), width 642-34 = 608. Heights: 17 + 131 + 16 + 131 + 17 = 312.
| Section | Id | x,y | w x h | Layout |
|---|---|---|---|---|
| "Frame 86" section 1 | `78:2529` | 17,17 | 608x131 | V g8 pad 0, sz FILL/HUG |
| T caption | `78:2530` | 0,0 | 608x16 | "Needs you (1)", Manrope Medium 12, Grey 300, FILL/HUG |
| Run card "Frame 56" | `78:2531` | 0,24 | 608x107 | fill Grey 500 #111213, stroke Grey 400 1 INSIDE, radius 8; AL H g36 pad 12/16/12/16 main SPACE_BETWEEN cross CENTER; FILL/HUG. Height 107 = 1+12+81+12+1 |
| "Frame 87" section 2 | `78:2552` | 17,164 (17+131+16) | 608x131 | V g8, FILL/HUG |
| T caption | `78:2553` | 0,0 | 608x16 | "With the team (1)", same style |
| Run card "Frame 56" | `78:2554` | 0,24 | 608x107 | same as `78:2531` |

Run card inner (card 1 = ids from `78:2531`; card 2 = from `78:2554`), the two cards have identical structure:
| Node | Card 1 id | Card 2 id | x,y | w x h | Props |
|---|---|---|---|---|---|
| Left column "Frame 89" | `78:2532` | `78:2555` | 17,13 | 493x81 | V g12 pad 0, main CENTER cross MIN; FILL/HUG. 17+493 = 510 = right column x (effective gap 0: FILL child consumes slack, SPACE_BETWEEN ignores itemSpacing 36) |
| T tag | `78:2533` | `78:2556` | 0,0 | 53x14 | "Main check", Manrope Regular 10, Purple (#9081E4), HUG/HUG |
| "Frame 55" (title+issue stack) | `78:2534` | `78:2557` | 0,26 | 493x55 | V g4, FILL/HUG |
| T company | `78:2535` | `78:2558` | 0,0 | 493x19 | "ALDER PEAK PTY LTD" / "CEDAR LOOP, INC.", Manrope Medium 14, White, FILL/HUG |
| Issue row "Frame 92" | `78:2536` | `78:2559` | 0,23 | 493x14 | H g4 pad 0, main MIN cross CENTER; FILL/HUG |
| Icon frame lucide/circle-exclamation-point | `78:2537` | `78:2560` | 0,1 | 12x12 | FRAME, fills: empty array (transparent), clipsContent true, FIXED/FIXED |
| Icon vector | `78:2538` | `78:2561` | 1,1 | 10x10 | stroke Orange (#F3AB52) w1 CENTER, constraints SCALE/SCALE |
| T issue lead | `78:2539` | `78:2562` | 16,0 | 131x14 / 262x14 | Manrope Medium 10, Grey 100 (#A6ACB6), HUG/HUG; text `Resolve 6 conflicting values ` / `Identify 2 documents ECHO couldn't classify confidently ` (both with trailing space, verbatim) |
| T "more" count | `78:2540` | `78:2563` | 151,0 / 282,0 | 25x14 | `(+11 )` / `(+10 )` (space before ")" verbatim), Manrope Regular 10, Grey 300 |
| Counts row "Frame 90" | `78:2541` | `78:2564` | 0,41 | 493x14 | H g8 pad 0, main MIN cross MIN; FILL/HUG |
| T count 1 | `78:2542` "6 conflicts" (49x14) | `78:2565` "19 conflicts" (53x14) | 0,0 | | Manrope Regular 10, Red |
| T count 2 | `78:2543` "1 ownership gap" (74x14) | `78:2566` "1 ownership gap" (74x14) | 57,0 / 61,0 | | Red |
| T count 3 | `78:2544` "3 missing docs" (68x14) | `78:2567` "4 missing docs" (69x14) | 139,0 / 143,0 | | Orange |
| T count 4 | `78:2545` "5 out of date" (59x14) | `78:2568` "1 out of date" (57x14) | 215,0 / 220,0 | | Orange |
| T count 5 (more) | `78:2546` "(+56)" (27x14) | `78:2569` "(+31 )" (26x14) | 282,0 / 285,0 | | Grey 300 |
| Ring wrapper "Frame 91" | `78:2547` | `78:2570` | 510,13 | 81x81 | no fill; sz FIXED/FILL; frame contains label T and Group 2 |
| T ring % | `78:2548` | `78:2571` | 26,34 / 23,34 | 33x13 / 39x13 | `41%` / `62%`: Jura MIXED: digits Medium 20, "%" Light 20; fill Blue; center; constraints CENTER/CENTER; FIXED/FIXED (box is cap-height 13 for 20px font; do not use as box) |
| Group 2 (ring) | `78:2549` | `78:2572` | 5,5 | 72x72 | asset progress-ring-72-short.svg / progress-ring-72-long.svg |
| Ellipse 1 (track) | `78:2550` | `78:2573` | 5,5 | 72x72 | ELLIPSE, stroke Black 900 #08090A w4 INSIDE (style "Black 900") |
| Ellipse 2 (arc, VECTOR) | `78:2551` | `78:2574` | 75,7 | 33.84x64.05 / 57x68 | rot -180; RAW stroke gradient #53B2ED@0 -> #7BE697@1, w4 INSIDE; DROP_SHADOW #000000@0.48 offset (-2,2) blur 6 spread 0. Arc length encodes progress (41% short, 62% long) |

#### 1.4.4 Panel "Clients loaded in (2)" `78:2575` (642x196)
Layout: pad 16 + stroke 1 -> children at x=17, width 608. Heights: 17 + 16 (title) + 16 + 57 + 16 + 57 + 17 = 196 (title at y17, row 1 at y49, row 2 at y122).
| Node | Id | x,y | w x h | Props |
|---|---|---|---|---|
| T title | `78:2576` | 17,17 | 608x16 | "Clients loaded in (2)", Manrope Medium 12, Grey 300, FILL/HUG |
| Client row 1 "Frame 57" | `78:2577` | 17,49 | 608x57 | fill Black 900 #08090A, no stroke, radius 8; AL H g36 pad 12/16/12/16 main SPACE_BETWEEN cross MIN; FILL/HUG. 12+33+12 = 57 |
| Left stack "Frame 95" | `78:2578` | 16,12 | 288x32 | V g2 pad 0, main CENTER cross MIN; FILL/HUG |
| "Frame 55" | `78:2579` | 0,0 | 288x16 | V g2, FILL/HUG |
| T client name | `78:2580` | 0,0 | 288x16 | "fx01-client-a", Manrope Medium 12, White |
| Status row "Frame 96" | `78:2581` | 0,18 | 91x14 | H g8 pad 0, main MIN cross CENTER; HUG/HUG |
| Dots "Frame 31" | `78:2582` | 0,4 | 16x6 | H g4, main MAX cross CENTER; HUG/HUG |
| Ellipse 6 | `78:2583` | 0,0 | 6x6 | fill Red (#F35352) |
| Ellipse 7 | `78:2584` | 10,0 | 6x6 | fill Orange (#F3AB52) |
| T status | `78:2585` | 24,0 | 67x14 | "Needs analyst", Manrope Medium 10, Grey 200 (#8A8F98) |
| Right stack "Frame 93" | `78:2586` | 304,12 | 288x33 | V g2 pad 0, main MIN cross MAX (right aligned); FILL/FILL. 16+288+0+288 = 592 = 608-16 |
| T action | `78:2587` | 229,0 | 59x14 | `KYC Check > ` (trailing space, ">" is literal), Manrope Medium 10, Blue |
| T percent | `78:2588` | 259,16 | 29x17 | "59%", Jura Medium 14, center, Blue, HUG/HUG |
| Client row 2 "Frame 58" | `78:2589` | 17,122 | 608x57 | same as row 1 |
| "Frame 95" | `78:2590` | 16,12 | 288x32 | as above |
| "Frame 55" | `78:2591` | 0,0 | 288x16 | |
| T client name | `78:2592` | 0,0 | 288x16 | "fx02-client-b" |
| "Frame 96" | `78:2593` | 0,18 | 81x14 | |
| "Frame 31" | `78:2594` | 0,4 | 6x6 | H g4 main MAX; contains ONE dot |
| Ellipse 7 | `78:2595` | 0,0 | 6x6 | fill Orange |
| T status | `78:2596` | 14,0 | 67x14 | "Needs analyst" |
| "Frame 93" | `78:2597` | 304,12 | 288x33 | as row 1 |
| T action | `78:2598` | 229,0 | 59x14 | `KYC Check > ` |
| T percent | `78:2599` | 263,16 | 25x17 | "51%" |

### 1.5 Component instances used on Pipeline
| Instance id | Main component | Variant | Text override | Size | Differences from component default |
|---|---|---|---|---|---|
| `78:2510` Select | `Select` `10:170` (110x32 component; instance 162x32 after the 2026-11-16 font change) | none | `I78:2510;9:137` = "Local Developer" | 148x32, AL H g32 pad 8/12/8/12, HUG/FIXED, fill Grey 500, stroke Grey 400 1 INSIDE, radius 8 | label colour White #DCE1E9 in this instance; component default label colour is #62666D (foundations 1.9) -> override; instance width 148 vs component 104 (text longer) |
| `78:2514` CTA Button | `CTA Button / Property 1=Default` `18:142` (set `18:248`) | `Property 1=Default` | label "Run KYC Check" | 134x32 HUG/HUG | width = 24+86+24 |

### 1.6 Visible copy (verbatim)
Header nav: "Pipeline", "Runs", "Wallet check", "System health", "Admin Dashboard"; Select: "Local Developer". Greeting: "Good afternoon, Alex. One run needs you." CTA: "Run KYC Check". KPI labels: "Active", "Need You", "ECHO Working", "Awaiting 4-eyes" (sic, "4-eyes"). Section captions: "Needs you (1)", "With the team (1)", "Clients loaded in (2)". Tags: "Main check" (x2). Companies: "ALDER PEAK PTY LTD", "CEDAR LOOP, INC.". Issue leads: "Resolve 6 conflicting values " and "Identify 2 documents ECHO couldn't classify confidently " (trailing spaces). Counts: "(+11 )", "(+10 )", "(+31 )" (space before paren), "(+56)" (no space: inconsistent), "6 conflicts", "19 conflicts", "1 ownership gap", "3 missing docs", "4 missing docs", "5 out of date", "1 out of date". Ring: "41%", "62%". Clients: "fx01-client-a", "fx02-client-b", "Needs analyst" (x2), "KYC Check > " (x2), "59%", "51%".
Flags: "(+56)" vs "(+11 )"/"(+10 )"/"(+31 )" spacing inconsistent; "Need You" capital Y; layer name "Frame 85" is used 3 times (`78:2511`, `78:2575`) and "Frame 58" for two different roles (`78:2528`, `78:2589`); card 1/2 issue count text values differ in length so "1 ownership gap" x offsets differ (57 vs 61) only due to hug widths.

### 1.7 ASCII reconstruction (Pipeline, 1920x1080; sizes in px)
```
+--------------------------------------------------------------------------------+  y0
| photo 78:2487 under everything: dot-arc rising from bottom, opacity 0.2        |
| HEADER 78:2488 1920x66, bottom border 1 Grey500, pad 16/40/16/40               |  y0-66
| [logo 85x20 @40] [ (Pipeline*)(Runs)(Wallet check)(System health)(Admin..)] [Local Developer v] |
|   *active 109x33 gradient 0.5 stroke r8; others r24      nav 643w @645.5   Select 148x32 @1732  |
|                                                                                |  gap 40
|            CONTENT 78:2511  642x718 @ (639,106)   (V g24)                      |
|            Good afternoon, Alex. One run needs you.   [Run KYC Check] 134x32 | 32
|            [ 2 Active ][ 1 Need You ][ 0 ECHO Working ][ 0 Awaiting 4-eyes ]  | y56..162, 4x142.5x106 g24
|            +-- panel 78:2528 642x312 r16 stroke Grey400, pad16 ------------+  | y186
|            | Needs you (1)                                                 |
|            | [card 608x107 r8 Grey500: Main check / ALDER PEAK PTY LTD /      |
|            |   (!)Resolve 6 conflicting values (+11 ) / 6 conflicts ...  (41%)ring 72 ] |
|            | With the team (1)                                             |
|            | [card 608x107: CEDAR LOOP, INC. ... (62%) ]                          |
|            +---------------------------------------------------------------+
|            +-- panel 78:2575 642x196 r16 Grey500 fill, stroke Grey400 ----+  | y522
|            | Clients loaded in (2)                                         |
|            | [row 608x57 r8 Black900: fx01-client-a .. KYC Check > 59%]    |
|            | [row 608x57 r8 Black900: fx02-client-b .. KYC Check > 51%]    |
|            +---------------------------------------------------------------+  y718 (abs 824)
|                                (empty 256px below)                             |
+--------------------------------------------------------------------------------+ 1080
```

---

## 2. Wallet Check `78:2600` (1920x1080)

### 2.1 Frame and top-level children (z bottom -> top)
| z | Id | Name | Type | x,y | w x h | Fill / stroke / radius | Layout | Notes |
|---|---|---|---|---|---|---|---|---|
| root | `78:2600` | Wallet Check | FRAME | page 6000,0 | 1920x1080 | fill Black 900; clip | NONE | constraints MIN/MIN |
| 0 | `78:2601` | Frame 8 (header) | FRAME | 0,0 | 1920x66 | stroke Grey 500 1px INSIDE bottom only | H g108 pad 16/40/16/40 SPACE_BETWEEN/CENTER; FIXED/HUG | constraints MIN/MIN |
| 1 (top) | `78:2624` | Frame 107 (content) | FRAME | 468,106 | 984x403 | none | H g38 pad 0, MIN/MIN; HUG/HUG | constraints CENTER/MIN. 468 = (1920-984)/2; 106 = 66+40. Bottom y=509; 571px empty below |
No background photo; nothing else.

### 2.2 Header `78:2601` (same as Pipeline header; differences marked)
| Node | Id | x,y | w x h | Props |
|---|---|---|---|---|
| Logo box "Frame 7" | `78:2602` | 40,16.5 | 162x32 | as `78:2489` |
| Group 1 / Union / 4 vectors | `78:2603` / `78:2604` / `78:2605`..`78:2608` | 0,6 / 15,6 / (68.46,6 16.54x20; 49.37,6 16.54x20; 31.55,6 15.27x20; 15,6 14x20) | 85x20 / 70x20 | same fills as Pipeline (Union Gradient main oposite; vectors #4DFFCD raw) |
| Vector (wordmark glyph, child idx 1 of Union `78:2604`) | `78:2606` | 49.37,6 (49.365, 6.0009) | 16.54x20 (16.544 x 19.999) | VECTOR, visible, opacity 1, rot 0, fill SOLID #4DFFCD (r0.302 g1 b0.804, raw, no style), no stroke |
| Vector (wordmark glyph, child idx 2 of Union `78:2604`) | `78:2607` | 31.55,6 (31.547, 6.0009) | 15.27x20 (15.272 x 19.999) | VECTOR, visible, opacity 1, rot 0, fill SOLID #4DFFCD (raw, no style), no stroke |
| Lines 1-3 | `78:2609`, `78:2610`, `78:2611` | 10,6 / 5,6 / 0,6 | 20x0 rot -90 | Blue 75% / 50% / 25% w1.5 CENTER |
| Nav "Frame 1" | `78:2612` | 645.5,16 | 643x33 | H g0, HUG/HUG |
| Pill "Frame 3" | `78:2613` | 0,0.5 | 108x32 | inactive radius 24; T `78:2614` "Pipeline" @32,8 44x16 Regular 12 |
| Pill "Frame 2" | `78:2615` | 108,0.5 | 93x32 | radius 24; T `78:2616` "Runs" @32,8 29x16 Manrope **Medium** 12 |
| Pill ACTIVE "Frame 4" | `78:2617` | 201,0 | 136x33 | stroke Gradient main oposite 0.5 INSIDE, radius 8; T `78:2618` "Wallet check" @32.5,8.5 71x16 Regular 12 |
| Pill "Frame 5" | `78:2619` | 337,0.5 | 144x32 | radius 24; T `78:2620` "System health" @32,8 80x16 |
| Pill "Frame 6" | `78:2621` | 481,0.5 | 162x32 | radius 24; T `78:2622` "Admin Dashboard" @32,8 98x16 |
| Select instance | `78:2623` | 1732,16.5 | 148x32 | main `Select` `10:170`; T `I78:2623;9:137` "Local Developer" White, 13,9 74x14; icon frame `I78:2623;18:308` @119,8 16x16 with `I78:2623;18:310` (12x6 @3,6) and `I78:2623;18:311` (6x3 @6,6, opacity 0.5) |
Active pill on Wallet is 136 wide (vs Pipeline's inactive "Wallet check" pill 135): +1 from the 0.5px stroke counted in layout; Wallet "Pipeline" pill is 108 (Pipeline's active 109). x positions: 0/108/201/337/481 vs Pipeline 0/109/202/337/481.

### 2.3 Content `78:2624` (984x403, H g38)
| Region | Id | x,y | w x h | Layout |
|---|---|---|---|---|
| Left column "Frame 85" | `78:2625` | 0,0 | 658x403 | V g24 pad 0, MIN/MIN; sz FIXED/HUG |
| Right panel "Frame 58" | `78:2652` | 696,0 (658+38) | 288x403 | V g16 pad 16, stroke Grey 400 1 INSIDE, radius 16, no fill; sz FIXED/FILL (height follows row = 403) |
Arithmetic: 658 + 38 + 288 = 984.

#### 2.3.1 Left column (V g24: header 49 + 24 + card 330 = 403)
| Node | Id | x,y | w x h | Props |
|---|---|---|---|---|
| Header "Frame 79" | `78:2626` | 0,0 | 658x49 | V g8 pad 0, MIN/MIN; FILL/HUG |
| T heading | `78:2627` | 0,0 | 658x22 | "Add a client wallet", Manrope Medium 16, White, FILL/HUG, text box HEIGHT-auto |
| T sub | `78:2628` | 0,30 | 658x19 | `Link a wallet to a client in ECHO. It's screened once in Elliptic, and kept on the client for future reviews.` Manrope Medium 14, Grey 300, HUG/HUG (single line; straight apostrophe) |
| Form card "Frame 85" | `78:2629` | 0,73 | 658x330 | fill Grey 500 #111213, stroke Grey 400 1 INSIDE, radius 16; V g24 pad 16 (children at x=17; width 658-34 = 624); FILL/HUG |
Card height: 1+16 + 64 + 24 + 64 + 24 + 64 + 24 + 32 + 16+1 = 330. Child y: 17 / 105 / 193 / 281.

Field 1 "Client" (`78:2630` "Frame 102", 17,17, 624x64, V g8, FILL/HUG)
| Node | Id | x,y | w x h | Props |
|---|---|---|---|---|
| Label row "Frame 103" | `78:2631` | 0,0 | 616x24 | H g8 pad 0, main MIN cross CENTER; HUG/HUG |
| Step chip "Frame 101" | `78:2632` | 0,0 | 24x24 | fill Grey 400 #1C1E1F, radius 24, AL V pad 0 CENTER/CENTER; FIXED/FIXED |
| T numeral | `78:2633` | 9,3.5 | 6x17 | "1", Jura Medium 14, text fill = gradient Gradient main (#7BE697@0 -> #53B2ED@1), HUG/HUG |
| T label | `78:2634` | 32,0 | 584x24 | "Client", Manrope Medium 12, Grey 100, FIXED/FILL, textAutoResize NONE |
| Search instance | `78:2635` | 0,32 | 624x32 | main `Search` `73:1680` (120x32); fill Grey 500, stroke Grey 400 1 INSIDE, radius 8; AL H g8 pad 8/32/8/8 (icon at left, 32 right pad), main MIN cross CENTER; FILL/FIXED |
| Search icon wrapper | `I78:2635;73:1665` | 9,8 | 16x16 | contains Vector `I78:2635;73:1672` (12x12 @2,3 stroke Gradient main w1 CENTER, r0.5, constraints CENTER/MAX) and Ellipse 9 `I78:2635;78:1708` (11x11 @2,3 fill Blue 15% #59BCFA@0.15 style "Blue 15%") |
| Placeholder T | `I78:2635;73:1664` | 33,9 | 141x14 | `Start typing the client's name…` (U+2026 ellipsis, straight apostrophe), Manrope Regular 10 center, Grey 300 |

Field 2 "Wallet address" (`78:2636` "Frame 103" (layer name duplicated with label row), 17,105, 624x64, V g8, FILL/HUG)
| Node | Id | x,y | w x h | Props |
|---|---|---|---|---|
| Label row "Frame 103" | `78:2637` | 0,0 | 616x24 | as `78:2631` |
| Step chip "Frame 101" | `78:2638` | 0,0 | 24x24 | as `78:2632` |
| T numeral | `78:2639` | 8,3.5 | 8x17 | "2" gradient text fill |
| T label | `78:2640` | 32,0 | 584x24 | "Wallet address" Manrope Medium 12 Grey 100 |
| Input instance | `78:2641` | 0,32 | 624x32 | main `Input` `73:1679` (120x32); fill Grey 500, stroke Grey 400 1 INSIDE, radius 8, AL H g8 pad 8/12/8/12 MIN/CENTER; FILL/FIXED |
| Placeholder T | `I78:2641;73:1678` | 13,9 | 174x14 | `Paste the address, e.g. bc1q…, 0x…, T…` (ellipsis U+2026 x3), Manrope Regular 10, Grey 300 |

Field 3 "Label and note (optional)" (`78:2642` "Frame 104", 17,193, 624x64, V g8, FILL/HUG)
| Node | Id | x,y | w x h | Props |
|---|---|---|---|---|
| Label row "Frame 103" | `78:2643` | 0,0 | 616x24 | |
| Step chip "Frame 101" | `78:2644` | 0,0 | 24x24 | |
| T numeral | `78:2645` | 8,3.5 | 8x17 | **"2"** (not "3": see conflicts), gradient text fill |
| T label (MIXED fills) | `78:2646` | 32,0 | 584x24 | `Label and note (optional)`, Manrope Medium 12, FIXED/FILL, textAutoResize NONE; segment 1 "Label and note" Grey 100 (#A6ACB6), segment " " Grey 200 (#8A8F98), segment "(optional)" Grey 300 (#62666D) |
| Inputs row "Frame 105" | `78:2647` | 0,32 | 624x32 | H g16 pad 0, MIN/MIN; FILL/HUG |
| Input instance (narrow) | `78:2648` | 0,0 | 193x32 | main `Input` `73:1679`; FIXED/FIXED; T `I78:2648;73:1678` `Label, e.g. Treasury wallet` @13,9 118x14 Regular 10 Grey 300 |
| Input instance (wide) | `78:2649` | 209,0 | 415x32 | main `Input`; FILL/FIXED; T `I78:2649;73:1678` `Note for Compliance (optional)` @13,9 143x14. 193+16+415 = 624 |

Action row "Frame 106" `78:2650` (17,281, 624x32): V g10 pad 0, main SPACE_BETWEEN, cross MAX (child right-aligned), FILL/FIXED. Child: CTA Button instance `78:2651` @449,0 175x32 (449+175 = 624), main `CTA Button / Property 1=Default` `18:142`, fill White, radius 8, AL H g10 pad 8/24/8/24; label T `I78:2651;10:169` `Add Wallet and Screen` @24,8 127x16 (Manrope Medium 12 center, Black 900).

#### 2.3.2 Right panel "Recently Added" `78:2652` (288x403)
| Node | Id | x,y | w x h | Props |
|---|---|---|---|---|
| T caption | `78:2653` | 17,17 | 254x16 | "Recently Added", Manrope Medium 12, Grey 300, FILL/HUG |
| Card 1 "Frame 57" | `78:2654` | 17,49 | 254x50 | fill Grey 500, stroke Grey 400 1 INSIDE, radius 8; H g36 pad 8/16/8/16 SPACE_BETWEEN/MIN; FILL/HUG |
| "Frame 55" | `78:2655` | 17,9 | 220x32 | V g2 pad 0, FILL/HUG |
| T | `78:2656` | 0,0 | 220x16 | "Client Name 1", Manrope Medium 12, White |
| T | `78:2657` | 0,18 | 220x14 | "Wallet Address 1", Manrope Medium 10, Grey 200 |
| Card 2 "Frame 58" | `78:2658` | 17,115 | 254x50 | same as card 1 (49+50+16 = 115) |
| "Frame 55" | `78:2659` | 17,9 | 220x32 | |
| T | `78:2660` | 0,0 | 220x16 | "Client Name 2" |
| T | `78:2661` | 0,18 | 220x14 | "Wallet Address 2" |
Panel is sz FIXED/FILL so it stretches to the row height (403); cards end at y=165, leaving 238px empty inside the panel. Widths: 254 = 288 - 34.

### 2.4 Component instances used on Wallet
| Instance id | Main component | Text override | Size | Notes |
|---|---|---|---|---|
| `78:2623` Select | `Select` `10:170` | "Local Developer" (colour White) | 148x32 | same as Pipeline `78:2510` |
| `78:2635` Search | `Search` `73:1680` | placeholder "Start typing the client's name…" | 624x32 (FILL) | padding 8/32/8/8 |
| `78:2641` Input | `Input` `73:1679` | "Paste the address, e.g. bc1q…, 0x…, T…" | 624x32 (FILL) | |
| `78:2648` Input | `Input` | "Label, e.g. Treasury wallet" | 193x32 (FIXED) | |
| `78:2649` Input | `Input` | "Note for Compliance (optional)" | 415x32 (FILL) | |
| `78:2651` CTA Button | `CTA Button / Property 1=Default` `18:142` | "Add Wallet and Screen" | 175x32 | |

### 2.5 Visible copy (verbatim)
Nav and Select as Pipeline. "Add a client wallet"; "Link a wallet to a client in ECHO. It's screened once in Elliptic, and kept on the client for future reviews."; step numerals "1", "2", "2" (sic); labels "Client", "Wallet address", "Label and note (optional)"; placeholders "Start typing the client's name…", "Paste the address, e.g. bc1q…, 0x…, T…", "Label, e.g. Treasury wallet", "Note for Compliance (optional)"; button "Add Wallet and Screen"; panel "Recently Added", "Client Name 1", "Wallet Address 1", "Client Name 2", "Wallet Address 2" (placeholder copy).
Flags: step numerals read 1, 2, 2 (third likely meant 3); layer names duplicated ("Frame 103" for `78:2631`, `78:2636`, `78:2637`; "Frame 85" for `78:2625` and `78:2629`; "Frame 58" for `78:2652` and Pipeline `78:2528`).

### 2.6 ASCII reconstruction (Wallet Check, 1920x1080)
```
+--------------------------------------------------------------------------------+
| HEADER 1920x66 (same as Pipeline; active = "Wallet check" 136x33)              |
| [logo]                (Pipeline)(Runs)(Wallet check*)(System health)(Admin..)  [Local Developer v] |
|                                                                                |  gap 40
|             CONTENT 984x403 @ (468,106), H g38                                 |
|   Left col 658 (V g24)                                  Right panel 288 @x696  |
|   Add a client wallet                    16/22          +-----------------------+ r16 stroke Grey400
|   Link a wallet to a client in ECHO ...  14/19 Grey300  | Recently Added        | pad 16
|   +-- form card 658x330 r16 Grey500 -----------------+  | [Client Name 1  ] 254x50 r8
|   | (1) Client                      label row 24      |  | [Wallet Address 1]    |
|   | [ search icon  Start typing the client's name..]  |  | [Client Name 2  ] 254x50
|   |   Search 624x32 r8                                |  | [Wallet Address 2]    |
|   | (2) Wallet address                                |  |   (empty to y=403)    |
|   | [ Paste the address, e.g. bc1q..., 0x..., T... ]  |  +-----------------------+
|   | (2) Label and note (optional)                     |
|   | [Label, e.g. Treasury wallet 193][Note for Compliance (optional) 415]  g16
|   |                            [Add Wallet and Screen] 175x32 right-aligned |
|   +---------------------------------------------------+  y 403 (abs 509)       |
|                          (empty 571px below)                                   |
+--------------------------------------------------------------------------------+
```

---

## 3. Cross-screen consistency
### 3.1 Shared shell (Pipeline vs Wallet)
| Item | Pipeline | Wallet | Same? |
|---|---|---|---|
| Header size/stroke/layout | `78:2488` 1920x66, bottom 1px Grey 500, H g108 pad 16/40/16/40 | `78:2601` identical | yes |
| Logo | `78:2489` 162x32 @40,16.5; Union etc. | `78:2602` identical geometry, fills | yes |
| Nav container | `78:2499` 643x33 @645.5,16 | `78:2612` same | yes |
| Active pill | `78:2500` 109x33 stroke Gradient main oposite 0.5, r8 | `78:2617` 136x33 same stroke/radius | yes (width by text) |
| Inactive pills | radius 24, y0.5, 32h | same | yes (x differ by 1px because active pill width +1) |
| "Runs" label | Manrope Medium 12 (`78:2503`) | Medium 12 (`78:2616`) | yes (both differ from the other four Regular 12 labels) |
| Select | `78:2510` 148x32 @1732,16.5 | `78:2623` same | yes |
| Content top | 106 (66+40), x centred | 106, x centred | yes |
| Content width | 642 (1 column) | 984 (column + 288 panel) | differ by design |
| Card/panel vocabulary | panels r16 Grey 400 stroke; inner cards r8 Grey 500 fill | same (`78:2652`, `78:2654`) | yes |
| Pad inside panels | 16 + 1 stroke | same | yes |

### 3.2 Conflicts and decisions needed
| Topic | Option A | Option B | Chosen / recommendation | Needs owner? |
|---|---|---|---|---|
| Pipeline background photo | foundations 6.2: photo outside the canvas, not visible | node bounds + screenshot: photo covers the whole frame at 0.2 opacity (this file 1.2) | Option B (measured). Needs image asset if rebuild should match | Yes: include the photo asset? (not on Wallet) |
| Step numerals on Wallet | "1","2","2" (`78:2633`, `78:2639`, `78:2645`) as drawn | likely intended 1,2,3 | Reproduce as drawn, flag | Yes |
| KPI card 4 sizing | `78:2526`/`78:2527` HUG/HUG | cards 1-3 FILL/HUG | no visual difference; build as FILL | no |
| "(+56)" vs "(+11 )" spacing | `78:2546` no space | `78:2540`, `78:2563`, `78:2569` space inside parens | copy verbatim | Optional |
| Active nav stroke | Pipeline/Wallet: Gradient main oposite (#53B2ED -> #7BE697) | Runs screens (group b): Gradient main | see foundations | Yes (already open) |
| Select label colour | instance override White | component default #62666D | instance wins on these screens | components harvester to confirm |

---

## 4. Repeating patterns (cross-reference for rebuild)
| Pattern | Seen in | Values |
|---|---|---|
| Panel (outlined) | `78:2528`, `78:2652` | r16, stroke Grey 400 1 INSIDE, no fill, pad 16, V g16 |
| Panel (filled) | `78:2575`, `78:2629` | r16, fill Grey 500, stroke Grey 400 1 INSIDE, pad 16 |
| KPI card | `78:2516`, `78:2519`, `78:2522`, `78:2525` | r16, fill Black 900, stroke Grey 400, pad 24, V g16, Jura 38 + Manrope Regular 12 |
| Run card | `78:2531`, `78:2554` | r8, fill Grey 500, stroke Grey 400, H pad 12/16, 608x107, right ring 81x81 |
| Client row | `78:2577`, `78:2589` | r8, fill Black 900, no stroke, H pad 12/16, 608x57, status dots + KYC link/percent right |
| Recent card | `78:2654`, `78:2658` | r8, fill Grey 500, stroke Grey 400, H pad 8/16, 254x50, name 12 White + address 10 Grey 200 |
| Form field | `78:2630`, `78:2636`, `78:2642` | label row (24 chip + 8 + label) + control 32 high, V g8, 64 high |
| Step chip | `78:2632`, `78:2638`, `78:2644` | 24x24 circle Grey 400, Jura Medium 14 gradient numeral |
| Issue row | `78:2536`, `78:2559` | 12px warning icon (Orange) + text 10 Medium, g4 |
| Progress ring | `78:2547`, `78:2570` | 81x81 wrapper, 72x72 ring (track Black 900 w4 + gradient arc w4 + shadow), centre % Jura 20 |
No pills/tags/tabs/toggles/tables/modals appear on these two screens.

---

## 5. GAPS / NOT FOUND IN THE DESIGN
| Area | Finding | How searched | Scope searched |
|---|---|---|---|
| Hover / focus / active / pressed on screens | Not drawn: no node in either frame is a hover/focus variant; the only variant property seen is `Property 1=Default` on CTA Button instances | instance `variantProperties` for all 6 instances + node-name scan of both full dumps | `78:2486`, `78:2600` |
| Disabled | No disabled controls (Wallet "Add Wallet and Screen" button is drawn enabled with empty form) | dump of all instances/fills, visual check | both frames |
| Error / validation | No error text, red field outlines or helper messages on the Wallet form (red appears only as issue text/dots on Pipeline) | stroke/fill colour scan of `78:2629` subtree | `78:2600` |
| Empty state | Not drawn for "Recently Added" or run lists | structure + copy scan (placeholder copy "Client Name 1" etc. only) | both |
| Loading / skeleton / progress states | Only static rings; no spinner/skeleton | node names + effect scan | both |
| Toast / tooltip / modal / dropdown open state | Not drawn; Select shown closed only | scan for overlays, extra top-level children (only 2-3 children per root) | both |
| Responsive / breakpoints | Single 1920x1080 frame each; centring via constraints CENTER/MIN on content frames (`78:2511`, `78:2624`) | frame sizes, constraints | both |
| Scrim / blur | None; only effect layer is DROP_SHADOW (-2,2 blur 6 @0.48) on `78:2551` and `78:2574` | effects scan of both dumps | both |
| Text styles / variables | none (foundations 0.1); only paint styles bound | `fillStyleId`, `boundVariables` | both |
| Interactions / prototype links | Not read (reactions not queried) | not searched | NOT HARVESTED |
| Drafts copies | `22:2621`, `73:1531` not re-diffed by this harvester; relied on foundations (0 differences) | not walked | NOT HARVESTED |
| Photo bytes | Image fill of `78:2487` not exported | by owner decision | NOT HARVESTED |
| Rate limits | No limit/timeout incidents occurred | | |
