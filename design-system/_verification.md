# echo — verification (independent, report only, FIX=false)

Date 2026-11-16. Method: markup of all 62 html snippets in `components.md` copied verbatim to a throwaway page (deleted afterwards; `<base href="../">` only to resolve `assets/`), rendered in an own browser tab (DPR 1.5, viewport 1184) from an own `serve` on port 3457 (stopped). Values compared against the SPEC files (foundations.md, components.md, screens-*.md), not against the CSS. Google Fonts were first not loaded (hug widths off by 2-5 px), then loaded and the widths re-measured.

## Result
checked 208 computed-style / box comparisons (+ about 25 further spot measurements: table, filter item, wallet, summary/detail card, ring/donut) · passed all but the explained items below · **real mismatches: 0** · verdict: **READY** (no listed deviation needs a fix).

First pass flagged 16 rows: 3 are a harness artefact (my check compared the whole `font-family` string `Jura, system-ui…` to `Jura`; the declared first family is correct), 10 were hug widths measured with fallback fonts (resolved after loading Manrope/Jura, see table), 3 are vertical-metric deviations (below).

## Checks (property | spec (node id) | measured | ok)
| Component | Property | Spec | Measured | ok |
|---|---|---|---|---|
| CTA default | bg / label / radius / pad-x / font | #DCE1E9 / #08090A / 8 / 24 / Manrope Medium 12, ls 0 (18:142) | same | ok |
| CTA default | box | 134x32 (78:2514 "Run KYC Check") | 133.29x32 (fonts loaded) | ok (hug) |
| CTA hover | fill / label | gradient #53B2ED -> #7BE697 / label unchanged #08090A (18:249) | linear-gradient(88.23deg, #53B2ED 0%, #7BE697 100%) / #08090A | ok |
| Outline | stroke / label / pad | 1px Grey 200 #8A8F98 centre (18:227) | inset 0 0 0 1px rgb(138,143,152) / #8A8F98 / 24 | ok |
| Outline | box | 87x32 | 86.3x32 | ok (hug) |
| Outline hover | stroke ring | 3 stops #53B2ED/#4CCED4@.5/#45EABB (18:253) | ::before gradient 0/50/100% with those 3 | ok |
| Outline hover | label | gradient #53B2ED -> #7BE697 (18:254) | background-clip text gradient | ok |
| Outline + icon | pad L/R, gap | 16/20, 12 (18:289) | 16/20, 12 | ok |
| Outline + icon | box | 142x32 (78:1807) | 142.97x32 | ok (hug) |
| Outline + icon hover | ring, icon | 2 stops (18:291), icon swap | 2-stop ring, `download-variant2.svg` bg | ok |
| Select | bg, border colour, radius, pad-x, gap | #111213, #1C1E1F 1px inside, 8, 12, 32 (10:170) | same; border declared 1px (reads 0.667 at DPR 1.5) | ok |
| Select | label colours / size | value #DCE1E9, placeholder #62666D, 10 | same | ok |
| Select | box / chevron | 148x32 (78:2510) / 16x16 | 146.46x32 (-1.5, fonts) / 16x16 | ok (hug) |
| Search | box, pad, gap | 120x32, 8, 8 (73:1680) | 120x32, 8, 8 | ok |
| Search | icon x / text x | 9 / 33 | 8.67 / 32.67 (border 0.667 at DPR 1.5) | ok |
| Search/Input | placeholder colour | #62666D | #62666D (::placeholder) | ok |
| Input | box, pad-x, font, bg, border | 120x32, 12, 10, #111213, #1C1E1F (73:1679) | same | ok |
| Tabs 32 | track bg, tab radius, pad-x, font | #1C1E1F, 8, 20, Medium 12 (21:384) | same | ok |
| Tabs 32 | active fill / label / inactive label | gradient #53B2ED -> #7BE697 / #08090A / #62666D | same | ok |
| Tabs 32 | box | 158x32 | 156.6x32 | ok (hug) |
| Tabs 24 | height, font, weight, pad-x | 24, Medium 10, 16 (21:401) | 24, 10, 500, 16 | ok |
| Tabs 24 | width | 128 (126 in instance 78:1995) | 125.08 | ok (-0.9 vs instance; -2.9 vs component; hug) |
| Toggle | box, track OFF, radius | 32x16, #62666D, 24 (21:33) | same | ok |
| Toggle | knob OFF / ON | 12x12 at x2 #111213 / x18 (21:35, 21:30) | 12/12/2px/#111213 / left 18px | ok |
| Toggle ON | track | gradient green #5DE7CB -> #66D74A (21:31) | linear-gradient(88.23deg, #5DE7CB, #66D74A) | ok |
| Toggle w text | gap, weight, label colours | 6, Medium 12, OFF #8A8F98 / ON #DCE1E9 | same | ok |
| Toggle w text | box OFF | 183x16 (78:1955) | 182.91x16 | ok |
| Pill tag | bg, label opacity, colour, weight, pad | #59BCFA@0.15, .7, #59BCFA, Medium 8, 4 (78:1974) | same | ok |
| Pill warning | outline | 0.5 OUTSIDE #F3AB52 (78:2007) | box-shadow 0 0 0 0.5px #F3AB52 (outside), text #F3AB52, Regular 8 | ok |
| Pill danger / success / role | fills | #F35352@.25 / #7BE697@.25 / #9081E4@.15 | same | ok |
| Pill lg | font / height | Regular 10 / 18 (78:2108) | 10 / 18 | ok |
| Pill widths | 56 / 66 / 51 / 33 / 62 / 80 | 55.9 / 65.82 / 50.94 / 32.31 / 61.26 / 79.3 | ok (hug <= 0.8) |
| Dots | size, colours | 6x6, #F35352/#F3AB52/#7BE697 | same | ok |
| KPI | bg, border, radius, pad, gap | #08090A, #1C1E1F 1, 16, 24, 16 (78:2516) | same | ok |
| KPI | value font / colour, label | Jura Medium 38 #59BCFA, label #62666D | same | ok |
| KPI | box | 142.5x106 | 142.5x105.33 | ok (line-height normal vs auto) |
| Panel | radius, pad, gap, border | 16, 16, 16, #1C1E1F (78:2528) | same | ok |
| Panel | filled / gradient fill | #111213 / bg gradient #111213@0.1 -> #161718 (78:2575, 78:1794) | #111213 / linear-gradient(85.08deg, rgba(17,18,19,.1), #161718) | ok |
| Panel caption | colour/weight | #62666D, Medium 12 | same | ok |
| Row card | bg, radius, pad run 8/16, dark 12/16 | #111213, 8 (78:2531, 78:1783) | same | ok |
| Row card dark | bg, border | #08090A, none (78:2577) | same | ok |
| Row card active | 1px gradient ring | #7BE697 -> #53B2ED (78:1778) | ::before gradient #7BE697 -> #53B2ED | ok |
| Row card run | height | 50 | 49.33 | ok |
| Notice critical/info | fills, text, pad, gap, radius | Red 25% / Purple 15%, 12, 8, 8, Medium 10 | same | ok |
| Notice warning | stroke / fill | 0.5 INSIDE #F3AB52, none (78:1970) | border 0.5px (0.667 at DPR) #F3AB52, transparent | ok |
| Notice suffix | opacity | 0.7 | 0.7 | ok |
| Step chip | box, bg, numeral | 24x24, #1C1E1F, Jura Medium 14 gradient text #7BE697 -> #53B2ED (78:2632) | same, background-clip text | ok |
| Nav pill inactive | h, radius, pad-x, weight, colour | 32, 24, 32, Regular, #DCE1E9 (78:2502) | same | ok |
| Nav pill active | h, radius, stroke, gradient (Pipeline) | 33, 8, 0.5 INSIDE #53B2ED -> #7BE697 (78:2500) | 33, 8, 0.5 (0.667), same gradient | ok |
| Nav pill alt (Runs) | stroke gradient | #7BE697 -> #53B2ED (78:1766) | same | ok |
| Nav widths | 109 / 93 / 94 | 109.21 / 92.56 / 91.99 (pipeline list 134.56/143.31/161.56 vs 135/144/162) | ok (hug) |
| Nav "Runs" | weight | Medium on all screens | 500 | ok |
| Type classes | heading-16 500, body-12 400, field-10 #62666D, label-10 #8A8F98, numeral-38 Jura, numeral-light 300, title-12 colour, ls 0 | as listed | same | ok |
| Icons | sizes/colours | 11x13 Grey 200, 12 Orange, 16 Blue | same | ok |
| Shell Pipeline | frame, header | 1920 wide, header 66, pad 40, border-bottom #111213 (78:2488) | 1920, 66, 40, #111213 | ok |
| Shell Pipeline | content col | 642 wide at x639 y106 (78:2511) | 642 at 639,106 | ok |
| Shell Pipeline | KPI row | 142.5 wide, x 0/166.5/333/499.5 | 142.5, 0/166.5/333/499.5 | ok |
| Shell Pipeline | nav group | 643x33 (78:2499) | 641.21x33 | ok (hug, -1.8) |
| Shell Pipeline | outline panel / filled panel heights | 312 / 196 (78:2528, 78:2575) | 309.33 / 194.67 | explained (see below) |
| Filter item | box, pad, radius, colour, selected | 202x32, 8/12/8/16, 8, #A6ACB6, 33 high Medium (78:1889, 78:1906) | 202x32, 8px 12px 8px 16px, 8, #A6ACB6, 33, 500 | ok |
| Stepper / donut | box | 1130x68 / 140x140 (78:1837, 78:1796) | 1130x68 / 140x140 | ok |
| Summary card | pad, gap | 24/32, 24 (78:1794) | 24px 32px, 24 | ok |
| Data table | frame radius, header row, UBO row 1 | 8, 31, 54 (78:2084, 78:2085, 78:2102) | 8, 30.67, 53.67 | ok |
| Data table | cell pad, header/body text | 8, #62666D 10 / #DCE1E9 12 | same | ok |
| Wallet | content box, offset, form card | 984x403 at 468,106; card 658x330 (78:2624, 78:2629) | 984x402 at 468,106; 658x329.33 | ok |
| Runs | screen, content offset | 1920x1293, 210,90 (78:1751, 78:1775) | 1920x1293, 210,90 | ok |

