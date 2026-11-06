# Vegetable Garden: one form for both editions — plan (draft 1)

November 5, 2026. Status: built (v14.4–v14.6, Nov 5, 2026). See section 8.

## 1. Decisions

| # | Decision | Source |
| :-- | :-- | :-- |
| U1 | Vegetable Garden first; Flower Garden later, as its own change | Claude, lower-risk path (see 2) |
| U2 | One form used by both editions, with collapsible sections | User |
| U3 | Keep every full-version feature, inside collapsible sections | User |

## 2. Why Vegetable first (risk = making a mistake)

- **Vegetable only:** the full Vegetable tab and the CE vegetable page already share their calculations (`gardenNPlanHTML`, `gardenLimeHTML`, `targetProductLbs`). The change is mostly layout, and the numbers can be checked against today's tab, case by case.
- **Both at once:** Flower Garden adds the Complete N-P-K mode, which the CE form doesn't have. That's new logic, not layout, on top of the vegetable change. If a test fails, it would be harder to tell which change caused it.
- **What doesn't change:** the full Flower tab keeps today's form and nutrient section (`renderNutrientStatusPanel('flr', ...)`), so it isn't affected.

## 3. How "one form" works

- **One copy of the form.** The CE garden form (`#ce-g-*`) moves between the Compact Edition panel and the Vegetable Garden tab when the mode changes. There is still only one copy, and entries stay when you switch.
- **Full-version-only parts** carry a `full-only` class and show only in the full version.
- **The old Vegetable tab's form is removed** only after the parity test passes (step 5).

## 4. What gets added to the form (all from the full tab today)

| Item | Where it goes |
| :-- | :-- |
| **VCE reports.** Nutrient rows read the Soil Test rating and show VCE Note 19 fixed rates (bone meal, granite dust, Epsom salts). Micronutrients use Deficient/Sufficient. No sulfur row. N in lbs per 100 sq. ft. | Each nutrient row: "number from report" (Waypoint) or "rating from your Soil Test tab" (VCE) |
| Carry-over: bed size, lime amount and type, organic matter, ENR, report N | Filled in from the Soil Test tab, as today |
| Nutrient checkboxes ticked from the Soil Test ratings / Waypoint numbers | Nutrient rows |
| Organic P and K sources (fixed rate by rating) | Product list in the P and K rows, offered on both report types |
| VCE Note 19 fixed-rate nitrogen options | Nitrogen product choices |
| Chelated manganese; borax liquid method | Mn and B rows |
| Crop guidance panel (feeding level, pH, side-dress timing) | Collapsible "About this crop" under the crop list |
| ENR comparison | Collapsible, under More options |
| Cup/spoon estimates and the density box | Inside each product's plan |
| Application Timing card, deficiency symptoms table, source notes | Collapsible sections under the shopping list |
| Print, survey prompt, Back to Soil Test Report | As today |

## 5. Build steps (one version each)

1. **v14.4:** add the full-version parts to the CE form (VCE rows, extra products, collapsibles). They are hidden in the CE, so the CE is unchanged and its tests must still pass.
2. **v14.5:**
   - Move the form into the Vegetable tab in full mode.
   - Point carry-over and printing at the form's ids.
   - Keep the old form for comparison, but out of sight.
3. **Parity test (no version):** run the same cases through the old tab and the new form and compare every amount (nitrogen, nutrients, lime). Cases: Waypoint and VCE, several crops and nitrogen sources, Note 19 fixed rates, targets, lime, organic matter. Explain any difference before going on.
4. **v14.6:** remove the old Vegetable tab form and the code only it used, then update the About steps, README and CLAUDE.md.

## 6. Tests each step

- **Snapshots:** the lawn snapshot stays identical. The garden snapshot gets a new baseline only after the parity test.
- **Existing tests:** t345 (modes, print matrix, keyboard golden 54.7) and the CE garden tests (sample numbers, Still-needed list) still pass.
- **Accessibility and layout:** axe 0 in both editions, 380 px wide, no duplicate ids, no page errors.

## 7. Open question

- The CE starts with all nutrient checkboxes empty. In the full version, should they start ticked from the Soil Test ratings (Low ticked), or empty as in the CE? Suggested: ticked, since the full version already has the ratings.

## 8. As built (Nov 5, 2026)

- v14.4 additions, v14.5 move and v14.6 removal were built in one session; the delivered file is v14.6.
- **Decision 7:** checkboxes start ticked from Low ratings (user). On a Waypoint report a ticked row with no number doesn't block the list (blank counts as 0, v13.8).
- **Organic P and K on Waypoint reports:** not offered. The full version already offered only products sized from the report's number on Waypoint reports (v13.8), so the plan's "both report types" line was dropped to keep the amounts the same as before.
- **Parity test** (`scratchpad/ce/vgparity.js`, 9 cases: Waypoint and VCE, crops, Note 19 nitrogen, targets, flat rates, liquid boron, lime with CCE and bags, organic matter): every amount matches the old tab, with one intended exception. When sulfate of potash supplies the sulfur the report asks for, the new form says so instead of listing a separate sulfur product (the Compact Edition rule since v13.4).
- **Compact Edition unchanged:** `scratchpad/ce/cegsnap.js` (8 cases) is identical before and after.
