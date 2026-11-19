# Echo — new UI (design system + clickable prototype)

The old Echo KYC platform rebuilt in the new Echo design system. Two things live here:

1. **`design-system/`** — the Echo design system (tokens, CSS components, copy-paste markup, icons, fonts, rules for Claude).
2. **`prototypes/general-information.html`** — a clickable prototype of the whole platform in that design system. All content and structure come from the old Echo; none of the old visual design does. All data is made up.

Works on Windows, macOS and Linux. No install, no server, no internet needed (fonts are bundled).

## 1. See it (30 seconds)
Unzip / clone, then **double-click `index.html`** (or open `prototypes/general-information.html` in Chrome, Edge or Firefox). Best on a desktop screen at least 1600 px wide; the design is dark-only and drawn for 1920 px.

If a browser blocks something when opened from a file, run a tiny local server instead (either one):
```bash
python -m http.server 5173      # Python 3, then open http://localhost:5173/prototypes/general-information.html
npx serve .                      # Node
```

## 2. What to click (so nothing is missed)
- **Pipeline** (home): move the mouse over the empty background, the dot grid lights up and eases away from the pointer. Hover the run cards; click a card to open that run. Header **select** (top right) switches the acting person and changes the greeting. The header is sticky.
- **Runs**: left list of runs (the active card has the gradient stroke); the section list on the left switches between Overview, General information, Business, Ownership, Regulation, Funds and wealth, Financials, Trading, Comments, Wallets, Country risk, Documents provided, Risk rating, Files, Activity. Scroll inside a section: the Recent Runs panel stays in view while the page scrolls.
- **Field rows** expand on click; **source chips** and **pills with ›** open the right-hand **drawer** (close with ✕ or Esc). **Show personal details** toggle replaces {PERSON_n} placeholders with made-up names, in every section that has people.
- **Ownership tree**, tables with hover rows, tooltips, toasts, the custom **date picker** (Admin → Log), custom selects, charts (hover bars and points), score meter, timeline.
- **Wallet check**: the form and the side panel. **System health**: connector list and modes. **Admin dashboard**: Checks / Team / Log tabs.
- The page remembers where you are: reload keeps the screen and section (URL hash such as `#runs/Ownership`, `#admin`).
- Hover states, focus rings and the dot grid are real CSS/JS, not screenshots.
- `prototypes/pills.html` shows every label pill variant on one page.

## 3. Work with it using Claude Code
1. Open this folder in Claude Code. The root `CLAUDE.md` makes Claude read `design-system/CLAUDE.md` for every UI task.
2. Ask in plain words ("add a Reports page with a table of runs and a date filter"). Claude must use `design-system/components.md` + `components.css` and may only use tokens from `tokens.css`. Anything not in the design is derived from existing tokens and marked **EXTENDED**, with a row in the Extended table of `components.md`.
3. For a new page, copy the pattern from `prototypes/general-information.html` (it is one HTML file: markup, a small prototype-only `<style>` block, and the script at the end).

Other facts worth knowing:
- Design source: Figma file "Echo" (see `figma-spec/_intake.md` for node ids). `figma-spec/` holds the extracted specification.
- The design is dark-only and fixed at 1920 px; it has no mobile or responsive layouts.
- **42 approved extensions** exist beyond the Figma design (field rows, drawer, date picker, charts, dot grid background and more). The list is at the end of `design-system/components.md`. Figma was not updated for these.
- Fonts: Manrope and Jura, bundled in `design-system/fonts/` (SIL Open Font License).
- `prototypes/_parked.md` holds markup for the List and Org chart tabs that were removed from Ownership.

## 4. Folder map
```
index.html                      start page (links)
CLAUDE.md                       tells Claude Code to follow the design system
design-system/
  CLAUDE.md                     the rules for AI assistants (read first)
  README.md                     human setup guide for the design system
  tokens.css / tokens.json      all design tokens
  components.css                all component styles
  components.md                 copy-paste markup + Extended table
  fonts.css, fonts/             bundled Manrope + Jura
  assets/                       icons, logo, rings (+ MANIFEST.md)
  .claude/skills/echo-ui/       optional Claude Code skill
figma-spec/                     extracted Figma specification
prototypes/
  general-information.html      the full clickable prototype
  pills.html                    all pill variants
  _parked.md                    removed tabs (List, Org chart)
```

## 5. Known gaps
- A few buttons are inert on purpose in this prototype: Show every document, Show the 51 documents, Show figures, Assignees, Record the MLRO's approval.
- A few ✓ glyphs remain on source chips and on "Agrees with ECHO's value".
- Figma still needs updating for: wallet step numerals 1, 2, 3; pill size 10 / 18 high; run card padding; the extended components.
- `design-system/assets/pipeline-bg.jpeg` is the original Figma background picture. Nothing references it any more (the prototype uses the interactive dot grid; to use the picture again, set `--bg-photo-image: url("assets/pipeline-bg.jpeg")` on `.screen-pipeline`).