Gradient angle: the CSS angle (88.23deg / 85.08deg) is derived from the Figma transform; Figma maps the gradient box-relative, so the true angle varies a few degrees with element aspect ratio. The builder documents this; not measurable here (not a defect).

## Coverage
Spec components (10 definitions: Select, Search, Input, CTA, Outline, Outline+icon, Tabs 32, Tabs 24, toggle, toggle w text, with all drawn states: CTA/Outline hover, Variant2, toggle ON/OFF): all documented in `components.md` and present in `components.css`. Patterns (spec 6.1-6.10): nav pill, status pill family, KPI card, panel/gradient/row card (+ active, dark), notice x3, table, sidebar filter list, stepper, ring/donut, step chip, section head, status dot, issue line, header shell, screens x4: all present. Missing: none. Extras not in spec and not labelled EXTENDED: none found (0 EXTENDED in CSS, Extended table has the single "none" row; consistent). Assets: all 18 files in `assets/` referenced (the `-default.svg`, `lucide-*.svg` non-`currentColor` originals are kept as source files and not referenced, which is fine). Photo layer: placeholder `--bg-photo-image` (the 3 console 404s are only the documented `/path/to/your-photo.jpg` placeholder in the Shell snippet).

## Precision / portability greps
- B1 rule blocks 239 vs `/* figma: */` comments 239; no rule more than 3 lines from a source comment.
- B2 raw hex/rgb in components.css rule bodies: 0 (hex only inside comments).
- B3 raw hex in non-token files: components.md 6 (prose mentions, e.g. "White = #DCE1E9"), CLAUDE.md 37, SKILL.md 1, assets/MANIFEST.md 23 (documentation text, not CSS values) - note only.
- C `tokens.json` valid JSON; 189 leaf entries == 189 custom properties in tokens.css, 0 duplicates; 128 `var(--x)` used in components.css, 0 undefined; 0 undefined refs in tokens.css. Palette: all 30 paint styles match foundations 1.1 (spot-checked all).
- D no `<svg`/`path d=` inline in CSS/MD; icons from `assets/`.
- E `{{` placeholders: 0. "(visual estimate)" markers in spec: 0 in use, so none needed in CSS.
- F absolute/machine paths: 0. Internal tooling mention (`design-system-kit|figma-ds|MCP|harvest`): 1 hit, `assets/MANIFEST.md:43` ("were NOT harvested"), a non-underscore file; wording only, optional tidy.

