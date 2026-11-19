# echo — Foundations (harvested from design file `<figma-file-key>`)

Scope: page "final " (`78:1750`, trailing space in name) › 4 canonical frames: "Pipeline" (`78:2486`, 1920x1080), "Runs / Ownership" (`78:1751`, 1920x1293), "Runs / Overview" (`78:2225`, 1920x1293), "Wallet Check" (`78:2600`, 1920x1080). Plus "components page" = page "drafts" (`3:10845`) component definitions `10:170 Select, 73:1680 Search, 73:1679 Input, 18:242 Outline Button, 18:248 CTA Button, 21:384 Tabs 32, 21:401 Tabs 24, 18:290 Outline Button + icon, 21:32 toggle, 21:55 toggle w text`. Harvested 2026-11-16 by `figma-harvester` (foundations), read-only via the Plugin API.
Owner decisions applied (from `_intake.md`): (1) screens from `final`, components/variants from `drafts` (only place they exist); (2) pages `old echo` (`0:1`, 5 children, sections) and `styling examples` (`2:600`, 2 children) SKIPPED (recorded by name only); (3) source of truth = Figma.

Legend: `id` = Figma node id. `{VarName}` = bound variable. `(visual estimate)` = not from node data. Counts = visible nodes incl. nodes inside instances. `x,y` parent-relative unless stated. "T" = text node. Screen abbreviations in count tables: P = Pipeline, Own = Runs/Ownership, Ov = Runs/Overview, W = Wallet Check. Paint-style names are quoted verbatim (including their odd spellings).

---

