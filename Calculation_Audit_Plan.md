# Soil Test Report Assistant — Calculation Audit Plan

**Why this exists:** a real, significant bug (10x overdose on every Waypoint-target-based nutrient
amendment) was found through actual use, not code review — a user entered their real report's
numbers and checked the output against hand arithmetic. That method worked. This plan is built
around doing that systematically, everywhere it could matter, rather than trusting that a formula
which *looks* internally consistent is therefore *correct*.

**The specific failure mode to prioritize:** the bug wasn't a broken formula — the math
`(target * hundredths) / (pct / 100)` is correct arithmetic. The bug was that its *input* was in
the wrong unit (lbs/1,000 sq ft treated as lbs/100 sq ft). This is a **unit-conversion bug**, not a
formula bug, and this codebase has many unit-conversion points because it supports two labs (VCE,
Waypoint) that report the same nutrients in different bases depending on purpose. Every other
audit priority below is secondary to finding more of *this specific shape* of error.

---

## Part 1 — Map every unit-conversion point (highest priority)

Before checking any single number, build a complete table of every place a value crosses from "the
unit a lab reports it in" to "the unit the internal formula assumes." This is the map the bug was
found on, and it should be finished and verified before doing anything else.

**Known conversion points, confirmed correct (verified while building this plan):**
| Value | VCE convention | Waypoint convention | Internal basis | Conversion applied? |
| :-- | :-- | :-- | :-- | :-- |
| Garden/Flower N recommendation | lbs/100 sq ft | lbs/1,000 sq ft | lbs/100 sq ft | ✅ `/10` when Waypoint |
| Garden/Flower lime recommendation | lbs/100 sq ft | lbs/1,000 sq ft | lbs/100 sq ft | ✅ `/10` when Waypoint |
| Lawn (Cool/Warm/Lime) lime recommendation | lbs/1,000 sq ft | lbs/1,000 sq ft (same) | lbs/1,000 sq ft | ✅ correctly *not* converted — both labs already match |
| Waypoint numeric target (any nutrient) | n/a — VCE doesn't publish one | lbs/1,000 sq ft | lbs/100 sq ft | ✅ **fixed Aug 4, 2026** — was missing entirely |

**Still needs verification (not yet individually confirmed):**
- [x] Shrub tab's P/K rating carry-over — **checked, no risk exists.** Shrub only uses P/K as
      rating strings (text lookups like "Use a fertilizer with phosphorus"), never as numeric
      lbs/area values. No unit conversion is possible where there's no unit to begin with.
- [x] Waypoint ppm-to-lbs conversion outside `WAYPOINT_TO_VCE` — **checked, no such path exists.**
      Searched for any ppm-based arithmetic; only the already-fixed lbs-based target system does
      numeric dosing math.
- [x] Organic matter, CEC, base saturation — **OM verified correct** (hand-calculated: 6% OM,
      200 sq ft → 2.4 lbs N/1,000 sq ft → ÷10 → 0.24 lbs/100 sq ft → ×2 → 0.48 lbs for the bed;
      matches the code exactly, and confirms the ÷10 convention the original bug was missing is
      correctly applied elsewhere). **CEC and Base Saturation confirmed unitless** — meq/100g and
      %, identical for both labs, used only for interpretive text, never converted into a dose.