## Mismatches
Real: none.
Explained:
1. Hug widths 0.1-2.9 px narrower than Figma (Select -1.5, Tabs 32 -1.4, Tabs 24 -2.9 vs component / -0.9 vs instance, nav group -1.8): font metrics; with fallback fonts (fonts not loaded) deviations were 2-6 px.
2. Pipeline panel heights 309.33 vs 312 and 194.67 vs 196, content stack y of the filled panel 519 vs 522 (cumulative -3): line-height `normal` (Manrope 1.366) vs Figma "auto" text boxes (and KPI 105.33 vs 106, row card 106 vs 107). Sub-pixel per row, no layout break.
3. 1px borders read 0.667 and 0.5px read 0.667 at DPR 1.5; declared CSS values are 1px / 0.5px.

## Remaining issues (all minor)
- `assets/MANIFEST.md:43` uses the word "harvested" (portability grep F).
- Hex values appear as prose in components.md / CLAUDE.md / SKILL.md / MANIFEST.md (B3 strict reading); acceptable as documentation.
- Documented design inconsistencies (alt gradient direction, "1, 2, 2", Medium "Runs", 3-stop vs 2-stop outline hover, Variant2 naming) are listed in CLAUDE.md as decisions; nothing to fix.

## Expand build 2026-11-16
See _expand-proposal.md (After approval table). 13 rows + drawn states built in components.css PART 3; tokens: 14 drawn-state/modal additions + 13 `--…-ext-…` aliases (group `extended`); assets: select-chevron-down-disabled.svg, search-disabled.svg added. Verified in the browser by computed styles on a throwaway test page (rule vs computed, exact) and 9 design-defined regression checks (all unchanged).
