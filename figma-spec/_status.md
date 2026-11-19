# echo — pipeline status

| Item | Value |
|---|---|
| Platform slug / display name | echo / Echo |
| Source | figma |
| Design file key · page · canonical node(s) | <figma-file-key> · 78:1750 (final) · 78:2486, 78:1751, 78:2225, 78:2600; components on 3:10845 (drafts) |
| SPEC_DIR · DS_DIR · AUDIT_PATH | Echo Claude/figma-spec/ · Echo Claude/design-system/ · Echo Claude/audit/ |
| Owner decisions | see `_intake.md` (binding) |
| Hub registry (if any) | not set |

## Coverage ledger (every node assigned to exactly one area)
| Node | Name | Area | State |
|---|---|---|---|
| 78:1750 (page) + whole file | file-level, palette, type, shell | foundations | covered |
| 78:2487 etc. icons/logos in all screens + drafts components | icons/logos | assets | covered |
| 10:170, 73:1680, 73:1679, 18:242, 18:248, 21:384, 21:401, 18:290, 21:32, 21:55 | component definitions (page 3:10845) | components | covered |
| 78:2486 Pipeline, 78:2600 Wallet Check | screens | screens: group-a | covered |
| 78:1751 Runs/Ownership, 78:2225 Runs/Overview | screens | screens: group-b | covered |
| 4:15408, 63:712, 22:2621, 73:1531 (drafts screen copies) | alternates | compared in screens groups, final wins | covered |
| 0:1 old echo (5 sections), 2:600 styling examples (2 sections + 3 images) | skipped: owner decision (old revisions / inspiration) | — | skipped |

## Steps
| Step | State | Date | Notes |
|---|---|---|---|
| extract · intake | done | 2026-11-16 | owner answered 3 conflict questions |
| extract · foundations | done | 2026-11-16 | foundations.md (6.2 photo claim corrected by screens-pipeline-wallet.md) |
| extract · assets | done | 2026-11-16 | 14 SVG (11 icons/logo + 3 rings), 4 currentColor copies, 1 IMAGE fill 78:2487 not exported; hashes verified by harvester. Open: export photo? rebuild ring arcs dynamically? download-variant2 = hover? Drafts screens not scanned for extra icons |
| extract · components | done | 2026-11-16 | components.md: 5 sets/10 variants + 5 components, 10 patterns; hover only on CTA/Outline/Outline+icon |
| extract · screens: group-a (Pipeline, Wallet Check) | done | 2026-11-16 | screens-pipeline-wallet.md; CORRECTS foundations 6.2: photo 78:2487 is visible (0.2 opacity, full-frame render) — asset export question open |
| extract · screens: group-b (Runs/Ownership, Runs/Overview) | done | 2026-11-16 | screens-runs.md; Overview ledger completed and +474 pairing verified (202 pairs); donut arc is static vector |
| extract · completeness check | done | 2026-11-16 | covered 907/907 canonical nodes (Pipeline 113, Wallet 61, Ownership 473, Overview 260) after 2 send-backs; value spot-check 22/22; GAPS re-search 1/1 name search on drafts (only 2 hover variants exist, matches spec; final page covered by full node ledger); assets: 14 SVG all in MANIFEST, hashes verified by harvester; 4 currentColor copies. Note: gradient `@0/@1` in components.md = stop position (alpha 1). |
| build · stage 1 (tokens + controls) | done | 2026-11-16 | tokens.json/css 189 entries each; components.css PART 1; 70 checks pass |
| build · stage 2 (layout patterns) | done | 2026-11-16 | 28 pattern groups, 239 rule blocks/239 source comments; ~83 checks pass |
| build · stage 3 (docs + package + light verification) | done | 2026-11-16 | components.md (63 snippets), CLAUDE.md, README.md, .claude/skills/echo-ui/SKILL.md; 165/166 checks (1 explained border snap). Independent verification: 208 comparisons, 0 real mismatches (design-system/_verification.md). Extensions: 0. |
| expand | done | 2026-11-16 | 13 rows proposed with a visual preview; owner approved all (changes on #1, #2, #9, #10, #11, #12; #13 modal was drawn by the owner; #6 narrowed to toggle/nav pill/rows). Built in components.css PART 3 with the drawn hover/disabled states (figma-spec/components.md §11) and the CSS stepper icons. Verified by computed-style comparison + 9 regression checks
| showcase / preview | | | |
| audit | | | |
| publish | | | |

## Open questions for the owner
- Pipeline background photo 78:2487 is VISIBLE (rotated 90, 0.2 opacity): export as PNG asset? (foundations 6.2 said clipped — corrected by screens-pipeline-wallet.md)
- Active-nav/sidebar/tab gradient direction: Pipeline/Wallet "Gradient main oposite" vs Runs "Gradient main" — which is canonical?
- Overview sidebar: active item has the stroke but inactive label style, and inactive "Ownership" has the active label style — copy slip? (Ownership screen is consistent)
- Outline button hover: is "Variant2" the hover state, and which recipe (3-stop raw gradient on 18:253 vs 2-stop style on 18:291)?
- Progress rings/donut: static vectors (arc hand-drawn, label 62% vs 60/116=51.7%) — rebuild dynamically (recommended)?
- Keep unused definitions (Outline Button, Tabs 32, toggle)? Wallet step numerals read 1,2,2 (keep as drawn?); nav "Runs" label Medium vs others Regular — intended?

## Next step
/figma-ds-expand (optional) · /figma-ds-publish

## Open questions after build (defaults applied, see _intake.md)
- Pipeline photo not shipped (`--bg-photo-image` hook only). Search/Input typed-text colour not drawn (placeholder colour used). Paragraph 78:2434 line breaks fixed from node data.


## 2026-11-16 changes after build/expand
- Owner changed Select/Search/Input text to Regular 12 in Figma; spec and DS updated.
- Owner added hover/disabled variants (§11) and the Modal (§11.1); built as design-defined.
- Stepper status icons rebuilt in pure CSS (assets/status-check-*.svg removed); `--color-gradient-progress` named by Claude (was an unnamed raw gradient).
- Gradient green is NOT visible in the stepper (hidden by the Union fill); only the toggle ON track uses it.
- Open: modal scrim starts at y=70 (4px below the 66px header) — kept as drawn, owner may change to 66.
- Open: toast success colour is derived (success pill); nav pill hover is a no-op because the inactive label is already White.