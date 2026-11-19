# Echo — Component Reference
HTML + usage notes for every component. Use these exact patterns — do not write new CSS for anything listed here.
Source: design file `Echo`, "final (screens) + drafts (components)" (extracted 2026-11-16). Components marked **EXTENDED** are not drawn in the design (see the table at the end). **There are 42 (all approved by the owner, 2026-11-16 to 2026-11-18).**

Load order on every page (paths relative to your page; keep `assets/` next to `components.css`):
```html
<link rel="stylesheet" href="design-system/fonts.css">
<link rel="stylesheet" href="design-system/tokens.css">
<link rel="stylesheet" href="design-system/components.css">
```
The design is dark only (screen background `Black 900`), desktop-only at a fixed 1920 px frame width. States drawn by the design are built; states the design does not draw (focus, disabled, error, pressed, open Select list, hover for Select/Search/Input/Tabs/toggles/nav) do not exist here and are not invented.

Index: [Text and type](#text-and-type) · [Icons](#icons) · Controls: [CTA button](#cta-button) · [Outline button](#outline-button) · [Outline button with icon](#outline-button-with-icon) · [Select](#select) · [Search](#search) · [Input](#input) · [Tabs](#tabs) · [Toggle](#toggle-and-toggle-with-text) · Patterns: [Pill](#status-pill--person-tag) · [Dot](#status-dot) · [KPI card](#kpi-card) · [Panel](#panel) · [Row card](#row-card) · [Notice](#notice) · [Step chip](#step-chip) · [Nav pill](#nav-pill) · Layout: [Helpers](#layout-helpers) · [Shell](#shell-screen-frame-header-photo-layer) · [Section head](#section-head) · [Data table](#data-table) · [Ownership tree](#ownership-tree) · [Stepper](#stepper) · [Ring and donut](#progress-ring-and-donut) · [Filter list](#filter-list-sidebar) · [Action list](#action-list) · [Side panel](#side-panel) · [Row card extras](#row-card-extras) · [Summary card](#summary-card) · [Detail card](#detail-card) · [Screens](#screen-compositions)

---

## Text and type
Design: Manrope (Regular 400 / Medium 500) for UI text, Jura (Light 300 / Medium 500 / SemiBold 600) for numerals; letter-spacing 0; line-height auto (one exception: the long paragraph `78:2434`, 16 px). Every real size/weight tuple has one class.

| Class | Font | Used for (node) |
|---|---|---|
| `.type-pill-10` | Manrope Regular 10 | pills (`78:2008`; Figma draws 8, owner raised to 10) |
| `.type-tag-10` | Manrope Medium 10 | person tag (`78:1975`; Figma draws 8, owner raised to 10) |
| `.type-field-10` | Manrope Regular 10 | table header cells, "Single Source" pill, counts (NOT Select/Search/Input text: those are now `.type-label-10`, Medium) (`73:1664`, `78:2087`) |
| `.type-label-10` | Manrope Medium 10 | sub-lines, notice text, tab 24 (`78:2539`, `21:398`) |
| `.type-paragraph-10` | Manrope Medium 10 / 16px | long paragraph (`78:2434`) |
| `.type-body-12` | Manrope Regular 12 | body, nav, labels (`78:2501`) |
| `.type-title-12` | Manrope Medium 12 | buttons, card titles, tabs 32 (`10:169`, `21:380`) |
| `.type-heading-14` | Manrope Medium 14 | panel / company titles (`78:2535`) |
| `.type-heading-16` | Manrope Medium 16 | page headings (`78:2513`) |
| `.type-numeral-38` / `-20` / `-14` / `-12` | Jura Medium 38 / 20 / 14, SemiBold 12 | KPI + donut, ring, percentages, donut caption |
| `.numeral-light` | Jura Light | the `%` glyph inside ring / donut labels |

Text colour classes: `.text-primary` (White #DCE1E9, the default body colour) · `.text-label` (Grey 100) · `.text-secondary` (Grey 200) · `.text-muted` (Grey 300) · `.text-inverse` (Black 900) · `.text-accent` (Blue) · `.text-danger` (Red) · `.text-warning` (Orange) · `.text-success` (Green) · `.text-info` (Purple).

```html
<div class="stack stack--g8">
  <span class="type-heading-16">Page heading — Medium 16</span>
  <span class="type-heading-14 text-muted">Sub heading — Medium 14, Grey 300</span>
  <span class="type-body-12">Body — Regular 12</span>
  <span class="type-title-12 text-label">Title — Medium 12, Grey 100</span>
  <span class="type-field-10 text-muted">Table header — Regular 10, Grey 300</span>
  <span class="type-label-10 text-secondary">Label — Medium 10, Grey 200</span>
  <span class="type-numeral-38 text-accent">62<span class="numeral-light">%</span></span>
  <span class="type-numeral-14 text-success">100%</span>
</div>
```
Notes: only the weights above exist in the design — do not use bold or other sizes. The design name "White" is the value #DCE1E9 (not #FFFFFF).

---

## Icons
Design: icons exist only as the files in `assets/` (see `assets/MANIFEST.md`). Monochrome icons are masks coloured by `currentColor`; coloured/gradient assets are `<img>`. Never redraw paths.

| Icon | Markup | Size / colour |
|---|---|---|
| download (`18:287`) | `<span class="icon icon--download"></span>` | 11x13, Grey 200 |
| circle-exclamation-point (`78:2537`) | `<span class="icon icon--exclamation"></span>` | 12x12, Orange |
| building (`78:2001`) | `<span class="icon icon--building"></span>` | 16x16, Blue (0.5 opacity is baked into the file) |
| circle-user-round (`78:2050`) | `<span class="icon icon--user-round"></span>` | 16x16, Blue (0.5 baked in) |
| select chevron (`18:308`) | `<img class="select__chevron" src="assets/select-chevron-down.svg" alt="">` | 16x16 gradient asset |
| search (`73:1665`) | `<img class="search__icon" src="assets/search.svg" alt="">` | 16x16 gradient asset |
| logo (`78:2490`) | `<img src="assets/logo.svg" alt="Echo">` inside `.app-header__logo` | 85x20 |
| step status (`78:1846`...) | **built in CSS, no image**: `<div class="step__icon step__icon--done|--current|--pending"></div>` (see Stepper) | 42x42 |
| progress rings | `assets/progress-ring-72-short.svg`, `-72-long.svg`, `-140.svg` as `<img>` | static |

```html
<div class="hstack hstack--g16">
  <span class="icon icon--download"></span>
  <span class="icon icon--exclamation"></span>
  <span class="icon icon--building"></span>
  <span class="icon icon--user-round"></span>
  <img class="select__chevron" src="assets/select-chevron-down.svg" alt="">
  <img class="search__icon" src="assets/search.svg" alt="">
</div>
```
Not in the design (searched): close, plus, minus, arrows, checkbox/radio glyphs, calendar, avatars, flags. Do not add them.

---

## CTA button
Design: `18:142` (set `18:248`), hover `18:249` · 32 high, radius 8, hug width, padding 0/24, label Manrope Medium 12 Black 900 on White fill. Hover = brand gradient fill (`#53B2ED -> #7BE697`). States: real `:hover` and forced `.is-hover`. No focus/disabled/pressed in the design.

```html
<button type="button" class="btn btn--cta">Run KYC Check</button>
```
```html
<button type="button" class="btn btn--cta is-hover">Run KYC Check</button>
```
Notes: HUG width; the label text is an override in each instance ("Run KYC Check", "Re-Run KYC Check", "Add Wallet and Screen").

---

## Outline button
Design: `18:227` (set `18:242`), hover `18:253` · 32 high, radius 8, 0.5 px stroke White (#DCE1E9, centre stroke, inset here), label White (owner changed the colour from Grey 200 and the stroke from 1 px to 0.5 px on 2026-11-17, Figma `18:227` / `18:289`; hover ring 0.5 px as well; disabled keeps 1 px). Hover: 3-stop gradient stroke + gradient label — the label MUST be in `<span class="btn__label">`. Not used on the final screens (definition only).

```html
<button type="button" class="btn btn--outline"><span class="btn__label">Button</span></button>
```
```html
<button type="button" class="btn btn--outline is-hover"><span class="btn__label">Button</span></button>
```

---

## Outline button with icon
Design: `18:289` (set `18:290`), hover = variant `Variant2` `18:291` · padding 0/20/0/16, gap 12, icon first (11x13 download glyph). Hover: 2-stop stroke, gradient label, icon swaps to `assets/download-variant2.svg` (done in CSS). Used at `78:1807` ("Checklist.docx").

```html
<button type="button" class="btn btn--outline btn--has-icon"><span class="icon icon--download"></span><span class="btn__label">Checklist.docx</span></button>
```
```html
<button type="button" class="btn btn--outline btn--has-icon is-hover"><span class="icon icon--download"></span><span class="btn__label">Checklist.docx</span></button>
```
Notes: the hover stroke recipe of this button (2 stops) differs from the plain Outline button (3 stops) — a design inconsistency, reproduced as drawn.

---

## Select
Design: `10:170` · 32 high, hug width, fill Grey 500, 1 px inside border Grey 400, radius 8, padding 0/12, gap 32, text Manrope Regular 12 (changed in Figma 2026-11-16; was Regular 10). The component default text is Grey 300 (placeholder look); every instance in the screens overrides it to White (value look): use `select__label--value`. Only the closed trigger is drawn (no open list).

```html
<button type="button" class="select"><span class="select__label select__label--value">Local Developer</span><img class="select__chevron" src="assets/select-chevron-down.svg" alt=""></button>
```
```html
<button type="button" class="select"><span class="select__label">Select an option</span><img class="select__chevron" src="assets/select-chevron-down.svg" alt=""></button>
```
Notes: the second snippet is the component's default (placeholder colour). Hug width (a browser may differ by ~1.5 px from the design because of font metrics).

---

## Search
Design: `73:1680` · 120x32 fixed (stretched to FILL on Wallet via `.search--fill`), fill Grey 500, 1 px inside border Grey 400, radius 8, padding 0/8, gap 8, icon at left, placeholder Manrope Regular 12 (changed in Figma 2026-11-16; was Regular 10) Grey 300. The typed-text colour is not drawn: text keeps the placeholder colour (Grey 300).

```html
<div class="search"><img class="search__icon" src="assets/search.svg" alt=""><input class="search__input" type="text" placeholder="Search"></div>
```
```html
<div class="search search--fill"><img class="search__icon" src="assets/search.svg" alt=""><input class="search__input" type="text" placeholder="Start typing the client's name…"></div>
```

---

## Input
Design: `73:1679` · 120x32 fixed (`.input--fill` = FILL width, `.input--narrow` = 193 wide fixed inside `.form-field__row`), fill Grey 500, 1 px inside border Grey 400, radius 8, padding 0/12, text Manrope Regular 12 Grey 300 (changed in Figma 2026-11-16; was Regular 10) (placeholder; typed colour not drawn).

```html
<input class="input" type="text" placeholder="Type here">
```
```html
<input class="input input--fill" type="text" placeholder="Paste the address, e.g. bc1q…, 0x…, T…">
```

---

## Tabs
Design: Tabs 32 `21:384`, Tabs 24 `21:401` · track fill Grey 400, radius 8; tab radius 8, Manrope Medium 12 (32) / Medium 10 (24), inactive label Grey 300, padding 0/20 (32) or 0/16 (24). Active tab = brand gradient fill with Black 900 label (`.is-active` or `aria-selected="true"`). The design has no state property: selection = which tab carries the class. Hover/focus not drawn.

```html
<div class="tabs" role="tablist">
  <button type="button" class="tab is-active" role="tab" aria-selected="true">Button</button>
  <button type="button" class="tab" role="tab" aria-selected="false">Button</button>
</div>
```
```html
<div class="tabs tabs--sm" role="tablist">
  <button type="button" class="tab is-active" role="tab" aria-selected="true">List</button>
  <button type="button" class="tab" role="tab" aria-selected="false">Org chart</button>
</div>
```
Behaviour: move `is-active` and `aria-selected` to the clicked tab.
```js
document.querySelectorAll('.tabs').forEach(function (tabs) {
  tabs.addEventListener('click', function (e) {
    var tab = e.target.closest('.tab'); if (!tab) return;
    tabs.querySelectorAll('.tab').forEach(function (t) {
      var on = t === tab;
      t.classList.toggle('is-active', on);
      t.setAttribute('aria-selected', on ? 'true' : 'false');
    });
  });
});
```
Notes: Tabs 24 padding 8 top/bottom in the design does not fit 24 px; the label is centred (height 24 reproduced).

---

## Toggle and toggle with text
Design: toggle set `21:32`, toggle w text set `21:55` · track 32x16 radius 24, knob 12x12 at 2 px. OFF: track Grey 100, knob Grey 500; ON (variant named "Default"): track "Gradient green", knob moved to the right. With text: gap 6, label Manrope Medium 12 — OFF label Grey 100, ON label White. Only OFF is drawn on a screen (`78:1955`).

```html
<button type="button" class="toggle" role="switch" aria-checked="false" aria-label="Toggle"></button>
```
```html
<button type="button" class="toggle is-on" role="switch" aria-checked="true" aria-label="Toggle"></button>
```
```html
<span class="toggle-field"><button type="button" class="toggle" role="switch" aria-checked="false"></button><span>Show Confidential Details</span></span>
```
```html
<span class="toggle-field is-on"><button type="button" class="toggle" role="switch" aria-checked="true"></button><span>Show Confidential Details</span></span>
```
Behaviour: flip `aria-checked` and `.is-on` (on the `.toggle`, or on the `.toggle-field` when it has a label).
```js
document.querySelectorAll('.toggle').forEach(function (t) {
  t.addEventListener('click', function () {
    var on = t.getAttribute('aria-checked') !== 'true';
    t.setAttribute('aria-checked', on ? 'true' : 'false');
    var host = t.closest('.toggle-field') || t;
    host.classList.toggle('is-on', on);
  });
});
```
Notes: the design's default labels are "Text ON"/"Text OFF" (placeholder copy); the screen copy is "Show Confidential Details".

---

## Status pill / person tag
Design: `78:1974`, `78:2007`, `78:2018`, `78:2046`, `78:2056`, `78:2108` · pattern (no component): height 18 (Figma 15), radius 4, padding 0/8, Manrope Regular 10 (Figma 8) — OWNER OVERRIDE 2026-11-16: all pill/tag text raised from 8 to 10, so pills are 18 high like the Single Source pill; update Figma to match. Variants: `--tag` (person tag, Blue 15% fill, Medium 10, label at 0.7 opacity via `.pill__label`), `--warning` (outline 0.5 Orange, Orange text), `--danger` (Red 25% fill), `--success` (Green 25% fill), `--role` (Purple 15% fill; also used for "✎ Draft to accept"), `--neutral` (Grey 400 fill, EXTENDED #18), `--action` (clickable, EXTENDED #16), `--lg` (the "Single Source" pill; now identical to the others, kept for compatibility).

```html
<div class="hstack hstack--g8">
  <span class="pill pill--tag"><span class="pill__label">{PERSON_2}</span></span>
  <span class="pill pill--warning">Not screened</span>
  <span class="pill pill--danger">1 problem</span>
  <span class="pill pill--success">UBO</span>
  <span class="pill pill--role">Shareholder</span>
  <span class="pill pill--warning pill--lg">Single Source</span>
</div>
```
Notes: texts are design copy ("Not screened", "Missing", "Conflict", "Confirmed", "Single Source", "Director", "8 problems"). The "Single Source" pill is 10 px / 18 high while the same label elsewhere is 8 px / 15 high (design inconsistency).

---

## Status dot
Design: `78:2583`, `78:2584`, `78:1900` · 6x6 circle: `--danger` Red, `--warning` Orange, `--success` Green.

```html
<span class="hstack hstack--g8"><span class="dot dot--danger"></span><span class="dot dot--warning"></span><span class="dot dot--success"></span></span>
```

---

## KPI card
Design: `78:2516` (x4: `78:2519`, `78:2522`, `78:2525`) · fill Black 900, 1 px inside border Grey 400, radius 16, padding 24, gap 16; numeral Jura Medium 38 (colour per meaning), label Manrope Regular 12 Grey 300. FILL width in a row (`.kpi-row`).

```html
<div class="kpi-row">
  <div class="kpi"><span class="kpi__value text-accent">2</span><span class="kpi__label">Active</span></div>
  <div class="kpi"><span class="kpi__value text-danger">1</span><span class="kpi__label">Need You</span></div>
  <div class="kpi"><span class="kpi__value text-info">0</span><span class="kpi__label">ECHO Working</span></div>
  <div class="kpi"><span class="kpi__value text-success">0</span><span class="kpi__label">Awaiting 4-eyes</span></div>
</div>
```
Notes: "Need You" (capital Y) is the design copy. Measured at 642 wide (4 x 142.5 + 3 x 24).

---

## Panel
Design: `78:2528` (outline), `78:2575` (filled), `78:1794`/`78:1950` (gradient) · radius 16, padding 16 + 1 px inside border Grey 400, gap 16, caption Manrope Medium 12 Grey 300 (`.panel__caption`). `--filled` = Grey 500 fill, `--gradient` = "bg gradient" fill.

```html
<div class="panel"><span class="panel__caption">Needs you (1)</span><div>Panel content</div></div>
```
```html
<div class="panel panel--filled"><span class="panel__caption">Clients loaded in (2)</span><div>Panel content</div></div>
```
```html
<div class="panel panel--gradient"><div>Gradient panel content (see Summary card and Detail card for the real inner gaps/paddings)</div></div>
```

---

## Row card
Design: `78:2531` (run card), `78:1778`/`78:1783`/`78:1788` (recent run), `78:2577` (client row), `78:2654` (recent card) · radius 8, fill Grey 500, 1 px inside border Grey 400, padding 12/16, space-between. `--run` = padding 12 all round (UPDATED 2026-11-17: vertical 12 from Figma `105:441`, card 254x58, was 8; horizontal 12 is an owner TRY, not yet drawn in Figma, was 16), top aligned; `--dark` = Black 900 fill, no border; `--fill`/`--top` + `__main`/`__aside` see Row card extras; `.is-active` = 0.5 px gradient border "Gradient main" (1 px until 2026-11-17, Figma `105:931`) (#7BE697 -> #53B2ED, the direction drawn on the Runs screen).

```html
<div class="row-card row-card--run row-card--fill" style="width:254px">
  <div class="row-card__main stack--g2"><span class="type-title-12">ALDER PEAK PTY LTD</span><span class="type-label-10 text-secondary">ECHO processing</span></div>
  <span class="type-numeral-14 text-accent">41%</span>
</div>
```
```html
<div class="row-card row-card--run row-card--fill is-active" style="width:254px">
  <div class="row-card__main stack--g2"><span class="type-title-12">CEDAR LOOP, INC.</span><span class="type-label-10 text-secondary">Needs analyst</span></div>
  <span class="type-numeral-14 text-accent">62%</span>
</div>
```
```html
<div class="row-card row-card--dark row-card--top row-card--fill" style="width:608px">
  <div class="row-card__main stack--g2"><span class="type-title-12">fx01-client-a</span><div class="hstack hstack--g8"><span class="dots"><span class="dot dot--danger"></span><span class="dot dot--warning"></span></span><span class="type-label-10 text-secondary">Needs analyst</span></div></div>
  <div class="row-card__aside"><span class="type-label-10 text-accent pre">KYC Check &gt; </span><span class="type-numeral-14 text-accent">59%</span></div>
</div>
```
**Width is required for `--fill` cards.** In the design these cards are FILL: they take the width of their container (254 in the Recent Runs sidebar, 608 in the Pipeline panel) and the FILL children (`__main`, `__aside`) split that width. A `--fill` card has no width of its own, so in a container that hugs its content (a flex column with `align-items: flex-start`, an inline block) it collapses to its text with no gap, and the text touches or wraps. Give the card a width (as in the snippets: 254 / 608) or put it in a block container with a set width. The snippets show the design widths.

Notes: percentage colour: Blue while in progress, Green (`text-success`) at 100%. The "Company  LTD" title in the design has two spaces — use `<span class="type-title-12 pre">Company  LTD</span>`. The plain `.row-card` (no `--fill`) uses `gap: 36px` between its two children (design value) — in the screens the cards are always `--fill` because a FILL child consumes the space.

---

## Notice
Design: `78:1957` (critical), `78:1970` (warning), `78:1989` (info), `78:2430` (overview warning) · radius 8, padding 12 (+0.5 border on warning), gap 8, text Manrope Medium 10. `--critical` Red 25% fill + Red text; `--warning` no fill, 0.5 inside border Orange, Orange text; `--info` Purple 15% fill + Purple text. Lines are `.notice__row` (gap 4, `--tight` gap 2 for rows with inline person tags); `.notice__suffix` = text at 0.7 opacity.

```html
<div class="notice-stack">
  <div class="notice notice--critical">
    <div class="notice__row"><span>Series A Investors is a group of holders: who is in it is not in the documents.</span><span class="notice__suffix">(16.33% of the client)</span></div>
    <div class="notice__row"><span>ESOP is a group of holders: who is in it is not in the documents.</span><span class="notice__suffix">12.86% of the client)</span></div>
    <div class="notice__row"><span>ESOP (Employee Stock Option Pool) is a group of holders: who is in it is not in the documents.</span><span class="notice__suffix">12.86% of the client)</span></div>
    <div class="notice__row"><span>Seed Investors is a group of holders: who is in it is not in the documents.</span><span class="notice__suffix">12.50% of the client)</span></div>
  </div>
  <div class="notice notice--warning">
    <div class="notice__row"><span class="pre"> Shareholdings in Marlow Finance Holdings Limited add up to 74.37%, not 100%.</span></div>
    <div class="notice__row notice__row--tight"><span class="pill pill--tag"><span class="pill__label">{PERSON_2}</span></span><span class="pre"> and </span><span class="pill pill--tag"><span class="pill__label">{PERSON_3}</span></span><span class="pre"> may be the same person: both hold 43.47% of Marlow Finance Holdings Limited, in different documents. If so, they are counted twice until an analyst resolves it.</span></div>
    <div class="notice__row notice__row--tight"><span class="pill pill--tag"><span class="pill__label">{PERSON_8}</span></span><span class="pre"> and </span><span class="pill pill--tag"><span class="pill__label">{PERSON_9}</span></span><span class="pre"> may be the same person: both hold 6.96% of Marlow Finance Holdings Limited, in different documents. If so, they are counted twice until an analyst resolves it.</span></div>
    <div class="notice__row"><span>! Screening: 0 of 50 parties have a World-Check report · 50 not screened (marked below).</span></div>
  </div>
  <div class="notice notice--info"><div class="notice__row"><span>23 small gaps below the 10% threshold</span></div></div>
</div>
```
Overview "Review and approval" warning notice — headline + a multi-line paragraph. The paragraph (`78:2434`, 918 wide, Manrope Medium 10, line-height 16, Grey 100) contains hard line breaks as drawn (use `<br>`; do not collapse them). The 5th line is longer than the box and wraps by itself:
```html
<div class="notice notice--warning">
  <div class="notice__headline">This run needs 4-eyes approval: the first approval sends it to a second approver.</div>
  <div class="type-paragraph-10 text-label">Critical item “Legal Entity type” is in conflict and not resolved by an analyst.<br>
Critical item “Registered address” is in conflict and not resolved by an analyst.<br>
Critical item “Licensing / registration number” is in conflict and not resolved by an analyst.<br>
22 parties have no World-Check report: {PERSON_18}, Hollis Family Trust, Rowan Investments Pty Ltd, {PERSON_17}, Whitlock Family Trust and 17 more.<br>
Wallet TExampleWalletAddressNotReal000001 needs an exposure assessment: OFAC Sanctioned Entity 0.04%; rule “Sanctioned, TF &amp; CSAM (Criminal Organization, Exchange, FinCEN Primary Money Laundering Concern,<br>
OFAC Sanctioned Entity)”.<br>
The ownership structure has 1 gap that could hide a UBO.</div>
</div>
```
Notes: typos are design copy (the missing "(" in "12.86% of the client)"). The info and critical notices have no border; the warning notice has a 0.5 px border (child content sits at 12.5).

---

## Step chip
Design: `78:2632`, `78:2638`, `78:2644` · 24x24 circle, fill Grey 400, numeral Jura Medium 14 with gradient text "Gradient main" (#7BE697 -> #53B2ED).

```html
<span class="step-chip"><span class="step-chip__num">1</span></span>
```
Notes: the Wallet screen shows the numerals 1, 2, 2 (design copy; the third likely meant 3).

---

## Nav pill
Design: `78:2502` (inactive), `78:2500` (active, Pipeline/Wallet), `78:1766` (active, Runs) · pattern (no component). Inactive: 32 high, padding 0/32, radius 24, label Manrope Regular 12 White. Active: radius 8, 33 high, 0.5 px gradient border. Active gradient: canonical "Gradient main oposite" (#53B2ED -> #7BE697) on Pipeline/Wallet; the Runs screens draw "Gradient main" (#7BE697 -> #53B2ED) — class `nav-pill--alt`. The "Runs" label is Manrope Medium 12 on all screens (`nav-pill--medium`).

```html
<button type="button" class="nav-pill is-active">Pipeline</button>
```
```html
<button type="button" class="nav-pill nav-pill--medium">Runs</button>
```
```html
<button type="button" class="nav-pill nav-pill--alt nav-pill--medium is-active">Runs</button>
```
```html
<button type="button" class="nav-pill">Wallet check</button>
```
Notes: hug widths differ ≤ 1.4 px from the design because of font metrics. Hover is not drawn.

---

## Layout helpers
Design: recorded auto-layout stacks (`78:2529`, `78:2536`, `78:2578`...).
- `.stack` (vertical flex) + `.stack--g2 | g4 | g8 | g12 | g16 | g24` (gap in px).
- `.hstack` (horizontal flex, centred cross axis) + `.hstack--g4 | g8 | g16`.
- `.pre` keeps copy spaces as drawn (`white-space: pre`): "KYC Check > ", "Resolve 6 conflicting values ", " and ".

```html
<div class="stack stack--g8">
  <div class="hstack hstack--g8"><span class="dot dot--warning"></span><span class="type-title-12">Row with gap 8</span></div>
  <span class="type-label-10 text-secondary pre">Trailing space kept </span>
</div>
```

---

## Shell: screen frame, header, photo layer
Design: frames `78:2486` Pipeline, `78:2600` Wallet Check (1920x1080), `78:1751` Runs / Ownership, `78:2225` Runs / Overview (1920x1293) · measured at those sizes. Frame: flex column, centred, clipped, fill Black 900. DOM order = z-order: [`.bg-photo`] `<header>` `<main class="screen__content …">`. Content top = 106 (header 66 + 40) on Pipeline/Wallet and 90 (66 + 24) on Runs. Frame heights are fixed (the content is shorter than the frame).

Header (`78:2488`): 1920x66, padding 16/40, bottom border 1 px Grey 500, space-between; logo box 162x32 (logo.svg 85x20), nav (643 wide in the design), Select at the right edge.
```html
<header class="app-header">
  <div class="app-header__logo"><img src="assets/logo.svg" alt="Echo"></div>
  <nav class="app-header__nav">
    <button type="button" class="nav-pill is-active">Pipeline</button>
    <button type="button" class="nav-pill nav-pill--medium">Runs</button>
    <button type="button" class="nav-pill">Wallet check</button>
    <button type="button" class="nav-pill">System health</button>
    <button type="button" class="nav-pill">Admin Dashboard</button>
  </nav>
  <button type="button" class="select"><span class="select__label select__label--value">Local Developer</span><img class="select__chevron" src="assets/select-chevron-down.svg" alt=""></button>
</header>
```
Active item per screen: Pipeline → "Pipeline" `is-active`; Wallet → "Wallet check" `is-active`; Runs screens → "Runs" `nav-pill nav-pill--alt nav-pill--medium is-active`.

Pipeline background photo layer (`78:2487`) — **pattern only, NO image is shipped** in this folder (the owner did not request the export). It is the bottom-most child of the Pipeline frame: an image 2165x2706 rotated 90°, painted at opacity 0.2 (`--opacity-photo`), clipped by the frame so it covers the whole 1920x1080. It renders nothing until you provide a picture through the custom property `--bg-photo-image`:
```html
<div class="screen-pipeline" style="--bg-photo-image: url('/path/to/your-photo.jpg')">
  <div class="bg-photo"></div>
  <!-- header + main follow (see Screens: Pipeline) -->
</div>
```
Notes: the design's photo shows a dark dotted horizon arc (visual estimate); supply a picture of that kind or leave `--bg-photo-image` unset (the layer stays empty). No scroll regions, overlays or scrims are drawn in any frame.

---

## Section head
Design: `78:1993`, `78:2082`, `78:2172` · 24 high row, space-between, gap 16; caption Manrope Medium 10 Grey 200; optional Tabs 24 on the right.

```html
<div class="section-head"><span class="section-head__caption">Who owns the client</span><div class="tabs tabs--sm" role="tablist"><button type="button" class="tab is-active" role="tab" aria-selected="true">List</button><button type="button" class="tab" role="tab" aria-selected="false">Org chart</button></div></div>
```
```html
<div class="section-head"><span class="section-head__caption">Directors</span></div>
```

---

## Data table
Design: `78:2084` (UBOs), `78:2174` (Directors) · frame radius 8, 1 px border Grey 400; every row (incl. the last and the header) has a 1 px bottom border; header cell padding 8, Manrope Regular 10 Grey 300; body cell padding 8, gap 4, value Manrope Regular 12 White or a person tag, second line a pill. Columns: UBOs = 70.07px + 7 equal; Directors = 7 equal. Measured at 943 wide. No sort arrows, hover or selected row are drawn.

```html
<div class="stack stack--g4" style="width:943px">
  <div class="section-head"><span class="section-head__caption">UBOs (10% or more)</span></div>
  <div class="data-table data-table--ubo">
    <div class="data-table__row data-table__row--head">
      <div class="data-table__cell">Share</div><div class="data-table__cell">Name</div><div class="data-table__cell">Date of birth</div><div class="data-table__cell">Nationality</div><div class="data-table__cell">Passport expiry</div><div class="data-table__cell">Proof of address</div><div class="data-table__cell">Address</div><div class="data-table__cell">World-Check</div>
    </div>
    <div class="data-table__row">
      <div class="data-table__cell"><span class="type-body-12">43.47%</span></div>
      <div class="data-table__cell"><span class="pill pill--tag"><span class="pill__label">{PERSON_2}</span></span><span class="pill pill--warning pill--lg">Single Source</span></div>
      <div class="data-table__cell"><span class="type-body-12">-</span><span class="pill pill--danger">Missing</span></div>
      <div class="data-table__cell"><span class="type-body-12">-</span><span class="pill pill--danger">Missing</span></div>
      <div class="data-table__cell"><span class="type-body-12">-</span><span class="pill pill--danger">Missing</span></div>
      <div class="data-table__cell"><span class="type-body-12">-</span><span class="pill pill--danger">Missing</span></div>
      <div class="data-table__cell"><span class="type-body-12">-</span><span class="pill pill--danger">Missing</span></div>
      <div class="data-table__cell"><span class="type-body-12">-</span><span class="pill pill--warning">Not screened</span></div>
    </div>
    <div class="data-table__row">
      <div class="data-table__cell"><span class="type-body-12">43.47%</span></div>
      <div class="data-table__cell"><span class="pill pill--tag"><span class="pill__label">{PERSON_3}</span></span><span class="pill pill--success">Confirmed</span></div>
      <div class="data-table__cell"><span class="pill pill--tag"><span class="pill__label">{DOB}</span></span><span class="pill pill--warning">Single Source</span></div>
      <div class="data-table__cell"><span class="pill pill--tag"><span class="pill__label">{NATIONALITY}</span></span><span class="pill pill--success">Confirmed</span></div>
      <div class="data-table__cell"><span class="pill pill--tag"><span class="pill__label">{PASSPORT_EXPIRY}</span></span><span class="pill pill--success">Confirmed</span></div>
      <div class="data-table__cell"><span class="pill pill--tag"><span class="pill__label">{DATE}</span></span><span class="pill pill--danger">Conflict</span></div>
      <div class="data-table__cell"><span class="pill pill--tag"><span class="pill__label">{ADDRESS}</span></span><span class="pill pill--danger">Conflict</span></div>
      <div class="data-table__cell"><span class="type-body-12">-</span><span class="pill pill--warning">Not screened</span></div>
    </div>
  </div>
</div>
```
```html
<div class="stack stack--g4" style="width:943px">
  <div class="section-head"><span class="section-head__caption">Directors</span></div>
  <div class="data-table data-table--directors">
    <div class="data-table__row data-table__row--head">
      <div class="data-table__cell">Name</div><div class="data-table__cell">Date of birth</div><div class="data-table__cell">Nationality</div><div class="data-table__cell">Passport expiry</div><div class="data-table__cell">Proof of address</div><div class="data-table__cell">Address</div><div class="data-table__cell">World-Check</div>
    </div>
    <div class="data-table__row">
      <div class="data-table__cell"><span class="pill pill--tag"><span class="pill__label">{PERSON_3}</span></span><span class="pill pill--success">Confirmed</span></div>
      <div class="data-table__cell"><span class="pill pill--tag"><span class="pill__label">{DOB}</span></span><span class="pill pill--warning">Single Source</span></div>
      <div class="data-table__cell"><span class="pill pill--tag"><span class="pill__label">{NATIONALITY}</span></span><span class="pill pill--success">Confirmed</span></div>
      <div class="data-table__cell"><span class="pill pill--tag"><span class="pill__label">{PASSPORT_EXPIRY}</span></span><span class="pill pill--success">Confirmed</span></div>
      <div class="data-table__cell"><span class="pill pill--tag"><span class="pill__label">{DATE}</span></span><span class="pill pill--danger">Conflict</span></div>
      <div class="data-table__cell"><span class="pill pill--tag"><span class="pill__label">{ADDRESS}</span></span><span class="pill pill--danger">Conflict</span></div>
      <div class="data-table__cell"><span class="type-body-12">-</span><span class="pill pill--warning">Not screened</span></div>
    </div>
  </div>
</div>
```
Notes: the placeholder tokens (`{PERSON_3}`, `{DATE}` …) are design copy. In the design the "Single Source" pill is 8 px in the row-2 cells and 10 px / 18 high (`pill--lg`) in the first row.

---

## Ownership tree
Design: `78:1996` · box 943 wide, radius 8, 1 px border Grey 400, padding 8/16; the rows are ABSOLUTELY positioned in a fixed 168 px high area (row pitch 30 = 18 + 12, rows are 18 high; level indent 24, level 3 sits at 71 = a 23 step as drawn) and three 1 px vertical spines (Grey 400, no elbows, 145 / 115 / 83 long) are drawn after the rows. UPDATED 2026-11-16 from Figma `105:613` (owner fixed the margins: was pitch 26, 147 high, spines 129/102/74; tag gap 8, was 4). Row classes: `tree-row--r1..r5` (row index) and `tree-row--l1..l3` (level). Measured at 943x186.

```html
<div class="tree" style="width:943px">
  <div class="tree__rows">
    <div class="tree-row">
      <div class="tree-row__name tree-row__name--root"><span class="icon icon--building"></span><span class="type-label-10">CEDAR LOOP, INC.</span><span class="type-label-10 text-muted">100% of the client</span></div>
      <span class="pill pill--warning">Not screened</span>
    </div>
    <div class="tree-row tree-row--r1 tree-row--l1">
      <div class="tree-row__name"><span class="icon icon--building"></span><span class="type-label-10">Marlow Finance Holdings LLC</span><span class="type-label-10 text-muted">100% of the client</span></div>
      <div class="tree-row__tags"><span class="pill pill--role">Shareholder</span><span class="pill pill--warning">Not screened</span></div>
    </div>
    <div class="tree-row tree-row--r2 tree-row--l2">
      <div class="tree-row__name"><span class="icon icon--building"></span><span class="type-label-10">Marlow Finance Holdings Limited</span><span class="type-label-10 text-muted">100% of the client</span></div>
      <div class="tree-row__tags"><span class="pill pill--warning">Not screened</span><span class="pill pill--warning">1 problem</span></div>
    </div>
    <div class="tree-row tree-row--r3 tree-row--l3">
      <div class="tree-row__name"><span class="icon icon--user-round"></span><span class="pill pill--tag"><span class="pill__label">{PERSON_2}</span></span><span class="type-label-10 text-muted">43.47%</span></div>
      <div class="tree-row__tags"><span class="pill pill--success">UBO</span><span class="pill pill--warning">Not screened</span><span class="pill pill--danger">8 problems</span></div>
    </div>
    <div class="tree-row tree-row--r4 tree-row--l3">
      <div class="tree-row__name"><span class="icon icon--user-round"></span><span class="pill pill--tag"><span class="pill__label">{PERSON_3}</span></span><span class="type-label-10 text-muted">43.47%</span></div>
      <div class="tree-row__tags"><span class="pill pill--success">UBO</span><span class="pill pill--role">Director</span><span class="pill pill--warning">Not screened</span><span class="pill pill--danger">8 problems</span></div>
    </div>
    <div class="tree-row tree-row--r5 tree-row--l3">
      <div class="tree-row__name"><span class="icon icon--building"></span><span class="type-label-10">Series A Investors</span><span class="type-label-10 text-muted">16.33% of the client</span></div>
      <div class="tree-row__tags"><span class="pill pill--warning">Not screened</span><span class="pill pill--danger">1 problem</span></div>
    </div>
    <i class="tree__spine tree__spine--1"></i>
    <i class="tree__spine tree__spine--2"></i>
    <i class="tree__spine tree__spine--3"></i>
  </div>
</div>
```
Notes: the "1 problem" pill is an orange-outline variant on level 2 and a red-filled one on the "Series A Investors" row (as drawn). The org-chart content behind the "Org chart" tab is not drawn.

---

## Stepper
Design: `78:1837` (Ownership), `78:2311` (Overview) · 1130x68, absolute children: 6 connector lines (136x2 at y 20) first, then 7 step wrappers (54x68). Line colours: lines 1-2 brand gradient (`--brand`), line 3 = Blue-to-Orange raw gradient (`--to-current`), lines 4-6 default Grey 400. Step states via the status asset (done = gradient ring + check, current = half-dashed orange ring, pending = Grey 400 ring). Label colour: done Blue (`text-accent`), current Orange (`text-warning`), pending Grey 300 (`text-muted`). Measured at 1130x68.

```html
<div class="stepper" style="width:1130px">
  <i class="stepper__line stepper__line--1 stepper__line--brand"></i>
  <i class="stepper__line stepper__line--2 stepper__line--brand"></i>
  <i class="stepper__line stepper__line--3 stepper__line--to-current"></i>
  <i class="stepper__line stepper__line--4"></i>
  <i class="stepper__line stepper__line--5"></i>
  <i class="stepper__line stepper__line--6"></i>
  <div class="stepper__step stepper__step--1"><div class="step__icon step__icon--done"></div><span class="step__label text-accent">Triggered</span></div>
  <div class="stepper__step stepper__step--2"><div class="step__icon step__icon--done"></div><span class="step__label text-accent">Gathering documents</span></div>
  <div class="stepper__step stepper__step--3"><div class="step__icon step__icon--done"></div><span class="step__label text-accent">ECHO processing</span></div>
  <div class="stepper__step stepper__step--4"><div class="step__icon step__icon--current"></div><span class="step__label text-warning">Needs analyst</span></div>
  <div class="stepper__step stepper__step--5"><div class="step__icon step__icon--pending"></div><span class="step__label text-muted">Awaiting review</span></div>
  <div class="stepper__step stepper__step--6"><div class="step__icon step__icon--pending"></div><span class="step__label text-muted">Awaiting 4-eyes</span></div>
  <div class="stepper__step stepper__step--7"><div class="step__icon step__icon--pending"></div><span class="step__label text-muted">Approved</span></div>
</div>
```
Notes: the state of each step is the icon modifier (`--done` Gradient main, `--current` Gradient orange half-dashed ring, `--pending` Grey 400 ring + Grey 300 check) + the label colour you choose; the icons are pure CSS (two pseudo-elements with masks, so one gradient spans ring + check, as in the design); positions are fixed to the 7-step layout of the design. Labels may overflow their 54 px wrapper (centred), as drawn.

---

## Progress ring and donut
Design: ring `78:2547`/`78:2570` (Pipeline, 81x81 wrapper, 72 px ring), donut `78:1796` (Runs summary, 140x140). **Static drawn assets**: the arc length does not change with the label (design: "62%" label on a 60 / 116 arc; Pipeline 41% short arc, 62% long arc). A real UI must draw the arc dynamically — that would be an extension and is not part of this system.

```html
<div class="ring"><span class="ring__label text-accent">41<span class="numeral-light">%</span></span><img class="ring__img" src="assets/progress-ring-72-short.svg" alt=""></div>
```
```html
<div class="ring"><span class="ring__label text-accent">62<span class="numeral-light">%</span></span><img class="ring__img" src="assets/progress-ring-72-long.svg" alt=""></div>
```
```html
<div class="donut">
  <div class="donut__label"><span class="donut__value text-accent">62<span class="numeral-light">%</span></span><span class="donut__caption text-success">60 out of 116</span></div>
  <img class="donut__img" src="assets/progress-ring-140.svg" alt="">
</div>
```
Notes: `.ring` stretches to the height of its row card (81 in the design); use the natural size of the `<img>`.

---

## Filter list (sidebar)
Design: `78:1889` (Ownership), `78:2363` (Overview) · 14 items, V gap 4, padding-right 16, 218 wide; item 202x32 (padding 8/12/8/16, radius 8, label Manrope Regular 12 Grey 100) with right-aligned `.dots` (red, orange, green order). Active item: 33 high, 0.5 px gradient border "Gradient main" (Runs direction), label Medium 12 White. Items without dots: "Overview", "Activity"; "Activity" has padding 8/16 (`.filter-item--plain`).

```html
<div class="filter-list" style="max-width:218px">
  <div class="filter-item"><span>Overview</span></div>
  <div class="filter-item"><span>General information</span><span class="dots"><span class="dot dot--danger"></span><span class="dot dot--warning"></span></span></div>
  <div class="filter-item"><span>Business</span><span class="dots"><span class="dot dot--success"></span></span></div>
  <div class="filter-item"><span>Regulation</span><span class="dots"><span class="dot dot--danger"></span><span class="dot dot--warning"></span></span></div>
  <div class="filter-item is-active"><span>Ownership</span><span class="dots"><span class="dot dot--danger"></span><span class="dot dot--warning"></span></span></div>
  <div class="filter-item"><span>Funds and wealth</span><span class="dots"><span class="dot dot--warning"></span></span></div>
  <div class="filter-item"><span>Financials</span><span class="dots"><span class="dot dot--danger"></span><span class="dot dot--warning"></span></span></div>
  <div class="filter-item"><span>Trading</span><span class="dots"><span class="dot dot--success"></span></span></div>
  <div class="filter-item"><span>Comments</span><span class="dots"><span class="dot dot--warning"></span></span></div>
  <div class="filter-item"><span>Wallets</span><span class="dots"><span class="dot dot--danger"></span><span class="dot dot--warning"></span></span></div>
  <div class="filter-item"><span>Country risk</span><span class="dots"><span class="dot dot--danger"></span><span class="dot dot--warning"></span></span></div>
  <div class="filter-item"><span>Documents provided</span><span class="dots"><span class="dot dot--danger"></span><span class="dot dot--warning"></span></span></div>
  <div class="filter-item"><span>Files</span><span class="dots"><span class="dot dot--danger"></span><span class="dot dot--warning"></span></span></div>
  <div class="filter-item filter-item--plain"><span>Activity</span></div>
</div>
```
Behaviour: move `is-active` to the chosen item (selection only; hover is not drawn).
Notes: the Overview screen draws a label swap (the "Overview" frame gets the gradient border while the "Ownership" label keeps Medium White; the active label itself stays Regular Grey 100). This is a design inconsistency and is NOT built: use the Ownership screen as the reference and put `is-active` on the current item.

---

## Action list
Design: `78:2438` · 943 wide, rows 33 high (padding 8/0, gap 8, bottom border 1 px Grey 400, no fill); dot + label (Manrope Medium 12 White) on the left; optional link on the right (Manrope Medium 10 Blue, trailing space kept). All dots in the design are Orange.

```html
<div class="action-list" style="width:943px">
  <div class="action-row"><div class="action-row__main"><span class="dot dot--warning"></span><span>Resolve 6 conflicting values</span></div></div>
  <div class="action-row"><div class="action-row__main"><span class="dot dot--warning"></span><span>22 parties have no World-Check report</span></div><span class="action-row__link">Go to Ownership &gt; </span></div>
  <div class="action-row"><div class="action-row__main"><span class="dot dot--warning"></span><span>3 items weren't found in the documents</span></div></div>
  <div class="action-row"><div class="action-row__main"><span class="dot dot--warning"></span><span>5 documents are out of date</span></div></div>
  <div class="action-row"><div class="action-row__main"><span class="dot dot--warning"></span><span>Check 3 values ECHO couldn't read clearly</span></div></div>
  <div class="action-row"><div class="action-row__main"><span class="dot dot--warning"></span><span>Check 10 values found in only one source</span></div></div>
  <div class="action-row"><div class="action-row__main"><span class="dot dot--warning"></span><span>Resolve a gap in the ownership graph that could hide a UBO</span></div><span class="action-row__link">Go to Ownership &gt; </span></div>
  <div class="action-row"><div class="action-row__main"><span class="dot dot--warning"></span><span>Answer 1 item only a person can fill</span></div></div>
  <div class="action-row"><div class="action-row__main"><span class="dot dot--warning"></span><span>5 documents to request from the client</span></div><span class="action-row__link">Go to Documents provided &gt; </span></div>
  <div class="action-row"><div class="action-row__main"><span class="dot dot--warning"></span><span>Write the exposure assessment for 1 wallet with sanctions-related exposure</span></div><span class="action-row__link">Go to Wallets &gt; </span></div>
  <div class="action-row"><div class="action-row__main"><span class="dot dot--warning"></span><span>1 wallet address fails its checksum</span></div><span class="action-row__link">Go to Wallets &gt; </span></div>
  <div class="action-row"><div class="action-row__main"><span class="dot dot--warning"></span><span>Review 22 inconsistencies</span></div></div>
</div>
```
Notes: the numbers on the Overview screen are not reconciled in the design ("Resolve 6 conflicting values" vs "19 conflicting values" on the summary): placeholder copy, kept.

---

## Side panel
Design: `78:1776`/`78:2250` ("Recent Runs"), `78:2652` ("Recently Added") · outline panel 288 wide that stretches to the height of its row; inner width 254. Contents: caption + run cards (`row-card row-card--run row-card--fill`).

```html
<div class="panel panel--side">
  <span class="panel__caption">Recent Runs</span>
  <div class="row-card row-card--run row-card--fill is-active"><div class="row-card__main stack--g2"><span class="type-title-12">CEDAR LOOP, INC.</span><span class="type-label-10 text-secondary">Needs analyst</span></div><span class="type-numeral-14 text-accent">62%</span></div>
  <div class="row-card row-card--run row-card--fill"><div class="row-card__main stack--g2"><span class="type-title-12">ALDER PEAK PTY LTD</span><span class="type-label-10 text-secondary">ECHO processing</span></div><span class="type-numeral-14 text-accent">41%</span></div>
  <div class="row-card row-card--run row-card--fill"><div class="row-card__main stack--g2"><span class="type-title-12 pre">Company  LTD</span><span class="type-label-10 text-secondary">Approved</span></div><span class="type-numeral-14 text-success">100%</span></div>
</div>
```
```html
<div class="panel panel--side">
  <span class="panel__caption">Recently Added</span>
  <div class="row-card row-card--run row-card--fill"><div class="row-card__main stack--g2"><span class="type-title-12">Client Name 1</span><span class="type-label-10 text-secondary">Wallet Address 1</span></div></div>
  <div class="row-card row-card--run row-card--fill"><div class="row-card__main stack--g2"><span class="type-title-12">Client Name 2</span><span class="type-label-10 text-secondary">Wallet Address 2</span></div></div>
</div>
```
Notes: "Company  LTD" (two spaces) and "Client Name 1" are placeholder copy. No empty state is drawn for these lists.

---

## Row card extras
Design: Pipeline run card `78:2531` (608x107 at 642 wide) · inside a `.row-card.row-card--fill`: `__main` (left column, FILL) holds a tag, a title stack (title + `.issue-row` + `.count-row`) and the `.ring` on the right. Count colours: Red, Red, Orange, Orange, Grey 300 for the "(+n)" part. The tag is Manrope Regular 10 Purple (`text-info`). Copy keeps the odd spaces: "(+11 )", "(+56)", the trailing space after the issue lead.

```html
<div class="row-card row-card--fill" style="width:608px">
  <div class="row-card__main stack--g12">
    <span class="type-field-10 text-info">Main check</span>
    <div class="stack stack--g4" style="align-self:stretch">
      <span class="type-heading-14">ALDER PEAK PTY LTD</span>
      <div class="issue-row"><span class="icon icon--exclamation"></span><span class="issue-row__lead">Resolve 6 conflicting values </span><span class="issue-row__more">(+11 )</span></div>
      <div class="count-row"><span class="text-danger">6 conflicts</span><span class="text-danger">1 ownership gap</span><span class="text-warning">3 missing docs</span><span class="text-warning">5 out of date</span><span class="text-muted">(+56)</span></div>
    </div>
  </div>
  <div class="ring"><span class="ring__label text-accent">41<span class="numeral-light">%</span></span><img class="ring__img" src="assets/progress-ring-72-short.svg" alt=""></div>
</div>
```
```html
<div class="row-card row-card--fill" style="width:608px">
  <div class="row-card__main stack--g12">
    <span class="type-field-10 text-info">Main check</span>
    <div class="stack stack--g4" style="align-self:stretch">
      <span class="type-heading-14">CEDAR LOOP, INC.</span>
      <div class="issue-row"><span class="icon icon--exclamation"></span><span class="issue-row__lead">Identify 2 documents ECHO couldn't classify confidently </span><span class="issue-row__more">(+10 )</span></div>
      <div class="count-row"><span class="text-danger">19 conflicts</span><span class="text-danger">1 ownership gap</span><span class="text-warning">4 missing docs</span><span class="text-warning">1 out of date</span><span class="text-muted">(+31 )</span></div>
    </div>
  </div>
  <div class="ring"><span class="ring__label text-accent">62<span class="numeral-light">%</span></span><img class="ring__img" src="assets/progress-ring-72-long.svg" alt=""></div>
</div>
```
Notes: the inline `style="align-self:stretch"` makes the title stack as wide as the column, as drawn. The "(+56)" vs "(+11 )" spacing inconsistency is design copy.

---

## Summary card
Design: `78:1794` (Ownership), `78:2268` (Overview) · measured at 1196x307: `panel panel--gradient summary-card` (gradient fill, radius 16, padding 24/32, gap 24) = a steps row (donut + info column, bottom border 1 px Grey 400, padding-bottom 24) + the stepper. Info column: heading row (heading Medium 16 + Outline-with-icon + CTA buttons, gap 16) and the "Still Open:" block with 3 issue columns (gap 64; lines Manrope Medium 12 at 0.7 opacity: Red for conflicts / gaps, Orange for the rest).

```html
<div class="panel panel--gradient summary-card" style="width:1196px">
  <div class="summary-steps">
    <div class="donut">
      <div class="donut__label"><span class="donut__value text-accent">62<span class="numeral-light">%</span></span><span class="donut__caption text-success">60 out of 116</span></div>
      <img class="donut__img" src="assets/progress-ring-140.svg" alt="">
    </div>
    <div class="summary-info">
      <div class="summary-info__head">
        <span class="type-heading-16">CEDAR LOOP, INC.</span>
        <div class="hstack hstack--g16">
          <button type="button" class="btn btn--outline btn--has-icon"><span class="icon icon--download"></span><span class="btn__label">Checklist.docx</span></button>
          <button type="button" class="btn btn--cta">Re-Run KYC Check</button>
        </div>
      </div>
      <div class="open-issues">
        <span class="panel__caption">Still Open:</span>
        <div class="open-issues__cols">
          <div class="open-issues__col">
            <span class="open-issues__line text-danger">19 conflicting values</span>
            <span class="open-issues__line text-danger">1 ownership structure incomplete</span>
            <span class="open-issues__line text-warning">4 missing documents</span>
            <span class="open-issues__line text-warning">1 out-of-date document</span>
          </div>
          <div class="open-issues__col">
            <span class="open-issues__line text-warning">11 values not found</span>
            <span class="open-issues__line text-warning">3 parties or wallets not screened</span>
            <span class="open-issues__line text-warning">3 need analyst approval (one source)</span>
            <span class="open-issues__line text-warning">4 need analyst approval (client-declared only)</span>
          </div>
          <div class="open-issues__col">
            <span class="open-issues__line text-warning">4 drafts to accept or edit</span>
            <span class="open-issues__line text-warning">1 item for the analyst to write</span>
            <span class="open-issues__line text-warning">4 inconsistencies to check</span>
          </div>
        </div>
      </div>
    </div>
  </div>
  <!-- stepper: see "Stepper" (1130 wide) -->
</div>
```
Notes: donut label "62%" vs arc "60 out of 116" mismatch is design (static drawing). The stepper snippet goes where the comment is.

---

## Detail card
Design: `78:1950` (Ownership, 977x841), `78:2425` (Overview card 1, 977x260), `78:2435` (card 2, 977x472) · `panel panel--gradient detail-card`: fixed 977 wide, gap 8, padding 16 (+1 border). `detail-card--flush` = gap 0 (card 2). Title row `.detail-title` (title Manrope Medium 14 White + subtitle Medium 10 Grey 200, optional toggle-with-text at the right, padding-bottom 4). Footer note `.detail-card__note` (Medium 10 Grey 200, 19 high).

Ownership card, composition order: title row · notice stack · tree block · UBOs table · Directors table.
```html
<div class="panel panel--gradient detail-card">
  <div class="detail-title">
    <div class="stack stack--g4"><span class="detail-title__title">Ownership</span><span class="detail-title__sub">2 UBOs at or above 10%, 1 director, 0 trusts, 50 parties.</span></div>
    <span class="toggle-field"><button type="button" class="toggle" role="switch" aria-checked="false"></button><span>Show Confidential Details</span></span>
  </div>
  <!-- notice stack: see "Notice" -->
  <div class="stack stack--g8">
    <!-- section head + tree: see "Section head" (Who owns the client + Tabs 24) and "Ownership tree" -->
  </div>
  <!-- UBOs table block: see "Data table" -->
  <!-- Directors table block: see "Data table" -->
</div>
```
Overview card 1 ("Review and approval", no toggle):
```html
<div class="panel panel--gradient detail-card">
  <div class="detail-title">
    <div class="stack stack--g4"><span class="detail-title__title">Review and approval</span><span class="detail-title__sub">71 items are still open: resolve them before sending the run for review.</span></div>
  </div>
  <!-- warning notice with headline + multi-line paragraph: see "Notice" -->
</div>
```
Overview card 2 ("What you need to do"):
```html
<div class="panel panel--gradient detail-card detail-card--flush">
  <div class="detail-title"><span class="detail-title__title">What you need to do</span></div>
  <!-- action list: see "Action list" -->
  <div class="detail-card__note">Still to come: reading what each World-Check report found, and the risk rating (section 15)</div>
</div>
```

---

## Screen compositions
All four screens are 1920 wide with fixed heights (1080 / 1293) and are clipped; the content is centred horizontally. In the Runs screens snippets marked `<!-- INSERT: … -->` stand for the complete pattern snippets above (copy them in; they have no screen-specific changes).

### Screen: Pipeline (`78:2486`, 1920x1080)
Content: `.pipeline-content` 642 wide at x 639, y 106, V gap 24: greeting row · 4 KPI cards · outline panel (two captioned run cards) · filled panel (caption + two client rows). The photo layer is the first child (see Shell).
```html
<div class="screen-pipeline">
  <div class="bg-photo"></div>
  <header class="app-header">
    <div class="app-header__logo"><img src="assets/logo.svg" alt="Echo"></div>
    <nav class="app-header__nav">
      <button type="button" class="nav-pill is-active">Pipeline</button>
      <button type="button" class="nav-pill nav-pill--medium">Runs</button>
      <button type="button" class="nav-pill">Wallet check</button>
      <button type="button" class="nav-pill">System health</button>
      <button type="button" class="nav-pill">Admin Dashboard</button>
    </nav>
    <button type="button" class="select"><span class="select__label select__label--value">Local Developer</span><img class="select__chevron" src="assets/select-chevron-down.svg" alt=""></button>
  </header>
  <main class="screen__content pipeline-content">
    <div class="greeting-row"><span class="greeting-row__text">Good afternoon, Alex. One run needs you.</span><button type="button" class="btn btn--cta">Run KYC Check</button></div>
    <div class="kpi-row">
      <div class="kpi"><span class="kpi__value text-accent">2</span><span class="kpi__label">Active</span></div>
      <div class="kpi"><span class="kpi__value text-danger">1</span><span class="kpi__label">Need You</span></div>
      <div class="kpi"><span class="kpi__value text-info">0</span><span class="kpi__label">ECHO Working</span></div>
      <div class="kpi"><span class="kpi__value text-success">0</span><span class="kpi__label">Awaiting 4-eyes</span></div>
    </div>
    <div class="panel">
      <div class="stack stack--g8">
        <span class="panel__caption">Needs you (1)</span>
        <div class="row-card row-card--fill">
          <div class="row-card__main stack--g12">
            <span class="type-field-10 text-info">Main check</span>
            <div class="stack stack--g4" style="align-self:stretch">
              <span class="type-heading-14">ALDER PEAK PTY LTD</span>
              <div class="issue-row"><span class="icon icon--exclamation"></span><span class="issue-row__lead">Resolve 6 conflicting values </span><span class="issue-row__more">(+11 )</span></div>
              <div class="count-row"><span class="text-danger">6 conflicts</span><span class="text-danger">1 ownership gap</span><span class="text-warning">3 missing docs</span><span class="text-warning">5 out of date</span><span class="text-muted">(+56)</span></div>
            </div>
          </div>
          <div class="ring"><span class="ring__label text-accent">41<span class="numeral-light">%</span></span><img class="ring__img" src="assets/progress-ring-72-short.svg" alt=""></div>
        </div>
      </div>
      <div class="stack stack--g8">
        <span class="panel__caption">With the team (1)</span>
        <div class="row-card row-card--fill">
          <div class="row-card__main stack--g12">
            <span class="type-field-10 text-info">Main check</span>
            <div class="stack stack--g4" style="align-self:stretch">
              <span class="type-heading-14">CEDAR LOOP, INC.</span>
              <div class="issue-row"><span class="icon icon--exclamation"></span><span class="issue-row__lead">Identify 2 documents ECHO couldn't classify confidently </span><span class="issue-row__more">(+10 )</span></div>
              <div class="count-row"><span class="text-danger">19 conflicts</span><span class="text-danger">1 ownership gap</span><span class="text-warning">4 missing docs</span><span class="text-warning">1 out of date</span><span class="text-muted">(+31 )</span></div>
            </div>
          </div>
          <div class="ring"><span class="ring__label text-accent">62<span class="numeral-light">%</span></span><img class="ring__img" src="assets/progress-ring-72-long.svg" alt=""></div>
        </div>
      </div>
    </div>
    <div class="panel panel--filled">
      <span class="panel__caption">Clients loaded in (2)</span>
      <div class="row-card row-card--dark row-card--top row-card--fill">
        <div class="row-card__main stack--g2"><span class="type-title-12">fx01-client-a</span><div class="hstack hstack--g8"><span class="dots"><span class="dot dot--danger"></span><span class="dot dot--warning"></span></span><span class="type-label-10 text-secondary">Needs analyst</span></div></div>
        <div class="row-card__aside"><span class="type-label-10 text-accent pre">KYC Check &gt; </span><span class="type-numeral-14 text-accent">59%</span></div>
      </div>
      <div class="row-card row-card--dark row-card--top row-card--fill">
        <div class="row-card__main stack--g2"><span class="type-title-12">fx02-client-b</span><div class="hstack hstack--g8"><span class="dots"><span class="dot dot--warning"></span></span><span class="type-label-10 text-secondary">Needs analyst</span></div></div>
        <div class="row-card__aside"><span class="type-label-10 text-accent pre">KYC Check &gt; </span><span class="type-numeral-14 text-accent">51%</span></div>
      </div>
    </div>
  </main>
</div>
```

### Screen: Wallet Check (`78:2600`, 1920x1080)
Content: `.wallet-content` 984 wide at x 468, y 106, H gap 38: `.wallet-form` (658, V gap 24: heading block + filled form card with 3 fields + action row) and `.panel.panel--side` "Recently Added" (288, stretches to the row height 403). No photo. The form shows placeholders only (no typed, error or disabled state is drawn).
```html
<div class="screen-wallet">
  <header class="app-header">
    <div class="app-header__logo"><img src="assets/logo.svg" alt="Echo"></div>
    <nav class="app-header__nav">
      <button type="button" class="nav-pill">Pipeline</button>
      <button type="button" class="nav-pill nav-pill--medium">Runs</button>
      <button type="button" class="nav-pill is-active">Wallet check</button>
      <button type="button" class="nav-pill">System health</button>
      <button type="button" class="nav-pill">Admin Dashboard</button>
    </nav>
    <button type="button" class="select"><span class="select__label select__label--value">Local Developer</span><img class="select__chevron" src="assets/select-chevron-down.svg" alt=""></button>
  </header>
  <main class="screen__content wallet-content">
    <div class="wallet-form">
      <div class="wallet-form__head">
        <span class="type-heading-16">Add a client wallet</span>
        <span class="type-heading-14 text-muted">Link a wallet to a client in ECHO. It's screened once in Elliptic, and kept on the client for future reviews.</span>
      </div>
      <div class="panel panel--filled form-card">
        <div class="form-field">
          <div class="form-field__label"><span class="step-chip"><span class="step-chip__num">1</span></span><span class="form-field__text">Client</span></div>
          <div class="search search--fill"><img class="search__icon" src="assets/search.svg" alt=""><input class="search__input" type="text" placeholder="Start typing the client's name…"></div>
        </div>
        <div class="form-field">
          <div class="form-field__label"><span class="step-chip"><span class="step-chip__num">2</span></span><span class="form-field__text">Wallet address</span></div>
          <input class="input input--fill" type="text" placeholder="Paste the address, e.g. bc1q…, 0x…, T…">
        </div>
        <div class="form-field">
          <div class="form-field__label"><span class="step-chip"><span class="step-chip__num">3</span></span><span class="form-field__text">Label and note<span class="form-field__sep"> </span><span class="form-field__optional">(optional)</span></span></div>
          <div class="form-field__row">
            <input class="input input--narrow" type="text" placeholder="Label, e.g. Treasury wallet">
            <input class="input input--fill" type="text" placeholder="Note for Compliance (optional)">
          </div>
        </div>
        <div class="form-actions"><button type="button" class="btn btn--cta">Add Wallet and Screen</button></div>
      </div>
    </div>
    <div class="panel panel--side">
      <span class="panel__caption">Recently Added</span>
      <div class="row-card row-card--run row-card--fill"><div class="row-card__main stack--g2"><span class="type-title-12">Client Name 1</span><span class="type-label-10 text-secondary">Wallet Address 1</span></div></div>
      <div class="row-card row-card--run row-card--fill"><div class="row-card__main stack--g2"><span class="type-title-12">Client Name 2</span><span class="type-label-10 text-secondary">Wallet Address 2</span></div></div>
    </div>
  </main>
</div>
```
Notes: the step numerals read 1, 2, 2 in Figma; OWNER DECISION 2026-11-18: use 1, 2, 3 (update Figma to match). Empty "Recently Added": the panel shows one centred Grey 300 line, "Wallets added here will show up in this list." (owner: placeholder text in the middle of the frame, no dashed box). Prototype behaviour: client suggestions use the Select open list (EXTENDED #9) under the Search field, the CTA stays disabled ("Choose a client first." / "Paste a wallet address.") until both are valid, an invalid address uses the field error (EXTENDED #7), and a successful add prepends a run card and shows a success toast (EXTENDED #12). The Wallet Search has a padding-right 32 override in the design with no visible effect (not built).

### Screen: Runs / Ownership (`78:1751`, 1920x1293)
Content: `.runs-content` 1500 wide at x 210, y 90, H gap 16: left `.panel.panel--side` (Recent Runs, stretches to the content height) + `.runs-main` (1196, V gap 13) = summary card + `.runs-lower` (H gap 1) = `.filter-list` (218) + the Ownership `.detail-card` (977). The header marks "Runs" active with the alternate gradient.
```html
<div class="screen-runs-ownership">
  <header class="app-header">
    <div class="app-header__logo"><img src="assets/logo.svg" alt="Echo"></div>
    <nav class="app-header__nav">
      <button type="button" class="nav-pill">Pipeline</button>
      <button type="button" class="nav-pill nav-pill--alt nav-pill--medium is-active">Runs</button>
      <button type="button" class="nav-pill">Wallet check</button>
      <button type="button" class="nav-pill">System health</button>
      <button type="button" class="nav-pill">Admin Dashboard</button>
    </nav>
    <button type="button" class="select"><span class="select__label select__label--value">Local Developer</span><img class="select__chevron" src="assets/select-chevron-down.svg" alt=""></button>
  </header>
  <main class="screen__content runs-content">
    <!-- INSERT: "Side panel" first snippet (Recent Runs) -->
    <div class="runs-main">
      <!-- INSERT: "Summary card" snippet, with the "Stepper" snippet at its end -->
      <div class="runs-lower">
        <!-- INSERT: "Filter list" snippet (Ownership item has is-active) -->
        <!-- INSERT: "Detail card" Ownership snippet filled with notice stack, tree block, UBOs table, Directors table -->
      </div>
    </div>
  </main>
</div>
```

### Screen: Runs / Overview (`78:2225`, 1920x1293)
Same left panel, summary card, stepper and sidebar as Ownership; the right side is `.runs-stack` (977 wide, V gap 16) with two detail cards. The frame is taller than its content (135 px empty below).
```html
<div class="screen-runs-overview">
  <header class="app-header">
    <div class="app-header__logo"><img src="assets/logo.svg" alt="Echo"></div>
    <nav class="app-header__nav">
      <button type="button" class="nav-pill">Pipeline</button>
      <button type="button" class="nav-pill nav-pill--alt nav-pill--medium is-active">Runs</button>
      <button type="button" class="nav-pill">Wallet check</button>
      <button type="button" class="nav-pill">System health</button>
      <button type="button" class="nav-pill">Admin Dashboard</button>
    </nav>
    <button type="button" class="select"><span class="select__label select__label--value">Local Developer</span><img class="select__chevron" src="assets/select-chevron-down.svg" alt=""></button>
  </header>
  <main class="screen__content runs-content">
    <!-- INSERT: "Side panel" first snippet (Recent Runs) -->
    <div class="runs-main">
      <!-- INSERT: "Summary card" snippet, with the "Stepper" snippet at its end -->
      <div class="runs-lower">
        <!-- INSERT: "Filter list" snippet (put is-active on "Overview" for this screen) -->
        <div class="runs-stack">
          <!-- INSERT: "Detail card" Overview card 1, with the multi-line warning notice -->
          <!-- INSERT: "Detail card" Overview card 2, with the action list and footer note -->
        </div>
      </div>
    </div>
  </main>
</div>
```

---

## States drawn by the owner after the first build (design-defined, Figma 2026-11-16)
The owner added hover and disabled variants in Figma (`figma-spec/components.md` §11). They are normal design states (not EXTENDED). Real pseudo-class AND a forced class for each.

| Component | State | Class / pseudo-class | What changes (design node) |
|---|---|---|---|
| Select, Search, Input | hover | `:hover`, `.is-hover` | 1 px border Grey 400 -> Grey 300 (`101:100`, `101:106`, `101:112`) |
| Select, Search, Input | disabled | `:disabled`, `.is-disabled`, `[aria-disabled="true"]` | fill Grey 400, border Grey 300, text Grey 300, chevron / search icon flat Grey 300 (use the same markup; the CSS swaps in `assets/select-chevron-down-disabled.svg` and `assets/search-disabled.svg`; if your framework ignores `content:` on `<img>`, point the `src` at those files yourself); no opacity (`101:114`, `101:119`, `101:124`) |
| CTA button | disabled | `:disabled`, `.is-disabled` | fill Grey 100 `#A6ACB6` instead of White, label Black 900 (`101:80`) |
| Outline / Outline + icon | disabled | same | fill Grey 500, 1 px stroke Grey 400, label and icon Grey 300, no hover ring (`101:82`, `101:84`) |
| Tabs 32 / Tabs 24 | disabled | `.tabs.is-disabled` | active tab fill Grey 300 with Grey 400 label; inactive tab unchanged (`101:88`, `101:94`) |

```html
<input class="input is-hover" placeholder="Type here">
<input class="input" placeholder="Type here" disabled>
<button class="btn btn--cta" disabled>Run KYC Check</button>
<button class="btn btn--outline is-disabled"><span class="btn__label">Cancel</span></button>
<div class="tabs is-disabled"><button class="tab is-active">Button</button><button class="tab">Button</button></div>
```
Notes: hover is not shown on a disabled control. Field hover and disabled share the Grey 300 border and differ by fill (Grey 500 vs Grey 400): drawn that way.

## Modal (design-defined, Figma `105:131`)
Scrim `.modal-scrim`: Black 900 at 25% plus a background blur of 12, fixed, starting 70 px from the top (so the 66 px header and 4 px of page stay unblurred; change `--layout-scrim-top` to 66 to cover from the header edge). Dialog `.modal`: Grey 400 fill, no border, radius 8, padding 24, gap 32, hugs content, no shadow. No close icon is drawn.
```html
<div class="modal-scrim">
  <div class="modal" role="dialog" aria-modal="true" aria-labelledby="m-title">
    <div class="modal__text"><span class="modal__title" id="m-title">Re-run KYC check?</span><span class="modal__body">This replaces the current result.</span></div>
    <div class="modal__actions"><button class="btn btn--outline"><span class="btn__label">Cancel</span></button><button class="btn btn--cta">Confirm</button></div>
  </div>
</div>
```

## Extended components and states (not in the design)
Approved by the owner in the expand step (2026-11-16). All use existing tokens only; the few aliases are named `--…-ext-…` in `tokens.css` / group `extended` in `tokens.json`. CSS: `EXTENDED — not in design` comments in `components.css` PART 3.

| # | Name | What | Derivation (existing tokens/patterns) |
|---|---|---|---|
| 1 | Field focus (click / typing / open) | Select, Search, Input, Textarea: the 1 px border becomes the brand gradient ring; Select also while its list is open. Hover is drawn (Grey 300), see above. Classes: `:focus`, `:focus-within` (Search), `:focus-visible` (Select), `.is-focus`, `.is-open`, `[aria-expanded="true"]` | owner decision; gradient-border technique of the active nav pill / outline hover |
| 2 | Focus ring (buttons, tabs group, nav pill, toggle) | 1 px brand-gradient ring drawn outside the control, outer edge 3 px outside (2 px gap), radius = control radius + 3; `:focus-visible` and `.is-focus`. Fields use #1 instead | owner: gradient instead of blue; `--gradient-brand`; `--size-ext-focus-ring-offset` (3 px, the only new number) |
| 3 | Typed value colour | Input / Search / Textarea text is White once a value is typed (`:not(:placeholder-shown)`, `.has-value`); placeholder stays Grey 300 | the White the Select instances override to |
| 4 | Inactive tab hover | label Grey 300 -> White; no fill/stroke change (the inactive nav pill label is already White, so nothing changes there) | `--color-text-primary` |
| 5 | Button pressed | `:active` / `.is-pressed` = the drawn hover recipe of the same button | no darker token exists |
| 6 | Disabled: toggle, nav pill, rows | `.is-disabled` / `[aria-disabled="true"]`: whole control at opacity 0.5, `cursor: not-allowed`, no hover/focus | the 0.5 the design uses on the Select chevron; owner may redraw later |
| 7 | Field error | `.is-error` / `[aria-invalid="true"]`: border Red; helper `.form-field__helper.is-error` Manrope Regular 10 Red, 4 px under the field | `--color-red`, Manrope 10 |
| 8 | Textarea | `.textarea` (+ `--fill`): Input recipe, padding 8/12, Manrope Regular 12, height from `rows`/content | Input recipe |
| 9 | Select open list | `.select-wrap` > `.select.is-open` + `.select-menu` (exactly as wide as the trigger, 4 px below) > `.select-menu__item` (hover Grey 400, `.is-selected` = 0.5 px gradient ring, Medium 12 White) | field fill + hairline, filter-item recipe (fills the width), active nav pill ring |
| 10 | Interactive row hover | fill Grey 400 on `.row-card.is-interactive`, `.data-table__row.is-interactive` and every sidebar `.filter-item` (not the active one); the drawn selected ring is kept | `--color-surface-raised` (same as #9 item hover) |
| 11 | Tooltip | `.tooltip`: Grey 400 fill, no border, radius 8, padding 8/12, Manrope Regular 12 Grey 100, no shadow, no arrow | owner revised |
| 12 | Toast | `.toast-stack` (fixed, top-right, 40 px from top and right) holding `.notice.toast` + `--critical`/`--warning`/`--info`/`--success`; text Manrope Medium 12; gap 8; max width 360 (`--size-ext-toast-max-width`, no token in the design); no shadow, no animation, display time is the developer's | notice recipes; `--success` = success-pill colours (Green 25% fill, Green text) |
| 14 | Scrollbar | `.scroll` on any container with a height or max-height: thin 6px bar, no track, no arrow buttons, thumb Grey 300 at the existing 50% opacity, thumb hover Grey 300, fully round. Chrome/Safari/Edge via `::-webkit-scrollbar`; Firefox gets thin + the same thumb colour (no hover colour) | owner picked option B (Grey 400 was too dark); `--color-ext-scroll-thumb`, `--opacity-half` |
| 15 | Field rows (expandable) | `.field-list` > `.field-row.is-interactive` = caret + label (224) \| value (+ `.chips`) \| status pill; click opens `.field-row__detail` (headline Medium 12, explanation, optional note, Outline "Show the source pages ›"). Hover fill Grey 500 (`--color-ext-hover-field-row`). Caret = owner-drawn `arrow-right.svg` / `arrow-down.svg` | data-table frame, row hover (#10) |
| 16 | Interactive pill | `button.pill.pill--… .pill--action`: pointer, hover/focus = 1 px ring in the pill's text colour; the trailing `›` is part of the label | pills |
| 17 | Source chip | `.chip` (+ `.chip__ok` green ✓ text glyph for verified text): Grey 400 fill, Grey 100 text, Regular 10, 18 high, radius 4, padding 0/8, hover = White | pill recipe, neutral colours |
| 18 | Neutral pill | `.pill--neutral`: Grey 400 fill, Grey 200 text (Declared, Below threshold, Not applicable) | Grey 400 / Grey 200 |
| 19 | Right drawer | `.drawer-scrim` (hidden) > `.drawer.scroll`: Modal scrim recipe, panel Grey 500 with 1 px Grey 400 left border, 960 wide (`--size-ext-drawer-width`), padding 24, scrolls; `.drawer__head/__title/__caption/__section/__page` | Modal |
| 20 | Radio | `input.radio` inside `label.radio-field`: 16 px circle, 1 px Grey 300 border; checked = brand-gradient ring + 8 px dot | toggle / field tokens |
| 21 | Long ownership tree | `.tree.tree--long`: the drawn tree with rows in normal flow (same 18 high rows, 12 gap, indents 24 / 48 / 71, spines run to the bottom) for any number of parties | tree |
| 22 | Below-threshold pill | the neutral pill (#18) | — |
| 23 | Text action | `button.link-action` (Medium 10, Blue accent, underline on hover/focus); `.link-action--light` = White on coloured notices | Blue accent text |
| 24 | Revealed personal data | "Show personal details": `.pill--tag.is-revealed` loses the blue chip and reads as plain White text that inherits the surrounding font (size, weight, family), so it matches the text around it; the text swap is the developer's. Toggle sits top-right of the card title row (`.toggle-field`), label flips to "Hide personal details" | tag pill |
| 25 | Dynamic ring / donut | `<span class="ring__dyn" style="--pct:54">` (72 px, stroke 4) and `<span class="donut__dyn" style="--pct:54">` (140 px, stroke 8) replace the `<img>` arcs: brand-gradient arc from 12 o'clock clockwise on a Black 900 track, drawn drop shadow kept; butt caps, conic gradient (differs from the drawn diagonal) | ring assets |
| 26 | Clamped long text | `.field-row__value--clamp`: 3 lines + ellipsis, full text once the row is open | field row |
| 27 | Notice paragraph 12 | `.type-paragraph-12`: Medium 12 / line-height 20 (owner: the 10 px paragraph was too small); person tags inside keep 10 px | `.type-title-12` |
| 28 | Figure tables | `.data-table.data-table--fig` (+ inline `--table-cols`): `.data-table__cell--num` right-aligned, `.fin-group` label row, `.fin-num` clickable number + 6 px status dot (green confirmed / orange one source, unclear, not found, arithmetic to check / red sources disagree), `.fin-legend` muted legend line | data table, dots |
| 29 | Score meter | `<span class="meter" style="--pct:50"></span>`: 4 px bar, 88 wide (`--size-ext-meter-width`), Grey 400 track, "Gradient orange" fill up to --pct; sits under the score text (e.g. "5.01 / 10") | surface-raised, gradient orange |
| 30 | Documents to request | `.req-party` (party name heading 14 + role Grey 200, hairline above, 24 padding) > `.req-item` (status pill + document title Medium 12 + muted explanation); 16 between items, 8 inside an item | pills, hairlines |
| 31 | Risk factors checklist | `.factor` in a `.field-list`: number \| title (+ EDD neutral pill) + explanation \| state pill + who set it; under it `.link-action` "Tick it" / "Clear it" / "Undo" and a comment form (Textarea + CTA Save + Outline Cancel). States: waiting = warning pill, not ticked = neutral, ticked = danger, cleared = success | field list, text action |
| 32 | Tally list | `.tally` > `div` columns > `.tally__row` (label left, `.tally__count` Jura Medium 14 Blue right, hairline under each row, `--warn` = Orange): a plain frameless "label ... count" list in two equal columns (gap 48) | Jura numerals, hairlines |
| 33 | Timeline | `.timeline` > `.timeline__day` (date, Medium 10 Grey 200) + `.timeline__item` = `.timeline__time` (Jura SemiBold 12, Grey 300) \| `.timeline__mark > i` (6 px dot on a hairline; `is-done` Green, `is-stage` Blue, `is-user` Purple, `is-fail` Red, none = Grey 300) \| `.timeline__body` (`.timeline__title` Medium 12 White + `.timeline__detail` Medium 10 Grey 200) | dots, Jura numerals |
| 34 | Chart card | `.panel.chart-card`: head (`.chart-card__title` Medium 12 White, `.chart-card__sub` Medium 10 Grey 200, a "Table" / "Chart" `.link-action` that swaps `.chart-view` for `.chart-table`), optional `.chart-legend` (line keys, always for 2+ series), the chart | panel, text action |
| 35 | Horizontal bars | `.hbars > .hbar` = `.hbar__label` (Regular 12 Grey 100, optional `<small>` muted) \| `.hbar__track` (8 px, Grey 400) with `.hbar__fill` (`--pct`, brand gradient, 4 px rounded data end at the right) \| `.hbar__val` (Jura Medium 14 Blue); hover/focus shows a tooltip | tokens only |
| 36 | SVG charts | `.chart-svg` for line and column charts: hairline Grey 400 grid, axis text Medium 10 Grey 300, 2 px lines (`.line`, series colours Blue / Green / Red for Started / Approved / Rejected), 8 px columns with a 4 px rounded top (`.col`), hover crosshair (`.cross`) and `.tooltip` listing every series; `.kpi__sub` = muted line under a KPI card | tokens only |
| 37 | Checkbox | `label.checkbox-field` > `input.checkbox` + text: 16 px square, 1 px Grey 300 border, radius 4; checked = brand-gradient fill with a Black 900 CSS check; label Regular 12 White | field tokens |
| 38 | Date picker | The FIELD is drawn (Figma `183:1139` default, `183:1141` hover, `183:1146`): `.datefield > input.input.datefield__input` (143 wide, "dd/mm/yyyy" Grey 300) + `img.datefield__icon` (`assets/calendar.svg`, 16 px). The calendar popup is NOT drawn; derived from tokens: `.calendar` (Grey 500 fill, 1 px Grey 400, radius 16, padding 16), title Medium 12, month arrows = your arrow icons, 7-column grid, Monday first, hover Grey 400, today = 0.5 px ring, selected = brand gradient, footer Clear / Today text actions | Input, panel |
| 39 | Avatar chip + person stats | `.avatar-chip` (32 px circle, Grey 400 fill, initials Grey 100 Medium 10); `.person-stats` (wrapping "number label" pairs, number Medium 12 White in `<b>`) | step chip |
| 40 | Sticky header | `.app-header.app-header--sticky`: stays at the top while the page scrolls under it; filled with Black 900 (the design draws no header fill), z-index 40 (below the drawer scrim 100 and toasts 200); the screen frame must not clip (no `overflow:hidden`). Recent Runs then sticks at `top: 66 + 24` | Black 900 |

```html
<!-- field focus / error with helper / textarea / open list -->
<input class="input is-focus" placeholder="Type here">
<div class="form-field"><input class="input is-error" value="abc"><div class="form-field__helper is-error">Enter a valid address</div></div>
<textarea class="textarea" rows="3" placeholder="Note for Compliance (optional)"></textarea>
<div class="select-wrap">
  <button class="select is-open" aria-expanded="true"><span class="select__label select__label--value">Local Developer</span><img class="select__chevron" src="assets/select-chevron-down.svg" alt=""></button>
  <div class="select-menu" role="listbox"><div class="select-menu__item">Production</div><div class="select-menu__item">Staging</div><div class="select-menu__item is-selected" aria-selected="true">Local Developer</div></div>
</div>
<!-- focus ring / pressed / disabled toggle -->
<button class="btn btn--cta is-focus">Run KYC Check</button>
<button class="btn btn--outline is-pressed"><span class="btn__label">Button</span></button>
<span class="toggle-field is-disabled"><button class="toggle" role="switch" aria-checked="false"></button><span>Show Confidential Details</span></span>
<!-- scrollable area (give it a height) -->
<div class="panel panel--filled"><div class="scroll" style="max-height:260px">…long list…</div></div>
<!-- row hover (opt-in) / tooltip / toasts -->
<div class="row-card row-card--run is-interactive">…</div>
<span class="tooltip">Download the KYC checklist</span>
<div class="toast-stack">
  <div class="notice notice--success toast"><div class="notice__row"><span>Run saved</span></div></div>
  <div class="notice notice--info toast"><div class="notice__row"><span>KYC check started</span></div></div>
  <div class="notice notice--warning toast"><div class="notice__row"><span>2 documents are missing</span></div></div>
  <div class="notice notice--critical toast"><div class="notice__row"><span>Could not save. Try again</span></div></div>
</div>
```

Not drawn and not provided (ask before extending): checkbox, avatar, calendar/date/time pickers, pagination/sort arrows, breadcrumbs, empty states, loading spinner/skeleton, icon-only button, transitions/motion, responsive breakpoints. (Radio, dynamic ring arcs, drawer, chips and field rows are now provided as EXTENDED rows 15-28 above.)


### Markup for the General information patterns (EXTENDED rows 15-28)
```html
<!-- pills: static / clickable / neutral / draft / not enough evidence -->
<span class="pill pill--success">Confirmed</span>
<button type="button" class="pill pill--warning pill--action">Single source ›</button>
<button type="button" class="pill pill--danger pill--action">Missing ›</button>
<button type="button" class="pill pill--role pill--action">Draft to accept ›</button>
<span class="pill pill--neutral">Declared</span>
<span class="pill pill--neutral">Below threshold</span>
<!-- source chip -->
<div class="chips"><button type="button" class="chip">Account opening form p.3 · image</button><button type="button" class="chip">Financial statements p.8 · text <span class="chip__ok">✓</span></button></div>
<!-- field row (add .is-open to expand) -->
<div class="field-list">
  <div class="field-row is-interactive">
    <div class="field-row__label"><span class="field-row__caret"></span><span>VAT/TIN/Tax identifier</span></div>
    <div class="field-row__main"><div class="field-row__value">EIN 12-3456789</div><div class="chips"><button type="button" class="chip">Account opening form p.3 · image</button></div></div>
    <div class="field-row__status"><button type="button" class="pill pill--warning pill--action">Single source ›</button></div>
    <div class="field-row__detail"><span class="type-title-12">Only declared by the client</span><span class="field-row__why">Only declared by the client; not yet evidenced by an independent document.</span><button type="button" class="btn btn--outline field-row__btn"><span class="btn__label">Show the source pages ›</span></button></div>
  </div>
</div>
<!-- text action in a notice -->
<div class="notice__row"><button type="button" class="link-action link-action--light">Accept gap</button><span class="text-secondary">or</span><button type="button" class="link-action link-action--light">Request the missing document</button></div>
<!-- reason form (Accept gap / Undo): textarea + CTA Save + Outline Cancel -->
<textarea class="textarea" rows="2" placeholder="Why the gap is acceptable"></textarea>
<div class="hstack hstack--g16"><button type="button" class="btn btn--cta">Save</button><button type="button" class="btn btn--outline"><span class="btn__label">Cancel</span></button></div>
<!-- radio -->
<label class="radio-field"><input class="radio" type="radio" name="v" checked> EIN 12-3456789</label>
<!-- dynamic ring and donut -->
<div class="ring"><span class="ring__label text-accent">54<span class="numeral-light">%</span></span><span class="ring__dyn" style="--pct:54"></span></div>
<div class="donut"><div class="donut__label"><span class="donut__value text-accent">54<span class="numeral-light">%</span></span><span class="donut__caption text-success">78 out of 144</span></div><span class="donut__dyn" style="--pct:54"></span></div>
<!-- figure table cell -->
<button type="button" class="fin-num">6,100 <span class="dot dot--success"></span></button>
<!-- drawer -->
<div class="drawer-scrim"><aside class="drawer scroll"><div class="drawer__head"><div class="stack stack--g8"><span class="drawer__caption">Section 1</span><h3 class="drawer__title">VAT/TIN/Tax identifier</h3></div><button type="button" class="btn btn--outline"><span class="btn__label">Close</span></button></div></aside></div>
```
Run cards (`.row-card--run`, Recent Runs / Recently Added): padding 12 all round (vertical 12 from Figma `105:441`; horizontal 12 is an owner TRY). A run card may carry a full-width `pill pill--danger` ("Risk High · 1 factor · provisional") when the card has `flex-wrap: wrap`.

Arrow icons (owner-drawn, Figma `128:1049`, `128:1050`): `assets/arrow-down.svg`, `assets/arrow-right.svg` (+ `.currentColor.svg`), classes `.icon--arrow-down` / `.icon--arrow-right`; the field-row caret uses the plain images so it also works from file://.


### Small helper classes added with rows 15-33
(Also: rows directly inside a framed panel are centred between separators: give that `.panel` `gap:0`; `.panel > .action-row` has 12 padding top and bottom; `.panel > .action-row:last-child` has no bottom border, so a list of rows inside a framed panel, like System health, ends on the panel border; `.action-list` keeps its drawn last separator.)
`.field-group` / `.field-group__title` (a captioned block above a `.field-list`, gap 8), `.field-row__req` (the grey `*` after a required label), `.field-row__note`, `.fin-label` / `.fin-plain` / `.fin-sub` (table text: label Regular 12 Grey 100, value Regular 12 White, sub-line Medium 10 Grey 300), `.data-table--aligned` (all rows share one set of column tracks via subgrid, so content-sized columns line up; use it whenever a column is `max-content`), `.link-action--md` (text action at Medium 12), `.drawer__section` / `.drawer__page` (a bordered block inside the drawer / the document-page placeholder), `.textarea--fill` (full-width textarea), `.factor__no|main|title|state|actions|form` (parts of the risk-factor row, row 31).

### Layering (z-index) — not in the design
The design is flat screens, so it has no stacking order. Floating pieces need one so they do not hide behind each other; these values are our own, not from Figma: dropdown list `.select-menu` 10, modal scrim `.modal-scrim` 100, toasts `.toast-stack` 200 (toasts stay above a modal). If your app already has a z-index scale, replace these three numbers in `components.css`.
| 41 | Interactive dot grid | `<canvas class="bg-grid">` inside `.bg-photo`: 20 px grid of 2 px Grey 100 dots at 7 % opacity; within 210 px of the pointer they light up (85 %), grow and ease up to 12 px away; eased pointer, ~1 px slow breathing; static with reduce-motion. Idea from nocodecommunity.nl. Replaces the Figma background picture (owner decision 2026-11-17) | Grey 100 |
| 42 | Row card hover | `.row-card.is-interactive` hover fill = `--color-ext-hover-row-card` (halfway between Grey 500 and Grey 400, ≈ #161718); the shared row hover (Grey 400) was too bright on run cards. Owner request 2026-11-17 | Grey 500 / Grey 400 |