## 0. Scope and provenance
| Item | Value |
|---|---|
| Canonical node(s) | Page `78:1750` "final " (flat, 4 top-level frames, no sections; canvas bg #F5F5F5 = r0.9608 g0.9608 b0.9608). Frames: `78:2486` Pipeline 1920x1080 @x0; `78:1751` Runs / Ownership 1920x1293 @x2000; `78:2225` Runs / Overview 1920x1293 @x4000; `78:2600` Wallet Check 1920x1080 @x6000. All four: type FRAME, `clipsContent` true, `layoutMode` NONE, fill = style "Black 900" #08090A, 0 hidden nodes. Visible node counts (incl. inside instances): P 119, Own 489, Ov 268, W 74. |
| Components page | `3:10845` "drafts", 14 children: 4 screen copies + 10 component definitions (see section 6). Canvas bg #F5F5F5. Component definition colours/type are profiled in 1.8 / 2.x tagged "components page". |
| Alternates seen | Drafts copies `22:2621` Pipeline (x-145), `4:15408` Runs/Ownership (x1855), `63:712` Runs/Overview (x3855), `73:1531` Wallet Check (x5938): same size as the finals. Owner decision: final wins. Compared by node-for-node walk (name, type, size, parent-relative x/y, text content, visibility, auto-layout gap/padding, fill-style id): **0 differences in 119/489/268/74 compared nodes**; per-frame colour/type/radius/stroke tallies are identical to the finals (section 6.3). Not compared: node ids differ (finals `78:*`, drafts `22:*, 4:*, 63:*, 73:*`) and gradient transforms/bound variables of drafts were not diffed. |
| Skipped pages | `0:1` "old echo" (5 sections, captures of the old built app) and `2:600` "styling examples" (2 sections + 3 images, coinbase.com / linear.app inspiration): not profiled, by owner decision. |
| Hidden nodes in scope | 0 in all four finals and four draft screens and ten component roots (fingerprint `hid` = 0). The pre-placed photo `78:2487` is VISIBLE but positioned off-canvas (see 6.2). |
| Extraction scripts | `figma-inventory.js` (LIST_PAGES + LIST_VARIABLES + LIST_STYLES; inlined/trimmed, same logic). `figma-fingerprint.js` logic run once per canonical root (one frame per call) in an EXTENDED form (adds example node ids per key, stroke sides, gradient stops+transform, effect layers, node opacity, blend, gap/pad per axis, text align) — a superset of the kit script, counts are identical in definition. Custom read-only walkers for: shell geometry (type, x,y,w,h, auto-layout, style names), final-vs-drafts diff, pill census, raw-paint census, icon census, fonts (`listAvailableFontsAsync`), mixed text segments. Nothing was written to Figma. |
| Not covered by this file | Component variants/states internals (components harvester), icon/SVG export (assets harvester), full per-screen content structure (screens harvesters). |

### 0.1 Variables, styles, applied-ness
| Item | Value | Node id / source |
|---|---|---|
| Variable collections | **0** local collections (`getLocalVariableCollectionsAsync` = []). One STRAY variable exists and is bound once: `VariableID:1:129` "corner radius/22369600" (single mode `1:0`, value 22369600, not remote) bound to topLeft/topRight/bottomLeft/bottomRight radius of the logo vector `78:2491` (Union 70x20; the node's radii read as null/mixed). It is import debris, not a design token; the same node exists in each screen's header logo (`78:2229`, `78:2604`, `78:1755`). | `78:2491`, fingerprint `vars` row |
| Text styles | **0** (local). `textStyles` tally in every fingerprint = empty: no text node has a text style. | inventory `styles.counts.text` = 0 |
| Effect styles | **0** (local); no node applies an effect style. | inventory |
| Grid styles | 0 | inventory |
| Local paint styles | **30** (list in 1.1). They ARE applied: only 4 paints in the four finals are unbound (section 1.8). Applied-style counts in the fingerprints, e.g. Own: Red x30, Orange x39, White x27, Grey 300 x28 (fills) / Grey 400 x24 (strokes). | fingerprint `paintStyles` |
| Remote (library) styles | **none**: no tallied style id carries the "(remote)" flag in any fingerprint. | fingerprint |
| Pages | `78:1750` "final " 4 children; `3:10845` "drafts" 14; `0:1` "old echo" 5; `2:600` "styling examples" 2. | inventory `pages` |

### 0.2 Font families found
| Family | Styles used | Where | Installed in file? |
|---|---|---|---|
| Manrope | Regular, Medium | All UI text: nav, labels, body, tables, pills, buttons, inputs, tabs (everywhere except big numerals) | `listAvailableFontsAsync`: Manrope has Bold, ExtraBold, ExtraLight, Light, Medium, Regular, SemiBold; only Regular and Medium are USED in finals/components |
| Jura | Medium, Light, SemiBold | Numerals / KPI figures: stat numbers "2/1/0/0" 38px (`78:2517`,`78:2520`,`78:2523`,`78:2526`), percentages 14px/20px/38px, "60 out of 116" (`78:1799`, SemiBold 12), Wallet step numbers 14px (`78:2633`,`78:2639`,`78:2645`). Mixed-font text: "41%" `78:2548`, "62%" `78:2571` (digits Jura Medium 20, "%" Jura Light 20) and "62%" `78:1798`/`78:2272` (digits Jura Medium 38, "%" Jura Light 38) | Jura has Bold, Light, Medium, Regular, SemiBold; Light/Medium/SemiBold used |
| (none other) | — | no mono, no Inter in finals | — |

---

## 1. Colour palette

Every colour in the four finals comes from the 30 local paint styles except 4 raw paints (1.8). Palette resolved by ROLE; counts supporting only. All hex are exact from node data (channel * 255, rounded for display only; no channel merged).

### 1.1 Named palette — the 30 local paint styles (verbatim names, resolved)
| Style name (verbatim) | Value | Style id | Role as used |
|---|---|---|---|
| Blue | #59BCFA | `S:68861d02f44612ade17ba89405186766146fadfb,` | text accent (percentages, numerals "2", links), icon strokes |
| Blue 75% | #59BCFA @0.75 | `S:9b7df76a631de4bd9f8b4eff053b511d0b90251e,` | logo line 1 stroke (`78:2496`) |
| Blue 50% | #59BCFA @0.5 | `S:19f581b286358c486ed352ac7ac04d9af505b850,` | logo line 2 stroke (`78:2497`); icon fills `78:2002`; icon strokes |
| Blue 25% | #59BCFA @0.25 | `S:a6c14623ba8b86d1097b990dc83f02bb7f8b4be7,` | logo line 3 stroke (`78:2498`) |
| Blue 15% | #59BCFA @0.15 | `S:d4490bcfb5d8630b35db266db6008beb6f1846ca,` | person-tag pill fill (`78:1974`), search icon ellipse (`I78:2635;78:1708`) |
| Black 900 | #08090A | `S:7774f5c6f177ae6a9bfb5d0b450b030ac8eba7f0,` | screen background; KPI cards; deepest surface; text on bright fills (button label) |
| Grey 500 | #171819 (was #111213) | `S:0187b185aaa2a944065d24f73aef9414f7191627,` | control fill (Select/Search/Input), inner row cards, header bottom border |
| Grey 400 | #2C2E2F (was #1C1E1F) | `S:7f06bc71069190c0a42a2eb4123713a66fef4704,` | hairline border colour on panels/controls/table rows; tab-track fill; step-number chip fill |
| Grey 300 | #62666D | `S:b5ce2d3ee5bca4ab6864f9f6fd3bdcb28b477736,` | muted text, section captions, placeholders, toggle-off track |
| Grey 200 | #8A8F98 | `S:59ecbb960d83a332e0fdaa330f88e06a9696dd4c,` | secondary text, outline-button border+label |
| Grey 100 | #A6ACB6 | `S:89c1fd6d3cb4acb098cd5ed55a5cf6d7762cd46b,` | tertiary/label text, form labels |
| White | #DCE1E9 | `S:78b047154bb8b3bb827aadb5e035e463f5e3aa2e,` | primary text AND CTA button fill. NOTE: the style is named "White" but its value is #DCE1E9 (not #FFFFFF) |
| Green | #7BE697 | `S:fb6ac848fff8f7d7ef3764562921d9f2a81115da,` | success/approved/UBO/100%, status dot |
| Green 75% | #7BE697 @0.75 | `S:72ab781471add739dfa0f87c2346f8249a2ae0da,` | not applied in finals |
| Green 50% | #7BE697 @0.5 | `S:4528c34b75e7f0ddd93d3fdeb1e2ccaf58fab712,` | not applied in finals |
| Green 25% | #7BE697 @0.25 | `S:f91150c21f0bde1dd74f76715b89aa6edcc325ef,` | success pill fill (`78:2056`) |
| Green 15% | #7BE697 @0.15 | `S:1e9447dbc79a2ced8f0f6417c483c99ff7cd7687,` | not applied in finals |
| Gradient green | linear #5DE7CB@p0 -> #66D74A@p1 | `S:5c9fbf12fc2370c5b82023805db7f3d2740dee17,` | stroke of completed-step circles (`78:1848` Ellipse 3 40x40) |
| Gradient green opposite | linear #66D74A@p0 -> #5DE7CB@p1 | `S:0e29eb759e576aebf9a2241a07a5bdebadd0061a,` | not applied in finals |
| Orange | #F3AB52 | `S:d25934040652a9af7dc5e16c32ffa87ad2c80852,` | warning/missing-doc text, status dot, "Not screened"/"Single Source" pill outline |
| Gradient orange | linear #F3892D@p0 -> #ECE040@p1 | `S:f8f0904c5601445926dddf08d61454ea1ad4ae65,` | current-step circle (`78:1865`, `78:2339` fill; `78:1867` Ellipse 5 stroke) |
| Gradient main | linear #7BE697@p0 -> #53B2ED@p1 | `S:9fb85a6a98ac2d3429f6a77f45ffa293f7cc7934,` | active card outline, completed-step fills (`78:1847`), chevron strokes, Wallet step numerals (text fill) |
| Gradient main oposite (sic) | linear #53B2ED@p0 -> #7BE697@p1 | `S:21c76f54d2bdf7f5001b400ee9746342392a1f46,` | logo Union fill, active nav pill stroke on Pipeline/Wallet screens |
| Red | #F35352 | `S:f5210b2fba24ddc4e36633ff4af38fe5f833ebc5,` | conflict/error text and status dot, "problem" pill text |
| Red 50% | #F35352 @0.5 | `S:c3de9ea11f3888f42bb15d51fe4ce43dddd571c1,` | not applied in finals |
| Red 25% | #F35352 @0.25 | `S:6952974d393d36e264137acfe69721623219652d,` | problem/missing pill fill (`78:2046`), critical-item panel fill (`78:1957`) |
| Purple | #9081E4 | `S:65e9155e008cab62b78bb52cc69dd3b3d9d8ed4c,` | "Main check"/shareholder/director text, KPI "0" |
| Purple 15% | #9081E4 @0.15 | `S:fb5453a9525c405169426450019d2e21b42fdd1e,` | shareholder/director pill fill (`78:2018`), info panel fill (`78:1989`) |
| Purple 50% | #9081E4 @0.5 | `S:b99bfe497b9796424785963b1f575ddb28750f2a,` | not applied in finals |
| bg gradient | linear #111213@0.1 (p0) -> #171819@1 (p1; was #161718) | `S:a0b8444852615c80a63c11bfe827abcacc0bbcc7,` | large panel fill (summary card `78:1794`, `78:1950`, `78:2268`, `78:2425`, `78:2435`) |

Gradient transform for the 4 "Gradient *" family styles and "Gradient main(opposite)": `[[0.97,-0.03,0.03],[1,1.04,-0.5]]` (same for all five 2-stop brand gradients, read from the style paints). "bg gradient" transform: `[[0.93,-0.08,0.07],[0.88,0.93,-0.4]]`. Note: first stop of "bg gradient" has stop alpha 0.1 (colour alpha, not paint opacity), second stop alpha 1.

Style names not applied in the canonical frames (checked by style name in the 4 finals): Green 75%, Green 50%, Green 15%, Gradient green opposite, Red 50%, Purple 50% (plus Blue 25%/Blue 75%/Blue 50% only as strokes/small icons, see above).

### 1.2 Fills (solid, non-text) — by role (counts per screen where it occurs)
| Colour | Count (P/Own/Ov/W) | Role (derived from the nodes) | Example node ids |
|---|---|---|---|
| #08090A (Black 900) | 7/1/1/1 | screen root fill (`78:2486`,`78:1751`,`78:2225`,`78:2600`); KPI cards "Frame 80..83" 142.5x106 (`78:2516`,`78:2519`) and nested "Frame 57" (`78:2577`) | `78:2516`, `78:2577` |
| #111213 (Grey 500) | 4/5/4/8 | input-like controls (Select instance `78:2510`; Search `78:2635`; Input `78:2641`), inner row cards "Frame 56" 608x107 (`78:2531`), Wallet form card `78:2629` | `78:2510`, `78:2531`, `78:2629` |
| #1C1E1F (Grey 400) | 0/1/0/3 | tab-track fill (Tabs 24 instance `78:1995`), step-number chips "Frame 101" 24x24 (`78:2632`,`78:2638`,`78:2644`) | `78:1995`, `78:2632` |
| #DCE1E9 (White) | 1/1/1/1 | CTA Button fill (instance 134x32 / 154x32 / 154x32 / 175x32) | `78:2514`, `78:1808`, `78:2282`, `78:2651` |
| #4DFFCD | 4/4/4/4 (raw) | logo wordmark glyph vectors (Vector 16.54x20 etc.) | `78:2492`, `78:2493`, `78:2494` |
| #F3AB52 (Orange) | 2/10/22/0 | 6x6 status dots "Ellipse 7" | `78:2584`, `78:1896`, `78:2370` |
| #F35352 (Red) | 1/8/8/0 | 6x6 status dots "Ellipse 6" | `78:2583`, `78:1895`, `78:2369` |
| #7BE697 (Green) | 0/2/2/0 | 6x6 status dots | `78:1900`, `78:1923`, `78:2374` |
| #59BCFA@0.15 (Blue 15%) | 0/19/0/1 | person tag pill fill "Frame 46" 56x15 | `78:1974`, `78:1977` |
| #F35352@0.25 (Red 25%) | 0/13/0/0 | problem pill fill; critical-item panel `78:1957` 943x104 | `78:2046`, `78:1957` |
| #7BE697@0.25 (Green 25%) | 0/8/0/0 | success pill fill (UBO / Confirmed) | `78:2056`, `78:2140` |
| #9081E4@0.15 (Purple 15%) | 0/3/0/0 | role pill fill; info panel `78:1989` 943x38 | `78:2018`, `78:1989` |
| #59BCFA@0.5 (Blue 50%) | 0/4/0/0 | icon glyph fill (Union 12.01x12.01) | `78:2002`, `78:2012` |
| #62666D (Grey 300) | 0/1/0/0 | toggle off-track rectangle inside the toggle-w-text instance | `I78:1955;21:59` |
| IMAGE FILL @0.2 | 1/0/0/0 | background photo `78:2487` (FILL scale mode, paint opacity 0.2, filters all 0) — off-canvas, see 6.2 | `78:2487` |

Gradient fills: see 1.6.

### 1.3 Status / category colour map (pill geometry)
Pill census (Ownership + Overview, visible, H-auto-layout frames 14-18px high with radius 4; counts are combined for Own+Ov). All text is Manrope, left aligned, line-height auto, letter-spacing 0%.

| Category (observed use) | Fill | Stroke | Text colour | Text style | Pill box (h | radius | padding T/R/B/L | gap) | Count | Examples |
|---|---|---|---|---|---|---|---|
| Person tag ("{PERSON_n}" placeholder strings) | #59BCFA@0.15 (Blue 15%) | none | #59BCFA (Blue) at node opacity 0.7 | Medium 8 | 15 | 4 | 2/4/2/4 | 10 | 19 | `78:1974` "{PERSON_2}", `78:1977`, `78:1981` |
| Not screened / Single-source (neutral warning) | none | #F3AB52 w0.5 OUTSIDE | #F3AB52 | Regular 8 (one is Regular 10: `78:2108` "Single Source", h18) | 15 (18) | 4 | 2/8/2/8 | 10 | 12 (+1) | `78:2007`, `78:2020`, `78:2031`; `78:2108` |
| Problem / Missing (error) | #F35352@0.25 (Red 25%) | none | #F35352 | Regular 8 | 15 | 4 | 2/8/2/8 | 10 | 12 | `78:2046` "1 problem", `78:2060` "8 problems", `78:2112` "Missing" |
| Confirmed / UBO (success) | #7BE697@0.25 (Green 25%) | none | #7BE697 | Regular 8 | 15 | 4 | 2/8/2/8 | 10 | 8 | `78:2056` "UBO", `78:2140` "Confirmed" |
| Shareholder / Director (role) | #9081E4@0.15 (Purple 15%) | none | #9081E4 | Regular 8 | 15 | 4 | 2/8/2/8 | 10 | 2 | `78:2018` "Shareholder", `78:2072` "Director" |

Status dots (6x6 ellipses, no stroke): Red #F35352 (`78:2583`, 21 total in finals), Orange #F3AB52 (`78:2584`, 34 total), Green #7BE697 (`78:1900`, 4 total). Inline issue text colours: Red = conflicts, Orange = missing/out-of-date docs, Purple = "Main check", Blue = percentage progress (see 1.4). Issue text lines ("19 conflicting val…", "4 missing document…") have NODE opacity 0.7 (T, 34 nodes in Own; 11 in Ov; e.g. `78:1814`, `78:1816`, `78:1818`).

### 1.4 Text colours (by role, counts P/Own/Ov/W)
| Colour (style) | Count | Role | Examples |
|---|---|---|---|
| #DCE1E9 (White) | 11/26/25/9 | primary text: nav labels, card titles, page headings | `78:2501`, `78:1765`, `78:2513` |
| #62666D (Grey 300) | 11/27/5/6 | muted captions: KPI labels, "Recent Runs", "Still Open:", placeholders ("Search", "Type here") | `78:2518`, `78:1777`, `I78:2635;73:1664` |
| #A6ACB6 (Grey 100) | 2/13/14/2 | secondary labels: tab/section labels (Overview, Business), form labels "Client", "Wallet address", action hint text | `78:2539`, `78:1891`, `78:2634` |
| #8A8F98 (Grey 200) | 2/9/6/2 | tertiary: run status ("Needs analyst", "Approved"), wallet address text | `78:2585`, `78:1781`, `78:2657` |
| #59BCFA (Blue) | 7/25/11/0 | percentages / metrics / "2" | `78:2517`, `78:1782`, `78:1798` |
| #F35352 (Red) | 5/22/2/0 | conflict counts, problem text, KPI "1" | `78:2520`, `78:1814`, `78:1959` |
| #F3AB52 (Orange) | 4/29/11/0 | missing / out-of-date counts | `78:2544`, `78:1818`, `78:2292` |
| #9081E4 (Purple) | 3/3/0/0 | "Main check", role text, KPI "0" | `78:2523`, `78:2533`, `78:1991` |
| #7BE697 (Green) | 1/10/2/0 | success: "100%", "UBO", KPI "0" | `78:2526`, `78:1792`, `78:2057` |
| #08090A (Black 900) | 1/2/1/1 | button label on CTA fill (inside CTA Button instance), Tabs 24 active label | `I78:2514;10:169`, `I78:1995;21:398` |
| gradient #7BE697 -> #53B2ED (Gradient main, text fill) | 0/0/0/3 | Wallet step numerals "1","2","2" in chips | `78:2633`, `78:2639`, `78:2645` |

### 1.5 Stroke colours by class (weight, align, sides)
| Class | Colour (style) | Weight | Align | Sides | Count (P/Own/Ov/W) | Examples |
|---|---|---|---|---|---|---|
| Header bottom border | #111213 (Grey 500) | 1 | INSIDE | bottom only (T0 R0 B1 L0) | 1/1/1/1 | `78:2488`, `78:1752`, `78:2226`, `78:2601` |
| Panel / card / control border | #1C1E1F (Grey 400) | 1 | INSIDE | all | 9/9/7/9 | `78:2510` Select, `78:2516` KPI card, `78:1776` panel, `78:2629` form card |
| Table / section divider | #1C1E1F (Grey 400) | 1 | INSIDE | bottom only | 0/6/13/0 | `78:1795`, `78:2085` header row, `78:2102` row, `78:2439` |
| Progress track lines | #1C1E1F (Grey 400) | 2 | CENTER | Line 13/14/15 (136x0) | 0/6/6/0 | `78:1841`, `78:2315` |
| Thin separators | #1C1E1F (Grey 400) | 1 | CENTER | Line 16/17/18 | 0/3/0/0 | `78:2078`, `78:2079`, `78:2080` |
| Active card outline | gradient #7BE697 -> #53B2ED (Gradient main) | 1 | INSIDE | all | 0/1/1/0 | `78:1778` Frame 56 254x50, `78:2252` |
| Active nav pill | gradient (Gradient main oposite on P and W; Gradient main on Own/Ov) | 0.5 | INSIDE | all | 1/1/1/1 | `78:2500`, `78:1766`, `78:2240`, `78:2617` |
| Select chevron | gradient #7BE697 -> #53B2ED | 1 | CENTER | vectors arrow-down 12x6 and 6x3 (6x3 at node opacity 0.5) | 2/2/2/3 | `I78:2510;18:310`, `I78:2510;18:311` |
| Warning pill / panel outline | #F3AB52 (Orange) | 0.5 | OUTSIDE (pills) / INSIDE (panel `78:1970`, `78:2430`) | all | 0/13+1/1/0 | `78:2007`, `78:1970` |
| Warning icon | #F3AB52 | 1 | CENTER | vector 10x10 | 2/0/0/0 | `78:2538`, `78:2561` |
| Info icons | #59BCFA / #59BCFA@0.5 | 1 | CENTER | vectors 4x2.5, 11x11, 12x12 | 0/8+2/0/0 | `78:2003`, `78:2004`, `78:2051` |
| Logo lines | Blue 75% / Blue 50% / Blue 25% | 1.5 | CENTER | 20x0 lines | 1 each/screen | `78:2496`,`78:2497`,`78:2498` |
| Step circle (done) | #5DE7CB -> #66D74A (Gradient green) | 2 | CENTER | Ellipse 3 40x40 | 0/3/3/0 | `78:1848` |
| Step tick (done / pending) | #08090A / #62666D | 2 | CENTER | check vectors 16x11 | 0/3+3/3+3/0 | `78:1849`, `78:1875` |
| Step circle (current, dashed) | #F3892D -> #ECE040 (Gradient orange) | 2 | CENTER | Ellipse 5 20x40 incl. dash pattern [6,6] on `78:1866` Ellipse 4 | 0/2+1/2+1/0 | `78:1867`, `78:1866` |
| Outline button + icon | #8A8F98 (Grey 200) | 1 | CENTER | instance 142x32 (stroke on instance) | 0/1/1/0 | `78:1807` |
| Progress ring track | #08090A | 4 | INSIDE | Ellipse 1 72x72 | 2/0/0/0 | `78:2550`, `78:2573` |
| Progress ring arc (RAW gradient #53B2ED -> #7BE697, transform `[[0.48,0.97,-0.37],[0,1.81,-0.19]]` / `[[0.8,1.03,-0.37],[0.01,1.92,-0.19]]`) | raw | 4 | INSIDE | Ellipse 2 33.84x64.05 / 57x68 | 2/0/0/0 | `78:2551`, `78:2574` |
| Donut track (big) | #111213 (stroke colour value of "Grey 500"; no style bound to this stroke in the tally) | 8 | INSIDE | Ellipse 1 140x140 | 0/1/1/0 | `78:1801`, `78:2275` |
| Donut arc (RAW gradient #53B2ED -> #7BE697, transform `[[0.8,1.03,-0.37],[0.01,1.92,-0.19]]`) | raw | 8 | INSIDE | Ellipse 2 111.18x131.76 | 0/1/1/0 | `78:1802`, `78:2276` |
| RAW line gradient #54B3E9 -> #F3892D, transform `[[0.97,-0.03,0.03],[1,1.04,-0.5]]` | raw | 2 | CENTER | Line 12 136x0 | 0/1/1/0 | `78:1840`, `78:2314` |

Strokes-in-layout: header and all content frames report `strokesIncludedInLayout = true` (children are inset by padding + stroke weight: a frame with padding 16 and a 1px INSIDE stroke places children at 17 and the child width = parent width - 34; e.g. `78:2511` > `78:2528`: 642 - 34 = 608 for `78:2529`). Rebuild consequence: CSS `border: 1px` + `padding: 16px` (border-box), not padding 17. Screen root frames report `strokesIncludedInLayout=false` (checked `78:2486`, `78:2600`).

### 1.6 Gradients (full stops + transform)
| Gradient | Stops (hex @ position, colour alpha) | gradientTransform | Used on | Node ids |
|---|---|---|---|---|
| Gradient main (style) | #7BE697@0 -> #53B2ED@1 (a1,a1) | `[[0.97,-0.03,0.03],[1,1.04,-0.5]]` | 42x42 step Union fills (3x/screen), active card outline, chevrons, Wallet numerals (text) | `78:1847`,`78:1853`,`78:1859`; `78:1778`; `78:2633` |
| Gradient main oposite (style) | #53B2ED@0 -> #7BE697@1 | same | logo Union 70x20 fill; active nav stroke (P,W) | `78:2491`, `78:2500`, `78:2617` |
| Gradient green (style) | #5DE7CB@0 -> #66D74A@1 | same | done-step circle stroke | `78:1848` |
| Gradient green opposite (style) | #66D74A@0 -> #5DE7CB@1 | same | not applied in finals | — |
| Gradient orange (style) | #F3892D@0 -> #ECE040@1 | same | current-step circle fill/stroke | `78:1865`, `78:2339`, `78:1867` |
| bg gradient (style) | #111213 alpha 0.1 @0 -> #171819 alpha 1 @1 (was #161718) | `[[0.93,-0.08,0.07],[0.88,0.93,-0.4]]` | big panels fill, 16px radius | `78:1794`, `78:1950`, `78:2268`, `78:2425`, `78:2435` |
| RAW gradient #53B2ED@0 -> #7BE697@1 | strokes of rings (no style) | see 1.5 | ring arcs | `78:2551`, `78:2574`, `78:1802`, `78:2276` |
| RAW gradient #54B3E9@0 -> #F3892D@1 | Line 12 stroke | `[[0.97,-0.03,0.03],[1,1.04,-0.5]]` | `78:1840`, `78:2314` |
| Components page: 3-stop gradient #53B2ED@0 -> #4CCED4@0.5 -> #45EABB@1 (all alpha 1) | stroke w1 CENTER of the Outline Button hover variant `18:253` ("Property 1=hover", 87x32, no fill), transform `[[0.97,-0.03,0.03],[1,1.04,-0.5]]`, NO paint style bound | — | `18:253` |
| Components page: 2-stop #53B2ED->#7BE697 (Gradient main oposite) | CTA Button variant overlay `18:249` fill; Outline Button hover label text `18:254`; Tabs active fill `21:379`/`21:397`; Outline+icon `18:291`/`18:293` | same | `18:249`, `18:254`, `21:379`, `21:397` |

Note the screen files show the brand gradient in BOTH directions ("Gradient main" #7BE697 -> #53B2ED and "Gradient main oposite" #53B2ED -> #7BE697): the direction used depends on role (see tables). Both use the same transform.

### 1.7 Overlays / scrims
| Item | Value | Node id | Notes |
|---|---|---|---|
| Background photo overlay | IMAGE fill, paint opacity 0.2, scale FILL, node opacity 1, rotation 90.0000025 deg, 2165x2706 at (1991, 2165) in Pipeline | `78:2487` | positioned outside the 1920x1080 clipped frame: effectively invisible (see 6.2) |
| Node-level opacities | TEXT 0.7 (issue lines; Blue person-tag text); VECTOR 0.5 (chevron small arrow `I78:2510;18:311`) | `78:1814`; `I78:2510;18:311` | only opacity usages found |
| Blur / backdrop-blur | none | — | 0 nodes with `LAYER_BLUR` / `BACKGROUND_BLUR` across the four finals |
| Scrim / modal overlay | none | — | none found (see GAPS) |

### 1.8 Unbound (raw) paints in the finals (no paint style)
| Paint | Count | Where | Examples |
|---|---|---|---|
| #4DFFCD solid fill | 16 | logo wordmark vectors (4 per screen) | `78:2492`,`78:2493`,`78:2494` |
| gradient #53B2ED->#7BE697 stroke (ring-specific transforms) | 4 | progress rings | `78:2551`,`78:2574`,`78:1802` |
| gradient #54B3E9->#F3892D stroke | 2 | Line 12 | `78:1840`,`78:2314` |
| IMAGE fill | 1 | `78:2487` | — |
Components page raw paints: #8A38F5 and #9747FF strokes on component-set frames `18:242`,`18:248`,`18:290` (#8A38F5) and `21:32`,`21:55` (#9747FF) = Figma's default purple component-set outline, NOT design colours (should be ignored); the 3-stop hover stroke `18:253`.

### 1.9 Components page colours (tag: components page)
| Component (id) | Colours seen | Notes |
|---|---|---|
| Select `10:170` | fill #111213; stroke #1C1E1F w1 INSIDE; chevron gradient stroke (#7BE697->#53B2ED) w1 CENTER, small arrow node opacity 0.5; text #62666D Manrope Medium 10 | radius 8 |
| Search `73:1680` | fill #111213; stroke #1C1E1F w1 INSIDE; icon stroke gradient w1; icon ellipse fill #59BCFA@0.15; text #62666D Regular 12 | radius 8 |
| Input `73:1679` | fill #111213; stroke #1C1E1F w1 INSIDE; text #62666D Regular 12 | radius 8 |
| Outline Button `18:242` | default `18:227` stroke #8A8F98 w1 CENTER, text #8A8F98 Medium 12; hover `18:253` 3-stop gradient stroke, text gradient #53B2ED->#7BE697 | radius 8 |
| CTA Button `18:248` | fill #DCE1E9, text #08090A Medium 12; hover overlay gradient fill `18:249` (#53B2ED->#7BE697) | radius 8 |
| Tabs 32 `21:384` / Tabs 24 `21:401` | track fill #1C1E1F; active tab fill gradient (#53B2ED->#7BE697), active text #08090A, inactive text #62666D; Manrope Medium 12 (32) / Medium 10 (24) | tab radius 8 (F8 x2), track radius 8 |
| Outline Button + icon `18:290` | like Outline Button; icon stroke #8A8F98 / gradient | radius 8 |
| toggle `21:32`, toggle w text `21:55` | track #62666D (off) / gradient #5DE7CB->#66D74A "Gradient green" (on); knob #111213 x2; radius 24; label #DCE1E9 / #8A8F98 Medium 12 | rect radius 24 |

---

## 2. Typography
No text styles, no variables, line-height `AUTO` everywhere except one node, letter-spacing 0% everywhere, textCase ORIGINAL, no underline/strike. Alignment L=left, C=center. Counts = visible TEXT nodes (incl. inside instances), P/Own/Ov/W.

| Family | Style | Size | Line-height | Letter-spacing | Case | Decoration | Align | Count (P/Own/Ov/W) | Roles | Examples |
|---|---|---|---|---|---|---|---|---|---|---|
| Manrope | Regular | 8 | auto | 0% | none | none | L | 0/34/0/0 | status-pill text ("Not screened", "1 problem", "UBO") | `78:2008`, `78:2019`, `78:2021` |
| Manrope | Medium | 8 | auto | 0% | none | none | L | 0/19/0/0 | person-tag pill text ("{PERSON_n}") (text colour Blue #59BCFA, node opacity 0.7) | `78:1975`, `78:1978` |
| Manrope | Regular | 10 | auto | 0% | none | none | L | 14/16/0/0 | table header cells, issue sub-labels ("Main check", "(+11 )", "6 conflicts") | `78:2533`, `78:2540`, `78:2087` |
| Manrope | Regular | 10 | auto | 0% | none | none | C | 1/1/1/5 | Select label (`9:137`), Search placeholder (`73:1664`), Input placeholder (`73:1678`) | `I78:2510;9:137`, `I78:2635;73:1664`, `I78:2641;73:1678` |
| Manrope | Medium | 10 | auto | 0% | none | none | L | 6/32/10/2 | sub-lines, run status ("Needs analyst"), action hints | `78:2539`, `78:1781`, `78:2657` |
| Manrope | Medium | 10 | auto | 0% | none | none | C | 0/2/0/0 | Tabs 24 labels | `I78:1995;21:398`, `I78:1995;21:400` |
| Manrope | Medium | 10 | 16px | 0% | none | none | L | 0/0/1/0 | long paragraph "Critical item ..." (918x128) | `78:2434` |
| Manrope | Regular | 12 | auto | 0% | none | none | C | 4/12/12/4 | nav labels ("Pipeline", "Wallet check", "System health", "Admin Dashboard") — note includes inactive tab labels | `78:2501`, `78:1765`, `78:2239`, `78:2614` |
| Manrope | Regular | 12 | auto | 0% | none | none | L | 4/22/12/0 | section/tab labels ("Overview", "General information", "Business"), KPI labels ("Active") | `78:2518`, `78:1891`, `78:2365` |
| Manrope | Medium | 12 | auto | 0% | none | none | L | 5/18/30/6 | card titles ("CEDAR LOOP, INC.", "Recent Runs"), section captions ("Needs you (1)"), form labels | `78:2530`, `78:1777`, `78:2251`, `78:2634` |
| Manrope | Medium | 12 | auto | 0% | none | none | C | 2/3/3/2 | button labels (CTA / Outline Button + icon inner "Button"), nav item "Runs" (see note) | `I78:2514;10:169`, `I78:1807;18:282`, `78:2503` |
| Manrope | Medium | 14 | auto | 0% | none | none | L | 2/1/2/1 | company names in cards ("ALDER PEAK PTY LTD"), panel titles ("Review and approval…", "Ownership") | `78:2535`, `78:1953`, `78:2428`, `78:2628` |
| Manrope | Medium | 16 | auto | 0% | none | none | L | 1/1/1/1 | page headings: "Good afternoon, Alex. One run…", "CEDAR LOOP, INC.", "Add a client wallet" | `78:2513`, `78:1805`, `78:2279`, `78:2627` |
| Jura | Medium | 38 | auto | 0% | none | none | L | 4/0/0/0 | KPI numerals ("2","1","0","0") | `78:2517`, `78:2520`, `78:2523`, `78:2526` |
| Jura | Medium | 14 | auto | 0% | none | none | C | 2/3/3/0 | progress percentages ("59%", "62%", "100%", "51%") | `78:2588`, `78:1782`, `78:2256` |
| Jura | Medium | 14 | auto | 0% | none | none | L | 0/0/0/3 | Wallet step numerals (gradient text fill) | `78:2633`, `78:2639`, `78:2645` |
| Jura | SemiBold | 12 | auto | 0% | none | none | C | 0/1/1/0 | "60 out of 116" (donut caption) | `78:1799`, `78:2273` |
| Jura (MIXED: digits Medium / "%" Light) | 20 | auto | 0% | none | none | C | 2/0/0/0 | ring labels "41%", "62%" | `78:2548`, `78:2571` |
| Jura (MIXED: digits Medium / "%" Light) | 38 | auto | 0% | none | none | C | 0/1/1/0 | donut label "62%" (`78:1798` 73x24, `78:2272`) | `78:1798`, `78:2272` |

Notes: (a) Nav label "Runs" is Manrope Medium 12 on ALL four screens (`78:2503`, `78:1767`, `78:2241`, `78:2616`) while the other four nav labels are Regular 12, regardless of which tab is active (active = pill with gradient stroke; e.g. on Pipeline the active "Pipeline" `78:2501` is Regular, "Runs" `78:2503` is Medium): looks like a design inconsistency; owner to decide. (b) Several text nodes have hug width but a fixed height from "cap-height / leading trim"-style boxes: e.g. `78:1799` "60 out of 116" is 75x8 for a 12px font, `78:1814` issue lines 115x9 for a 10px font — do not copy those heights as boxes (BUILD_RULES 2). (c) Placeholder tokens such as `{PERSON_2}` are literal copy in the design (verbatim).
Components page type (tag: components page): Manrope Regular 10 (Select `9:137`, Search `73:1664`, Input `73:1678`), Manrope Medium 12 (buttons `18:226`,`10:169`,`18:282`; Tabs 32 `21:380`,`21:382`; toggle label `21:53`,`21:57`), Manrope Medium 10 (Tabs 24 `21:398`,`21:400`).

---

## 3. Shape & depth

### 3.1 Radii by role
| Radius | Role | Count (P/Own/Ov/W) | Node ids |
|---|---|---|---|
| 4 | pills, person tags (FRAME, 15px high) | 0/54/0/0 | `78:1974`, `78:1977`, `78:2007` |
| 8 | Select / CTA Button / Outline Button+icon / Search / Input instances (INSTANCE 8) | 2/4/3/6 | `78:2510`, `78:1807`, `78:1808`, `78:2635` |
| 8 | active nav pill; inner row cards (Frame 56/57, 254x50 / 608x107); small panels | 5/26/19/3 | `78:2500`, `78:1766`, `78:2531`, `78:1778` |
| 16 | large cards and panels: KPI cards 142.5x106, side panel 288x1161, bg-gradient summary card 1196x307, content card 977x841 | 6/3/4/2 | `78:2516`, `78:1776`, `78:1794`, `78:2629` |
| 24 | inactive nav pills (32px high, fully rounded) | 4/4/4/7 | `78:2502`, `78:2504`, `78:2506`, `78:2613` |
| 24 | toggle track rectangle 32x16 (inside toggle-w-text instance) | 0/1/0/0 | `I78:1955;21:59` |
| 0.5 | chevron arrow vectors | 2/2/2/3 | `I78:2510;18:310` |
| {corner radius/22369600} (bound, stray var) | logo Union | 1/1/1/1 | `78:2491` |
| 8 (component) | Select `10:170`, Search `73:1680`, Input `73:1679`, Outline/CTA buttons `18:227`/`18:142`, Tabs track `21:384`/`21:401` (tab F8 x2) | — | components page |
| 5 (component set frames) | set frames `18:242` etc. (C5) | — | Figma set-frame default, ignore |
Circle shapes (ellipses 6x6 dots, 40x40, 72x72, 140x140) have no corner radius.

### 3.2 Strokes by role
See 1.5 (weights 0.5 / 1 / 1.5 / 2 / 4 / 8; aligns INSIDE for boxes, CENTER for lines and vectors, OUTSIDE for the 13 warning pills).

### 3.3 Effects / shadows (every layer)
| Effect | Value | Node ids | Notes |
|---|---|---|---|
| DROP_SHADOW | color #000000 @0.48, offset x -2, y 2, blur radius 6, spread 0 (none), blend NORMAL | `78:2551`, `78:2574` (Pipeline ring arcs), `78:1802` (Own donut arc), `78:2276` (Ov donut arc) | only effect layer in the finals; used on gradient ring arcs; none on cards/panels |
| Layer blur / background blur | none | — | 0 nodes with blur effects (checked all four finals) |
| Effect styles | none | — | 0 local effect styles |
Components page effects: none found in the 10 component roots (fingerprint `e` absent).

### 3.4 Opacity usage
| Opacity | Where | Ids |
|---|---|---|
| node 0.7 | issue-text lines (34 Own, 11 Ov), person-tag text (19 Own) | `78:1814`, `78:1974` text child |
| node 0.5 | small chevron vector in Select instance (4 across screens) | `I78:2510;18:311` |
| paint 0.2 | background photo fill | `78:2487` |
| colour alpha (in paint styles) | Blue 75/50/25/15, Green 75/50/25/15, Red 50/25, Purple 50/15, bg gradient first stop 0.1 | section 1.1 |

---

## 4. Spacing and sizing observed
Observed values only (not design tokens; no spacing variables exist). Counts are visible auto-layout frames incl. inside instances (P/Own/Ov/W).

### 4.1 Item gaps
| Gap | Direction | Count | Roles | Example ids |
|---|---|---|---|---|
| 1 | H | 0/1/1/0 | gap between sidebar list and card (`78:1888`) | `78:1888`, `78:2362` |
| 2 | V | 6/3/3/2 | two-line text stacks (title+sub) | `78:2578`, `78:1779` |
| 2 | H | 0/2/0/0 | pill row | `78:1973` |
| 4 | H | 4/40/25/0 | icon + short text rows | `78:2536`, `78:1813`, `78:2287` |
| 4 | V | 2/28/2/2 | label stacks | `78:2534`, `78:1889`, `78:2363` |
| 6 | H | 0/1/0/0 | toggle + label | `78:1955` |
| 8 | H | 4/0/17/7 | issue rows, Wallet label rows | `78:2541`, `78:2439`, `78:2631` |
| 8 | V | 2/6/3/4 | title+form stacks | `78:2529`, `78:1809`, `78:2626` |
| 10 | H | 1/57/1/1 | CTA/button inner gap; pill inner gap (Own: 57 incl. 43 pill frames) | `78:2514`, `78:1974` |
| 10 | V | 1/2/1/2 | logo box (`78:2489`) | `78:2489`, `78:1753` |
| 12 | H | 0/1/0/0 | Outline Button + icon inner gap | `78:1807` |
| 12 | V | 2/4/4/0 | stacked blocks | `78:2532`, `78:1797`, `78:2271` |
| 13 | V | 0/1/1/0 | main column (`78:1793`, `78:2267`) between summary card and lower area | `78:1793` |
| 16 | H | 0/5/2/1 | Frame 62 columns (Ownership/Overview, panel-to-column gap), Wallet button row | `78:1775`, `78:2249`, `78:2647` |
| 16 | V | 6/1/2/1 | card inner stacks (KPI 106 high), side panel | `78:2516`, `78:1776` |
| 24 | V | 2/2/2/2 | section stacks (Pipeline `78:2511`, Wallet `78:2625`) | `78:2511`, `78:1794` |
| 24 | H | 1/0/0/0 | KPI card row | `78:2515` |
| 32 | H | 1/1/1/1 | Select inner gap | `78:2510` |
| 36 | H | 4/3/3/2 | row-card gap between left text and right value | `78:2531`, `78:1778`, `78:2654` |
| 38 | H | 0/0/0/1 | Wallet content columns | `78:2624` |
| 40 | H | 0/6/0/0 | table header column gaps | `78:1999`, `78:2009` |
| 48 | H | 0/1/1/0 | step row | `78:1795`, `78:2269` |
| 64 | H | 0/1/1/0 | step row cluster | `78:1811`, `78:2285` |
| 108 | H | 1/1/1/1 | header (space-between) | `78:2488` |
| 211 | H | 1/0/0/0 | greeting row (space-between) | `78:2512` |
| 309 | H | 0/1/2/0 | table title row | `78:1951`, `78:2426` |
| 391 | H | 0/1/1/0 | breadcrumb row | `78:1804` |

### 4.2 Paddings (T/R/B/L)
| Padding | Role | Count (P/Own/Ov/W) | Example ids |
|---|---|---|---|
| 8/32/8/32 | nav pills | 5/5/5/5 | `78:2500`, `78:1764`, `78:2613` |
| 16/40/16/40 | header | 1/1/1/1 | `78:2488` |
| 8/12/8/12 | Select / Input / Search controls | 1/1/1/4 | `78:2510`, `78:2641` |
| 8/32/8/8 | Search (icon at right) | 0/0/0/1 | `78:2635` |
| 8/24/8/24 | CTA Button | 1/1/1/1 | `78:2514`, `78:1808` |
| 8/20/8/16 | Outline Button + icon | 0/1/1/0 | `78:1807` |
| 8/16/8/16 | row cards Frame 56/57 254x50 / 608x107 variants | 0/7/4/2 | `78:1778`, `78:2654` |
| 12/16/12/16 | row cards 608x107 / 608x57 | 4/0/0/0 | `78:2531`, `78:2577` |
| 24/24/24/24 | KPI cards | 4/0/0/0 | `78:2516` |
| 16/16/16/16 | panels / big cards | 2/2/3/2 | `78:2528`, `78:1776`, `78:2629` |
| 24/32/24/32 | summary card (bg gradient) | 0/1/1/0 | `78:1794`, `78:2268` |
| 12/12/12/12 | notice panels (critical/info) | 0/3/1/0 | `78:1957`, `78:1970`, `78:2430` |
| 8/16/8/12 | filter list item "Frame 3/16/17" 202x32 | 0/13/13/0 | `78:1890`, `78:2364` |
| 8/8/8/8 | table cells | 0/38/0/0 | `78:2086`, `78:2088` |
| 8/0/8/0 | table rows (Overview) | 0/0/12/0 | `78:2439` |
| 2/8/2/8 | pills | 0/35/0/0 | `78:2007`, `78:2018` |
| 2/4/2/4 | person tags | 0/19/0/0 | `78:1974` |
| 0/0/24/0, 0/0/4/0, 0/16/0/0 | step block, table title, sidebar list | 0/1+1/1+2/0 | `78:1795`, `78:1951`, `78:1889` |

### 4.3 Fixed control heights by role (FIXED-height FRAME/INSTANCE <= 100px)
| Height | Role | Count | Node ids |
|---|---|---|---|
| 32 | Select, CTA Button, Outline Button + icon, Search, Input, nav pills (inactive: 32; active 33 because of 0.5 stroke counted in layout), logo box "Frame 7" 162x32 | 2/2/2/7 (frame-level) | `78:2510`, `78:2514`, `78:2635`, `78:2641`, `78:2489` |
| 24 | Tabs 24 instance 126x24, step-number chips "Frame 101" 24x24, lucide/check 24x24 | 0/8/4/3 | `78:1995`, `78:2632`, `78:1868` |
| 16 | icon wrappers "Frame 11" 16x16, toggle 32x16 (`I78:1955;21:58`), lucide/building 16x16, lucide/circle-user-round 16x16 | 1/8/1/2 | `I78:2510;18:308`, `78:2001`, `78:2050` |
| 12 | lucide/circle-exclamation 12x12 | 2/0/0/0 | `78:2537`, `78:2560` |
| 40 | step circle wrapper "Frame 11" 40x40 (check circles) | 0/7/7/0 | `78:1846`, `78:2320` |
| 68 | step rows "Frame 22"/"Frame 54/53" | 0/8/8/0 | `78:1837`, `78:1844`, `78:2311` |
| 50 | row card 254x50 (hug vertical, not fixed) | — | `78:1778` |
Component sizes (components page): Select `10:170` 110x32, Search `73:1680` 120x32, Input `73:1679` 120x32, Tabs 32 `21:384` 158x32, Tabs 24 `21:401` 128x24, Outline Button variants 87x32, set sizes 127x138 / 127x124 / 137x124, toggle sets 72x92 / 122x92 (instances in screens are wider/fill; instance size taken from the instance: Select 148x32, Search 624x32, Input 624/193/415x32, CTA 134/154/154/175x32, Outline+icon 142x32, Tabs 24 126x24, toggle w text 183x16).

### 4.4 Icon sizes
| Size | Role | Count (P/Own/Ov/W) | Node ids |
|---|---|---|---|
| 12x12 | lucide/circle-exclamation (warning), info Union 12.01x12.01, Vector 12x12 | 2/many/0/0 | `78:2537`, `78:2002`, `78:2051` |
| 16x16 | lucide/building, lucide/circle-user-round, Frame 11 icon wrapper, search icon wrapper | 1/8/4/2 | `78:2001`, `78:2050`, `I78:2635;73:1665` |
| 12x6 / 6x3 | Select chevron (arrow-down vectors) | 1/1/1/1 | `I78:2510;18:310`, `I78:2510;18:311` |
| 24x24 | lucide/check (steps), step chips | 0/8/4/3 | `78:1868` |
| 40x40 | step circles | 0/7/7/0 | `78:1846` |
| 70x20 logo | logo Union (85x20 group with 3 lines) | 1/1/1/1 | `78:2490` group, `78:2491` |
| 6x6 / 11x11 | status dots / search ellipse | 34+21+4 / 1 | `78:2583`, `I78:2635;78:1708` |

---

## 5. Shell geometry
All screens: root 1920 wide, fill #08090A, clipsContent true, absolute-positioned children (layoutMode NONE). Constraints (read from node data): header "Frame 8" = MIN/MIN (`cMM`); Pipeline and Wallet content frames = CENTER/MIN (`cCM`); Runs content frames not recorded.

### 5.1 Screen frames
| Screen | Id | Size | x on page | Content frame | Content geometry (x,y,w,h in screen) |
|---|---|---|---|---|---|
| Pipeline | `78:2486` | 1920x1080 | 0 | `78:2511` "Frame 85" V auto-layout g24, constraint CENTER/MIN | 639,106, 642x718 (centred horizontally: (1920-642)/2 = 639; top = 66 header + 40) |
| Runs / Ownership | `78:1751` | 1920x1293 | 2000 | `78:1775` "Frame 62" H g16 HUG/HUG | 210,90, 1500x1161 (centred: (1920-1500)/2 = 210; top = 66+24; bottom gap 1293-90-1161 = 42) |
| Runs / Overview | `78:2225` | 1920x1293 | 4000 | `78:2249` "Frame 62" H g16 HUG/HUG | 210,90, 1500x1068 (bottom gap 1293-90-1068 = 135, frame taller than content) |
| Wallet Check | `78:2600` | 1920x1080 | 6000 | `78:2624` "Frame 107" H g38 HUG/HUG, constraint CENTER/MIN | 468,106, 984x403 (centred: (1920-984)/2 = 468; top 66+40) |

### 5.2 Header ("Frame 8", every screen)
| Property | Value | Node id(s) |
|---|---|---|
| Size / position | 1920x66 at 0,0 | `78:2488`, `78:1752`, `78:2226`, `78:2601` |
| Auto-layout | HORIZONTAL, itemSpacing 108 (overridden by SPACE_BETWEEN), padding T16 R40 B16 L40, primary align SPACE_BETWEEN, counter align CENTER, sizing FIXED horiz x HUG vert | same |
| Fill | none (transparent; screen #08090A shows) | same |
| Border | bottom only 1px INSIDE #111213 (style "Grey 500"), strokesIncludedInLayout true: height 66 = 16 + 33 (nav content) + 16 + 1 | same |
| Children (x,y,w,h) | logo box "Frame 7" 40,16.5 162x32 (V g10, centre); nav "Frame 1" 645.5,16 643x33 (H g0, centre); Select instance 1732,16.5 148x32 (H g32, p8/12/8/12; Own/Ov/W identical) | `78:2489`, `78:2499`, `78:2510` (P); `78:1753`..; `78:2227`..; `78:2602`.. |
| Nav items | 5 pills "Frame 3..6/1": Pipeline, Runs, Wallet check, System health, Admin Dashboard. P screen widths 109(active, 33h)/93/135/144/162 at x 0/109/202/337/481; each H auto-layout, padding 8/32/8/32, align centre, HUG x HUG, radius 24 inactive / 8 active with gradient 0.5px INSIDE stroke | `78:2500`..`78:2508` (P) |
| Logo | Group 1 85x20 at 0,6 inside box: Union 70x20 at 15,6 (gradient fill) + 3 lines 20x0 at x 10/5/0 (Blue 75/50/25 strokes w1.5) + wordmark vectors (#4DFFCD) | `78:2490`,`78:2491`,`78:2496`..`78:2498`, `78:2492`.. |

Active nav item per screen: Pipeline -> "Pipeline" (`78:2500`, stroke Gradient main oposite); Ownership/Overview -> "Runs" (`78:1766` / `78:2240`, stroke Gradient main); Wallet -> "Wallet check" (`78:2617`, stroke Gradient main oposite). Overview and Ownership use the SAME style name (Gradient main) for the active nav stroke, whereas Pipeline and Wallet use "Gradient main oposite": inconsistency in the design (see 7).

### 5.3 Pipeline content column (`78:2511`, 642x718, V g24, no padding)
- `78:2512` greeting row 642x32 (H, space-between): heading T `78:2513` "Good afternoon, Alex. One run…" 508x22 (Manrope Medium 16, #DCE1E9) + CTA Button instance `78:2514` 134x32 at x508.
- `78:2515` KPI row 642x106 at y56 (H g24): four KPI cards 142.5x106 at x 0 / 166.5 / 333 / 499.5 (V g16, padding 24, fill #08090A, stroke #1C1E1F 1 INSIDE, radius 16): numeral Jura Medium 38 + label Manrope Regular 12 (#62666D): `78:2516`,`78:2519`,`78:2522`,`78:2525`.
- `78:2528` "Frame 58" 642x312 at y186 (V g16, padding 16, stroke #1C1E1F, radius 16, no fill): two sections ("Needs you (1)" / "With the team (1)") each 608x131 (V g8): caption + row card "Frame 56" 608x107 (H g36 space-between, padding 12/16, fill #111213, stroke #1C1E1F, radius 8).
- `78:2575` "Frame 85" 642x196 at y522 (V g16, padding 16, fill #111213, stroke #1C1E1F, radius 16): "Clients loaded in (2)" + two rows 608x57 (H g36, padding 12/16, fill #08090A, radius 8).

### 5.4 Runs screens (Ownership `78:1775` / Overview `78:2249`; both 1500 wide, H g16)
| Region | Id | x,y,w,h (in `Frame 62`) | Details |
|---|---|---|---|
| Left panel "Recent Runs" | `78:1776` / `78:2250` | 0,0, 288x1161 / 288x1068 | V g16, padding 16, stroke #1C1E1F 1 INSIDE, radius 16, no fill; caption "Recent Runs" Medium 12 #62666D; 3 run cards 254x50 (`78:1778` active: stroke Gradient main 1px; `78:1783`, `78:1788`: stroke #1C1E1F), each H g36 p8/16/8/16 radius 8 fill #111213 |
| Main column | `78:1793` / `78:2267` | 304,0, 1196x1161 / 1196x1068 | V g13 |
| Summary card (bg gradient) | `78:1794` / `78:2268` | 0,0, 1196x307 | V g24, padding 24/32/24/32, fill "bg gradient", stroke #1C1E1F, radius 16; contains steps row `78:1795` (1130x165, H g48, bottom border) and `78:1837` row 1130x68 |
| Lower area | `78:1888` / `78:2362` | 0,320, 1196x841 / 1196x748 | H g1: sidebar filter list `78:1889` / `78:2363` 218x501 (V g4, padding R16) + card `78:1950` 977x841 (V g8, padding 16, fill bg gradient, stroke #1C1E1F, radius 16) in Ownership; in Overview `78:2424` 977x748 (V g16) holds `78:2425` 977x260 and `78:2435` 977x472 (bg gradient cards) |

### 5.5 Wallet content (`78:2624`, 984x403, H g38)
- Left form column `78:2625` 658x403 (V g24): header `78:2626` 658x49 (V g8: heading Manrope Medium 16 #DCE1E9 + sub Manrope Medium 14 #62666D) and form card `78:2629` 658x330 (V g24, padding 16, fill #111213, stroke #1C1E1F, radius 16) with field groups `78:2630`/`78:2636`/`78:2642` 624x64 (V g8; label rows with numeral chips 24x24 #1C1E1F) and action row `78:2650` 624x32.
- Right panel `78:2652` 288x403 at x696 (V g16, padding 16, stroke #1C1E1F, radius 16; "Recently Added" + two cards 254x50, radius 8, fill #111213).

---

## 6. Inventory

### 6.1 Canonical frames — direct children and top-level contents
| Id | Name | Type | Size | Position (in parent) | Hidden? | Current/obsolete |
|---|---|---|---|---|---|---|
| `78:2486` | Pipeline | FRAME | 1920x1080 | page x0,y0 | no | current (canonical) |
| `78:2487` | unsplash:jZRGh3IuVb8 | RECTANGLE | 2165x2706 (rotation 90) | 1991,2165 | no | present but off-canvas (see 6.2) |
| `78:2488` | Frame 8 (header) | FRAME | 1920x66 | 0,0 | no | current |
| `78:2511` | Frame 85 (content) | FRAME | 642x718 | 639,106 | no | current |
| `78:1751` | Runs / Ownership | FRAME | 1920x1293 | page x2000,y0 | no | current |
| `78:1752` | Frame 8 (header) | FRAME | 1920x66 | 0,0 | no | current |
| `78:1775` | Frame 62 (content) | FRAME | 1500x1161 | 210,90 | no | current |
| `78:2225` | Runs / Overview | FRAME | 1920x1293 | page x4000,y0 | no | current |
| `78:2226` | Frame 8 (header) | FRAME | 1920x66 | 0,0 | no | current |
| `78:2249` | Frame 62 (content) | FRAME | 1500x1068 | 210,90 | no | current |
| `78:2600` | Wallet Check | FRAME | 1920x1080 | page x6000,y0 | no | current |
| `78:2601` | Frame 8 (header) | FRAME | 1920x66 | 0,0 | no | current |
| `78:2624` | Frame 107 (content) | FRAME | 984x403 | 468,106 | no | current |

### 6.2 Pipeline background photo `78:2487`
RECTANGLE named "unsplash:jZRGh3IuVb8", 2165x2706, rotation 90.0000025 deg, position (1991, 2165) inside the 1920x1080 clipped frame; rotating about the top-left puts its bounding box at roughly x -715..1991, y 2165..4330 — wholly below the 1080px frame bottom, so it is clipped away: the photo does NOT appear on the canvas (computed from node data; confirm visually if needed). Image fill: scaleMode FILL, paint opacity 0.2, filters all 0, node opacity 1, no effects. The same image fill exists on the draft Pipeline copy (`39:143`). Do not export unless the owner asks (see 7).

### 6.3 Drafts page `3:10845` (14 children)
| Id | Name | Type | Size | Position (page) | Kids | Hidden | Judgement |
|---|---|---|---|---|---|---|---|
| `22:2621` | Pipeline | FRAME | 1920x1080 | -145,0 | 3 | no | alternate of `78:2486`; 119 nodes, 0 diffs vs final (see 0) |
| `4:15408` | Runs / Ownership | FRAME | 1920x1293 | 1855,0 | 2 | no | alternate of `78:1751`; 489 nodes, 0 diffs |
| `63:712` | Runs / Overview | FRAME | 1920x1293 | 3855,0 | 2 | no | alternate of `78:2225`; 268 nodes, 0 diffs |
| `73:1531` | Wallet Check | FRAME | 1920x1080 | 5938,0 | 2 | no | alternate of `78:2600`; 74 nodes, 0 diffs |
| `10:170` | Select | COMPONENT | 110x32 | 3021,-253 | 2 | no | component definition (canonical for components) |
| `73:1680` | Search | COMPONENT | 120x32 | 3178,-253 | 2 | no | component definition |
| `73:1679` | Input | COMPONENT | 120x32 | 3345,-253 | 1 | no | component definition |
| `18:242` | Outline Button | COMPONENT_SET | 127x138 | 2107,-262 | 2 | no | component set (Default `18:227` + hover `18:253`) |
| `18:248` | CTA Button | COMPONENT_SET | 127x124 | 1930,-267 | 2 | no | component set |
| `21:384` | Tabs 32 | COMPONENT | 158x32 | 2687,-253 | 2 | no | component definition |
| `21:401` | Tabs 24 | COMPONENT | 128x24 | 2687,-185 | 2 | no | component definition |
| `18:290` | Outline Button + icon | COMPONENT_SET | 137x124 | 2254,-265 | 2 | no | component set |
| `21:32` | toggle | COMPONENT_SET | 72x92 | 2411,-267 | 2 | no | component set |
| `21:55` | toggle w text | COMPONENT_SET | 122x92 | 2509,-267 | 2 | no | component set |
Component/screens coexist at overlapping canvas coordinates only because of the canvas layout (components lie at y -253..-124 above the screens).

Final vs drafts per-frame tallies (fills, text colours, strokes, fonts, radii, effects, opacity): equal in every row for all four pairs (examples: both Ownership frames have Manrope Regular 8 x34, Medium 8 x19, #F3AB52 text x29, #59BCFA@0.15 fills x19, DROP_SHADOW x1). Drafts Ownership/Overview/Pipeline/Wallet nodes have ids from different prefixes only.

### 6.4 Skipped pages
`0:1` "old echo" (5 children; owner: ignore), `2:600` "styling examples" (2 children; owner: ignore).

---

## 7. Conflicts and decisions needed
| Topic | Option A (node ids, value) | Option B (node ids, value) | Chosen / recommendation | Needs owner? |
|---|---|---|---|---|
| Paint style named "White" | value #DCE1E9 (`S:78b04715…`), used for all primary text and CTA fill | pure #FFFFFF does not occur anywhere | Use #DCE1E9 as-is; keep the design name "White" in the `figma` group, add a role alias `--color-text-primary` | no (note name/value mismatch) |
| Active nav stroke gradient direction | P and W: "Gradient main oposite" #53B2ED->#7BE697 (`78:2500`, `78:2617`) | Own and Ov: "Gradient main" #7BE697->#53B2ED (`78:1766`, `78:2240`) | Same transform; direction differs by screen. Record both; recommend one component (Tabs/active nav) with the "oposite" direction as canonical default since logo and Tabs active fills (components page `21:379`) use it | yes |
| Nav label weight | "Runs" Medium 12 on all screens (`78:2503`,`78:1767`,`78:2241`,`78:2616`) | other nav labels Regular 12 incl. active "Pipeline" (`78:2501`) and "Wallet check" (`78:2618`) | Reproduce as drawn; flag as inconsistency (active state is not drawn through weight) | yes |
| Active nav pill height | 33px (0.5 stroke counted in layout, `78:2500`: 109x33 / `78:2617` 136x33) vs 32px inactive | — | Reproduce 32 + 0.5px inset stroke -> 33 | no |
| Raw ring-arc gradients | `78:2551`,`78:2574`,`78:1802`,`78:2276`: raw #53B2ED->#7BE697 with ring-specific transforms | style "Gradient main oposite" (`78:2491`) with the common transform | Create `raw` tokens named by role ("ring-arc gradient"), keep the node transforms | no |
| Raw #4DFFCD | logo wordmark glyphs, no style | — | Token group `raw`, role "logo wordmark" | no |
| Raw gradient #54B3E9->#F3892D | Line 12 stroke (`78:1840`, `78:2314`) | — | `raw` token | no |
| Stray variable | `VariableID:1:129` "corner radius/22369600" bound to logo radii | no design token needed | Ignore (import debris) | no |
| Background photo | `78:2487` off-canvas, paint op 0.2 | — | Do not render/export; owner to confirm photo is unwanted | yes |
| Hover recipe for Outline Button | 3-stop gradient stroke #53B2ED->#4CCED4->#45EABB (`18:253`) | 2-stop brand gradient elsewhere | Use drawn 3-stop for that variant only | no |
| Non-standard heights | Ownership content bottom gap 42 vs Overview 135 | — | Screen heights are fixed frame heights (1293), not hug | no |

---

## 8. GAPS / NOT FOUND IN THE DESIGN (searched; absent as designed states)
| Area | Finding | How searched | Scope searched |
|---|---|---|---|
| Variables / tokens | 0 collections; only one stray bound variable (radius) | `getLocalVariableCollectionsAsync`, `boundVariables` tally in all fingerprints | file + 4 finals + 4 drafts screens + 10 components |
| Text styles / effect styles / grid styles | 0 / 0 / 0; no `textStyleId`/`effectStyleId` on any node | `getLocalTextStylesAsync` / `getLocalEffectStylesAsync` / `getLocalGridStylesAsync`; fingerprint style tallies | file; finals |
| Remote (library) styles | none | style-id resolution by `getStyleByIdAsync` flagged "(remote)" | finals |
| Spacing tokens | none; spacing only as observed values (section 4) | variables search; auto-layout tally | finals |
| Backdrop blur / layer blur / glass | none | effects scan for `LAYER_BLUR`/`BACKGROUND_BLUR` over all nodes | 4 finals |
| Box shadows on cards/panels | none (only drop shadow on 4 gradient ring arcs) | effects tally | 4 finals + components |
| Scrim / modal overlay / dark overlay layer | none | node names and fills (no node with >=0.3 alpha black full-frame fill) | 4 finals (by fill tally) |
| Hover / focus / active / disabled / error colours | only Outline Button hover (`18:253`) and CTA hover overlay (`18:249`) exist; no focus/active/disabled/error colours in the palette other than Red for text | component variant names (`Property 1=Default/hover`), colours on components | 10 component roots |
| Monospace font | none | `fontName` family tally over finals + components | 4 finals + 10 components |
| Text style variants (bold, italic, uppercase, underline, letter-spacing) | none: letter-spacing 0%, case ORIGINAL, decoration NONE everywhere | fingerprint `fontTuples` | 4 finals + 4 drafts + 10 components |
| Responsive / breakpoints | only 1920 wide screens; no other widths | frame size survey | both pages |
| Not harvested / partial | (a) final-vs-drafts diff did not compare gradient transforms, bound variables, image hashes or effects (tallies equal); (b) "old echo" and "styling examples" skipped by owner decision; (c) `get_variable_defs` not used by rule; (d) per-node component internals (variant props) left to the components harvester; (e) top-40 limit per fingerprint table was not hit for fills/fonts (all rows shown), strokes rows complete; (f) visual confirmation of the off-canvas photo was not taken (computed from node data); (g) no rate-limit incidents occurred | — | — |
