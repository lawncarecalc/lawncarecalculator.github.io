# Shrubs & Trees tab: steps one at a time, plus clean-up — plan (draft 1)

November 6, 2026. Status: decisions made (S1 a, S2 a, S3 yes). v15.0 and v15.1 built.

## 1. What the tab has today

- A "Before fertilizing: does your plant need it?" box (VCE Note 20 symptoms), then 7 numbered steps, all shown at once:
  1. Plant type (6 types)
  2. Canopy size (diameter, or L × W, or area entered directly)
  3. Next to a fertilized lawn?
  4. Report nitrogen (optional; the plant type's default is used if blank)
  5. Fertilizer: type an N-P-K grade, or pick from 8 products
  6. Phosphorus rating
  7. Potassium rating
- Results card, timing card, print button, survey prompt.
- Lime isn't on this tab. Shrub reports still unlock the separate Lime tab, the last purpose that uses it.

## 2. Problems found while reading the code

| # | Problem | Rule |
| :-- | :-- | :-- |
| A | Steps 6–7 ask for the P and K ratings again. Carry-over already fills them from the Soil Test tab, so they're a second copy that can drift. | Rule 20 (ask once) |
| B | Two products use brand names: "Osmocote 18-6-12" and "Holly-tone 4-3-4". | Rule 16 (no brands) |
| C | Every shrub product has a cups-per-pound figure with no source, and a typed grade gets a guess (1.75 or 2.5). Urea shows 3.3 here, while the garden list has VCE Note 19's figure. | Rule 23 (sourced density only) |
| D | Product notes say "≥50% WIN". Since v10.4/v10.8 the app counts slow-release N by source (coated urea; methylene urea = WIN line + slowly-available footnote; stabilized = none). | Consistency |
| E | Step 4's hint says the default is "the midpoint" of the range; the code uses the low end (e.g. deciduous 3 in a 3–6 range). | Accuracy |

## 3. Proposed changes

### 3.1 Steps one at a time (same pattern as the lawn and garden tabs)
- Shown first: the "does your plant need it?" box and step 1 (plant type).
- Step 2 (size) appears once a plant type is chosen; step 3 (lawn nearby) once size > 0; steps 4–5 (nitrogen and fertilizer) after that.
- Once shown, a step stays. A step that already holds a value is always shown. "Show all steps" button, and a "Next:" line saying what's needed.
- Results, timing and print are not gated.

### 3.2 P and K from the Soil Test tab (fixes A)
- Remove the two rating selects. The results card reads the ratings from the Soil Test tab and shows them, e.g. "Soil Test tab: Phosphorus Low, Potassium Optimum", as the garden tabs do.
- Same P/K advice as today (P_REC / K_REC through the Waypoint-to-VCE conversion), so amounts and advice don't change.

### 3.3 Product list clean-up (fixes B, C, D)
- Rename by grade and type only: "18-6-12 (coated, slow-release)", "4-3-4 (organic, acid-forming)".
- Cups per pound: keep only where sourced. Ammonium sulfate, urea and calcium nitrate would use the same VCE Note 19 figures as the garden list; the others become weight only, with the bulk-density box. A typed grade gets weight only.
- Slow-release wording follows the lawn rule ("check the bag: coated urea, or methylene urea WIN + slowly-available line, should be at least half the nitrogen").

### 3.4 Hint fix (E)
- "Leave blank to use the low end of VCE's range for your plant type", with the number shown once a type is chosen.

## 4. Decisions needed

- **S1. Lime.** (a) Leave lime on the separate Lime tab, as now. (b) Add a lime step to this tab (amount, type, CCE, bag; skipped for acid-loving plants) and retire the Lime tab. Suggested: (a) for now. VCE discourages lime for many shrubs, and (b) is a bigger change better done on its own.
- **S2. Products.** (a) Clean up the list as in 3.3. (b) Also add the garden list's single-nutrient products. Suggested: (a); VCE 430-018 gives a ratio (3-1-2) for complete fertilizers, which the current list follows.
- **S3. Order.** Do 3.2–3.4 (content fixes) first as one version, then 3.1 (steps) as the next. Suggested: yes, so number changes and layout changes are tested separately.

## 5. Build steps (one version each)

1. **v15.0:** P and K from the Soil Test tab, product clean-up, hint fix. Test: same advice for every rating; amounts unchanged except where volume is dropped.
2. **v15.1:** steps one at a time.
3. Update About (Shrubs & Trees steps), README and CLAUDE.md.

## 6. Tests

- Before/after snapshot of the shrub results for each plant type × lawn nearby × fertilizer (typed and product) × P/K ratings, VCE and Waypoint. Only intended differences allowed (volume removed, names, wording).
- Lawn, vegetable, flower and CE snapshots unchanged; t345 (print matrix, golden 54.7).
- Step order, Show all, samples and carry-over leave no filled field hidden; axe 0; 380 px; no duplicate ids; no page errors.

## 7. As built

- **v15.0 (Nov 6, 2026):** 3.2–3.4 done. Snapshot `scratchpad/ce/shsnap.js` (18 cases: 6 plant types × lawn nearby × typed and product fertilizers × VCE and Waypoint ratings, canopy and direct area): every amount and every P/K advice line is the same as v14.9. Differences: volume removed where unsourced (with the bulk-density box), urea and calcium nitrate cups now VCE Note 19 (2.5 and 2.0; were 3.3 and 2.5), product names, the "From your Soil Test tab" line, slow-release wording in the evergreen timing note. CE, vegetable, flower and lawn snapshots unchanged; t345 passes; axe 0; 380 px; no duplicate ids; no page errors.
- **v15.1 (Nov 6, 2026):** 3.1 done. Wrappers `shrub-step2` and `shrub-step345` (steps 3–5 appear together, since step 3 has a default), `shrubRevealSteps(appArea)` (sticky `shrubReached`; a step holding a value, area/L×W size mode or product mode is shown), `shrub-showall-btn`, `shrub-next`. `shsnap.js` identical to v15.0; lawn, CE, vegetable and flower snapshots unchanged; t345, pdvg, pdvg2 pass; new `pdsh.js` (order, sticky after clearing, Show all, value shows its step) passes; axe 0; 380 px; no duplicate ids; no page errors. About Shrubs &amp; Trees steps rewritten (also fixed a stale "with Lawn" line: lawn tabs stopped using the Lime tab July 31).
