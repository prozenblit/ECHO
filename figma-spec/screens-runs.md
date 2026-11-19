# echo — Screens group-b: Runs / Ownership + Runs / Overview (harvested from design file `<figma-file-key>`)

Scope: page "final " (`78:1750`) › "Runs / Ownership" (`78:1751`, 1920x1293 @page x2000) and "Runs / Overview" (`78:2225`, 1920x1293 @page x4000). Harvested 2026-11-16 by `figma-harvester` (screens:group-b), read-only via the Plugin API.
Owner decisions applied (from `_intake.md`): (1) screens from `final` (these are the finals); (2) drafts copies `4:15408` / `63:712` NOT re-walked here — foundations found them node-for-node identical (0 diffs); I saw no evidence to the contrary; (3) source of truth = Figma. Component definitions are canonical on page `drafts` (`3:10845`) and belong to the components harvester; here only the instances are recorded.

Legend: `id` = Figma node id. `{Name}` = applied paint style (resolved). `(visual estimate)` = not from node data (none used in this file). Counts = visible nodes incl. nodes inside instances. `x,y` parent-relative unless stated; for children of a GROUP the Plugin API reports x,y in the coordinate space of the nearest frame ancestor, not the group. "T" = text. Layout shorthand: `H/V gN pT/R/B/L main/cross szWH` (F=FILL, H=HUG, X=FIXED; main = primaryAxisAlign, cross = counterAxisAlign). All text is Manrope unless a Jura font is named; line-height AUTO and letter-spacing 0% unless stated (verified in foundations; the only fixed line-height here is `78:2434` = 16px). Overview ids that are shared structure with Ownership are given as `Own id / Ov id` (Ov = Own + 474, verified by the structural diff in 7.1 for header, left panel, summary card, sidebar).

---

## 0. Scope and provenance
| Item | Value |
|---|---|
| Canonical node(s) | `78:1751` "Runs / Ownership" 1920x1293 (page x2000,y0); `78:2225` "Runs / Overview" 1920x1293 (page x4000,y0). Both: FRAME, fill `{Black 900}` #08090A, clipsContent true, layoutMode NONE (absolute children), constraints MIN/MIN, 0 hidden nodes. |
| Alternates seen | Drafts `4:15408` Runs/Ownership and `63:712` Runs/Overview: identical per foundations section 0 / 6.3 (489 / 268 nodes, 0 diffs); not re-walked. Final wins (owner decision 1). |
| Hidden nodes in scope | 0 (walks used visible-only plus all-children listing at frame level; every child enumerated by `children` was visible). |
| Extraction scripts | Custom read-only compact walker (same fields as `figma-dump-subtree.js` plus constraints, rotation, style names, dash, effects) run per sub-tree (all < 25k chars); a structural diff walker (name/type/x,y/size/fills/strokes/style ids/radius/layout/text) over 4 region pairs, 202 node pairs; a transform/vectorPath probe for the ring vectors and connector lines. Nothing written to Figma. |
| Not covered by this file | Pipeline / Wallet Check (group-a); component internals (components harvester); icon SVG export (assets); global colour/type/radius tallies (foundations). |

---

## 1. Frames and top-level structure

### 1.1 Frame summary
| Property | Ownership `78:1751` | Overview `78:2225` |
|---|---|---|
| Size | 1920x1293 | 1920x1293 |
| Page position | x2000, y0 | x4000, y0 |
| Fill | `{Black 900}` #08090A (style `S:7774f5c6…`) | same |
| Stroke / radius / effects | none / 0 / none | same |
| clipsContent | true | true |
| Auto-layout | NONE (all children absolutely positioned) | NONE |
| Constraints (root) | MIN / MIN | MIN / MIN |
| Children, z-order bottom→top | 1: `78:1752` header; 2: `78:1775` content | 1: `78:2226` header; 2: `78:2249` content |

### 1.2 Top-level children
| Id (Own / Ov) | Name | x,y | w x h | Constraints | Auto-layout | Notes |
|---|---|---|---|---|---|---|
| `78:1752` / `78:2226` | Frame 8 (header) | 0,0 | 1920x66 | MIN/MIN | H g108 p16/40/16/40 SPACE_BETWEEN/CENTER szFH (fixed width, hug height) | fill none; stroke bottom-only 1px INSIDE `{Grey 500}` #111213 (T0 R0 B1 L0) -> 66 = 16+33+16+1. Same in both. |
| `78:1775` | Frame 62 (content) | 210,90 | 1500x1161 | CENTER/MIN | H g16 p0 MIN/MIN szHH | 210 = (1920-1500)/2; y 90 = 66 header + 24; bottom gap 1293-90-1161 = **42** |
| `78:2249` | Frame 62 (content) | 210,90 | 1500x1068 | CENTER/MIN | H g16 p0 MIN/MIN szHH | bottom gap 1293-90-1068 = **135** (frame is taller than its content; screen height is a fixed 1293) |

Gutter arithmetic (content, both screens): left panel 288 + gap 16 + main column 1196 = 1500. Main column: summary card 307 + gap 13 + lower area (841 Own / 748 Ov) = 1161 / 1068. Lower area: sidebar 218 + gap 1 + card 977 = 1196.

---

## 2. Header (identical on both screens; diff 7.1 = 0 differences)
Header geometry also profiled in foundations 5.2; repeated here as the reachable node list for these two frames.

| Region | Own id / Ov id | x,y | w x h | Fill / stroke / radius | Layout / notes |
|---|---|---|---|---|---|
| Logo box "Frame 7" | `78:1753` / `78:2227` | 40,16.5 | 162x32 | none | V g10 p0 CENTER/MIN szFF |
| Logo Group 1 | `78:1754` / `78:2228` | 0,6 | 85x20 | — | GROUP |
| Logo Union | `78:1755` / `78:2229` | 15,6 | 70x20 | F `{Gradient main oposite}` #53B2ED->#7BE697; radius bound to stray variable (see foundations 0.1) | BOOLEAN_OPERATION with 4 children (wordmark glyph vectors #4DFFCD raw, foundations 1.8) |
| Logo Line 1 / 2 / 3 | `78:1760`,`78:1761`,`78:1762` / `…2234`,`2235`,`2236` (ids by +474) | x10 / 5 / 0, y6 | 20x0, rotation -90 | S `{Blue 75%}` / `{Blue 50%}` / `{Blue 25%}`, w1.5 CENTER | LINE |
| Nav container "Frame 1" | `78:1763` / `78:2237` | 645.5,16 | 643x33 | none | H g0 p0 MIN/CENTER szHH |
| Select instance | `78:1774` / `78:2248` | 1732,16.5 | 148x32 | F `{Grey 500}` #111213; S `{Grey 400}` #1C1E1F w1 INSIDE; R8 | H g32 p8/12/8/12 CENTER/CENTER szHF |

Nav items (Own ids; Ov = +474: `78:2238`..`78:2247`). All H p8/32/8/32 CENTER/CENTER szHH, text Manrope 12 centred, fill `{White}` #DCE1E9:
| Item | Own frame / text | x,y | w x h | Radius | Stroke | Text style |
|---|---|---|---|---|---|---|
| Pipeline | `78:1764` / `78:1765` | 0,0.5 | 108x32 | 24 | none | Regular 12 |
| Runs (ACTIVE) | `78:1766` / `78:1767` | 108,0 | 94x33 | 8 | GRAD `{Gradient main}` #7BE697->#53B2ED, w0.5 INSIDE (33 = 32 + stroke) | **Medium** 12 |
| Wallet check | `78:1768` / `78:1769` | 202,0.5 | 135x32 | 24 | none | Regular 12 |
| System health | `78:1770` / `78:1771` | 337,0.5 | 144x32 | 24 | none | Regular 12 |
| Admin Dashboard | `78:1772` / `78:1773` | 481,0.5 | 162x32 | 24 | none | Regular 12 |

Select instance text override "Local Developer" (`I78:1774;9:137`, Regular 10, `{White}`, 74x14 at 13,9); chevron frame `I78:1774;18:308` 16x16 at 119,8 with vectors `I78:1774;18:310` (12x6) and `I78:1774;18:311` (6x3, node opacity 0.5), stroke `{Gradient main}` w1 CENTER, radius 0.5. Main component `Select` `10:170`. Both screens are visually identical in the header; text copy is the same.

---

## 3. Runs / Ownership — body (`78:1775`, 1500x1161)

