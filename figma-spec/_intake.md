# Echo — intake (binding owner decisions)

- Date: 2026-11-16
- Platform slug / name: `echo` / Echo
- Source: **Figma** (read-only) — Figma file "Echo", page "final" (link removed for the public repo)
- File key: `<figma-file-key>` · Figma MCP session id used for this task: `<session-id>`
- Node `78:1750` is the PAGE "final " (note trailing space). It is a flat page of 4 top-level screen frames (no sections).

## Pages
| Page id | Name | Children | Role |
|---|---|---|---|
| 78:1750 | final | 4 frames | **CANONICAL screens** |
| 3:10845 | drafts | 14 | Older copies of the same 4 screens (alternates) + **the only component definitions** (canonical for components) |
| 0:1 | old echo | 5 sections | Captures of the old built app (devtunnels URL screenshots) — **skipped** |
| 2:600 | styling examples | 2 sections + 3 images | Inspiration captures (coinbase.com, linear.app) — **skipped** |

## Canonical nodes
Screens (page 78:1750, 1920 wide):
- 78:2486 Pipeline 1920x1080 (x0)
- 78:1751 Runs / Ownership 1920x1293 (x2000)
- 78:2225 Runs / Overview 1920x1293 (x4000)
- 78:2600 Wallet Check 1920x1080 (x6000)

Components (page 3:10845, drafts): 10:170 Select · 73:1680 Search · 73:1679 Input · 18:242 Outline Button (set) · 18:248 CTA Button (set) · 21:384 Tabs 32 · 21:401 Tabs 24 · 18:290 Outline Button + icon (set) · 21:32 toggle (set) · 21:55 toggle w text (set)

## Alternates (status)
- drafts screens: 4:15408 Runs/Ownership · 63:712 Runs/Overview · 22:2621 Pipeline · 73:1531 Wallet Check — older/alternate copies; harvester compares with final, records differences, final wins.

## Owner decisions (verbatim)
1. Canonical source: "Final screens + drafts components" — screens from `final`; components/variants from `drafts` (only place they exist).
2. Other pages: "Ignore both" — `old echo` and `styling examples` recorded as skipped (old revisions / inspiration).
3. Source of truth Figma; output "Echo Claude/figma-spec + design-system".

## Assumptions
- Project root = `Echo Claude` folder (current working dir); SPEC_DIR/DS_DIR directly under it (no extra `echo/` level).
- No variables defined (0 collections), no text styles, no effect styles; 30 local paint styles exist.
- Extensions only from existing tokens (expand step, optional). Font availability to be checked by foundations harvest.
- Pipeline frame has a background image (unsplash rectangle 78:2487, 2165x2706) — photo, not exported unless owner asks.

## Paths
- SPEC_DIR = `figma-spec/`
- DS_DIR = `design-system/`
- AUDIT_DIR = `.../Echo Claude/audit/`

## Scope
All areas: foundations · assets · components · screens (group A: Pipeline + Wallet Check; group B: Runs/Ownership + Runs/Overview).

## Build-step defaults (2026-11-16) — owner did not answer the extract open questions; defaults applied, all alternates kept as `--alt-*` and listed under "Known design inconsistencies"
1. Pipeline photo 78:2487: NOT exported (owner never asked). Documented as a pattern (bottom-most layer, rotated 90deg, 0.2 opacity, covers the frame) with a placeholder note; no asset in the package.
2. Active gradient direction: canonical = "Gradient main oposite" for nav pill and tabs (Pipeline, Wallet, component Tabs 21:379/21:384); "Gradient main" direction kept as `--alt-*` (Runs sidebar). Both documented.
3. Overview sidebar label swap: Ownership screen (78:1751) treated as canonical (consistent); Overview variant listed as inconsistency, not built.
4. Outline button hover: built as DRAWN (3-stop raw gradient 18:253 for Outline; "Variant2" 18:291 for Outline+icon, 2-stop style), each labelled with its node; difference listed as inconsistency. Nothing extended.
5. Progress rings/donut: static drawn vectors from assets; documented as static, label/arc mismatch listed. No dynamic rebuild (would be an extension).
6. Unused definitions (Outline Button, Tabs 32, toggle) are kept and built. Wallet step numerals "1,2,2" and nav "Runs" Medium weight kept verbatim, listed as inconsistencies.
7. Gradient notation in components.md like `#7BE697@0 -> #53B2ED@1` means stop POSITION (alpha is 1).

## Owner overrides after build (2026-11-16)
8. All status pills and person tags: text 8 -> 10 (pills Regular 10, tags Medium 10), pill height 15 -> 18 (same as the Single Source pill). Figma still draws 8/15. A re-extract must NOT revert this unless the owner changes Figma. Tokens: --type-pill-10, --type-tag-10, --h-pill 18.

9. Ownership card re-read from Figma 105:613 (owner fixed the margins, 2026-11-16): table cell tag/pill gap 8 (was 4), tree rows 18 high at pitch 30, tree box 186, tree tag gap 8, spines 145/115/83, card 977x893. Pills/tags already 10px (Regular/Medium) and 18 high there, same as the DS override in item 8. Applied to components.css.
