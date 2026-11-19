# echo — Components (harvested from design file `<figma-file-key>`)

Scope: component definitions on page "drafts" (`3:10845`) (the ONLY place definitions exist) + usage in the canonical frames of page "final " (`78:1750`, trailing space): `78:2486` Pipeline, `78:1751` Runs / Ownership, `78:2225` Runs / Overview, `78:2600` Wallet Check. Harvested 2026-11-16 by `figma-harvester` (components), read-only via the Plugin API (custom compact versions of `figma-inventory.js` LIST_COMPONENTS and `figma-dump-subtree.js` logic, plus an instance scan and keyword scans; nothing written to Figma).
Owner decisions applied (from `_intake.md`): (1) "Final screens + drafts components": screens from `final`, components/variants from `drafts`; (2) pages `old echo` (`0:1`) and `styling examples` (`2:600`) ignored (only a component/instance COUNT was taken to prove they hold no definitions: 0 and 0); (3) source = Figma.

Legend: `id` = Figma node id. Style names are paint-style names from foundations.md section 1.1 (quoted verbatim, "White" = #DCE1E9). `sil` = `strokesIncludedInLayout` (true on every control: padding + stroke weight both count, so a 1px INSIDE stroke + padding 8/12 puts the text at x=13/y=9; CSS: `border:1px` + same padding, border-box). Sizing is given as horizontal/vertical: HUG, FIXED, FILL. `T` = text node. Counts = visible nodes; "instances" counted as outermost INSTANCE nodes in the 4 finals. No component has a description (`description` empty on all 5 sets and 5 components). All variant property names are the unrenamed Figma default `Property 1`.

---

## 0. Scope and provenance
| Item | Value |
|---|---|
| Canonical node(s) | Definitions (page `3:10845`): 5 COMPONENT_SETs `18:242`, `18:248`, `18:290`, `21:32`, `21:55` (10 variant COMPONENTs inside) + 5 standalone COMPONENTs `10:170`, `73:1680`, `73:1679`, `21:384`, `21:401`. 15 COMPONENT nodes total (`findAllWithCriteria`), 5 sets. Usage: 4 canonical frames above. |
| Alternates seen | Drafts screen copies `22:2621`, `4:15408`, `63:712`, `73:1531` (not re-examined here; foundations found 0 diffs vs finals). The drafts copies contain their own instances; instance census below is for the finals only. Final wins (owner decision 1). |
| Hidden nodes in scope | 0 (every dumped component node is visible). |
| Extraction scripts used | inventory (sets+components, variant names/ids/sizes) on `3:10845`; dump (depth 5, adds `strokesIncludedInLayout`, constraints, truncation, text align H/V, resolved style names) of all 10 definition roots; instance scan of the 4 finals (outermost INSTANCE + `getMainComponentAsync` + text overrides + layout); compact dumps (depth 1-3) of pattern nodes; keyword and type scans of the 4 finals; instance/component count of `0:1` and `2:600`. |
| Not covered by this file | Palette / type tables (foundations.md); icon SVGs (assets); per-screen structure (screens specs). `componentPropertyDefinitions` was not read (variant-owner rule); the only property is the default `Property 1` variant axis visible from variant names. |

---

## 1. Definition inventory
| Id | Name | Type | Size | Variants (name, id, size) | Description | Instantiated in finals? |
|---|---|---|---|---|---|---|
| `10:170` | Select | COMPONENT | 110x32 (was 104x32 at Regular 10) | none | none | YES, 4 (header, every screen) |
| `73:1680` | Search | COMPONENT | 120x32 | none | none | YES, 1 (Wallet `78:2635`) |
| `73:1679` | Input | COMPONENT | 120x32 | none | none | YES, 3 (Wallet `78:2641`, `78:2648`, `78:2649`) |
| `18:242` | Outline Button | COMPONENT_SET (127x138, at 2107,-262) | 87x32 each | `Property 1=Default` `18:227` 87x32; `Property 1=hover` `18:253` 87x32 | none | NO (0 instances; the Outline Button + icon set is used instead) |
| `18:248` | CTA Button | COMPONENT_SET (127x124) | 87x32 each | `Property 1=Default` `18:142` 87x32; `Property 1=hover` `18:249` 87x32 | none | YES, 4 (Default only) |
| `18:290` | Outline Button + icon | COMPONENT_SET (137x124) | 97x32 each | `Property 1=Default` `18:289` 97x32; `Property 1=Variant2` `18:291` 97x32 | none | YES, 2 (Default only) |
| `21:384` | Tabs 32 | COMPONENT | 158x32 | none | none | NO (0 instances) |
| `21:401` | Tabs 24 | COMPONENT | 128x24 | none | none | YES, 1 (`78:1995`) |
| `21:32` | toggle | COMPONENT_SET (72x92) | 32x16 each | `Property 1=Default` `21:31` (ON); `Property 1=off` `21:33` (OFF) | none | NO (0 instances; toggle w text is used) |
| `21:55` | toggle w text | COMPONENT_SET (122x92) | 82x16 / 86x16 | `Property 1=Default` `21:54` 82x16 (ON); `Property 1=off` `21:56` 86x16 (OFF) | none | YES, 1 (`78:1955`, variant `off`) |

Totals: 5 sets, 10 set-variants, 5 standalone components (15 COMPONENT nodes). 16 outermost instances in the 4 finals (Select 4, CTA Button 4, Outline Button + icon 2, toggle w text 1, Tabs 24 1, Search 1, Input 3; the node-type census of the finals shows exactly 16 INSTANCE nodes in total, so there are no nested/other instances). No instance has a remote (library) main component: all mains are the drafts-page nodes above.
Set frames `18:242`, `18:248`, `18:290` carry a raw `#8A38F5` dashed stroke (dash 10,5, w1, INSIDE, radius 5, clip) and `21:32`, `21:55` `#9747FF`: Figma's default set outline, not design values (ignore).
Never instantiated in the finals: Outline Button (`18:242`), Tabs 32 (`21:384`), toggle (`21:32`), and every `hover` / `Variant2` / `Default`(ON) state of the toggles. Those exist only on the definitions page.

---

## 2. Shared control geometry (stated once)
| Property | Value | Source ids |
|---|---|---|
| Control height | **32** for Select, Search, Input, CTA Button, Outline Button, Outline Button + icon, Tabs 32 (inner tab 32). Tabs 24: 24. | `10:170`, `73:1680`, `73:1679`, `18:142`, `18:227`, `18:289`, `21:384`, `21:401` |
| Corner radius | **8** on every control and on tab frames inside tracks (track and tabs both 8). Toggle track 24 (fully round at 32x16). | all component roots; toggle `21:28`, `21:34` r24 |
| Field family (Select, Search, Input) | fill #111213 "Grey 500"; stroke #1C1E1F "Grey 400" 1 INSIDE all sides; sil true; text Manrope Regular 12 (re-read 2026-11-16, owner changed 10→12; Select 110 wide, text boxes 16 high), lh auto, ls 0%, case ORIGINAL, colour #62666D "Grey 300" (placeholder look) | `10:170`, `73:1680`, `73:1679` |
| Field padding / gap | Select 8/12/8/12 gap 32; Input 8/12/8/12 gap 8; Search 8/8/8/8 gap 8 (icon first, text second). Text box 14 high, text x=13 (12+1 stroke), y=9 (8+1) | `10:170`, `73:1679`, `73:1680` |
| Button family (CTA, Outline, Outline + icon) | label Manrope Medium 12, lh auto, ls 0%, ORIGINAL; text box 16 high; padding 8/24/8/24, gap 10 (CTA, Outline); 8/20/8/16 gap 12 (Outline + icon); main/cross alignment CENTER/CENTER; HUG x HUG | `18:142`, `18:227`, `18:289` |
| Button strokes | CTA: no stroke. Outline family: 1 CENTER stroke (sil true but the 1px CENTER stroke does not change the 32 height or the padding positions: text at x=24, y=8). CSS: treat as inside (`box-shadow: inset 0 0 0 1px`) per BUILD_RULES section 2 | `18:227`, `18:289` |
| Tabs | track fill #1C1E1F "Grey 400", radius 8, no stroke, padding 0, gap 0, HUG; each tab = frame radius 8, padding 8/20 (Tabs 32) or 8/16 (Tabs 24), gap 10, label Manrope Medium (12 / 10) | `21:384`, `21:401` |
| Focus / hover / disabled / error | NOT drawn for fields, tabs or toggles (see section 9, GAPS) | — |

Field widths are NOT part of the definition (instances override): Select hugs text, Search/Input default 120 FIXED and are stretched to FILL in screens.

---

## 3. Component specs

### 3.1 Select — `10:170` (COMPONENT, 110x32, sizing HUG/FIXED, constraints MIN/MIN)
| Part | Id | Value |
|---|---|---|
| Root | `10:170` | HORIZONTAL auto-layout, gap 32, padding T8 R12 B8 L12, main CENTER, cross CENTER, sizing HUG x FIXED(32); fill #111213 (style "Grey 500"); stroke #1C1E1F (style "Grey 400") 1 INSIDE all sides; radius 8; sil true; no effects; no clip |
| Label T "Select" | `9:137` | 30x14 at 13,9; Manrope Regular 12 (was Regular 10; now 36x16 at 13,8); lh auto; ls 0%; ORIGINAL; align CENTER/CENTER; fill #62666D (style "Grey 300"); HUG x HUG, textAutoResize WIDTH_AND_HEIGHT |
| Chevron box "Frame 11" | `18:308` | 16x16 at 75,8 (FIXED x FIXED); no fill; no stroke; no clip |
| Chevron big "arrow-down" VECTOR | `18:310` | 12x6 at 3,6 (in box); stroke gradient #7BE697@0 -> #53B2ED@1 (style "Gradient main"), w1, CENTER, cap ROUND, join ROUND, radius 0.5; no fill |
| Chevron small "arrow-down" VECTOR | `18:311` | 6x3 at 6,6; same stroke (style "Gradient main"); node opacity 0.5 |
Width arithmetic: 13 + label 30 + gap 32 + chevron 16 + 13 = 104 (hug). In screens the label is overridden to "Local Developer" (74 wide) and its fill to #DCE1E9 "White": instance width 148 (13+74+32+16+13).
Variants/states: none.

### 3.2 Search — `73:1680` (COMPONENT, 120x32, FIXED/FIXED)
| Part | Id | Value |
|---|---|---|
| Root | `73:1680` | HORIZONTAL, gap 8, padding 8/8/8/8, main MIN, cross CENTER; sizing FIXED x FIXED (120x32); fill #111213 "Grey 500"; stroke #1C1E1F "Grey 400" 1 INSIDE; radius 8; sil true |
| Icon box "Frame 11" | `73:1665` | 16x16 at 9,8 |
| Lens VECTOR | `73:1672` | 12x12 at 2,3 (in box); gradient stroke #7BE697 -> #53B2ED (style "Gradient main") w1 CENTER, round cap/join, radius 0.5; constraints CENTER/MAX |
| Lens tint ELLIPSE "Ellipse 9" | `78:1708` | 11x11 at 2,3; fill #59BCFA@0.15 (style "Blue 15%") |
| Placeholder T "Search" | `73:1664` | 33x14 at 33,9; Manrope Regular 12 (was Regular 10; now 39x16 at 33,8) lh auto ls 0% align CENTER/CENTER; fill #62666D "Grey 300"; HUG x HUG |
Icon is on the LEFT (x=9). (Foundations 4.2 describes padding "8/32/8/8 (Search, icon at right)": that is the Wallet INSTANCE's padding override, R=32; the icon is not at the right in node data.)

### 3.3 Input — `73:1679` (COMPONENT, 120x32, FIXED/FIXED)
Root: HORIZONTAL, gap 8, padding 8/12/8/12, main MIN, cross CENTER; fill #111213 "Grey 500"; stroke #1C1E1F "Grey 400" 1 INSIDE; radius 8; sil true. One child: T "Type here" `73:1678` 46x14 at 13,9; Manrope Regular 12 (was Regular 10; now 55x16 at 13,8); lh auto; ls 0%; align CENTER/CENTER; fill #62666D "Grey 300"; HUG x HUG.
Variants/states: none (no filled/value state, no label, no error).

### 3.4 CTA Button — set `18:248` (127x124)
| Property | Default `18:142` | hover `18:249` |
|---|---|---|
| Size / sizing | 87x32, HUG x HUG | 87x32, HUG x HUG |
| Layout | H, gap 10, pad 8/24/8/24, main/cross CENTER; sil true; radius 8; no stroke | identical |
| Fill | #DCE1E9 (style "White") | gradient LINEAR #53B2ED@0 -> #7BE697@1 (alpha 1) (style "Gradient main oposite"); transform per foundations 1.6 |
| Label T "Button" | `10:169` 39x16 at 24,8; Manrope Medium 12; fill #08090A (style "Black 900"); HUG x HUG; align CENTER/CENTER | `18:250` identical geometry; fill #08090A (style "Black 900") (unchanged) |
Only the fill changes between Default and hover. Label is `Button` in both; instances override the text (see section 6).

### 3.5 Outline Button — set `18:242` (127x138)
| Property | Default `18:227` | hover `18:253` |
|---|---|---|
| Size / sizing | 87x32, HUG x HUG | 87x32, HUG x HUG |
| Layout | H, gap 10, pad 8/24/8/24, CENTER/CENTER; sil true; radius 8 | identical |
| Fill | none | none |
| Stroke | #8A8F98 (style "Grey 200") w1 CENTER | gradient LINEAR 3 stops #53B2ED@0, #4CCED4@0.5, #45EABB@1 (all alpha 1), w1 CENTER, NO style bound (raw) |
| Label T | `18:226` Manrope Medium 12, 39x16 at 24,8; fill #8A8F98 (style "Grey 200") | `18:254` same geometry; fill gradient #53B2ED@0 -> #7BE697@1 (style "Gradient main oposite") |
No instance of this set in the finals.

### 3.6 Outline Button + icon — set `18:290` (137x124)
| Property | Default `18:289` | `Variant2` `18:291` |
|---|---|---|
| Size / sizing | 97x32, HUG x HUG | 97x32, HUG x HUG |
| Layout | H, gap 12, pad T8 R20 B8 L16, CENTER/CENTER; sil true; radius 8 | identical |
| Fill | none | none |
| Stroke | #8A8F98 (style "Grey 200") w1 CENTER | gradient #53B2ED@0 -> #7BE697@1 (style "Gradient main oposite") w1 CENTER |
| Icon VECTOR (first child) | `18:287` 10x12 at 16,10; stroke #8A8F98 (style "Grey 200") w1 CENTER, cap/join ROUND; no fill; no radius | `18:292` same geometry; stroke gradient #53B2ED -> #7BE697 (style "Gradient main oposite") |
| Label T "Button" | `18:282` 39x16 at 38,8; Manrope Medium 12; fill #8A8F98 "Grey 200" | `18:293` same; fill gradient #53B2ED -> #7BE697 (style "Gradient main oposite") |
Icon vector name is "Vector"; it is a 10x12 outline glyph drawn directly in the component (not an icon instance; assets harvester covers its shape). Variant2 is the hover look (same recipe as Outline Button hover except 2-stop stroke) but is NOT named "hover".
Instance in screens: stroke weight/colour live on the instance (`78:1807` stroke #8A8F98 w1 CENTER, style "Grey 200"), no fill.

### 3.7 Tabs 32 — `21:384` (COMPONENT, 158x32, HUG x HUG)
| Part | Id | Value |
|---|---|---|
| Track (root) | `21:384` | H, gap 0, padding 0, main MIN, cross CENTER; fill #1C1E1F (style "Grey 400"); radius 8; no stroke; sil true |
| Tab 1 = ACTIVE "Button" FRAME | `21:379` | 79x32 at 0,0; H, gap 10, pad 8/20/8/20, CENTER/CENTER; HUG x HUG; radius 8; fill gradient #53B2ED@0 -> #7BE697@1 (style "Gradient main oposite") |
| Tab 1 label T | `21:380` | 39x16 at 20,8; Manrope Medium 12; fill #08090A "Black 900" |
| Tab 2 = INACTIVE "Button" FRAME | `21:381` | 79x32 at 79,0; same layout; radius 8; NO fill |
| Tab 2 label T | `21:382` | 39x16 at 20,8; Manrope Medium 12; fill #62666D "Grey 300" |
Selection is expressed only by which tab frame carries the gradient fill (hard-coded: first = active). There is no variant/property for the selected state, no hover, no per-tab states. Width arithmetic: 20+39+20 = 79 each.

### 3.6b Tabs 24 — `21:401` (COMPONENT, 128x24, HUG x FIXED)
Same structure with: track `21:401` fill #1C1E1F "Grey 400", radius 8, FIXED height 24; active tab `21:397` 64x24 (pad 8/16/8/16, gap 10, HUG x FILL, radius 8, gradient fill "Gradient main oposite"), label `21:398` Manrope Medium **10** 32x14 at 16,5, fill #08090A "Black 900"; inactive tab `21:399` 64x24 at 64,0, no fill, label `21:400` Manrope Medium 10, fill #62666D "Grey 300". Note padding top/bottom 8 would not fit 14px text in 24px (8+14+8 = 30): the tab height is FILL = 24 and the label is vertically centred (text at y=5). Reproduce as `height:24; padding:0 16px; align-items:center`.

### 3.8 toggle — set `21:32` (72x92); toggle w text — set `21:55` (122x92)
| Property | toggle Default (ON) `21:31` | toggle off `21:33` |
|---|---|---|
| Size / sizing | 32x16 FIXED x FIXED, no auto-layout (absolute children, constraints SCALE) | same |
| Track RECTANGLE "Rectangle 1" | `21:28` 32x16 at 0,0; radius 24; fill gradient #5DE7CB@0 -> #66D74A@1 (style "Gradient green") | `21:34`; radius 24; fill #62666D (style "Grey 300") |
| Knob ELLIPSE "Ellipse 8" | `21:30` 12x12 at 18,2; fill #111213 (style "Grey 500") | `21:35` 12x12 at 2,2; fill #111213 (style "Grey 500") |
So ON: knob at right (x 18 = 32-2-12); OFF: knob at left (x 2). Variant NAMED "Default" is the ON state; "off" is OFF.

| Property | toggle w text Default (ON) `21:54` | off `21:56` |
|---|---|---|
| Size / layout | 82x16, H, gap 6, padding 0, main MIN, cross CENTER, HUG x HUG, sil true | 86x16, same |
| toggle FRAME | `21:42` 32x16 FIXED, contains `21:43` track (gradient "Gradient green", r24) + `21:44` knob 12x12 at 18,2 (#111213) | `21:58` contains `21:59` track (#62666D "Grey 300", r24) + `21:60` knob at 2,2 |
| Label T | `21:53` "Text ON" 44x16 at 38,0; Manrope Medium 12; lh auto; ls 0%; align LEFT/CENTER; fill #DCE1E9 (style "White") | `21:57` "Text OFF" 48x16; same type; fill #8A8F98 (style "Grey 200") |
The ON label is lighter/brighter (White) than the OFF label (Grey 200): label colour is part of the state.
Instance `78:1955` (Ownership): variant OFF, label overridden to "Show Confidential Details" (145x16), instance 183x16: 32 + 6 + 145.

---

## 4. State diff summary (what exists)
| Component | Default | hover | focus | pressed/active | disabled | error | selected/on |
|---|---|---|---|---|---|---|---|
| Select | yes | NO | NO | NO | NO | NO | n/a |
| Search | yes | NO | NO | NO | NO | NO | n/a |
| Input | yes | NO | NO | NO | NO | NO | n/a |
| CTA Button | yes (`18:142`) | YES `18:249` (fill -> gradient) | NO | NO | NO | n/a | n/a |
| Outline Button | yes (`18:227`) | YES `18:253` (stroke 3-stop gradient, text gradient) | NO | NO | NO | n/a | n/a |
| Outline Button + icon | yes (`18:289`) | `Variant2` `18:291` (stroke/icon/text gradient) (named Variant2, not hover) | NO | NO | NO | n/a | n/a |
| Tabs 32 / 24 | one composed state (tab 1 active) | NO | NO | NO | NO | n/a | active tab = gradient fill; no property |
| toggle / toggle w text | ON (`Default`) | NO | NO | NO | NO | n/a | ON/OFF variants |

Property-by-property diffs (only what changes):
| Set | Property | Default | other |
|---|---|---|---|
| CTA | fill | #DCE1E9 "White" | gradient #53B2ED -> #7BE697 "Gradient main oposite" (`18:249`); label unchanged #08090A |
| Outline | stroke | #8A8F98 "Grey 200" | 3-stop #53B2ED/#4CCED4@0.5/#45EABB (raw, `18:253`) |
| Outline | label fill | #8A8F98 "Grey 200" | gradient #53B2ED -> #7BE697 "Gradient main oposite" (`18:254`) |
| Outline + icon | stroke / icon stroke / label fill | #8A8F98 "Grey 200" | gradient #53B2ED -> #7BE697 "Gradient main oposite" (`18:291`, `18:292`, `18:293`) |
| toggle | track fill | "Gradient green" #5DE7CB -> #66D74A (ON) | #62666D "Grey 300" (OFF) |
| toggle | knob x | 18 | 2 |
| toggle w text | label fill / width | #DCE1E9 "White" / 82 | #8A8F98 "Grey 200" / 86 |
Geometry (size, radius, padding, gap, type) is identical across all states of every set.

---

## 5. Usage in screens (16 instances in the 4 finals)
| Frame | Instance id | Component / variant | Rendered size (sizing H/V) | Text override | Other overrides |
|---|---|---|---|---|---|
| Pipeline `78:2486` | `78:2510` | Select | 148x32 (HUG/FIXED) at 1732,16.5 in header `78:2488` | "Local Developer" (`I78:2510;9:137`) | label fill #DCE1E9 "White" (default #62666D) |
| Pipeline | `78:2514` | CTA Button Default | 134x32 (HUG/HUG) at 508,0 in `78:2512` | "Run KYC Check" (`I78:2514;10:169`) | none (#08090A) |
| Ownership `78:1751` | `78:1774` | Select | 148x32 at 1732,16.5 in `78:1752` | "Local Developer" | label fill "White" |
| Ownership | `78:1807` | Outline Button + icon Default | 142x32 (HUG/HUG) at 0,0 in `78:1806` | "Checklist.docx" (`I78:1807;18:282`) | none |
| Ownership | `78:1808` | CTA Button Default | 154x32 at 158,0 in `78:1806` | "Re-Run KYC Check" | none |
| Ownership | `78:1955` | toggle w text `off` | 183x16 (HUG/HUG) at 760,0 in `78:1951` | "Show Confidential Details" (`I78:1955;21:57`, fill #8A8F98) | none |
| Ownership | `78:1995` | Tabs 24 | 126x24 (HUG/FIXED) at 817,0 in `78:1993` | "List" (active, `I78:1995;21:398`, #08090A) / "Org chart" (inactive, `I78:1995;21:400`, #62666D) | none; tab widths 50 + 76 |
| Overview `78:2225` | `78:2248` | Select | 148x32 in header `78:2226` | "Local Developer" | label fill "White" |
| Overview | `78:2281` | Outline Button + icon Default | 142x32 in `78:2280` | "Checklist.docx" | none |
| Overview | `78:2282` | CTA Button Default | 154x32 | "Re-Run KYC Check" | none |
| Wallet `78:2600` | `78:2623` | Select | 148x32 in header `78:2601` | "Local Developer" | label fill "White" |
| Wallet | `78:2635` | Search | 624x32 (FILL/FIXED) at 0,32 in `78:2630` | "Start typing the client's name…" (U+2026, `I78:2635;73:1664`) | padding R=32 (T8 R32 B8 L8 vs component 8/8/8/8); fill/placeholder colour unchanged #62666D |
| Wallet | `78:2641` | Input | 624x32 (FILL/FIXED) at 0,32 in `78:2636` | "Paste the address, e.g. bc1q…, 0x…, T…" (`I78:2641;73:1678`) | none |
| Wallet | `78:2648` | Input | 193x32 (FIXED/FIXED) at 0,0 in `78:2647` | "Label, e.g. Treasury wallet" | none |
| Wallet | `78:2649` | Input | 415x32 (FILL/FIXED) at 209,0 in `78:2647` | "Note for Compliance (optional)" | none |
| Wallet | `78:2651` | CTA Button Default | 175x32 (HUG/HUG) at 449,0 in `78:2650` | "Add Wallet and Screen" | none |

Counts by component: Select 4 (one per screen header, identical), CTA 4, Outline + icon 2, toggle w text 1, Tabs 24 1, Search 1, Input 3. Observations: Select text colour is overridden in 4/4 instances to White (the component default Grey 300 is a placeholder colour; there is no separate "value" state). Search and Input are only drawn as placeholders (Grey 300); no instance shows typed text, focus or error. No instance uses a hover/Variant2 variant. Instance widths: Search/Input are stretched via FILL (624 and 415) or fixed (193); one Input is FIXED 193 inside a row with a FILL sibling (gap 16 in `78:2647`).
Wallet button row: `78:2650` has CTA at x449 right-aligned in 624.

---

## 6. Patterns without a component (spec from real nodes; label "pattern (no component)")
All are plain frames/texts in the finals (no component instance). Values from node data; styles in quotes. "Own"/"Ov" = Ownership/Overview.

### 6.1 Nav item / header nav pill (pattern (no component)) — 5 per screen x 4 screens
Sightings: Pipeline `78:2500`, `78:2502`, `78:2504`, `78:2506`, `78:2508`; Own `78:1764`, `78:1766`, `78:1768`, `78:1770`, `78:1772`; Ov `78:2238`..`78:2246`; Wallet `78:2613`..`78:2621`. Parent nav "Frame 1" (`78:2499`, `78:1763`, `78:2237`, `78:2612`): 643x33, H gap 0, padding 0, main MIN, cross CENTER, HUG/HUG, at x645.5,y16.
Common: H auto-layout, gap 0, padding T8 R32 B8 L32, main/cross CENTER, HUG x HUG. Label T: Manrope 12, lh auto, ls 0%, left-aligned box, fill #DCE1E9 "White".
| State | Fill | Stroke | Radius | Height | Label weight |
|---|---|---|---|---|---|
| Inactive | none | none | 24 | 32 (y 0.5 in the 33 nav) | Regular, except "Runs" Medium on all 4 screens |
| Active | none | 0.5 INSIDE gradient: "Gradient main oposite" (#53B2ED -> #7BE697) on Pipeline `78:2500` and Wallet `78:2617`; "Gradient main" (#7BE697 -> #53B2ED) on Own `78:1766` and Ov `78:2240` | 8 | 33 (stroke counted) | Regular for Pipeline/Wallet check labels; Medium for "Runs" (`78:1767`, `78:2241`) |
Widths (HUG): Pipeline 108 (inactive, 109 when active), Runs 93/94, Wallet check 135/136, System health 144, Admin Dashboard 162.

### 6.2 Status pill / badge family (pattern (no component)) — 74+ nodes (foundations 1.3 census)
Common: H auto-layout gap 10, main/cross CENTER, HUG x HUG, radius 4, height 15 (18 for the one 10px variant). Label Manrope, lh auto, ls 0%, left.
| Kind | Fill | Stroke | Padding T/R/B/L | Label | Sightings (ids) |
|---|---|---|---|---|---|
| Person tag | #59BCFA@0.15 "Blue 15%" | none | 2/4/2/4 | Manrope Medium 8, #59BCFA "Blue", node opacity 0.7 | `78:1974` (56x15, "{PERSON_2}"), `78:1977`, `78:1981`, `78:2106` |
| Warning outline | none | #F3AB52 "Orange" 0.5 OUTSIDE | 2/8/2/8 | Manrope Regular 8, #F3AB52 "Orange" | `78:2007` "Not screened" 66x15, `78:2020`, `78:2031`; variant `78:2108` "Single Source" 80x18, label Regular **10** |
| Problem / missing | #F35352@0.25 "Red 25%" | none | 2/8/2/8 | Regular 8, #F35352 "Red" | `78:2046` "1 problem" 51x15, `78:2060`, `78:2112` "Missing" 45x15 |
| Success | #7BE697@0.25 "Green 25%" | none | 2/8/2/8 | Regular 8, #7BE697 "Green" | `78:2056` "UBO" 33x15, `78:2140` "Confirmed" 56x15 |
| Role | #9081E4@0.15 "Purple 15%" | none | 2/8/2/8 | Regular 8, #9081E4 "Purple" | `78:2018` "Shareholder" 62x15, `78:2072` "Director" 46x15 |
Frame names are the unrelated defaults ("Frame 46/65/67/68/69"). The same node names are reused across different pill kinds (e.g. "Frame 65" is both the warning outline `78:2007` and the success pill `78:2056`).

### 6.3 KPI card (pattern (no component)) — 4 on Pipeline: `78:2516`, `78:2519`, `78:2522`, `78:2525`
Frame 142.5x106 (FILL x HUG in the KPI row `78:2515`, H gap 24, row 642x106); V gap 16, padding 24/24/24/24, main/cross MIN; fill #08090A "Black 900"; stroke #1C1E1F "Grey 400" 1 INSIDE; radius 16; sil true. Children: numeral T (Jura Medium 38, FILL x HUG, left; colour by meaning: `78:2517` Blue "2", `78:2520` Red "1", Purple "0", Green "0") + label T (Manrope Regular 12, fill #62666D "Grey 300"; "Active", "Need You", ...). Numeral text box reports h24 (leading trim).

### 6.4 Panel (outline card), big card, row card (pattern (no component))
| Variant | Fill | Stroke | Radius | Layout | Sightings |
|---|---|---|---|---|---|
| Outline panel | none | #1C1E1F "Grey 400" 1 INSIDE | 16 | V gap 16, padding 16 | `78:2528` (642x312), `78:1776` (288x1161), `78:2652` (288x403), `78:2250` |
| Filled panel | #111213 "Grey 500" | #1C1E1F 1 INSIDE | 16 | V gap 16, padding 16 | `78:2575` (642x196), Wallet form card `78:2629` (658x330) |
| Gradient card ("bg gradient") | style "bg gradient" (#111213@0.1 -> #161718, transform in foundations 1.6) | #1C1E1F 1 INSIDE | 16 | V gap 8 (or 0 / 24), padding 16 (or 24/32/24/32 for the summary card) | `78:1794` (1196x307, pad 24/32/24/32, gap 24), `78:1950` (977x841, gap 8, pad 16), `78:2425` (977x260, gap 8), `78:2435` (977x472, gap 0) |
| Row card | #111213 "Grey 500" | #1C1E1F "Grey 400" 1 INSIDE | 8 | H gap 36, main SPACE_BETWEEN, FILL x HUG; padding 12/16/12/16 (Pipeline `78:2531` 608x107, cross CENTER) or 8/16/8/16 (254x50 run cards, cross MIN) | `78:2531`, `78:1783`, `78:1788`, `78:2654`, `78:2658` |
| Row card, active | #111213 | gradient "Gradient main" (#7BE697 -> #53B2ED) 1 INSIDE | 8 | same as row card 254x50 | `78:1778` (62% text Blue; others #1C1E1F) |
| Row card, dark (nested) | #08090A "Black 900" | none | 8 | H gap 36, SPACE_BETWEEN, padding 12/16/12/16, FILL x HUG | `78:2577`, `78:2589` (inside filled panel `78:2575`) |
Panel caption text: Manrope Medium 12, #62666D "Grey 300" (e.g. `78:2576`, `78:1777`, `78:2653`).

### 6.5 Notice panel (pattern (no component)) — 3 kinds
| Kind | Fill | Stroke | Radius | Padding / gap | Text | Ids |
|---|---|---|---|---|---|---|
| Critical (red) | #F35352@0.25 "Red 25%" | none | 8 | V gap 8, padding 12 | lines Manrope Medium 10, #F35352 "Red"; suffix "(...% of the client)" at node opacity 0.7 | `78:1957` (943x104) |
| Warning (orange outline) | none | #F3AB52 "Orange" 0.5 INSIDE | 8 | V gap 8, padding 12 (child x 12.5 = 12 + 0.5) | Manrope Medium 10 (or 12 in `78:2431`), #F3AB52 | `78:1970` (943x107), `78:2430` (943x177; body `78:2434` Manrope Medium 10 #A6ACB6 "Grey 100", line-height auto) |
| Info (purple) | #9081E4@0.15 "Purple 15%" | none | 8 | V gap 8, padding 12 | Manrope Medium 10, #9081E4 "Purple" | `78:1989` (943x38) |
Inline person-tag pills sit inside warning text rows (`78:1973`, `78:1980`: H gap 2).

### 6.6 Table (header / row / cell) (pattern (no component)) — "Ownership" tables
Table frame `78:2084` (943x139): V gap 0, padding 0, stroke #1C1E1F 1 INSIDE all sides, radius 8, FILL x HUG; also `78:1996` (outline frame, V gap 10, pad 8/16/8/16, radius 8). Rows: header row `78:2085` (941x31), body row `78:2102` (941x54): H gap 0, padding 0, cross CENTER, FILL x HUG; each has a BOTTOM-only stroke #1C1E1F "Grey 400" 1 INSIDE (sides 0/0/1/0). Cell: V auto-layout, padding 8/8/8/8, gap 0 (header cell `78:2086`) or 4 (body cell `78:2103`, `78:2105`); widths FIXED (70.07) or FILL.
Header cell text: Manrope Regular 10, #62666D "Grey 300" (`78:2087` "Share"). Body cell text: Manrope Regular 12, #DCE1E9 "White" (`78:2104` "43.47%"); cells can hold person-tag and warning pills (`78:2106`, `78:2108`). Table label above: Manrope Medium 10 #8A8F98 "Grey 200" (`78:2083`, `78:1994`). Overview list rows (`78:2439`, `78:2442`): H gap 8, padding 8/0/8/0, bottom 1px #1C1E1F stroke, 33 high; icon 6x6 dot + Medium 12 text. No sort, pager or selection state seen.
Sort/pagination: absent (section 8).

### 6.7 Sidebar filter list item (pattern (no component)) — 26 across Own (`78:1889`) and Ov (`78:2363`)
Frame 202x32 (FILL x HUG), H, gap 0, padding 8/12/8/16, main SPACE_BETWEEN, cross CENTER, radius 8, no fill, no stroke. Label Manrope Regular 12, #A6ACB6 "Grey 100", FILL x HUG. Optional right group: H gap 4, MAX-aligned, holding 1-2 status dots (6x6 ellipses: Red `78:1895` #F35352, Orange `78:1896` #F3AB52, Green #7BE697). List parent: V gap 4, padding 0/16/0/0 (right 16), 218 wide.
Selected: stroke "Gradient main" 0.5 INSIDE (height 33), label Manrope Medium 12 #DCE1E9 "White": Own `78:1906` "Ownership"; Ov `78:2364` "Overview". Same recipe as the active nav pill (6.1).

### 6.8 Stepper (pattern (no component)) — Own `78:1837`, Ov (`78:2311` row)
Row 1130x68 with 7 steps (frames 54 wide; step circle 40x40 box "Frame 11" at x 7 and label below at y 52) joined by 2px CENTER lines 136 long at y 21. Done step: "Union" 42x42 at -1,-1 gradient fill "Gradient main" (`78:1847`, `78:1853`, `78:1859`), label Manrope Regular 12 #59BCFA "Blue" (`78:1845`). Current: Union gradient "Gradient orange" (#F3892D -> #ECE040) (`78:1865`), label Orange #F3AB52 (`78:1863`). Pending: Ellipse 40x40 stroke #1C1E1F w2 CENTER (`78:1873`, `78:1879`, `78:1885`) + lucide/check 24x24 at 8,8; label #62666D "Grey 300". Line segments: gradient #53B2ED -> #7BE697 (`78:1838`, `78:1839`), raw #54B3E9 -> #F3892D (`78:1840`), #1C1E1F (`78:1841`..`78:1843`). Labels hug 54 wide centred under circles (labels wider than the 54 box overflow symmetrically: x -34 for "Gathering documents").

### 6.9 Progress ring / donut (pattern (no component)) — `78:2549`, `78:2572`(P), `78:1800` (Own), `78:2274` (Ov)
Ring 72x72: track Ellipse stroke #08090A w4 INSIDE (`78:2550`); arc VECTOR stroke raw gradient #53B2ED -> #7BE697 w4 INSIDE with DROP_SHADOW (foundations 3.3) (`78:2551`). Donut 140x140: track stroke #111213 "Grey 500" value w8 INSIDE (`78:1801`), arc stroke raw gradient w8 INSIDE (`78:1802`). Centre text Jura Medium 20 (ring) / 38 (donut) mixed digits Medium + "%" Light, #59BCFA; caption "60 out of 116" Jura SemiBold 12 #7BE697 (`78:1799`, text box 75x8 leading-trim).

### 6.10 Other repeated fragments (pattern (no component))
| Fragment | Spec | Sightings |
|---|---|---|
| Section title block | V gap 4: title Manrope Medium 14 #DCE1E9 "White" + sub Manrope Medium 10 #8A8F98 "Grey 200" (FILL x HUG) | `78:1952` ("Ownership"), `78:2427`, Wallet header `78:2626` (gap 8: Medium 16 + Medium 14 #62666D) |
| Title row | H, SPACE_BETWEEN, gap 309 (nominal), padding 0/0/4/0, FILL x HUG; right slot toggle w text | `78:1951`, `78:2426`, `78:2436` |
| Step-number chip | 24x24, fill #1C1E1F "Grey 400", radius 24, V center; numeral Jura Medium 14, gradient text "Gradient main" | `78:2632`, `78:2638`, `78:2644` |
| Status dot | ELLIPSE 6x6, no stroke, fill Red/Orange/Green | `78:2583`, `78:2584`, `78:1900`, `78:1895`, `78:1896` |
| Issue line | H gap 4, text Manrope Medium 12 (box h9 leading-trim), fill Red `78:1814` / Orange `78:1818`; node opacity 0.7 per foundations 1.3 (not re-measured) | `78:1814`, `78:1816`, `78:1818`, `78:1823` |
| Page title / breadcrumb row | H SPACE_BETWEEN gap 391, FILL x HUG, height 32: title Manrope Medium 16 + button group (H gap 16: Outline + icon, CTA) | `78:1804`, Ov equivalent |
| Header | see foundations 5.2 | `78:2488` etc. |

---

## 7. Controls checklist
| Control | Present? | Evidence |
|---|---|---|
| Button, solid (CTA) | YES, component (Default + hover) | `18:248` |
| Button, outline | YES, components (Outline `18:242`; Outline + icon `18:290`) | |
| Button sizes | only 32 high; no small/large | all |
| Icon-only button | ABSENT | name/type scan of finals + drafts |
| Link | text-link look only: "Go to Ownership >" (`78:2446`) Manrope Medium 10 #59BCFA, "KYC Check >" (`78:2587`); no link component or hover | patterns |
| Input (text) | YES, component `73:1679` (placeholder state only) | |
| Search | YES, component `73:1680` | |
| Select | YES, trigger only (`10:170`); no open list | |
| Textarea, date, time, password, number | ABSENT | name scan; only copy text "Date of birth" (`78:2091`) and "{DATE}" placeholders |
| Checkbox / radio | ABSENT | name scan for checkbox/radio/check: only `lucide/check` icon 24x24 in stepper |
| Toggle (switch) | YES, components `21:32`, `21:55` | |
| Segmented control / tabs | YES, Tabs 32 `21:384`, Tabs 24 `21:401` | |
| Pills / chips / badges | YES, pattern only (6.2) | |
| Tooltip / popover / menu / dropdown list | ABSENT | name scan (tooltip, popover, menu, dropdown) = 0 hits |
| Modal / drawer / scrim | ABSENT | name scan = 0 |
| Toast / alert / banner | Notice panels exist as inline patterns (6.5); no toast | |
| Table header / row / cell | YES, pattern only (6.6); sort/pager absent | |
| Card / panel | YES, pattern only (6.4) | |
| Avatar | ABSENT | name scan = 0 (person tags are text pills) |
| Scrollbar | ABSENT | name scan = 0; frames are fixed-size |
| Calendar | ABSENT | |
| Progress / loader | progress rings/donut + stepper (patterns); no spinner/skeleton | |
| Breadcrumbs | ABSENT as a trail (page title row only) | |
| Empty states | ABSENT | |
| Stepper | YES, pattern only (6.8) | |
| Pagination | ABSENT | |

---

## 8. Inconsistencies
1. **Outline Button + icon second variant is named `Variant2`**, not `hover` (set `18:290`, node `18:291`), unlike `Property 1=hover` in sets `18:242` / `18:248`.
2. **Hover recipe differs**: Outline Button hover stroke is a raw 3-stop gradient (`18:253`: #53B2ED, #4CCED4@0.5, #45EABB) with no style; Outline + icon `Variant2` stroke is the 2-stop style "Gradient main oposite" (`18:291`). Label/icon colours match ("Gradient main oposite").
3. **Toggle variant naming**: `Property 1=Default` is the ON state, `off` is OFF (`21:31`/`21:33`, `21:54`/`21:56`); ON label White vs OFF label Grey 200.
4. **Tabs have no state property**; active tab is whichever frame has the gradient (`21:379`, `21:397`); Tabs 24 padding 8 top/bottom does not fit its 24px height (label centred, text y=5).
5. **Select text colour**: component default #62666D (Grey 300) but all four instances override to #DCE1E9 (White) (`I78:2510;9:137` etc.): there is no value-vs-placeholder state in the component.
6. **Search padding** differs from Input/Select (8/8 vs 8/12), and the Wallet Search instance overrides padding to R32 (`78:2635`): cosmetic, FILL width, no visual effect.
7. **Stroke alignment**: fields use INSIDE strokes, outline buttons CENTER strokes (all weight 1); active nav/selected pills use 0.5 INSIDE; warning pills 0.5 OUTSIDE; warning notice panels 0.5 INSIDE.
8. **Active gradient direction** differs between screens (foundations conflict row): nav pill and sidebar selected item use "Gradient main" (#7BE697 -> #53B2ED) on Own/Ov, "Gradient main oposite" on Pipeline/Wallet; Tabs/CTA/outline variants use "Gradient main oposite".
9. **Nav "Runs" label** Medium 12 on all four screens regardless of active tab (others Regular 12).
10. **Pill label size**: "Single Source" (`78:2108`) Regular 10 / height 18 vs all other pills Regular 8 / height 15.
11. **Issue-line text size**: leading-trim text boxes in the stepper issue lines (`78:1814` etc.) are fontSize 12 Manrope Medium with box height 9 (foundations 1.3/2 mention a 10px font and "115x9"; node data shows size 12): trust node data.
12. **Typos / odd copy kept verbatim**: "Need You" (`78:2521`), "Show Confidential Details", "Text ON"/"Text OFF" (default toggle labels), "Run KYC Check", "Re-Run KYC Check", "Add Wallet and Screen", "Local Developer", "Paste the address, e.g. bc1q…, 0x…, T…", "Label, e.g. Treasury wallet", "Note for Compliance (optional)", placeholder tokens "{PERSON_n}", "{DATE}". Components are all labelled "Button"/"Select"/"Type here" in defaults.
13. **Frame naming**: all pattern frames carry Figma defaults ("Frame 46", "Frame 65" reused for different pill kinds) and the two "toggle" frame/sets share a name (set `21:32` "toggle" vs frame `21:42` "toggle" inside "toggle w text").
14. **Dead definitions**: Outline Button (`18:242`), Tabs 32 (`21:384`), toggle (`21:32`), and all hover/Variant2 states exist in the file but are never used in the final screens.

---

## 9. Conflicts and decisions needed
| Topic | Option A (node ids, value) | Option B (node ids, value) | Chosen / recommendation | Needs owner? |
|---|---|---|---|---|
| Hover recipe for outline buttons | 3-stop raw stroke `18:253` | 2-stop "Gradient main oposite" `18:291` | Reproduce each as drawn; record the second as `--alt-` | yes (which is canonical) |
| Which variant of Outline + icon is "hover" | `18:291` "Variant2" | not named hover | Treat `Variant2` as hover (matches Outline hover recipe) | yes (confirm) |
| Selected-gradient direction in nav / sidebar | "Gradient main" on Own/Ov (`78:1766`, `78:2240`, `78:1906`, `78:2364`) | "Gradient main oposite" on Pipeline/Wallet (`78:2500`, `78:2617`) and Tabs `21:379` | See foundations; pick one for the component | yes |
| Control text colour for entered values | Select value White (instances) | placeholder Grey 300 (definitions) | Document both; value = White, placeholder = Grey 300 | no (only a Select value is drawn) |
| Unused definitions | keep Outline Button, Tabs 32, toggle in the system | drop | Keep (they are definitions in the design) | no |
| Pill / card / nav / table / stepper as components | drawn only as frames (6.x) | — | Build as patterns (CSS classes), not Figma components | no |

---

## 10. GAPS / NOT FOUND IN THE DESIGN (searched; absent as designed states)
| Area | Finding | How searched | Scope searched |
|---|---|---|---|
| Hover states | Present only for CTA Button (`18:249`), Outline Button (`18:253`), Outline + icon (`18:291`, named Variant2). Absent for Select, Search, Input, Tabs, toggles, nav pills, row cards, table rows, links, pills | component variant names; name scan (hover) of the 4 finals; colour comparison of variants | page `3:10845` (15 components), 4 finals |
| Focus | Absent (no focus ring/stroke on any control) | variant names for focus/press/active; name scan `focus`; no component has a stroke/colour distinct from default except hover | same |
| Active / pressed | Absent (the word "active" appears only as KPI label text "Active" `78:2518`; Tabs "active" is a hard-coded fill) | name/text scan `active|press` | same |
| Disabled | Absent for all controls (no disabled variant, no dimmed colours; only node opacity 0.5 on the Select chevron arrow and 0.7 on text) | variant names, name scan `disabled`, opacity tallies from foundations | same |
| Error / validation | Absent for fields (no red stroke/message); Red is used only for text/pills/panels | name+text scan `error`; no field variants | same |
| Select open state / menu / dropdown list | Absent | name scan `select|menu|dropdown|popover` (only the 4 Select instances) | 4 finals + `3:10845` |
| Checkbox / radio | Absent | name scan `checkbox|radio` | 4 finals + `3:10845` |
| Textarea / date / time / password / number | Absent (only copy text "Date of birth", "{DATE}") | node-name and text scan | 4 finals |
| Tooltip / popover / modal / drawer / scrim | Absent | name scan; foundations scrim fill search | 4 finals |
| Toast / alert | Absent as toast; inline notice panels exist (6.5) | name scan `toast|alert|banner` | 4 finals |
| Avatar / scrollbar / calendar | Absent | name scan | 4 finals |
| Pagination / sort | Absent | name+text scan `pager|page|sort|prev|next` | 4 finals |
| Loading / skeleton / empty state | Absent | name+text scan `loading|spinner|skeleton|empty|no result` | 4 finals |
| Icon-only button | Absent | scan of INSTANCE/FRAME names `button`; only 3 button components | 4 finals + `3:10845` |
| Component descriptions / property docs | Absent (description empty on all 10 component roots) | `description` read on every set and component | `3:10845` |
| Components on skipped pages | None | `findAllWithCriteria` COMPONENT/COMPONENT_SET/INSTANCE: `0:1` -> 0, `2:600` -> 0 | pages `0:1`, `2:600` |
| Components in the finals | No COMPONENT nodes in the finals (type census: FRAME 425, TEXT 314, ELLIPSE 73, VECTOR 61, LINE 27, BOOLEAN_OPERATION 16, INSTANCE 16, GROUP 12, RECTANGLE 2) | type tally over the 4 finals | 4 finals |
| Variables / text styles bound to controls | Absent (no variable bound; paint styles only; radii raw) | `boundVariables` presence in dump (`bv` empty on all roots), style ids | 10 roots |
| Responsive / min-max sizes | Absent (no min/max width on any control) | node data | 10 roots |
| Motion / transitions | Absent (no prototype interactions read) | not read via this API pass: prototype reactions were NOT inspected | — |
| Not harvested | (a) prototype interactions / variant transitions not read; (b) `componentPropertyDefinitions` not read; (c) the 4 drafts screen copies' own instances not enumerated (only the finals); (d) pattern values for Overview-only duplicates (`78:2250`, `78:2311`, `78:2274`, `78:2572`) and the remaining pill/row members are taken from the matching Ownership/Pipeline nodes and foundations counts, not individually re-dumped; (e) no rate-limit incidents | — | — |

## 11. Design update 2026-11-16 — hover / disabled variants added by the owner in Figma (re-read, read-only)
Components page `3:10845`. New COMPONENT_SETs wrap the old standalone components (the old node ids are now the "Default" variant and are unchanged): Tabs 32 `101:87` (Default `21:384`), Tabs 24 `101:93` (Default `21:401`), Select `101:99` (Default `10:170`), Search `101:105` (Default `73:1680`), Input `101:111` (Default `73:1679`). Variant property name: `Property 1`.

| Component | Variant | Node | Drawn change vs Default |
|---|---|---|---|
| CTA Button `18:248` | disabled | `101:80` | fill "Grey 100" #A6ACB6 (Default: White #DCE1E9); label unchanged Black 900 #08090A; no opacity |
| Outline Button `18:242` | disabled | `101:82` | fill "Grey 500" #111213 (Default: none); stroke "Grey 400" #1C1E1F 1 CENTER (Default: Grey 200); label "Grey 300" #62666D (Default: Grey 200) |
| Outline Button + icon `18:290` | disabled | `101:84` | like Outline disabled; icon stroke "Grey 300" #62666D (Default: Grey 200); label Grey 300 |
| Tabs 32 `101:87` / Tabs 24 `101:93` | disabled | `101:88` / `101:94` | track fill Grey 400 unchanged; ACTIVE tab fill "Grey 300" #62666D (Default: gradient) with label "Grey 400" #1C1E1F (Default: Black 900); inactive tab label Grey 300 unchanged |
| Select `101:99` | hover | `101:100` | stroke "Grey 300" #62666D 1 INSIDE (Default: Grey 400); fill Grey 500, text, chevron unchanged |
| Select | disabled | `101:114` | fill "Grey 400" #1C1E1F (Default: Grey 500); stroke Grey 300 1 INSIDE; text Grey 300; both chevron strokes Grey 300 #62666D (Default: gradient), the 0.5-opacity chevron stays 0.5 |
| Search `101:105` | hover | `101:106` | stroke Grey 300 1 INSIDE; rest unchanged |
| Search | disabled | `101:119` | fill Grey 400; stroke Grey 300 1 INSIDE; text Grey 300; icon stroke Grey 300 (Default: gradient); icon ellipse fill removed (Default: Blue 15%) |
| Input `101:111` | hover | `101:112` | stroke Grey 300 1 INSIDE; rest unchanged |
| Input | disabled | `101:124` | fill Grey 400; stroke Grey 300 1 INSIDE; text Grey 300 |

Notes: no opacity is used for any disabled state (all opacity 1; paints are swapped). Hover on the three buttons was already drawn (`18:253`, `18:249`, `18:291` "Variant2"). Not drawn: toggle disabled/hover, tab hover, nav pill hover/disabled, focus, pressed, error. Field focus/active is not drawn (owner decided it in the expand step: gradient ring).
Observation: field hover and field disabled share the same stroke (Grey 300); they differ only by fill (Grey 500 vs Grey 400).

### 11.1 Modal / dialog — drawn 2026-11-16 (page drafts, frame `105:131` "Modal", 1920x1293, a full screen mock with a header and Runs/Overview-like content behind the modal)
| Part | Node | Values |
|---|---|---|
| Scrim | `105:400` "Frame 108" | 1920x1223 at (0,70) (the header is 66 high; the scrim starts at y=70, so 4px of page shows above it); fill #08090A "Black 900" colour at paint opacity 0.25 (no style); effect BACKGROUND_BLUR radius 12; no stroke |
| Dialog | `105:411` "Frame 109" | 254x149 at (833,537) = centred horizontally; VERTICAL auto-layout gap 32, padding 24 all sides, primary/counter MIN; fill #1C1E1F "Grey 400"; no stroke; radius 8; no effects |
| Text block | `105:401` | VERTICAL gap 4, 206 wide: title `105:402` "Re-run KYC check?" Manrope Medium 14 White #DCE1E9; text `105:403` "This replaces the current result." Manrope Medium 10 "Grey 200" #8A8F98 |
| Button row | `105:404` | HORIZONTAL gap 24, 206x32, left aligned: instance Outline Button (Default `18:227`) label "Cancel" 88x32; instance CTA Button (Default `18:142`) label "Confirm" 94x32 |
Notes: first background-blur effect in the design (all earlier effects are a drop shadow on ring arcs). No close icon, no focus/hover shown. Scrim does not cover the header.