### 3.1 Region map (x,y relative to `Frame 62`; absolute = +210,+90 in the screen)
| Region | Id | x,y | w x h | Fill | Stroke | Radius | Layout |
|---|---|---|---|---|---|---|---|
| Left panel "Recent Runs" | `78:1776` (Frame 58) | 0,0 | 288x1161 | none | `{Grey 400}` #1C1E1F w1 INSIDE | 16 | V g16 p16/16/16/16 MIN/MIN szFF |
| Main column | `78:1793` (Frame 61) | 304,0 | 1196x1161 | none | none | 0 | V g13 p0 MIN/MIN szFH |
| Summary card | `78:1794` (Frame 36) | 0,0 in column | 1196x307 | `{bg gradient}` (linear #111213@alpha 0.1 -> #161718@1) | `{Grey 400}` w1 INSIDE | 16 | V g24 p24/32/24/32 MIN/MIN szFH |
| Lower area | `78:1888` (Frame 60) | 0,320 in column | 1196x841 | none | none | 0 | H g1 p0 MIN/MIN szFH |
| Sidebar filter list | `78:1889` (Frame 1) | 0,0 in lower | 218x501 | none | none | 0 | V g4 p0/16/0/0 CENTER/MIN szFH |
| Detail card | `78:1950` (Frame 59) | 219,0 in lower | 977x841 | `{bg gradient}` | `{Grey 400}` w1 INSIDE | 16 | V g8 p16/16/16/16 MIN/MIN szFH |

Strokes are counted in layout (strokesIncludedInLayout true): with p16 + 1px stroke, child x = 17 and child width = parent - 34 (288-34 = 254; 977-34 = 943; summary 1196-66 = 1130).

### 3.2 Left panel "Recent Runs" (`78:1776`)
Caption `78:1777` T "Recent Runs" Manrope Medium 12 `{Grey 300}` #62666D, 254x16 at 17,17, szFH.
Run card pattern ("Frame 56/57/58"): 254x50, fill `{Grey 500}` #111213, R8, H g36 p8/16/8/16 SPACE_BETWEEN/MIN szFH; left child "Frame 55" V g2 p0 szFH (192/196/185 x32) = title (Medium 12 `{White}`, 16 high) + status (Medium 10 `{Grey 200}` #8A8F98, 14 high); right child T Jura Medium 14 centred (percentage). Gap between cards 16 (parent g16): y 49, 115, 181.
| # | Card id | y | Stroke | Left stack | Title T | Status T | Pct T (id, colour) |
|---|---|---|---|---|---|---|---|
| 1 ACTIVE | `78:1778` | 49 | GRAD `{Gradient main}` #7BE697->#53B2ED w1 INSIDE | `78:1779` | `78:1780` "CEDAR LOOP, INC." | `78:1781` "Needs analyst" | `78:1782` "62%" `{Blue}` #59BCFA, 28x17 |
| 2 | `78:1783` | 115 | `{Grey 400}` w1 INSIDE | `78:1784` | `78:1785` "ALDER PEAK PTY LTD" | `78:1786` "ECHO processing" | `78:1787` "41%" `{Blue}`, 24x17 |
| 3 | `78:1788` | 181 | `{Grey 400}` w1 INSIDE | `78:1789` | `78:1790` "Company  LTD" (**two spaces**, verbatim) | `78:1791` "Approved" | `78:1792` "100%" `{Green}` #7BE697, 35x17 |
Percentage colour is data-driven by state: Blue while in progress, Green at 100%. Unused panel height below card 3 is empty (panel is FILL height 1161; no more cards).

### 3.3 Summary card (`78:1794`, 1196x307): contains two children
Layout arithmetic: 25 + 165 + 24 + 68 + 25 = 307 (25 = pad 24 + stroke 1). Children x = 33.
**(a) Steps row `78:1795` "Frame 35"** 1130x165 at 33,25: H g48 p0/0/24/0 MIN/CENTER szFH; stroke bottom-only `{Grey 400}` w1 INSIDE (T0 R0 B1 L0). 140 + 24 pad + 1 = 165. Children: donut group + info column.
- **Donut `78:1796` "Group 3"** GROUP 140x140 at 0,0 (szFF) with, in z-order: `78:1797` "Frame 4" V g12 CENTER... (center label, 75x44 at 32,49, szHH) containing `78:1798` T "62%" 73x24 at 1,0 (mixed: digits "62" Jura Medium 38, "%" Jura Light 38, fill `{Blue}`, centred) and `78:1799` T "60 out of 116" Jura SemiBold 12 `{Green}` centred (75x8 — leading-trimmed box, do not copy height); and `78:1800` "Group 2" GROUP 140x140 containing the track `78:1801` ELLIPSE 140x140 (no fill, stroke #111213 = value of `{Grey 500}` w8 INSIDE) and the data arc `78:1802` "Ellipse 2" VECTOR 111.18x131.76, relativeTransform [[-1,0,136.91],[0,1,4.12]] (mirrored on X, rotation -180 as reported), stroke RAW gradient #53B2ED@0 -> #7BE697@1 w8 INSIDE, strokeCap ROUND, effect DROP_SHADOW #000000@0.48 offset -2,2 blur 6 spread 0. **Data-driven arc**: an open vector arc (not an ellipse arcData; Ellipse 1 arcData is the full 0..2pi, innerRadius 0) whose path covers 62% (60 of 116 = 51.7%; the label says 62% — the label and arc are independent, see conflicts). Starts at top (path start 65.998, 0).
- **Info column `78:1803` "Frame 34"** at 188,0, 942x140, V g24 SPACE_BETWEEN/MIN szFF. Because SPACE_BETWEEN, the real gap is 140-32-96 = 12 (children at y0 and y44; itemSpacing 24 is not used). Children:
  - `78:1804` "Frame 33" 942x32 H g391 SPACE_BETWEEN/CENTER szFH: heading `78:1805` T "CEDAR LOOP, INC." Medium 16 `{White}` 62x22; button group `78:1806` "Frame 32" 312x32 at 630,0 H g16 szHH holding (1) `78:1807` Outline Button + icon instance 142x32 (variant `Property 1=Default` `18:289`, set `Outline Button + icon` `18:290`; stroke `{Grey 200}` w1 CENTER, R8, H g12 p8/20/8/16; text `I78:1807;18:282` "Checklist.docx" Medium 12 `{Grey 200}`; icon `I78:1807;18:287` Vector 10x12 at 16,10 stroke `{Grey 200}` w1) and (2) `78:1808` CTA Button instance 154x32 at 158,0 (variant `Property 1=Default` `18:142`, set `CTA Button` `18:248`; fill `{White}` #DCE1E9, R8, H g10 p8/24/8/24; text `I78:1808;10:169` "Re-Run KYC Check" Medium 12 `{Black 900}`).
  - `78:1809` "Frame 57" 942x96 at 0,44 V g8 szFH: label `78:1810` T "Still Open:" Medium 12 `{Grey 300}`; then `78:1811` "Frame 30" 942x72 H g64 szFH with 3 issue columns (each V g12; each issue row = "Frame 2x" H g4 MIN/MAX with one T, Manrope Medium 12 at node opacity 0.7, hug box height 9 = leading trim):
    - Column A `78:1812` (188x72): `78:1813`/`78:1814` "19 conflicting values" `{Red}`; `78:1815`/`78:1816` "1 ownership structure incomplete" `{Red}`; `78:1817`/`78:1818` "4 missing documents" `{Orange}`; `78:1819`/`78:1820` "1 out-of-date document" `{Orange}`.
    - Column B `78:1821` (258x72) at x252: `78:1822`/`78:1823` "11 values not found"; `78:1824`/`78:1825` "3 parties or wallets not screened"; `78:1826`/`78:1827` "3 need analyst approval (one source)"; `78:1828`/`78:1829` "4 need analyst approval (client-declared only)" — all `{Orange}`.
    - Column C `78:1830` (162x51) at x574: `78:1831`/`78:1832` "4 drafts to accept or edit"; `78:1833`/`78:1834` "1 item for the analyst to write"; `78:1835`/`78:1836` "4 inconsistencies to check" — all `{Orange}`.
  - Column pitch: A at x0 (w188), B at 252 (188+64), C at 574 (252+258+64) ✓ gap 64.

**(b) Stepper `78:1837` "Frame 22"** 1130x68 at 33,214, absolute children (no auto-layout, szFF). 7 steps + 6 connectors.
| Step | Wrapper id (x,y; 54x68, szFF) | Label T (Regular 12, centred, label y52, may overflow wrapper: x negative) | Circle frame (40x40 at wrapper x+7,y0) | State |
|---|---|---|---|---|
| 1 | `78:1844` Frame 54 @9,0 | `78:1845` "Triggered" `{Blue}` 54x16 | `78:1846` Frame 11 | DONE |
| 2 | `78:1850` Frame 53 @185,0 | `78:1851` "Gathering documents" `{Blue}` 122x16 at -34 | `78:1852` | DONE |
| 3 | `78:1856` Frame 52 @361,0 | `78:1857` "ECHO processing" `{Blue}` 96x16 at -21 | `78:1858` | DONE |
| 4 | `78:1862` Frame 51 @537,0 | `78:1863` "Needs analyst" `{Orange}` 79x16 at -13 | `78:1864` Frame 13 | CURRENT |
| 5 | `78:1870` Frame 50 @717,0 | `78:1871` "Awaiting review" `{Grey 300}` 86x16 at -16 | `78:1872` | PENDING |
| 6 | `78:1876` Frame 49 @890,0 | `78:1877` "Awaiting 4-eyes" `{Grey 300}` 89x16 at -18 | `78:1878` | PENDING |
| 7 | `78:1882` Frame 48 @1067,0 (53x68) | `78:1883` "Approved" `{Grey 300}` 53x16 at 0 | `78:1884` (at x5) | PENDING |
Circle states (all circles 40x40, Union boolean 42x42 at -1,-1 for done/current):
- DONE (`78:1847`/`78:1853`/`78:1859` Union fill `{Gradient main}` #7BE697->#53B2ED): children `78:1848`/`78:1854`/`78:1860` "Ellipse 3" 40x40 stroke `{Gradient green}` #5DE7CB->#66D74A w2 CENTER; `78:1849`/`78:1855`/`78:1861` check Vector 16x11 at 12,14 stroke `{Black 900}` w2 CENTER (constraint SCALE).
- CURRENT (`78:1865` Union fill `{Gradient orange}` #F3892D->#ECE040): `78:1866` "Ellipse 4" VECTOR 20x40 (left half arc) stroke `{Gradient orange}` w2 CENTER **dash [6,6]**; `78:1867` "Ellipse 5" VECTOR 20x40 at 40,0 mirrored X (right half arc), stroke `{Gradient orange}` w2, cap ROUND; `78:1868` lucide/check FRAME 24x24 at 8,8 clip, containing `78:1869` Vector 16x11 at 4,6 stroke `{Gradient orange}` w2. (Half dashed / half solid ring = "in progress".)
- PENDING (`78:1873`/`78:1879`/`78:1885` "Ellipse 3" 40x40 stroke `{Grey 400}` #1C1E1F w2 CENTER, no fill; lucide/check frames `78:1874`/`78:1880`/`78:1886` 24x24 at 8,8 with Vector `78:1875`/`78:1881`/`78:1887` 16x11 at 4,6 stroke `{Grey 300}` #62666D w2).
Connectors (LINE 136x0 at y21, stroke w2 CENTER, szFF): `78:1838` x56 `{Gradient main oposite}` (done->done); `78:1839` x232 `{Gradient main oposite}`; `78:1840` x408 RAW gradient #54B3E9->#F3892D (done->current); `78:1841` x584, `78:1842` x761, `78:1843` x936 `{Grey 400}` (pending). Connector pitch 176 / 176 / 176 / 177 / 175 (positions 56, 232, 408, 584, 761, 936). Z-order inside Frame 22: 6 lines first (bottom), then 7 step wrappers.

### 3.4 Sidebar filter list (`78:1889`, 218x501, V g4 p0/16/0/0)
Item pattern: H g0 p8/12/8/16 SPACE_BETWEEN/CENTER, 202x32, radius 8, fill none, szFH (202 = 218-16). Label T Regular 12 `{Grey 100}` #A6ACB6 at x16; right: dots frame "Frame 31" H g4 MAX/CENTER szHH with 6x6 ellipses (Red `78:1895`-style #F35352, Orange #F3AB52, Green #7BE697). Frame bottom item "Activity" has padding 8/16/8/16 (others 8/12/8/16) and no dots.
| # | Item id | y | Label T id / text | Dots frame / ellipses |
|---|---|---|---|---|
| 1 | `78:1890` Frame 3 | 0 | `78:1891` "Overview" | none |
| 2 | `78:1892` Frame 16 | 36 | `78:1893` "General information" | `78:1894`: `78:1895` Red, `78:1896` Orange |
| 3 | `78:1897` Frame 17 | 72 | `78:1898` "Business" | `78:1899`: `78:1900` Green |
| 4 | `78:1901` Frame 18 | 108 | `78:1902` "Regulation" | `78:1903`: `78:1904` Red, `78:1905` Orange |
| 5 ACTIVE | `78:1906` Frame 23 | 144 | `78:1907` "Ownership" (Medium 12 `{White}` #DCE1E9, at 16.5,8.5) | `78:1908`: `78:1909` Red, `78:1910` Orange |
| 6 | `78:1911` Frame 19 | 181 | `78:1912` "Funds and wealth" | `78:1913`: `78:1914` Orange |
| 7 | `78:1915` Frame 20 | 217 | `78:1916` "Financials" | `78:1917`: `78:1918` Red, `78:1919` Orange |
| 8 | `78:1920` Frame 21 | 253 | `78:1921` "Trading" | `78:1922`: `78:1923` Green |
| 9 | `78:1924` Frame 22 | 289 | `78:1925` "Comments" | `78:1926`: `78:1927` Orange |
| 10 | `78:1928` Frame 24 | 325 | `78:1929` "Wallets" | `78:1930`: `78:1931` Red, `78:1932` Orange |
| 11 | `78:1933` Frame 25 | 361 | `78:1934` "Country risk" | `78:1935`: `78:1936` Red, `78:1937` Orange |
| 12 | `78:1938` Frame 26 | 397 | `78:1939` "Documents provided" | `78:1940`: `78:1941` Red, `78:1942` Orange |
| 13 | `78:1943` Frame 27 | 433 | `78:1944` "Files" | `78:1945`: `78:1946` Red, `78:1947` Orange |
| 14 | `78:1948` Frame 15 | 469 | `78:1949` "Activity" (T hug, centre-aligned) | none |
Active item: 202x33 (0.5px stroke counted), stroke GRAD `{Gradient main}` w0.5 INSIDE, label Medium 12 `{White}`; subsequent y offset 36 -> 37 (after active). 14 rows: 12 x 32 + 1 x 33 + ... = items span 0..501. Row pitch 36 (32 + gap 4). Dots semantics: red = conflicts, orange = missing/needs check, green = clean; order red then orange.

### 3.5 Detail card (`78:1950`, 977x841, V g8 p16): vertical stack, all children x17, width 943 (szFH)
Arithmetic: 17 + 41 + 8 + 257 + 8 + 197 + 8 + 167 + 8 + 113 + 16 + 1 = 841.
| Block | Id | y | h | Contents |
|---|---|---|---|---|
| Title row "Frame 44" | `78:1951` | 17 | 41 | H g309 p0/0/4/0 SPACE_BETWEEN/MIN: `78:1952` "Frame 43" 304x37 V g4 (T `78:1953` "Ownership" Medium 14 `{White}` 19h; T `78:1954` "2 UBOs at or above 10%, 1 director, 0 trusts, 50 parties." Medium 10 `{Grey 200}` 14h) + toggle w text instance `78:1955` 183x16 at 760,0 |
| Notice stack "Frame 63" | `78:1956` | 66 | 257 | V g4: critical `78:1957` (104), warning `78:1970` (107), info `78:1989` (38) |
| Table block "Frame 73" (org tree) | `78:1992` | 331 | 197 | V g8: header row `78:1993` (24) + tree box `78:1996` (165) |
| Table "UBOs" "Frame 77" | `78:2081` | 536 | 167 | V g4: caption row `78:2082` (24) + table `78:2084` (139) |
| Table "Directors" "Frame 78" | `78:2171` | 711 | 113 | V g4: caption row `78:2172` (24) + table `78:2174` (85) |

**Toggle instance `78:1955`**: main `toggle w text` variant `Property 1=off` `21:56` (set `21:55`); H g6 CENTER; children `I78:1955;21:58` "toggle" 32x16 (track `I78:1955;21:59` Rectangle 32x16 R24 fill `{Grey 300}` #62666D; knob `I78:1955;21:60` Ellipse 12x12 at 2,2 fill `{Grey 500}`); label `I78:1955;21:57` T "Show Confidential Details" Medium 12 `{Grey 200}` 145x16 at 38,0. Only the OFF state is drawn.

**Critical panel `78:1957`** (943x104, fill `{Red 25%}` #F35352@0.25, R8, V g8 p12): 4 rows H g4 MIN/CENTER szHH (rows 14 high, pitch 22: y12,34,56,78). Each row: T Medium 10 `{Red}` message + T Medium 10 `{Red}` at node opacity 0.7 (percentage):
- `78:1958` > `78:1959` "Series A Investors is a group of holders: who is in it is not in the documents." + `78:1960` "(16.33% of the client)"
- `78:1961` > `78:1962` "ESOP is a group of holders: who is in it is not in the documents." + `78:1963` "12.86% of the client)" (**missing opening "(" — typo, verbatim**)
- `78:1964` > `78:1965` "ESOP (Employee Stock Option Pool) is a group of holders: who is in it is not in the documents." + `78:1966` "12.86% of the client)" (same typo; row is szFH 919 wide)
- `78:1967` > `78:1968` "Seed Investors is a group of holders: who is in it is not in the documents." + `78:1969` "12.50% of the client)" (same typo)
**Warning panel `78:1970`** (943x107, no fill, stroke `{Orange}` #F3AB52 w0.5 INSIDE, R8, V g8 p12; children x12.5 because of the 0.5 stroke): 
- `78:1971` > `78:1972` T Medium 10 `{Orange}` " Shareholdings in Marlow Finance Holdings Limited add up to 74.37%, not 100%." (leading space in the text, verbatim)
- `78:1973` "Frame 38" H g2 MIN/CENTER (918x15): person-tag `78:1974` (T `78:1975` "{PERSON_2}") + T `78:1976` " and " + person-tag `78:1977` (T `78:1978` "{PERSON_3}") + T `78:1979` " may be the same person: both hold 43.47% of Marlow Finance Holdings Limited, in different documents. If so, they are counted twice until an analyst resolves it." (szFH, 780 wide)
- `78:1980` "Frame 41" same pattern: `78:1981` ("{PERSON_8}", T `78:1982`), `78:1983` " and ", `78:1984` ("{PERSON_9}", T `78:1985`, tag 57 wide), `78:1986` " may be the same person: both hold 6.96% of Marlow Finance Holdings Limited, in different documents. If so, they are counted twice until an analyst resolves it."
- `78:1987` > `78:1988` "! Screening: 0 of 50 parties have a World-Check report · 50 not screened (marked below)." (contains a middle dot U+00B7)
**Info panel `78:1989`** (943x38, fill `{Purple 15%}` #9081E4@0.15, R8, p12): `78:1990` > `78:1991` "23 small gaps below the 10% threshold" Medium 10 `{Purple}` #9081E4.
Notice panels differ in treatment: critical = filled (Red 25%), warning = outlined (Orange 0.5), info = filled (Purple 15%). Paddings all 12 (+0.5 stroke on the outlined one).

### 3.6 Ownership tree table (`78:1992`)
- Header row `78:1993` 943x24 H g16 SPACE_BETWEEN/CENTER: T `78:1994` "Who owns the client" Medium 10 `{Grey 200}` 95x14 at y5; Tabs 24 instance `78:1995` 126x24 at x817 (main `Tabs 24` `21:401`; track fill `{Grey 400}` R8, szHF): active tab `I78:1995;21:397` "Button" frame 50x24 fill GRAD `{Gradient main oposite}` #53B2ED->#7BE697, R8, H g10 p8/16/8/16, text `I78:1995;21:398` "List" Medium 10 `{Black 900}` 18x14; inactive tab `I78:1995;21:399` 76x24 at x50, text `I78:1995;21:400` "Org chart" Medium 10 `{Grey 300}` 44x14. Only the "List" selection is drawn; the displayed content is the tree below (labelled "List"; the "Org chart" content is not drawn).
- Tree box `78:1996` 943x165, no fill, stroke `{Grey 400}` w1 INSIDE, R8, V g10 p8/16/8/16. Inner: `78:1997` Group 5 (462x147 at 17,9) > `78:1998` Group 4 (462x146 at 17,9) containing 6 row frames and 3 connector lines (children coordinates in Frame 74 space). Rows are absolutely positioned (not auto-layout), row height 16, pitch 26 (16 + 10), indent 24 per level (level 3 is x88, i.e. 23 not 24: record as drawn).
| Row (frame) | Level | x,y | w | Row content (H g40 MIN/CENTER) |
|---|---|---|---|---|
| `78:1999` Frame 67 | 0 | 17,9 | 261 | name block `78:2000` (H g8, 155 wide): icon `78:2001` lucide/building 16x16 (Union `78:2002` fill `{Blue 50%}` 12.01x12.01 at 1.99,1.99; vectors `78:2003` 4x2.5 at 6,5.5 and `78:2004` 11.01x11.01 at 2.49,2.49 stroke `{Blue}` w1 CENTER) + T `78:2005` "CEDAR LOOP, INC." Medium 10 `{White}` + T `78:2006` "100% of the client" Medium 10 `{Grey 300}`; pill `78:2007` (T `78:2008` "Not screened") at x195 |
| `78:2009` Frame 70 | 1 | 41,35 | 408 | name block `78:2010` (g4, 236): icon `78:2011` (`78:2012`,`78:2013`,`78:2014`), T `78:2015` "Marlow Finance Holdings LLC", T `78:2016` "100% of the client"; tag group `78:2017` (g4, 132 at x276): pill `78:2018` (T `78:2019` "Shareholder", purple) + pill `78:2020` (T `78:2021` "Not screened") |
| `78:2022` Frame 71 | 2 | 65,61 | 414 | name block `78:2023` (253): icon `78:2024` (`78:2025`,`78:2026`,`78:2027`), T `78:2028` "Marlow Finance Holdings Limited", T `78:2029` "100% of the client"; tag group `78:2030` (121 at x293): pill `78:2031` (T `78:2032` "Not screened") + pill `78:2033` (T `78:2034` "1 problem", **orange outline** variant) |
| `78:2048` Frame 68 | 3 | 88,87 | 319 | name block `78:2049` (115): icon `78:2050` lucide/circle-user-round 16x16 (Vector `78:2051` 12x12 stroke `{Blue 50%}` w1), person-tag `78:2052` (T `78:2053` "{PERSON_2}") at x20, T `78:2054` "43.47%" `{Grey 300}`; tags `78:2055` (164 at x155): pill `78:2056` (T `78:2057` "UBO", green) + `78:2058` (T `78:2059` "Not screened") + `78:2060` (T `78:2061` "8 problems", red filled) |
| `78:2062` Frame 69 | 3 | 88,113 | 369 | name block `78:2063` (115): icon `78:2064` (Vector `78:2065`), person-tag `78:2066` (T `78:2067` "{PERSON_3}"), T `78:2068` "43.47%"; tags `78:2069` (214 at x155): `78:2070` (T `78:2071` "UBO") + `78:2072` (T `78:2073` "Director", purple) + `78:2074` (T `78:2075` "Not screened") + `78:2076` (T `78:2077` "8 problems", red filled) |
| `78:2035` Frame 72 | 3 | 88,139 | 361 | name block `78:2036` (200): icon `78:2037` (`78:2038`,`78:2039`,`78:2040`), T `78:2041` "Series A Investors", T `78:2042` "16.33% of the client"; tags `78:2043` (121 at x240): `78:2044` (T `78:2045` "Not screened") + `78:2046` (T `78:2047` "1 problem", **red filled** variant) |
Z-order in Group 4 (bottom->top): `78:1999`, `78:2009`, `78:2022`, `78:2035`, `78:2048`, `78:2062` (note `78:2035` at y139 precedes y87/113 rows — document order != visual order). Connector lines (after the rows, on top): `78:2078` Line 16 at (25,27) 129x0 rot -90.00000250447991, `78:2079` Line 17 at (49,54) 102x0 rot -89.99999763, `78:2080` Line 18 at (73,82) 74x0 rot -89.99999765; stroke `{Grey 400}` w1 CENTER. Rotated -90 they are vertical bars: x = 25 / 49 / 73, running from y 27 up... (relativeTransform [[0,-1,25],[1,0,27]]: runs y27 -> y156 for Line 16, y54 -> 156 for Line 17, y82 -> 156 for Line 18, i.e. downward spines for levels 0/1/2 ending at the last row's y156 band); no horizontal elbow connectors are drawn. Spines at x=25/49/73 sit 8 px right of each level's x (17/41/65), under the building icon centre.

### 3.7 Data tables (`78:2081` UBOs, `78:2171` Directors)
Table pattern: caption row (H g16 SPACE_BETWEEN/CENTER 943x24, szFF; caption T Medium 10 `{Grey 200}` at y5) + table frame (943 wide, stroke `{Grey 400}` w1 INSIDE all sides, R8, V g0 p0, szFH, no fill) containing "header row" + body rows. Row frames inner x=1 width 941 (stroke counted), H g0 p0 MIN/CENTER szFH, bottom-only stroke `{Grey 400}` w1 INSIDE (T0 R0 B1 L0). Header row 941x31 (cells 30 high + 1 border), cell = V g0 p8/8/8/8 MIN/MIN szFH, header T Regular 10 `{Grey 300}` #62666D. Body row 941x54 / 52 (cells 53 / 51 + 1 border), cell V g4 p8/8/8/8 szFF; primary value T Regular 12 `{White}` (16h) or a pill; second line a pill (y 27/28).
Last row also carries the bottom border (no last-row special case drawn). No sort arrows, no selected/hover row drawn, no row dividers between columns.
**UBOs table**: caption `78:2083` "UBOs (10% or more)" Medium 10 `{Grey 200}` 94x14. Header row `78:2085`; 8 columns: Share (70.07 wide), then 7 x 124.42 (Name, Date of birth, Nationality, Passport expiry, Proof of address, Address, World-Check) x positions 0, 70.07, 194.49, 318.91, 443.33, 567.74, 692.16, 816.58. Sum 70.07 + 7 x 124.42 = 941.01.
| Header cell id / text id | Text |
|---|---|
| `78:2086` / `78:2087` | Share |
| `78:2088` / `78:2089` | Name |
| `78:2090` / `78:2091` | Date of birth |
| `78:2092` / `78:2093` | Nationality |
| `78:2094` / `78:2095` | Passport expiry |
| `78:2096` / `78:2097` | Proof of address |
| `78:2098` / `78:2099` | Address |
| `78:2100` / `78:2101` | World-Check |
Row 1 `78:2102` (941x54, cells 53 high): `78:2103` T `78:2104` "43.47%"; `78:2105` person-tag `78:2106` (T `78:2107` "{PERSON_2}") + pill `78:2108` "Single Source" (T `78:2109`, **Regular 10**, pill 80x18, p2/8/2/8, orange outline — only pill with 10px text and 18 high); `78:2110` T `78:2111` "-" + red pill `78:2112` (T `78:2113` "Missing"); `78:2114` T `78:2115` "-" + `78:2116`/`78:2117` "Missing"; `78:2118` T `78:2119` "-" + `78:2120`/`78:2121` "Missing"; `78:2122` T `78:2123` "-" + `78:2124`/`78:2125` "Missing"; `78:2126` T `78:2127` "-" + `78:2128`/`78:2129` "Missing"; `78:2130` T `78:2131` "-" + orange-outline pill `78:2132` (T `78:2133` "Not screened").
Row 2 `78:2134` (941x52, cells 51): `78:2135` T `78:2136` "43.47%"; `78:2137` person-tag `78:2138` ("{PERSON_3}", T `78:2139`) + green pill `78:2140` "Confirmed" (T `78:2141`); `78:2142` tag `78:2143` "{DOB}" (T `78:2144`) + orange pill `78:2145` "Single Source" (T `78:2146`, Regular 8, 67x15); `78:2147` tag `78:2148` "{NATIONALITY}" (T `78:2149`, 65 wide) + green `78:2150` "Confirmed" (T `78:2151`); `78:2152` tag `78:2153` "{PASSPORT_EXPIRY}" (T `78:2154`, 87 wide) + green `78:2155` "Confirmed" (T `78:2156`); `78:2157` tag `78:2158` "{DATE}" (T `78:2159`, 35 wide) + red pill `78:2160` "Conflict" (T `78:2161`, 46 wide); `78:2162` tag `78:2163` "{ADDRESS}" (T `78:2164`, 51 wide) + red `78:2165` "Conflict" (T `78:2166`); `78:2167` T `78:2168` "-" + orange `78:2169` "Not screened" (T `78:2170`).
**Directors table**: caption `78:2173` "Directors" 44x14. Header row `78:2175`; 7 columns each 134.43 (0, 134.43, 268.86, 403.29, 537.71, 672.14, 806.57): `78:2176`/`78:2177` Name, `78:2178`/`78:2179` Date of birth, `78:2180`/`78:2181` Nationality, `78:2182`/`78:2183` Passport expiry, `78:2184`/`78:2185` Proof of address, `78:2186`/`78:2187` Address, `78:2188`/`78:2189` World-Check. Row `78:2190` (941x52): cells `78:2191` (tag `78:2192` "{PERSON_3}" T `78:2193` + green `78:2194` "Confirmed" T `78:2195`), `78:2196` (`78:2197` "{DOB}" T `78:2198` + orange `78:2199` "Single Source" T `78:2200`), `78:2201` (`78:2202` "{NATIONALITY}" T `78:2203` + green `78:2204` T `78:2205`), `78:2206` (`78:2207` "{PASSPORT_EXPIRY}" T `78:2208` + green `78:2209` T `78:2210`), `78:2211` (`78:2212` "{DATE}" T `78:2213` + red `78:2214` "Conflict" T `78:2215`), `78:2216` (`78:2217` "{ADDRESS}" T `78:2218` + red `78:2219` "Conflict" T `78:2220`), `78:2221` (T `78:2222` "-" + orange `78:2223` "Not screened" T `78:2224`).
Note the Directors table's first column is Name (a person-tag) whereas the UBOs table has a leading Share column; the Directors row has the same "Name" tag "{PERSON_3}" as the UBO row 2 (a person can be both UBO and director — consistent with the tree).

---

## 4. Runs / Overview — body (`78:2249`, 1500x1068)

### 4.1 Region map (x,y relative to `Frame 62`)
| Region | Id | x,y | w x h | Fill | Stroke | R | Layout |
|---|---|---|---|---|---|---|---|
| Left panel | `78:2250` | 0,0 | 288x**1068** | none | `{Grey 400}` w1 INSIDE | 16 | V g16 p16 szFF (same children as Ownership: caption `78:2251`, cards `78:2252` active (stroke gradient), `78:2257`, `78:2262`; texts `78:2253`..`78:2266`, pct `78:2256` "62%", `78:2261` "41%", `78:2266` "100%") |
| Main column | `78:2267` | 304,0 | 1196x1068 | none | none | 0 | V g13 |
| Summary card | `78:2268` | 0,0 | 1196x307 | `{bg gradient}` | `{Grey 400}` w1 INSIDE | 16 | V g24 p24/32/24/32 — identical to Own `78:1794` incl. steps row `78:2269` and stepper `78:2311` (all 202 compared node pairs equal except 7.1 items) |
| Lower area | `78:2362` | 0,320 | 1196x748 | none | none | 0 | H g1 |
| Sidebar | `78:2363` | 0,0 | 218x501 | none | none | 0 | V g4 p0/16/0/0 — same 14 items as Own (Overview ids = Own + 474, e.g. `78:2364` "Overview" ... `78:2423` "Activity") |
| Right stack "Frame 97" | `78:2424` | 219,0 | 977x748 | none | none | 0 | V g16 p0 CENTER/MIN szHH |
| Card 1 "Review and approval" | `78:2425` (Frame 60) | 0,0 | 977x260 | `{bg gradient}` | `{Grey 400}` w1 INSIDE | 16 | V g8 p16 szFH |
| Card 2 "What you need to do" | `78:2435` (Frame 59) | 0,276 | 977x472 | `{bg gradient}` | `{Grey 400}` w1 INSIDE | 16 | V **g0** p16 szFH |
Arithmetic: 260 + 16 + 472 = 748 ✓. Card 1: 17 + 41 + 8 + 177 + 16 + 1 = 260 ✓. Card 2: 17 + 23 + 0 + 396 + 19 + 16 + 1 = 472 ✓.

### 4.2 Overview ids that differ from Own by structure (not shared)
Id mapping Ownership -> Overview was VERIFIED node by node: pairing the header, left panel, summary card and sidebar sub-trees child-by-child (202 pairs, instance-internal ids included) gives an offset of exactly +474 for all 202 pairs and identical child counts (0 exceptions). Overview has 268 descendants (78:2226..78:2485 plus 7 instance-internal `I…` ids) vs 489 in Ownership. Full real Overview id list: section 4.5 "Node ledger".
**Sidebar active state differs** (see 7.1): in Overview the ACTIVE item is "Overview" `78:2364` (202x33, stroke GRAD `{Gradient main}` w0.5 INSIDE, y0, label `78:2365` at 16.5,8.5 173 wide but still Regular 12 `{Grey 100}` #A6ACB6 — i.e. active frame gets the stroke but the label keeps the inactive style); the other 13 items are 1px lower (y 37,73,109,145,...) and "Ownership" `78:2380` is a normal 202x32 item without stroke but with its label `78:2381` still Medium 12 `{White}` #DCE1E9 at 16,8 (copied from the Ownership screen's active label). Dots frame `78:2382` at x174,y13.

### 4.3 Card 1 "Review and approval" (`78:2425`)
- Title row `78:2426` (943x41, H g309 p0/0/4/0 SPACE_BETWEEN/MIN) > `78:2427` V g4 943x37: T `78:2428` "Review and approval" Medium 14 `{White}` (943x19 szFH), T `78:2429` "71 items are still open: resolve them before sending the run for review." Medium 10 `{Grey 200}`. No toggle on this card.
- Orange panel `78:2430` (943x177 at 17,66, stroke `{Orange}` w0.5 INSIDE, R8, V g8 p12, no fill): `78:2431` > `78:2432` T Medium 12 `{Orange}` "This run needs 4-eyes approval: the first approval sends it to a second approver." (445x16); `78:2433` (918x128, H g4) > `78:2434` T Medium 10 `{Grey 100}` #A6ACB6, line-height 16px (fixed), 918x128 szFH, one paragraph: "Critical item “Legal Entity type” is in conflict and not resolved by an analyst. Critical item “Registered address” is in conflict and not resolved by an analyst. Critical item “Licensing / registration number” is in conflict and not resolved by an analyst. 22 parties have no World-Check report: {PERSON_18}, Hollis Family Trust, Rowan Investments Pty Ltd, {PERSON_17}, Whitlock Family Trust and 17 more. Wallet TExampleWalletAddressNotReal000001 needs an exposure assessment: OFAC Sanctioned Entity 0.04%; rule “Sanctioned, TF & CSAM (Criminal Organization, Exchange, FinCEN Primary Money Laundering Concern, OFAC Sanctioned Entity)”. The ownership structure has 1 gap that could hide a UBO." (curly quotes U+201C/U+201D; the paragraph is one text node with no inline emphasis; the 4-eyes headline is the Orange line above).

### 4.4 Card 2 "What you need to do" (`78:2435`)
Title row `78:2436` (943x23, H g309 p0/0/4/0) > T `78:2437` "What you need to do" Medium 14 `{White}` (943x19, szFF). Action list `78:2438` "Frame 99" 943x396 at 17,40, V g0 p0 (12 rows x 33 = 396): each row H g8 p8/0/8/0 MIN/CENTER (or SPACE_BETWEEN with a link), 943x33, stroke bottom-only `{Grey 400}` w1 INSIDE, no fill, szFH; left: 6x6 Orange ellipse (`{Orange}` #F3AB52 fill, 14px offset incl. gap 8) + T Medium 12 `{White}` (16h); right (rows with links): T Medium 10 `{Blue}` #59BCFA "Go to … >" right-aligned (x ends at 943). In link rows the dot+text are wrapped in "Frame 98" H g8 (hug).
| Row | Frame id | y | Dot id | Label T id / text | Link T id / text |
|---|---|---|---|---|---|
| 1 | `78:2439` Frame 37 | 0 | `78:2440` | `78:2441` "Resolve 6 conflicting values" | — |
| 2 | `78:2442` Frame 45 | 33 | `78:2444` (in `78:2443`) | `78:2445` "22 parties have no World-Check report" | `78:2446` "Go to Ownership > " (86x14 at 857) |
| 3 | `78:2447` Frame 46 | 66 | `78:2448` | `78:2449` "3 items weren't found in the documents" | — |
| 4 | `78:2450` Frame 48 | 99 | `78:2451` | `78:2452` "5 documents are out of date" | — |
| 5 | `78:2453` Frame 50 | 132 | `78:2454` | `78:2455` "Check 3 values ECHO couldn't read clearly" | — |
| 6 | `78:2456` Frame 52 | 165 | `78:2457` | `78:2458` "Check 10 values found in only one source" | — |
| 7 | `78:2459` Frame 56 | 198 | `78:2461` (in `78:2460`) | `78:2462` "Resolve a gap in the ownership graph that could hide a UBO" | `78:2463` "Go to Ownership > " |
| 8 | `78:2464` Frame 47 | 231 | `78:2465` | `78:2466` "Answer 1 item only a person can fill" | — |
| 9 | `78:2467` Frame 57 | 264 | `78:2469` (in `78:2468`) | `78:2470` "5 documents to request from the client" | `78:2471` "Go to Documents provided > " (133x14 at 810) |
| 10 | `78:2472` Frame 58 | 297 | `78:2474` (in `78:2473`) | `78:2475` "Write the exposure assessment for 1 wallet with sanctions-related exposure" | `78:2476` "Go to Wallets > " (71x14 at 872) |
| 11 | `78:2477` Frame 59 | 330 | `78:2479` (in `78:2478`) | `78:2480` "1 wallet address fails its checksum" | `78:2481` "Go to Wallets > " |
| 12 | `78:2482` Frame 55 | 363 | `78:2483` | `78:2484` "Review 22 inconsistencies" | — |
Footer note `78:2485` T Medium 10 `{Grey 200}` "Still to come: reading what each World-Check report found, and the risk rating (section 15)" 943x19 at 17,436, szFF (child of the card, after the list, no divider). Note "Resolve 6 conflicting values" vs Ownership summary "19 conflicting values"/"Review 22 inconsistencies": the numbers on one screen are not reconciled (placeholder copy). All dot colours in this list are Orange; no Red/Green rows.
Straight apostrophes in "weren't"/"couldn't" (ASCII); curly quotes only in `78:2434`.

---

### 4.5 Node ledger — Runs / Overview (`78:2225`), every descendant (all ids real, read from the frame; 268 nodes)
Types: F frame, T text, E ellipse, V vector, L line, G group, B boolean operation, I instance. Parent in brackets. Ownership twin = id - 474 (verified).
| Ids | Name | Type | Role |
|---|---|---|---|
| `78:2226` | Frame 8 | F | header [2225] |
| `78:2227` | Frame 7 | F | logo box [2226] |
| `78:2228` | Group 1 | G | logo group [2227] |
| `78:2229` | Union | B | logo Union [2228] |
| `78:2230`, `78:2231`, `78:2232`, `78:2233` | Vector | V | wordmark glyphs #4DFFCD raw, children of Union [2229]: 68.46,6 16.54x20; 49.37,6 16.54x20; 31.55,6 15.27x20; 15,6 14x20 |
| `78:2234`, `78:2235`, `78:2236` | Line 1/2/3 | L | logo lines [2228], rotation -90, Blue 75/50/25% w1.5 |
| `78:2237` | Frame 1 | F | nav container [2226] |
| `78:2238` / `78:2239` | Frame 3 / Pipeline | F/T | nav item (inactive, R24) |
| `78:2240` / `78:2241` | Frame 2 / Runs | F/T | nav item ACTIVE (R8, gradient stroke 0.5, Medium 12) |
| `78:2242` / `78:2243` | Frame 4 / Wallet check | F/T | nav item |
| `78:2244` / `78:2245` | Frame 5 / System health | F/T | nav item |
| `78:2246` / `78:2247` | Frame 6 / Admin Dashboard | F/T | nav item |
| `78:2248`; `I78:2248;9:137`, `I78:2248;18:308`, `I78:2248;18:310`, `I78:2248;18:311` | Select; Select (T "Local Developer"); Frame 11; arrow-down x2 | I; T; F; V; V | Select instance [2226] and its internals |
| `78:2249` | Frame 62 | F | content frame [2225] |
| `78:2250` | Frame 58 | F | left panel [2249] |
| `78:2251` | Recent Runs | T | caption [2250] |
| `78:2252` / `78:2253` / `78:2254` / `78:2255` / `78:2256` | Frame 56 / Frame 55 / CEDAR LOOP, INC. / Needs analyst / 62% | F/F/T/T/T | run card 1 ACTIVE, left stack, title, status, pct |
| `78:2257` / `78:2258` / `78:2259` / `78:2260` / `78:2261` | Frame 57 / Frame 55 / ALDER PEAK PTY LTD / ECHO processing / 41% | F/F/T/T/T | run card 2 |
| `78:2262` / `78:2263` / `78:2264` / `78:2265` / `78:2266` | Frame 58 / Frame 55 / "Company  LTD" (two spaces) / Approved / 100% | F/F/T/T/T | run card 3 |
| `78:2267` | Frame 61 | F | main column [2249] |
| `78:2268` | Frame 36 | F | summary card [2267] |
| `78:2269` | Frame 35 | F | steps row [2268] |
| `78:2270` / `78:2271` / `78:2272` / `78:2273` | Group 3 / Frame 4 / 62% / 60 out of 116 | G/F/T/T | donut group, centre label stack, "62%" (Jura 38 mixed), caption |
| `78:2274` / `78:2275` / `78:2276` | Group 2 / Ellipse 1 / Ellipse 2 | G/E/V | donut inner group [2270], track ellipse, arc vector (drop shadow) — `78:2274` is the "Overview-only duplicate" cited by the components harvester |
| `78:2277` / `78:2278` / `78:2279` / `78:2280` | Frame 34 / Frame 33 / CEDAR LOOP, INC. / Frame 32 | F/F/T/F | info column, heading row, heading, button group |
| `78:2281`; `I78:2281;18:287`, `I78:2281;18:282` | Outline Button + icon; Vector; Button (T "Checklist.docx") | I; V; T | instance [2280] |
| `78:2282`; `I78:2282;10:169` | CTA Button; Button (T "Re-Run KYC Check") | I; T | instance [2280] |
| `78:2283` / `78:2284` / `78:2285` | Frame 57 / Still Open: / Frame 30 | F/T/F | "Still Open:" block, label, columns row |
| `78:2286` / `78:2287` `78:2288` / `78:2289` `78:2290` / `78:2291` `78:2292` / `78:2293` `78:2294` | Frame 27 (col A) then Frame 23/24/26/25 + their T | F/F+T | col A: 19 conflicting values; 1 ownership structure incomplete; 4 missing documents; 1 out-of-date document |
| `78:2295` / `78:2296` `78:2297` / `78:2298` `78:2299` / `78:2300` `78:2301` / `78:2302` `78:2303` | Frame 28 (col B) then rows | F/F+T | col B: 11 values not found; 3 parties or wallets not screened; 3 need analyst approval (one source); 4 need analyst approval (client-declared only) |
| `78:2304` / `78:2305` `78:2306` / `78:2307` `78:2308` / `78:2309` `78:2310` | Frame 29 (col C) then rows | F/F+T | col C: 4 drafts to accept or edit; 1 item for the analyst to write; 4 inconsistencies to check |
| `78:2311` | Frame 22 | F | stepper [2268] |
| `78:2312`, `78:2313`, `78:2314`, `78:2315`, `78:2316`, `78:2317` | Line 4, 11, 12, 13, 14, 15 | L | connectors (2312/2313 Gradient main oposite; 2314 raw #54B3E9->#F3892D; 2315-2317 Grey 400) |
| `78:2318` / `78:2319` / `78:2320` / `78:2321` / `78:2322` / `78:2323` | Frame 54 / Triggered / Frame 11 / Union / Ellipse 3 / Vector | F/T/F/B/E/V | step 1 DONE |
| `78:2324` / `78:2325` / `78:2326` / `78:2327` / `78:2328` / `78:2329` | Frame 53 / Gathering documents / Frame 11 / Union / Ellipse 3 / Vector | F/T/F/B/E/V | step 2 DONE |
| `78:2330` / `78:2331` / `78:2332` / `78:2333` / `78:2334` / `78:2335` | Frame 52 / ECHO processing / Frame 11 / Union / Ellipse 3 / Vector | F/T/F/B/E/V | step 3 DONE |
| `78:2336` / `78:2337` / `78:2338` / `78:2339` / `78:2340` / `78:2341` / `78:2342` / `78:2343` | Frame 51 / Needs analyst / Frame 13 / Union / Ellipse 4 (dashed) / Ellipse 5 / lucide/check / Vector | F/T/F/B/V/V/F/V | step 4 CURRENT |
| `78:2344` / `78:2345` / `78:2346` / `78:2347` / `78:2348` / `78:2349` | Frame 50 / Awaiting review / Frame 11 / Ellipse 3 / lucide/check / Vector | F/T/F/E/F/V | step 5 PENDING |
| `78:2350` / `78:2351` / `78:2352` / `78:2353` / `78:2354` / `78:2355` | Frame 49 / Awaiting 4-eyes / Frame 11 / Ellipse 3 / lucide/check / Vector | F/T/F/E/F/V | step 6 PENDING |
| `78:2356` / `78:2357` / `78:2358` / `78:2359` / `78:2360` / `78:2361` | Frame 48 / Approved / Frame 11 / Ellipse 3 / lucide/check / Vector | F/T/F/E/F/V | step 7 PENDING |
| `78:2362` | Frame 60 | F | lower area [2267] |
| `78:2363` | Frame 1 | F | sidebar list [2362] |
| `78:2364`/`78:2365` | Frame 3 / Overview | F/T | sidebar item 1 ACTIVE (no dots) |
| `78:2366`/`78:2367`, dots `78:2368` (`78:2369` Red, `78:2370` Orange) | Frame 16 / General information | F/T | item 2 |
| `78:2371`/`78:2372`, dots `78:2373` (`78:2374` Green) | Frame 17 / Business | F/T | item 3 |
| `78:2375`/`78:2376`, dots `78:2377` (`78:2378` Red, `78:2379` Orange) | Frame 18 / Regulation | F/T | item 4 |
| `78:2380`/`78:2381`, dots `78:2382` (`78:2383` Red, `78:2384` Orange) | Frame 23 / Ownership | F/T | item 5 (inactive; label keeps Medium White) |
| `78:2385`/`78:2386`, dots `78:2387` (`78:2388` Orange) | Frame 19 / Funds and wealth | F/T | item 6 |
| `78:2389`/`78:2390`, dots `78:2391` (`78:2392` Red, `78:2393` Orange) | Frame 20 / Financials | F/T | item 7 |
| `78:2394`/`78:2395`, dots `78:2396` (`78:2397` Green) | Frame 21 / Trading | F/T | item 8 |
| `78:2398`/`78:2399`, dots `78:2400` (`78:2401` Orange) | Frame 22 / Comments | F/T | item 9 |
| `78:2402`/`78:2403`, dots `78:2404` (`78:2405` Red, `78:2406` Orange) | Frame 24 / Wallets | F/T | item 10 |
| `78:2407`/`78:2408`, dots `78:2409` (`78:2410` Red, `78:2411` Orange) | Frame 25 / Country risk | F/T | item 11 |
| `78:2412`/`78:2413`, dots `78:2414` (`78:2415` Red, `78:2416` Orange) | Frame 26 / Documents provided | F/T | item 12 |
| `78:2417`/`78:2418`, dots `78:2419` (`78:2420` Red, `78:2421` Orange) | Frame 27 / Files | F/T | item 13 |
| `78:2422`/`78:2423` | Frame 15 / Activity | F/T | item 14 |
| `78:2424` | Frame 97 | F | right stack [2362] |
| `78:2425`..`78:2434` | see 4.3 | | card 1 (`78:2426` title row, `78:2427` Frame 43 title stack, `78:2428`/`78:2429` texts, `78:2430` orange panel, `78:2431`/`78:2432`, `78:2433`/`78:2434`) — `78:2427` is the "Overview duplicate" cited by the components harvester: the title-stack Frame 43 (Ownership twin `78:1952`) |
| `78:2435`..`78:2485` | see 4.4 | | card 2 and action list (all ids listed in the 4.4 table plus wrappers `78:2438`, `78:2443`, `78:2460`, `78:2468`, `78:2473`, `78:2478`) |
Note on the harvester cross-references: `78:2572` is a Pipeline node (not in either Runs frame); the Runs-frame equivalents are `78:2274` (donut inner group) and `78:2427` (card-1 title stack).

### 4.6 Node ledger — Runs / Ownership ids not described elsewhere
| Ids | Name | Type | Role |
|---|---|---|---|
| `78:1756`, `78:1757`, `78:1758`, `78:1759` | Vector | V | wordmark glyphs of the logo Union `78:1755`, fill raw #4DFFCD (r0.302 g1 b0.804): 68.46,6 16.54x20; 49.37,6 16.54x20; 31.55,6 15.27x20; 15,6 14x20 |
(Ownership Left panel/summary/sidebar/body nodes are all itemised in sections 3.1-3.7; header ids in section 2.)

## 5. Component instances used (main components live on `drafts` `3:10845`; internals belong to components harvester)
| Instance (Own id / Ov id) | Main component | Variant | Overrides / size | Screen |
|---|---|---|---|---|
| Select `78:1774` / `78:2248` | `Select` `10:170` (COMPONENT) | single | label "Local Developer"; 162x32 (was 148 before the 2026-11-16 font change) (component 104x32); hug-x, fill-y; gap 32; p8/12/8/12 | header, both |
| Outline Button + icon `78:1807` / `78:2281` | `Property 1=Default` `18:289` in set `Outline Button + icon` `18:290` | Default | text "Checklist.docx"; 142x32 | summary card, both |
| CTA Button `78:1808` / `78:2282` | `Property 1=Default` `18:142` in set `CTA Button` `18:248` | Default | text "Re-Run KYC Check"; 154x32 | summary card, both |
| Tabs 24 `78:1995` | `Tabs 24` `21:401` | single (first tab active) | "List" active / "Org chart"; 126x24 | Ownership only |
| toggle w text `78:1955` | `Property 1=off` `21:56` in set `toggle w text` `21:55` | off | text "Show Confidential Details"; 183x16 | Ownership only |
No other instances. Not drawn: Select open, hover variants (Outline `18:253`, CTA overlay `18:249`), toggle on, Tabs 24 second tab active, Search/Input components (absent from Runs screens).

---

## 6. Repeating patterns (summary with exact values)
| Pattern | Values | Evidence |
|---|---|---|
| Panel (outline card) | no fill, stroke `{Grey 400}` 1 INSIDE, R16, p16, V g16 | `78:1776`, `78:2250` |
| Gradient card | `{bg gradient}`, stroke `{Grey 400}` 1 INSIDE, R16; p24/32 (summary) or p16 (detail) | `78:1794`, `78:1950`, `78:2425`, `78:2435` |
| Run card | 254x50, `{Grey 500}`, R8, p8/16, g36, stroke `{Grey 400}` 1 (active: `{Gradient main}` 1) | `78:1778`.. |
| Notice panels | filled R8 p12 (critical `{Red 25%}`, info `{Purple 15%}`) or outlined `{Orange}` 0.5 INSIDE | `78:1957`, `78:1989`, `78:1970`, `78:2430` |
| Pills (status) | h15, R4, H p2/8/2/8 g10, T Regular 8; filled variants Red 25% / Green 25% / Purple 15%; outlined `{Orange}` 0.5 OUTSIDE; one 18-high "Single Source" with Regular 10 | `78:2007`, `78:2046`, `78:2056`, `78:2018`, `78:2108` |
| Person/data tag | 15 high, R4, fill `{Blue 15%}`, p2/4/2/4, text Medium 8 `{Blue}` at node opacity 0.7; text placeholders {PERSON_n}, {DOB}, {NATIONALITY}, {PASSPORT_EXPIRY}, {DATE}, {ADDRESS} | `78:1974`, `78:2106`, `78:2143` |
| Table | frame stroke `{Grey 400}` 1 INSIDE R8 V g0; header row 31; body row 52–54; cell p8; cell texts Regular 10 / Regular 12 | `78:2084`, `78:2174` |
| Sidebar filter item | 202x32, R8, p8/12/8/16, label Regular 12 `{Grey 100}`, dots 6x6 g4 | `78:1890`.. |
| Action row | 943x33, bottom border `{Grey 400}` 1, p8/0, dot 6x6 + g8 + Medium 12 label, link Medium 10 `{Blue}` | `78:2439`.. |
| Stepper | circle 40, label Regular 12 below (y52), connectors 136x0 w2; 3 states | `78:1837` |
| Donut ring | 140x140, track stroke 8 `{Grey 500}` value, arc stroke 8 raw gradient, round cap, drop shadow | `78:1796` |
| Tabs 24 | see 3.6 | `78:1995` |
| Toggle | see 3.5 | `78:1955` |
Progress rings are "data-driven" only in the sense of a hand-drawn arc vector; no variable/component property drives them.

---

## 7. Cross-screen consistency (Ownership vs Overview)
### 7.1 Structural diff (202 node pairs: header, left panel, summary card, sidebar)
| Region | Result |
|---|---|
| Header `78:1752` vs `78:2226` | 0 differences (names, x/y/size, fills/strokes/style ids, text, fonts) |
| Summary card `78:1794` vs `78:2268` | 0 differences (all descendants incl. stepper, donut, buttons, issue columns) |
| Left panel `78:1776` vs `78:2250` | only height 1161 vs 1068; children identical |
| Sidebar `78:1889` vs `78:2363` | differences = active-state swap: Own item 1 "Overview" plain 202x32 / item 5 "Ownership" active; Ov item 1 "Overview" active 202x33 with gradient stroke, label still Regular 12 `{Grey 100}`; Ov item 5 "Ownership" no stroke 202x32 but label Medium 12 `{White}`; all other rows 1px lower (y+1) in Ov because the active item is 33 high |
### 7.2 Layout differences
| Item | Ownership | Overview |
|---|---|---|
| Content frame | 1500x1161 | 1500x1068 |
| Lower area | 1196x841: sidebar + one detail card 977x841 | 1196x748: sidebar + stack of 2 cards 977x260 + 977x472 (g16, Frame 97 HUG) |
| Detail content | title + 3 notice panels + org tree (List/Org chart tabs) + UBOs table + Directors table + toggle | Review & approval card (orange 4-eyes panel + paragraph) + "What you need to do" action list |
| Header copy | identical | identical |

---

## 8. ASCII reconstruction sketches
Not to scale; sizes from sections above.
### 8.1 Runs / Ownership 1920x1293 (bg #08090A)
```
x=0                                                              x=1920
+-------------------------------------------------------------------------------+ y=0
| HEADER 1920x66 (bottom 1px #111213)                                           |
| [logo 162x32 @40,16.5]      [nav 643x33 @645.5,16]      [Select 148x32 @1732] |
+-------------------------------------------------------------------------------+ y=66
|  (24 gap)                                                                     |
|   x=210                                                              x=1710   |
|  +----------+ 16 +-----------------------------------------------------------+ | y=90
|  |Recent Runs|   | SUMMARY CARD 1196x307 (bg gradient, R16, p24/32)          | |
|  | 288x1161  |   |  [donut 140]  CEDAR LOOP, INC.   [Checklist.docx] [Re-Run KYC]   | |
|  | R16 1px   |   |   62%         Still Open:  3 issue columns (64 gap)       | |
|  | p16       |   |  ---------------------------------------------------------| |
|  | [run card]|   |  stepper 1130x68: o--o--o--(o)..o..o..o  (7 steps)        | |
|  | 254x50 x3 |   +-----------------------------------------------------------+ |
|  |           |  13 gap                                                       | | y=410
|  |           |   +---------+1+---------------------------------------------+  | |
|  |           |   |sidebar  |  | DETAIL CARD 977x841 (bg gradient, R16, p16) |  | |
|  |           |   |218x501  |  | title+toggle(41) / notices 257 / tree 197   |  | |
|  |           |   |14 items |  | UBOs table 167 / Directors table 113        |  | |
|  +----------+    +---------+  +---------------------------------------------+  | | y=1251
|                                                                               | (42 bottom)
+-------------------------------------------------------------------------------+ y=1293
```
### 8.2 Runs / Overview 1920x1293
```
+-------------------------------------------------------------------------------+ y=0
| HEADER 1920x66 (identical)                                                    |
+-------------------------------------------------------------------------------+ y=66
|  +----------+    +-----------------------------------------------------------+ | y=90
|  |Recent Runs|   | SUMMARY CARD 1196x307 (identical to Ownership)            | |
|  | 288x1068  |   +-----------------------------------------------------------+ |
|  |  3 cards  |   +---------+1+---------------------------------------------+  | | y=410
|  |           |   |sidebar  |  | CARD 1 977x260: Review and approval         |  | |
|  |           |   |218x501  |  |  orange 4-eyes panel + paragraph            |  | |
|  |           |   |Overview |  +---------------------------------------------+  | |
|  |           |   |is active|  16 gap                                           | |
|  |           |   |         |  | CARD 2 977x472: What you need to do (12 rows)|  | |
|  +----------+    +---------+  +---------------------------------------------+  | | y=1158
|                                                                               | (135 empty)
+-------------------------------------------------------------------------------+ y=1293
```

---

## 9. Conflicts and decisions needed
| Topic | Option A (node ids, value) | Option B (node ids, value) | Chosen / recommendation | Needs owner? |
|---|---|---|---|---|
| Sidebar active-item styling | Ownership screen: active item "Ownership" `78:1906` = stroke Gradient main 0.5 + label Medium 12 `{White}` | Overview screen: active item "Overview" `78:2364` = same stroke but label Regular 12 `{Grey 100}` (`78:2365`); inactive "Ownership" `78:2380` has the active label style (Medium 12 `{White}`, `78:2381`) without stroke | Treat Ownership screen as the reference (stroke + Medium White label = active). Overview looks like a copy/paste slip in the label styles | yes |
| Active nav pill gradient | Runs screens use `{Gradient main}` #7BE697->#53B2ED (`78:1766`, `78:2240`) | Pipeline/Wallet use `{Gradient main oposite}` (foundations) | Reproduce as drawn per screen; component decision pending (foundations item) | yes |
| Nav label weight | "Runs" Medium 12 (`78:1767`) while others Regular 12 | — | reproduce as drawn | yes (foundations) |
| Donut label vs arc | label "62%" and "60 out of 116" (`78:1798`, `78:1799`; 60/116 = 51.7%) | arc `78:1802` stroke covers ~62% of the ring (path starts at top) | Reproduce both as drawn; flag mismatch (placeholder data) | no (note) |
| Left panel percentages vs donut | Run card 1 "62%" (`78:1782`) matches donut "62%" | card 2 "41%", card 3 "100%" | consistent | no |
| Copy typos | `78:1963`, `78:1966`, `78:1969` "12.86% of the client)" / "12.50% of the client)" missing "("; `78:1960` has "(16.33% of the client)" | `78:1790` "Company  LTD" double space; `78:1972` leading space; `78:1976`/`78:1979` leading/trailing spaces; `78:2446` trailing space "Go to Ownership > " | Reproduce verbatim | no |
| Pill type scale | Regular 8 in 15-high pills (most) | `78:2108` "Single Source" Regular 10 in 18-high pill (UBO row 1) | Reproduce; the 10/18 variant is likely an inconsistency | yes |
| Orange pill variants | outlined (`78:2007`, `78:2033` "1 problem") | red-filled "1 problem" (`78:2046`) — same text, two treatments | reproduce as drawn | yes |
| Tree connector geometry | vertical spines only at x 25/49/73 (`78:2078`..`78:2080`) | no horizontal elbows | reproduce as drawn | no |
| Level indent | levels 0..2 step 24 (17,41,65) | level 3 at x88 (step 23) | reproduce | no |
| Info column spacing | itemSpacing 24 but SPACE_BETWEEN gives 12 (`78:1803`) | — | use 12 (measured y44) | no |
| Overview vertical slack | bottom gap 135 vs 42 on Ownership | — | frame height fixed 1293 | no |
| Activity item padding | `78:1948` p8/16/8/16 | other items p8/12/8/16 | reproduce | no |

## 10. GAPS / NOT FOUND IN THE DESIGN (searched; absent as designed states)
| Area | Finding | How searched | Scope searched |
|---|---|---|---|
| Hover states (table rows, sidebar items, run cards, action rows, links) | not drawn; only the Runs-screen CTA/Outline instances are Default variants | variant names on all 5 instances (`Property 1=…`); enumerated all nodes in both frames | `78:1751`, `78:2225` |
| Selected row / expanded row / sort arrows / column filters in tables | not drawn (only the "List" tab selection and the active sidebar/run card) | walked both table frames node by node, names/strokes | `78:2084`, `78:2174` |
| "Org chart" tab content | not drawn (tab inactive; only List/tree view) | tab instance `78:1995` + siblings | `78:1992` |
| Toggle ON state | not drawn (instance is `off`) | `78:1955` variant `21:56` | Ownership |
| Select open dropdown | not drawn | header instance `78:1774`/`78:2248`, siblings | both |
| Empty / loading / skeleton | none | node names and text content | both |
| Error / validation (inputs) | none (no inputs on these screens); issue colours exist as text/pill colours only | node types (no Input/Search instances) | both |
| Toast / tooltip / modal / popover / scrim | none | no overlay frames among top-level children; frames have only header+content | both |
| Scrolling / overflow | none drawn; Ownership content is a fixed 1161 frame, Overview 1068; no scrollbars | clipsContent flags, child bounds vs parent | both |
| Other run cards beyond 3 / pagination | none | left panel child list | `78:1776`, `78:2250` |
| Responsive / breakpoints | only 1920-wide frames | frame sizes | both |
| Motion / prototyping | not read (no reactions/interactions inspected) | not searched — Plugin API `reactions` was not queried | — |
| Text styles / variables on these frames | none (0 text styles, no variable bindings except the stray radius var on the logo Union `78:1755` / Ov `78:2229`) | `textStyleId`, `boundVariables` via walker/dump fields | both |
| Not harvested | (a) drafts copies `4:15408` / `63:712` not re-walked (foundations reports identical); (b) per-instance component internals (components harvester); (c) full text of every ownership-tree row not re-read beyond the compact walk, but all texts above are from node names/characters; (d) Overview ids for header/left panel/summary/sidebar: the +474 mapping was subsequently verified for all 202 pairs and the real ids are listed in 4.5; (e) `Group 3`/`Group 2` children positions are in frame space as returned by the API; (f) no rate-limit incidents occurred | — | — |