- [x] Sulfur and Boron's liquid-dilution instructions — **found a real gap, fixed.** Boron's
      liquid-method entry used `calc:'none'`, meaning it displayed UMD's rate ("1 tbsp per gallon
      of water, applied per 100 sq. ft.") as a flat, unscaled note — a user with anything other than
      exactly 100 sq. ft. had to scale it themselves. The generic `calc:'none'` wrapper text ("no
      specific rate published") was also factually wrong here, since UMD does publish a rate.
      Converted to a new `calc:'liquid'` type that scales tbsp and gallons to the user's actual bed
      size, same as every other amendment on the tab. Verified: 300 sq ft bed → 3.0 tbsp in 3.0
      gallons; 100 sq ft → 1.0 tbsp in 1.0 gallon.
- [x] Bulk-density-to-cups conversion (`cupsPerLbFromDensity`) — **verified correct** via
      independent dimensional analysis: 1 m³ = 4226.75 US cups (1000 L ÷ 0.236588 L/cup) — matches
      the hardcoded constant exactly; kg→lbs factor (2.20462) is the standard conversion. Confirmed
      physically sensible using the Triple Superphosphate example (1075 kg/m³ → 1.78 cups/lb, less
      than water's ~1.92 cups/lb, consistent with a denser granular product).

**Method:** for each row, don't just re-read the code — find a real or realistic report number,
compute the expected correct output by hand (independently, not by re-deriving the same formula),
and compare. This is exactly how the original bug was found and should be the standard for every
row in this table.

---

## Part 2 — Hand-verify one golden test case per distinct calculation category

For each category below, pick one clean, "nice round number" scenario, compute the answer
independently (calculator or spreadsheet, not by reading the code), and compare against the app's
actual output. Record the golden numbers here once verified, so future changes can be checked
against them without redoing the full derivation.

- [ ] **Nitrogen preplant amount** (Vegetable Garden) — a specific N%, crop default rate, bed size
- [ ] **Nitrogen sidedress schedule** (Vegetable Garden) — VCE/Rutgers fixed per-crop rates, confirm
      against the primary sources directly (already done for tomato this session; extend to at
      least 2–3 other crops in `SIDEDRESS_GUIDE`)
- [x] **Lime — CCE-adjusted rate, total, applications, bags** (`calcLimeForBed`) — 40 lbs/1,000
      sq ft, 90% CCE, 8,000 sq ft, 50 lb bags → adjRate **44.4**, total **355.6 lbs**, **1**
      application, **9 bags** (⌈355.6÷40⌉). **Correction:** this was previously recorded here (and
      in CLAUDE.md) as "8 bags," from dividing by 50 (the application cap) instead of 40 (the bag
      size) — an arithmetic slip in the original hand-verification, not a code bug. Re-checked and
      corrected August 4, 2026 during this audit. The formula itself
      (`Math.ceil(totalLbs / bagSize)`) was always right; only the recorded "golden number" was
      wrong — a reminder that a number labeled "verified" still needs to be checked against the
      actual inputs, not trusted on sight.
- [x] **WIN% / Program detection** (`detectProgram`) — hand-checked against realistic fertilizer
      label examples: 29-3-4 with 4.5% WIN (as printed on a real Guaranteed Analysis, i.e. percent
      of *total product*) → 15.5% of nitrogen → Program 2, correct per VCE 430-011's 15–49% band.
      Straight urea (46-0-0, no WIN) → Program 1, correct. **Found a real risk, not a code bug:**
      the formula converts the bag's raw WIN-of-product figure into VCE's WIN-of-nitrogen criterion
      correctly, but the field label ("WIN % (if listed on bag)") didn't specify which of the two
      numbers to enter — a user who mistakenly entered an already-computed "% of my nitrogen" value
      instead of the bag's raw label figure would get a wrong classification with no way to tell.
      Clarified all three occurrences of this field's label to specify "the bag's Guaranteed
      Analysis" figure explicitly.
- [ ] **Flat-rate amendment** (e.g. Bone Meal, 10 lbs/100 sq ft when P is Low) — confirm the
      multiplication by bed size and the volume conversion both independently
- [ ] **Target-based amendment** (any nutrient) — re-verify with a *second* real or realistic
      number now that the fix is in, not just the one number already checked
- [x] **Cool/Warm auto-plan** — WIN%/program detection, per-application cap, number of applications
      needed, lbs per application — verified with tall fescue, 5,000 sq ft, 3.0 lb N target,
      32-0-8, no WIN: 5 applications, 0.6 lbs N/1,000 sq ft per app, 9.375 lbs product per app,
      46.875 lbs total. **Cross-checked two ways**: via the app's own formula chain, and
      independently via total-N-needed-for-whole-lawn ÷ N% — both produced 46.875 lbs exactly.
- [x] **Cool/Warm custom-plan** — season summary totals across multiple slots. Hand-verified a
      2-slot scenario (32-0-8 and 46-0-0 urea, both at 0.7 lbs N/1,000 sq ft per application,
      5,000 sq ft lawn): total N 1.4 lbs/1,000 sq ft (matches 0.7+0.7 directly, as expected since
      N-per-application already is in that basis), total K 0.175 lbs/1,000 sq ft, total fertilizer
      18.546 lbs. **My own first hand-check of the K total was wrong** — I initially expected
      0.056 by incorrectly multiplying N-delivered-per-1,000-sq-ft by the K fraction, conflating
      two different bases (N delivered vs. total product delivered). Redone correctly (product
      delivered per 1,000 sq ft × K fraction = 0.175) and confirmed the app was right the first
      time — recorded deliberately, same as the `fmtMeasure` case, as a reminder that a disagreement
      between hand-check and app is not automatically the app's fault.
- [x] **Shrub canopy area** (`calcShrubCanopy`) — 6 ft diameter → 28.27 sq ft canopy (π×3²) → 56.55
      sq ft application area (2× canopy, per VCE Note 20). Standard circle-area formula, correctly
      applied; doubling matches the cited source.
- [x] **Shade and clipping adjustments** (`shadeFactor`, `clipCredit`, `effectiveNRate`) — confirmed
      shade is applied first (multiplicatively), then clipping credit is computed from the
      *shade-adjusted* rate (not the original), then subtracted. Verified against a 2.5 lb target
      with shade: matches the exact range ("1.25–1.67 lbs after shade, then 0.8–1.1 lbs after
      clipping credit") already documented earlier this session, confirming this wasn't a new
      check but a successful *re*-verification of prior work.
- [x] **`fmtMeasure()` tsp/tbsp/cup transitions** — spot-checked 0.05, 0.2, 0.6, and 2.5 lbs at
      2.0 cups/lb. **First pass flagged a false alarm**: hand-calculated 1.6 tbsp for the smallest
      case, which didn't match the app's "1.5 tbsp." Before reporting this as a bug, re-read the
      actual current function and found the discrepancy was in my own memory, not the code — I'd
      recalled an *older* rounding rule (nearest 0.1 tbsp) that no longer matches what's actually
      implemented (nearest 0.5 tbsp, i.e. matching real measuring-spoon increments). All four
      values confirmed correct against the actual current logic. Recorded here specifically as a
      reminder that "my hand-calculation disagrees with the app" isn't automatically the app's
      fault — the assumption being hand-verified has to be checked too.

---

## Part 3 — Cross-tab consistency for every shared function

Several functions are deliberately shared across tabs specifically so a fix in one place fixes
everywhere — which is exactly why fixing the target-conversion bug once corrected P, K, Mg, S, Zn,
Cu, Mn, and B all at once. That same sharing means a **new** bug introduced in a shared function is
also instantly a multi-tab bug. For each shared function, confirm the same correct numbers come out
regardless of which tab calls it:

- [x] `calcLimeForBed()` — called from Vegetable Garden, Flower Garden, Cool-Season Lawn,
      Warm-Season Lawn. Lawn and Garden/Flower use genuinely different native bases (lbs/1,000 vs.
      lbs/100 sq ft), so "same raw inputs" isn't the right test — verified instead that **the same
      real-world scenario** (a 40 lbs/1,000 sq ft report figure, 100% CCE, exactly 1,000 sq ft,
      40 lb bags) produces the same real-world total (40 lbs, 1 bag) whether expressed in the Lawn
      tab's native basis (`kSq=1`, cap 50) or the Garden tab's (`hundredths=10`, rec converted to
      4, cap 5). Confirms the four tabs agree physically, not just share code.
- [x] `renderNutrientStatusPanel()` — called from Vegetable Garden and Flower Garden. **Verified
      live on the deployed site**, not assumed from shared code: identical inputs (P Low, K
      Medium, Mg Low, 200 sq ft bed, Calcium Nitrate N source) on both tabs produced the identical
      2.00 lbs Epsom Salts amount. Genuine empirical confirmation, not just "it's the same function
      so it must match."
- [ ] `fmtMeasure()` — called from many places for volume display. Confirm a handful of specific
      lbs values (spanning the tsp → tbsp → cup transition points, e.g. 0.05, 0.2, 0.6, 2.5 lbs)
      produce correct, sensible volume strings everywhere it's used, not just where it was
      originally tested.

---

## Part 4 — Extra scrutiny on the newest code

The bug that started this whole plan was in a feature built earlier the *same session* — new code
had less real-world use before the bug surfaced. Apply the same rigor specifically to:

- [x] Zinc and Copper amendments (added this session, target-calc only) — the elemental
      percentages were independently verified via search at the time they were added (Zinc Sulfate
      monohydrate/heptahydrate, Copper Sulfate pentahydrate), and the shared target-calc formula
      itself is what this whole audit started by fixing. No further gap found specific to these two
      beyond the already-fixed conversion bug.
- [x] Magnesium Oxide and K-Mag/Sul-Po-Mag (added this session) — percentages verified via search
      when added; K-Mag's combined K/S/Mg composition was deliberately flagged in its own note
      rather than presented as Mg-only. No calculation issue found specific to these two.
- [x] The Waypoint report-order nutrient reordering (P, K, Mg, S, B, Cu, Mn, Zn, Fe) — confirmed
      this was a pure array-reordering (display order only); the amendment lookups are keyed by
      nutrient symbol (`n.key`), not array position, so reordering the array cannot have disturbed
      which amendment data attaches to which nutrient.
- [x] Lime absorbed into Cool/Warm-Season Lawns (added this session) — hand-verified when built,
      and **the bag-count portion of that original verification was wrong** (see Part 2's Lime
      entry above) — corrected during this audit, not a new problem introduced since.

**Net assessment:** Part 4's items were already substantially covered by verification done at
build time, not skipped — this pass mainly confirmed that verification held up, and caught the one
place (the bag-count arithmetic) where it hadn't been fully correct originally.

---

## Part 5 — How to actually execute this (methodology, not just a checklist)

- **Compute independently.** For every check, the correct answer should come from a calculator,
  not from reading the code and confirming it matches itself. Re-deriving the same formula from the
  same source only proves internal consistency, which is exactly what this bug had — the formula
  was consistent with itself and still wrong.
- **Use real numbers where possible.** Actual soil test reports (like the one that surfaced this
  bug) are better than invented round numbers, since real reports occasionally have values or
  combinations an invented test case wouldn't think to include.
- **Check both labs for every dual-path calculation.** Anywhere VCE and Waypoint diverge in units,
  test both explicitly — don't assume testing one confirms the other.
- **Prefer live testing over static review**, consistent with how every significant bug this
  project has found was actually caught — enter values in the live app (or the local file via
  simulation) and read the actual output, rather than reasoning about what the code *should*
  produce.
- **Log every verified golden number in this document** as it's confirmed, so this becomes a
  living regression reference — the next time a shared function changes, these numbers are what
  should be re-checked against, not re-derived from scratch.
