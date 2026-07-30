# CLAUDE.md — Soil Report Assistant Project Context

Use this file to bring a new Claude session up to speed on the project.

---

## Project Overview

A single-file interactive HTML web calculator (`index.html`) — named **"Soil Report Assistant"**
(tagline: *"No more guessing what to feed your lawn or garden"*) — that helps Virginia homeowners
interpret soil test results and calculate fertilizer and lime applications. Supports **VCE /
Virginia Tech** and **Waypoint Analytical** reports for **lawn**, **vegetable garden**, **flower
garden**, and **shrub/tree** contexts (four purposes × two labs = 8 report-type combinations).

**Primary audience:** Chesterfield County, Virginia (Zone 7b, Piedmont clay soils). Secondary: all of Virginia.

No server, no build step — single self-contained HTML file. Single-column responsive layout on all calculator tabs. Soil Test tab retains two-column `st-layout`.

**Core navigation principle (added July 26–27, 2026):** the app is gated. Only **Soil Test Report**
and **About & Instructions** are visible on load. A resident answers one question — "what is this
report for?" (lab + purpose combined) — and the one matching calculator tab appears. This
reflects a deliberate philosophy: a user should not be able to apply fertilizer without a soil
test telling them their starting point. See "Session Updates — July 26–27, 2026" for full detail.

---

## Source Documents

### VCE Primary Sources

| Publication | Title | Authors |
| :---- | :---- | :---- |
| SPES-40A | Spreadsheet-Based Calculator | Wilson (VSU); Goatley (VT) |
| 430-011 / SPES-334P | Lawn Fertilization in Virginia | Goatley et al. — VCE 2021 |
| 430-520 / SPES-223P | Fall Lawn Care | Goatley, Askew, McCall — VCE 2025 |
| 430-522 / SPES-669P | Maintenance Calendar for Warm-Season Turfgrasses | Goatley, Askew, McCall, Wilson — VCE 2025 |
| 430-523 / SPES-670P | Maintenance Calendar for Cool-Season Turfgrasses | Goatley, Askew, McCall, Wilson — VCE 2025 |
| 452-717 / SPES-306P | Soil Test Note 17: Cool-Season Grasses | Goatley, Ervin, Heckendorn — VCE 2021 |
| 452-718 / SPES-305P | Soil Test Note 18: Warm-Season Grasses | Goatley, Ervin, Heckendorn — VCE 2021 |
| 452-719 / SPES-687P | Soil Test Note 19: Vegetable and Flower Gardens | Latimer, Heckendorn — VCE 2025 |
| 426-323 / SPES-803P | Fertilizing the Vegetable Garden | Relf, McDaniel, Donohue — VCE 2026 |
| 452-701 / SPE-605NP | Soil Test Note 1: Explanation of Soil Tests | Maguire, Heckendorn — VCE 2024 |
| Agronomy Facts 8 | Soil Test Interpretation | Large/Ruiz Jr. — Waypoint 2023 |
| DCR 2014 | Virginia Nutrient Management Standards | Virginia DCR |
| SPES-384NP | Your Soil Test Report Simplified | Bolles — VCE 2021 |

### VCE Crop-Specific Sources

| Publication | Crop | Key sidedress guidance |
| :---- | :---- | :---- |
| 426-418 / SPES-795P | Tomatoes | Sidedress \#1 when first fruit \= half dollar; \#2 after first ripe tomato; \#3 for long-season |
| 426-413 / SPES-794 | Peppers, eggplant, potatoes | After fruit set; avoid excess N on potatoes |
| 426-405 / SPES-780P | Sweet corn | 3 tbsp 10-10-10/10-ft row at 12–18 inches |
| 426-403 / SPES-792P | Cole crops | 3 tbsp 10-10-10/10-ft row at 3 weeks after transplanting |
| 426-408 / SPES-785P | Leafy greens, spinach, lettuce | 1 lb 10-10-10 or 2 lbs 5-10-5 per 100 ft of row |
| 426-406 / SPES-779P | Cucumbers, squash, melons | 3 tbsp 33-0-0/10-ft row 1 week after blossoming |
| 426-422 / SPES-789P | Root crops | 0.5–2 lbs 10-10-10/100 sq. ft. at 4–6 inches tall |
| 426-402 / SPES-676NP | Beans, peas | Legumes fix own N; modest sidedress only at pod set |
| 426-411 / SPES-788P | Onions, garlic, shallots | Stop N when bulbing starts |

### Supplementary Regional Sources (Tier 2\)

| Source | Used for |
| :---- | :---- |
| University of Maryland Extension | N rates by feeding level (0.10/0.20/0.30 lbs/100 sq. ft.); liquid Borax method; OM-to-N credit **(garden context only** — 0.4 lbs N per 1% OM per 1,000 sq. ft.); fish emulsion in cool soils |
| Clemson HGIC | 35% preplant / 65% sidedress split; sandy soil flag; calcium nitrate as preferred sidedress |
| Rutgers NJAES FS626 | Organic fertilizer N% and release rates (Table 1); tomato sidedress schedule (Table 2); blood meal as medium-rapid; bat guano/bone meal/dried cow manure. **NPK ratios only — FS626 does NOT give bulk density; a prior session mistakenly cited it for bone meal density and this was corrected July 26.** |
| NC State Cooperative Extension | Calcium nitrate as preferred sidedress N source — delivers N without adding excess P or K. Blossom end rot and tip burn are calcium *uptake* disorders primarily caused by inconsistent watering and underdeveloped root systems, not soil calcium deficiency. Calcium nitrate provides direct corrective value only when soil calcium is low. **Also: manganese guidance (Torres Quezada, 2024) — see July 26–27 session.** |
| Mid-Atlantic Commercial Veg Guide 2026/2027 | Per-crop pH targets (Table B-1); soil testing 1–3 years. **Commercial guide — principles only, not home garden rates** |
| SARE LS16-269 | Blood meal \>80% available N within 2–4 weeks in warm soil |
| GitHub Fertilizer Calculator | Bulk density data; Borax sodium accumulation note |
| **Ohio State University Extension, Ohioline FABE-550** (Fulton, 2016) | *(Added July 26, 2026)* Physical Properties of Granular Fertilizers — loose bulk density ranges for Triple Superphosphate (950–1200 kg/m³) and Ammonium Nitrate (850–975 kg/m³); midpoints used |
| **NMSU Cooperative Extension, Guide H-119** | *(Added July 26, 2026)* Determining Amounts of Fertilizer for Small Areas — direct oz/cup bulk density figures for Muriate of Potash (10.0 oz/cup loose), Elemental Sulfur (10.2 oz/cup loose), Langbeinite (11.1 oz/cup loose) |
| **NC State Extension — Torres Quezada, 2024** | *(Added July 26, 2026)* "The Importance of Manganese in Vegetable Crop Nutrition in North Carolina" — Manganese Sulfate rates (20–25 lbs/acre broadcast, scaled to ~0.05 lbs/100 sq ft), pH-availability thresholds, chelated-Mn alkaline-soil guidance |

**Source policy:** VCE always primary. UMD and Clemson co-primary for home garden where VCE is silent. Rutgers FS626 and NC State supporting. Mid-Atlantic Veg Guide principles only. Never cite OSU, UNH, or non-regional extensions. **Exception carved out July 26, 2026: Ohio State Ohioline and NMSU Cooperative Extension are accepted specifically for bulk-density/volume-conversion data, where no closer regional source could be found and the non-.edu sourcing rule's "other universities" allowance applies — this is a narrow exception for physical/density data, not a general policy change for agronomic recommendations.**

**Bulk density sourcing standard (added July 26, 2026):** a product's volume conversion (cups/lbs) is shown ONLY if backed by a named, checkable source meeting the non-.edu rule (VCE, another university Extension, a government agency, or peer-reviewed publication). Where no such source exists, the calculator shows weight only ("weigh for accuracy") rather than an estimated figure. Fabricated/vague citation labels ("Industry sources", "Est. bulk density", "FAO Database" with no specific document) are not acceptable and were purged from the codebase July 26, 2026 — see that session's notes for the full audit.

**Specific gravity is NOT an acceptable density input (added July 26, 2026).** MSDS/SDS Section 9 "Specific Gravity" values reflect the pure crystal or absolute compound density, not the packaged granular/prilled form actually sold. Confirmed example: Southern Ag Sulfate of Potash SDS lists SG 2.66 (≈166 lbs/ft³ absolute crystal density) while the actual granular product is 75–81 lbs/ft³ loose — using the SDS value would understate volume by roughly half. Only bulk density (lbs/ft³ or kg/m³) from a product label or technical data sheet is accepted as user-entered density data.

**Critical rule:** Never infer soil texture from CEC or Buffer Index values.

---

## File Structure

Single HTML file — all CSS, JS, HTML inline. No external dependencies except Google Fonts CDN.

### Tabs (8) — reordered and gated July 26–27, 2026

Tab bar order: **Soil Test Report, About & Instructions**, then six calculator tabs that are
`display:none` until unlocked.

1. **Soil Test Report** (`tab-soiltest`) — interpretation cards, carry-over, single "what is this
   report for?" question. Always visible.
2. **About & Instructions** (`tab-about`) — moved to position 2 (was last) so it's discoverable
   before any data entry. Always visible.
3. **Cool-Season Lawns** (`tab-cool`) — hidden until a lawn report + Cool grass type entered
4. **Warm-Season Lawns** (`tab-warm`) — hidden until a lawn report + Warm grass type entered
5. **Lime** (`tab-lime`) — hidden until ANY report has P or K values entered (not purpose-specific)
6. **Vegetable Garden** (`tab-garden`) — hidden until a Vegetable Garden report entered
7. **Flower Garden** (`tab-flower`) — hidden until a Flower Garden report entered
8. **Shrubs & Trees** (`tab-shrub`) — hidden until a Shrubs & Trees report entered

Only ONE calculator tab is ever visible at a time (plus Lime, which is purpose-agnostic). See
`updateTabLocks()`, `soilTestTargetTab()`, `soilTestPurpose()` below and the July 26–27 session
notes for full mechanics.

### Key JavaScript Functions

| Function | Purpose |
| :---- | :---- |
| `interpretSoilTest()` | All soil test cards — string concatenation only, no backticks |
| `calcMulti(prefix)` | Custom plan engine for cool/warm |
| `calcAutoplan(prefix)` | Auto plan — no cap at 4 apps |
| `calcCool()` / `calcWarm()` | Route to auto or custom |
| `calcLime()` | Lime calculator — writes to `lime-results-panel` |
| `calcGarden()` | Vegetable Garden calculator — N preplant/sidedress plan + calls `renderNutrientStatusPanel()` for P/K/other nutrients; single merged "Nutrient Application Plan" card |
| `calcFlower()` | Flower Garden calculator — **still uses the pre-restructure blended-fertilizer approach**; not yet brought to parity with `calcGarden()` |
| `calcShrub()` | Shrubs & Trees calculator |
| `onCropTypeChange()` | Vegetable Garden crop change: calls `renderCropInfoPanel()` (merged single guidance panel) and `calcGarden()` |
| `renderCropInfoPanel()` | **(added, replaces `updateCropGuidancePanel`)** Single merged crop-guidance panel — reads directly from `CROP_FEEDING_LEVELS[cropKey]` and `SIDEDRESS_GUIDE[cropKey]`, both keyed by the exact crop dropdown value (no translation table). Shows feeding level, target pH, the **actual N default number**, sidedress timing, caution, all in one place — was previously split across two near-duplicate boxes |
| `renderNutrientStatusPanel(gardenType, area)` | **(signature changed — dropped pRating/kRating params)** Renders the P/K/Ca/Mg/S/micronutrient section of the Nutrient Application Plan. P/K now read directly from `st-p-rating`/`st-k-rating` (Soil Test tab canonical fields), same as Ca/Mg/S/micros |
| `nutrientRatingStatus(rating)` | Normalizes VCE/Waypoint/SUFF ratings to 'low'/'adequate'/'' |
| `gdnSetNutrientChoice(key, idx)` | Persists organic/synthetic product choice per nutrient across re-renders |
| `gdnSetTarget(key, val)` / `gdnTargets` | **(added)** Waypoint numeric nutrient targets — now entered inline in each nutrient's own row (not a separate 9-field grid); persisted in JS state (`gdnTargets` object) because the input elements are generated dynamically and don't exist when `prefillSampleReport()` runs |
| `gdnDensityToCupsPerLb(key)` / `gdnSetDensity(key,field,val)` / `gdnDensityInputHtml(key)` / `gdnCustomDensity` | **(added)** User-entered bulk density (lbs/ft³ or kg/m³ only — specific gravity intentionally NOT accepted, see Source Documents) for products with no verified density source |
| `cupsPerLbFromDensity(densityKgM3)` | Converts kg/m³ → cups/lb via the OSU-Extension-verified formula: `lbsPerCup = (kg/m³ × 2.20462) / 4226.75` |
| `fmtMeasure(lbs, cupsPerLb)` | tsp / tbsp / cup fractions based on bulk density |
| `detectProgram(fertN, winLbs)` | P1/P2/P3 WIN branch |
| `setPlanMode(prefix, mode)` | Toggle auto/custom |
| `printPlan(prefix)` | Always use this — never call window.print() directly |
| `getReportType()` | **(changed)** Reads the single `st-report-type` value directly (8 possible values); no longer defaults to `'vce-lawn'` when blank — returns `''` |
| `soilTestPurpose()` | **(added)** Returns `'vegetable'\|'flower'\|'shrub'\|'lawn'\|''` derived via substring match on the single report-type value |
| `isGardenReport()` | **(changed)** `true` for vegetable/flower/shrub (was a `'garden'` substring match against the old 4-value scheme) |
| `isWaypointReport()` | Substring 'waypoint' — unchanged behavior, still correct against the new 8-value scheme |
| `soilTestTargetTab()` | **(added)** Resolves which single calculator tab a report unlocks: 'garden'\|'flower'\|'shrub'\|'cool'\|'warm'\|null |
| `updateTabLocks()` | **(added)** Shows/hides calculator tabs (`display:none`, not dimmed) based on `soilTestTargetTab()`; redirects to Soil Test tab if the active tab gets hidden out from under the user |
| `activateTab(tab)` | **(changed)** Gate now checks `style.display === 'none'` (was `hasAttribute('disabled')`); central chokepoint for all tab-switch entry points (click, arrow-key, Continue button) |
| `onReportTypeChange()` | **(changed)** Toggles `inert` alongside `display` on hidden field blocks via a `setVisible()` helper (accessibility fix — hidden fields were previously still in tab order); calls `updateTabLocks()` |
| `carryOverToCalculators()` | Copies soil test values to calculators; uses setTimeout. Simplified July 26 — sub-type values (rose/deciduous-shrub/etc.) no longer carried over from Soil Test tab since that question moved entirely to the destination tab (asked once, not twice) |
| `prefillSampleReport(type)` | Types: `'lawn'`, `'garden'` (flower, now `waypoint-flower`), `'veggie'` (now `waypoint-vegetable`), `'vce-veggie'` (now `vce-vegetable`). Also resets/sets `gdnTargets` directly (not DOM fields) |
| `toggleCollapsible(baseId)` | **(added)** Generic collapsible toggle for About-tab per-tab mini-guides — replaces one-off dedicated toggle functions for new sections |
| ~~`updateCropGuidancePanel()`~~ | **REMOVED** — renamed/replaced by `renderCropInfoPanel()` |
| ~~`CROP_DATA` / `CROP_GUIDANCE_MAP`~~ | **REMOVED (dead code)** — only 2 of CROP_DATA's 5 fields were ever rendered; SIDEDRESS_GUIDE already covered every crop directly and more completely (including potato/okra/sweet potato/asparagus, which CROP_DATA lacked) |
| ~~`onGardenProductSelect()` / `setGardenFertMode()`~~ | **REMOVED** — the blended N-P-K product picker (old step 6) no longer exists for vegetable gardens; replaced by the single Nitrogen Source dropdown + per-nutrient amendment system |
| ~~`sgToCupsPerLb()` / `gdnCustomSG` / `gdnSGInputHtml()`~~ | **REMOVED** — specific gravity input removed entirely, see Source Documents |
| ~~`useRecommendedN()`~~ | Removed in an earlier session, **then the underlying rule was reversed July 21, 2026** — see "Nitrogen is NOT a lab-measured parameter" below. The N field is optional and defaults to the CROP_FEEDING_LEVELS research rate when blank; there is no separate `useRecommendedN()` function anymore because this is now the automatic default behavior, not an opt-in action |

---

## Vegetable Garden Tab (restructured July 21–27, 2026)

**This tab was fully restructured across the July 21 and July 26–27 sessions.** Everything below
supersedes the old "Vegetable & Flower Gardens Tab" documentation, which described a single
shared 8-step tab. Vegetable Garden and Flower Garden are now architecturally different — see the
separate "Flower Garden Tab (legacy, not yet restructured)" section below.

### Field numbering (current — 3 numbered steps, down from 8)

1. Lime recommendation from report (moved up from old position 8)
2. Crop selector (`gdn-crop-type`) — shows merged guidance panel (feeding level, target pH,
   research-based N default **number**, sidedress timing, caution) via `renderCropInfoPanel()`;
   N-override toggle sits directly below it, not ten lines away
3. "Calculate your Nutrient Application Rates" — bed status, Nitrogen Source (single-nutrient,
   organic or synthetic — no blended N-P-K picker), and (if a Waypoint report) numeric targets
   entered inline in each nutrient's own row in the results below

Bed size is an unnumbered practical sub-field under step 1's umbrella. Garden type (`gdn-type`,
vegetable/mixed) was **removed entirely July 26** — mixed beds folded under vegetable, since the
logic was identical; garden type/purpose is now established once, on the Soil Test tab.

### What was removed (do not reintroduce without explicit request)

- The blended N-P-K fertilizer picker (old step 6) — vegetable gardens address nitrogen as a
  single-nutrient choice; P/K/Ca/Mg/S/micronutrients are each handled individually below
- The "Can't find the recommended grade?" substitution table
- The standalone P/K rating select fields — P/K now auto-fill from the Soil Test tab's canonical
  fields (`st-p-rating`/`st-k-rating`), exactly like Ca/Mg/S/micronutrients already did
- The separate 9-field Waypoint numeric-target grid — targets are now entered inline per-nutrient
- `CROP_DATA` / `CROP_GUIDANCE_MAP` (dead code, see Key Functions table)
- Specific gravity as a density input option (see Source Documents)

### Report type and N/lime units

| Report type value | N unit | Lime unit | calcGarden() handling |
| :---- | :---- | :---- | :---- |
| vce-vegetable | lbs/100 sq. ft. | lbs/100 sq. ft. | direct |
| waypoint-vegetable | lbs/1,000 sq. ft. | lbs/1,000 sq. ft. | ÷ 10 before calculating |

(Report-type values changed July 26 from `vce-garden`/`waypoint-garden` — see "Single Combined
Report-Type Question" in the July 26–27 session notes.)

### CROP\_FEEDING\_LEVELS — seasonal N rates (unchanged data, now the sole source for guidance)

| Level | Rate | Crops |
| :---- | :---- | :---- |
| Heavy | 0.20 lbs/100 sq. ft. \= 2 lbs/1,000 sq. ft. | Tomato, pepper, potato, broccoli, cabbage, corn, beet, spinach, onion, okra |
| Medium | 0.20 lbs/100 sq. ft. \= 2 lbs/1,000 sq. ft. | Leafy greens, lettuce, cucumber, squash, melon, sweet potato, asparagus |
| Light | 0.10 lbs/100 sq. ft. \= 1 lb/1,000 sq. ft. | Beans/peas, carrot, root crops |
| Mixed | 0.20 lbs/100 sq. ft. \= 2 lbs/1,000 sq. ft., pH target 6.5 | Mixed bed key retained in data for legacy compatibility but no longer selectable (folded under vegetable July 26) |
| Annual/Perennial/Rose flower | (unchanged) | Retained in CROP_FEEDING_LEVELS/SIDEDRESS_GUIDE for the Vegetable Garden tab's crop dropdown, which still includes flower options as a legacy holdover — **not the same as the separate Flower Garden tab** |

### Nitrogen — research default is now visibly shown (fixed July 26)

Previously the crop hint said "leave it blank to use this research-based default" but never showed
the actual number. `renderCropInfoPanel()` now prints it directly: e.g. *"Research-based N default:
**0.20 lbs N per 100 sq. ft.** at planting."* The N-override toggle sits immediately below this
line (was a collapsible ten lines further down the page). Its hint text now also acknowledges that
a soil test report is sometimes a *range* (not a single number) when no specific crop was disclosed
on the original lab submission form.

**Key principle (unchanged):** Step 3's N field \= **preplant amount only**, defaulting to
CROP\_FEEDING\_LEVELS when blank. Sidedress amounts are **additional** fixed applications from crop
research (SIDEDRESS_GUIDE), not a split.

### SIDEDRESS\_GUIDE — now the sole source, keyed directly by crop dropdown value

`SIDEDRESS_GUIDE[cropKey]` covers all ~24 crop dropdown values directly (no translation table).
Confirmed to cover several crops CROP_DATA never had (potato, okra, sweet potato, asparagus).
Structure unchanged: `apps: [{n, trigger}]`, `note` (source-grounded caution + citation),
`SIDEDRESS_DEFAULT` fallback for unlisted vegetable crops only.

### Single-Nutrient Amendment System (`NUTRIENT_AMENDMENTS`, added July 21, expanded July 26)

For vegetable gardens, `renderNutrientStatusPanel()` renders one row per nutrient (P, K, Ca, Mg, S,
Zn, Mn, Cu, Fe, B) reading ratings directly from the Soil Test tab's canonical fields. Three calc modes:

- `calc:'flat'` — VCE Soil Test Note 19 flat rates (lbs/100 sq ft), fires when rating is Low
- `calc:'target'` — synthetic (or in some cases organic) products sized from the report's own
  numeric target via guaranteed-analysis %. **Fires even when the rating is Adequate**, if a
  Waypoint report prints a nonzero target — Waypoint's target is a maintenance figure, not just a
  deficiency flag (added July 26; lead-in text: "Rated adequate, but your report's own target
  calls for…")
- `calc:'none'` — VCE/other source names the product but publishes no specific rate (e.g. Chelated
  Manganese for alkaline soils, Borax liquid method)

**Manganese (added July 26, NC State Extension — Torres Quezada 2024):** Manganese Sulfate
(28–32% Mn) flat ~0.05 lbs/100 sq ft (scaled from 20–25 lbs/acre), plus a sized-to-target variant,
plus Chelated Manganese for alkaline soils. Mn removed from `NUTRIENT_NO_RATE_NOTE` accordingly.
S, Zn, Cu remain in `NUTRIENT_NO_RATE_NOTE` ("seldom a problem… no rate published"). **Both Mn
entries and Borax's "granular, weighed to target" entry now recommend dissolving the calculated
amount in 1–2 gallons of water and pouring over the bed, rather than dry-broadcasting — see
"Application method for tiny quantities" in the July 27–28 session notes for the full reasoning.**

**Waypoint numeric targets are entered inline** in each nutrient's own row (`gdnTargets` JS state
object, `gdnSetTarget()`), not in a separate grid — see Key Functions table.

**Bulk density / volume estimates:** shown only when a source meets the sourcing standard (see
Source Documents). Where not sourced, the panel shows weight only plus an inline widget for the
user to enter their own product's bulk density (lbs/ft³ or kg/m³ — **not** specific gravity).

### Output — single merged "Nutrient Application Plan" card (changed July 26)

Previously two separate cards ("Nitrogen Application Plan" + "Nutrient Status & Individual
Amendments"). Now ONE card: Nitrogen section first, "Phosphorus, Potassium & Other Nutrients"
section second, ONE "Print Plan" button after both (previously the print button was embedded
inside the nitrogen-only HTML, sandwiching it between the two sections — fixed).

### Organic product sidedress logic (unchanged)

**Fast-release organics** (`fastOrganic: true` — blood meal, fish meal, fish emulsion, bat guano)
\+ warm-season crops: can sidedress. **Fast-release organics \+ cool-season crops** OR
**slow-release organics**: all preplant. **Warm-season crops:** tomato, pepper, potato, corn,
squash, cucumber, melon, okra, beans, sweetpotato.

### GARDEN\_PRODUCTS — key fields (bulk density sourcing corrected July 26)

All products: `name`, `npk[N,P,K]`, `cupsPerLb`, `organic`, `fastOrganic`, `source`, `note19Rate`, `note`

| Product | fastOrganic | cupsPerLb source |
| :---- | :---- | :---- |
| Blood meal (13% N) | true | **No verified density source** — weigh for accuracy (was mislabeled "FAO Database") |
| Fish meal (10-6-2) | true | **No verified density source** — weigh for accuracy |
| Fish emulsion (~5-1-1) | true | Liquid; fast even in cool soil |
| Bat guano (10% N) | true | **No verified density source** — weigh for accuracy |
| Feather meal (10% N) | false | **No verified density source** — weigh for accuracy |
| Soybean/cottonseed/poultry/bone meal | false | **No verified density source** — weigh for accuracy (bone meal was mislabeled "Rutgers FS626," which only ever gave NPK ratios, never density — corrected July 26) |
| Calcium Nitrate, Nitrate of Soda, Ammonium Sulfate, Urea | — | VCE Note 19 / actual VCE garden report — exact, sourced |
| Ammonium Nitrate (34-0-0, added July 26) | false | Ohio State Ohioline FABE-550 |

Cottonseed meal NPK corrected to **6-3-2** (was 7-3-2 in an earlier pass; verify against Rutgers
FS626 Table 1 before changing again).

### fmtMeasure(lbs, cupsPerLb) — unchanged

- ≥ 4 cups → cups to nearest half
- 0.5–4 cups → cups as Unicode fractions
- 1–16 tbsp → tablespoons
- \< 1 tbsp → teaspoons
- Always flagged as approximate

---

## Flower Garden Tab (partially restructured July 28, 2026 — SUPERSEDES "legacy, not restructured")

**No longer accurately described as untouched legacy.** As of July 28, Flower Garden has a
**Complete N-P-K Fertilizer / Individual N, P, K Fertilizers** mode toggle (`flowerFertilizerMode`,
default `'complete'`) — a choice deliberately NOT offered on Vegetable Garden (single-nutrient
only there; the two tabs are allowed to diverge by explicit user decision). "Complete" mode is the
original blended-picker architecture, kept byte-for-byte as one of two paths, not removed.
"Individual" mode is the new build: a Nitrogen Source dropdown (mirrors Vegetable Garden's, no
Note-19-flat-rate bypass) plus the same shared, prefix-namespaced Nutrient Status panel Vegetable
Garden uses (`renderNutrientStatusPanel('flr', area, suppressPK)` — see Key Functions table).
`suppressPK` is true only in Complete mode, where P/K rows show "Handled by your Complete N-P-K
Fertilizer selection above" instead of an independent amendment, avoiding double-applying P/K the
blended product already supplies. The old manual `flr-p-rating`/`flr-k-rating` selects are gone —
P/K auto-fill from the Soil Test tab regardless of mode, same as Vegetable Garden.

**Lime is also now fully absorbed here** (July 28) — CCE % and bag-size fields, real
CCE-adjusted-rate + bag-count math, matching the standalone Lime tab's precision exactly. The
standalone Lime tab no longer unlocks for Flower (or Vegetable) purposes at all — see "Lime Tab"
section below.

This is stated explicitly in the app's own About tab instructions so users aren't misled about
which mode does what. **Still not brought over:** Vegetable Garden's crop-specific N guidance panel
(feeding level/pH/sidedress-timing merged card) has no Flower Garden equivalent — Flower Garden's
own crop-type-driven N defaults and caution box (below) remain its own separate, unmerged system.

Field numbering, N/lime unit handling, and the `annual`/`perennial`/`rose`/`bulb` crop-type
architecture (feeding levels, flower caution box, `SIDEDRESS_GUIDE` flower entries) are unchanged
from the pre-July-21 documentation:

### Report type and N/lime units

| Report type value | N unit | Lime unit | calcFlower() handling |
| :---- | :---- | :---- | :---- |
| vce-flower | lbs/100 sq. ft. | lbs/100 sq. ft. | direct |
| waypoint-flower | lbs/1,000 sq. ft. | lbs/1,000 sq. ft. | ÷ 10 before calculating |

(Changed July 26 from the shared `vce-garden`/`waypoint-garden` values — see July 26–27 session.)

**Flower entries in SIDEDRESS\_GUIDE** (unchanged):

| Key | apps | Note |
| :---- | :---- | :---- |
| `annual` | 1 app: 0.5 lbs N/1,000 sq. ft. at mid-season peak bloom, half preplant rate | Wash fertilizer off foliage; excess N suppresses flowers. *(VCE Note 19\)* |
| `perennial` | `apps: []` — no sidedress | Established perennials; early spring only; compost often sufficient; late-season N causes frost damage. *(VCE Note 19\)* |
| `rose` | 5 apps: 0.5 lbs N/1,000 sq. ft. each for April–August | Monthly March–August per VCE Note 19 |

**`SIDEDRESS_DEFAULT` fallback exclusion** — flower crop keys bypass `SIDEDRESS_DEFAULT` entirely.

**Flower caution box** — amber advisory whenever a flower crop type is selected: *"Avoid excessive
nitrogen — promotes vegetative growth at the expense of blooms."* Source: VCE Note 19.

**OM credit (garden-family tabs only)** — when `st-om` ≥ 5%: yellow notice showing `omVal * 0.4`
lbs N/1,000 sq. ft. natural release. Source: UMD Extension. **Not applicable to lawn tabs** —
lawn equivalent is the clipping return credit (VCE 430-011).

---

## Soil Test Report Tab

### Report type options (changed July 26, 2026 — one question, not two)

Previously report type (lab) and garden purpose were two separate questions/fields. **Now a single
`#st-report-type` dropdown asks both at once** — 8 values, 2 labs × 4 purposes, grouped by lab in
optgroups. The separate `#st-garden-type` field is **removed entirely**.

| Value | Lab | Purpose | Lime unit | Unlocks |
| :---- | :---- | :---- | :---- | :---- |
| vce-lawn | VCE | Lawn | lbs/1,000 sq. ft. | Cool or Warm (needs Grass Type too) + Lime |
| waypoint-lawn | Waypoint | Lawn | lbs/1,000 sq. ft. | Cool or Warm (needs Grass Type too) + Lime |
| vce-vegetable | VCE | Vegetable Garden | lbs/100 sq. ft. | Vegetable Garden + Lime |
| waypoint-vegetable | Waypoint | Vegetable Garden | lbs/1,000 sq. ft. | Vegetable Garden + Lime |
| vce-flower | VCE | Flower Garden | lbs/100 sq. ft. | Flower Garden + Lime |
| waypoint-flower | Waypoint | Flower Garden | lbs/1,000 sq. ft. | Flower Garden + Lime |
| vce-shrub | VCE | Shrubs & Trees | lbs/100 sq. ft. | Shrubs & Trees + Lime |
| waypoint-shrub | Waypoint | Shrubs & Trees | lbs/1,000 sq. ft. | Shrubs & Trees + Lime |

For lawn reports, Grass Type (`st-crop`: cool/warm) is still asked separately — that's a
legitimate remaining question the Soil Test tab can't resolve on its own. For garden/flower/shrub
reports, the single dropdown fully resolves which tab unlocks; the finer sub-type (which flower,
which shrub/tree) is asked exactly once, on the destination tab itself (was previously asked
TWICE — once via `st-garden-type`, again on the destination tab — this redundancy is why the field
was removed).

New helpers: `soilTestPurpose()`, `soilTestTargetTab()`. See Key Functions table.

### Sample report buttons (PII-free) — 4 buttons (was 3)

| Button | Type | report-type value | Key values |
| :---- | :---- | :---- | :---- |
| 📋 Lawn Sample | VCE warm-season | vce-lawn | pH 5.5, K Low, lime 60 lbs |
| 🌸 Flower Garden Sample | Waypoint annual flowers | waypoint-flower | pH 5.2, P Low, K Optimum, OM 5.6%, lime 87 lbs/1,000 sf, agricultural lime |
| 🌿 Vegetable Garden Sample (Waypoint) | Waypoint vegetable | waypoint-vegetable | Jim Myracle, Report No. 26-188-0532. P Very High (394 ppm), K Low (100 ppm) — the exact adequate-P/low-K case the Nutrient Status panel was built to handle. Sets `gdnTargets` (K2O 2.0, S 0.13, B 0.04, Mn 0.05) directly, not DOM fields |
| 🌿 VCE Vegetable Garden Sample | VCE vegetable | vce-vegetable | *(Added July 21)* Jim Myracle, VCE Lab ID 23-15911, Sample "VEGGD" (2023). All nutrients VH/SUFF, N-only fertilizer recommended, lime 3 lbs/100 sq ft. Contains VCE's own cup conversions for 4 N products — demonstrates the report's own math matches CROP_FEEDING_LEVELS defaults exactly |

Micronutrient prefill values must use `L`, `M`, `SUFF`, `H` — not Waypoint keys (ME, OP, VH).

### "Need to see the instructions?" prompt (added July 26)

Dismissible callout at the very top of the Soil Test tab card body (not inside the `role="heading"`
card-header — that was an ARIA violation, fixed; see July 26–27 session notes). "Yes, show me"
jumps to About & Instructions; "No thanks" dismisses. Either hides it for the session.

### Soil test card notes

- **"Your result:"** — always on new paragraph: `</p><p><strong>Your result:</strong>`  
- **pH alkaline** — "allow to drop naturally" removed; sulfur \+ consult VCE  
- **Base saturation** — softened per SPES-384: not critical in most home lawn situations  
- **Lime card** — not applied annually; covers three-year period (SPES-384)  
- **Soluble salts 400–640 ppm** — conditional on isGarden (garden version adds seedling note)  
- **Organic matter** — herbicide note removed; all high tiers action-good  
- **Micronutrient cards** — all use `isGarden` for context-specific guidance  
- **Boron garden** — liquid Borax method: 1 tbsp per gallon per 100 sq. ft.; do not band; sodium accumulation caution

### Lawn calculator notes

- Soil testing: **3–4 years** for lawns (SPES-669, SPES-670)  
- Cool-season spring N: 0.25–0.5 lbs water-soluble N/1,000 sq. ft. every 4–8 weeks (secondary timing, SPES-670)  
- Zoysiagrass/centipedegrass annual N: **1–2 lbs** per SPES-669 and Soil Test Note 18 (452-718). The calculator previously used 0.5–1.0 lbs for centipede — corrected to 1.0–2.0 lbs in index.html (June 10, 2026). JavaScript `maxN` for centipede corrected from 1.0 to 2.0.  
- Clipping recycling credit: 0.5–1 lb N per year, up to one-third of seasonal requirement (VCE 430-011, SPES-384NP). **Lawn-context equivalent of the garden OM credit. Do not use Rutgers FS626 or UMD OM formula for lawn N calculations — those are garden sources.**  
- Measuring collapsible: Google Earth (UMN instructions), Google Maps right-click, tape measure — no Chesterfield GIS, no time estimates

---

## Critical Implementation Rules

1. Never infer soil texture from CEC or Buffer Index
2. Only use thresholds explicitly stated in source documents
3. "Your result:" always on new paragraph
4. Action boxes use `abox()` — genuine actions only
5. No backtick template literals — string concatenation only (Safari)
6. No Unicode/emoji in JS string literals — HTML entities only
7. `numApps` never capped in `calcAutoplan` — warn if \>4 needed
8. `carryOverToCalculators()` setTimeout must not be removed
9. `printPlan(prefix)` always — never call `window.print()` directly
10. `calcLime()` writes to `lime-results-panel` — old individual IDs gone
11. Micronutrient selects: `L`, `M`, `SUFF`, `H` only
12. No PII anywhere in code or comments
13. Soil Test tab `st-layout` is two-column — do NOT change
14. ~~`showCropGuidance()` is removed — use `updateCropGuidancePanel()`~~ **SUPERSEDED**: `updateCropGuidancePanel()` itself removed July 26 — use `renderCropInfoPanel()`
15. Soil testing: "3–4 years" lawns; "every 2–3 years" active vegetable beds
16. Never recommend brand names — NPK ratios and WIN % only
17. ~~`onGardenProductSelect()` must call `setGardenFertMode('product')`~~ **REMOVED July 26** — both functions no longer exist; the blended product picker they governed is gone
18. **REVERSED July 21, 2026** (was: "calculator requires a soil test — do not add N rate suggestions"): Nitrogen is NOT a lab-measured parameter (nitrate-N leaches within a day or two of rain; neither VCE nor Waypoint lab-measures it — the report's "N" figure is a generic crop-based recommendation, not a test result). The N field is optional for vegetable/flower gardens; when blank, falls back to the CROP_FEEDING_LEVELS research default. The research default number is now **shown to the user directly**, not just used silently (fixed July 26 — previously computed but never displayed)
19. **(Added July 21)** Each visible Soil Test field carries a `data-canon` attribute pointing at its hidden canonical counterpart in `#st-canonical-fields`. `interpretSoilTest()`, `carryOverToCalculators()`, and all downstream calculation functions read ONLY from canonical fields — never the suffixed -vce/-wp IDs directly. `stSync(el)` and `stPushBlockToCanonical(blockId)` are the only bridge
20. **(Added July 26)** Each soil sample gets its own report for one purpose. The Soil Test tab's job is to identify ONE destination calculator tab — never ask the same purpose/sub-type question twice (once on Soil Test tab, again on the destination tab). If a destination tab has its own legitimate sub-type question (e.g. Flower Garden's annual/perennial/rose/bulb), the Soil Test tab must NOT also ask for it
21. **(Added July 26)** Locked/not-yet-relevant calculator tabs must be `display:none` AND carry `inert` on their container if they hold form fields that could otherwise remain in tab order — `display:none` alone does not reliably remove content from screen-reader/keyboard navigation in all cases actually tested
22. **(Added July 26)** Never put interactive elements (buttons, inputs, links) inside an element carrying `role="heading"` — this caused a real, confirmed focus-skip bug in Chrome (sample-report buttons became unreachable by Tab). Card headers needing action buttons must place those buttons in a sibling element, not inside the heading role
23. **(Added July 26)** Bulk density volume estimates require a named, checkable source (VCE, another university Extension, a government agency, or peer-reviewed publication) — see Source Documents sourcing standard. Specific gravity from an MSDS/SDS is NEVER an acceptable substitute density input (crystal density ≠ packaged granular density)
24. **(Added July 27)** Always call the shared `isGardenReport()` / `isWaypointReport()` / `soilTestPurpose()` helpers to inspect `st-report-type` — never re-implement the check locally (e.g. `rt.indexOf('garden')`). A stale local re-implementation of this exact check in both `carryOverToCalculators()` and `interpretSoilTest()` silently broke garden/flower/shrub carry-over and soil-test interpretation for an entire session after the report-type scheme changed from 4 values to 8 (see July 27 session notes). Any future change to the `st-report-type` value scheme must `grep` the whole file for every raw string inspection of report-type values, not just confirm the shared helpers were updated
25. **(Added July 27)** Tab bar buttons must NOT use the strict ARIA "roving tabindex" pattern (only the active tab in the Tab sequence, `tabindex="-1"` on the rest) — confirmed via live testing on the deployed site that this causes a real, reported "Tab skips the next tab" experience. Every visible, enabled tab button keeps `tabindex="0"` at all times; arrow-key navigation between tabs is offered as an addition, not a replacement, for sequential Tab
26. **(Added July 27)** When a reported bug can't be reproduced via static code reading, live-test the actual deployed page (a real, publicly reachable URL) with simulated keyboard/mouse input and `document.activeElement`/DOM inspection — this sandbox cannot reach a locally-hosted file from the real browser (file://, localhost, and data: URLs are all blocked from that context), so static analysis alone repeatedly failed to catch two real, confirmed bugs this session that live testing found immediately
27. **(Added July 28)** Never write a citation URL into the app or About tab based on a search-result snippet alone — navigate to (or `fetch()`) the actual URL and confirm it resolves (HTTP 200, correct content type) before citing it. A source first attributed to "Maryland Department of Agriculture" from a snippet turned out, on direct verification, to be a 404 — the real document was hosted by Hood College instead. The organization named in a search snippet's displayed URL path is not guaranteed to be who's actually hosting the content once you follow the link
28. **(Added July 29)** When verifying whether a specific CSS rule exists or is winning the cascade on a live page, walk the parsed CSSOM by rule type and check individual `selectorText` values — never rely on a substring match against a large block's concatenated `cssText` (e.g. an entire `@media` block), since unrelated rules sharing vocabulary can produce a false "it's there" positive. This exact mistake was made and caught in the same debugging session — see July 28–29 notes
29. **(Added July 29)** `index.html` is produced here; the user deploys it to GitHub Pages as a separate manual step with no push access from this side. "Is this fixed in the file" and "is this fixed on the live URL" are two different questions — when a user reports a bug that should already be fixed, check the deployed site directly (and re-check after they say they've redeployed) rather than assuming the latest local file is what they're looking at
30. **(Added July 29)** Any `body:not(.printing-X):not(.printing-Y)...` exclusion list controlling default print visibility must be updated every time a new `printing-*` prefix is added — the list is not self-maintaining. This was missed for `.printing-flower` and `.printing-shrub` when those prefixes were added, causing the Soil Test tab to print simultaneously with whichever of those two was actually requested. More generally: when a specific, confirmed-correct fix doesn't resolve a reported symptom, widen the search to every rule in the same media block rather than re-confirming the same rule again — the actual cause can be adjacent to, not inside, the thing already under suspicion

---

## Attributions

- **Chantel Wilson** — Assistant Professor and 4-H STEAM Extension Specialist, Virginia State University  
- **Michael Goatley Jr.** — Professor and Extension Specialist, Virginia Tech

Virginia Cooperative Extension is a partnership of Virginia Tech, Virginia State University, USDA, and local governments.

---

## Files

| File | Description |
| :---- | :---- |
| `index.html` | Main application — **Soil Report Assistant** (renamed July 26, 2026; was `lawn_garden_calc_v1_5.html` / "VCE Lawn & Garden Care Calculator") |
| `CLAUDE.md` | Project context for AI-assisted development |
| `README.md` | User-facing documentation |

---

## Session Updates — May 20, 2026

### Garden Calculator — Major Redesign

#### Application plan architecture (Option B)

The garden calculator now treats the step 4 N rec as **preplant-only** — exactly what the soil test report shows. Sidedress amounts are **additional fixed applications** from crop-specific research, not a split of the soil test number. This matches how actual Rutgers and VCE soil test reports work (both show 2 lbs N/1,000 sq. ft. preplant; sidedress is additional per FS626).

#### SIDEDRESS\_GUIDE data object

Fixed sidedress amounts in lbs actual N per 1,000 sq. ft. for 20 crops. Sources: Rutgers FS626 Table 2, VCE 426-series, Clemson HGIC, UMD Extension. Each entry has:

- `apps[]` — array of `{n: lbs_N_per_1000, trigger: 'timing description'}`  
- `note` — source-grounded caution  
- `SIDEDRESS_DEFAULT` — fallback: 1.0 lb N/1,000 sq. ft. at 3–4 weeks

Key tomato plan: 2 sidedress steps × 1.0 lb N/1,000 sq. ft. — matches Rutgers FS626 Table 2 exactly.

#### Sidedress product consistency

- If user selected a zero-P zero-K product (N-only synthetic or fast organic): use their product for sidedress (`useUserProduct = fertAlreadyZeroPK && npct > 0`)  
- If user selected a complete fertilizer (10-10-10, 5-10-5): default to calcium nitrate for sidedress  
- **Critical bug fixed:** `onGardenProductSelect()` now calls `setGardenFertMode('product')` before `calcGarden()` — previously product selection was ignored because mode stayed `'npk'`

#### CROP\_FEEDING\_LEVELS N rates corrected

Heavy feeders corrected to `nPer100: 0.20` (= 2 lbs/1,000 sq. ft.) — matches actual soil test report preplant recommendations. The old 0.30 figure was total seasonal N including sidedress, which was wrong for this field.

#### Step 3 crop selector — simplified

- Shows feeding level, target pH, and timing context only  
- No N amounts, no "Use X in step 4" button — calculator is for users with soil tests  
- `useRecommendedN()` function **removed**  
- `nDisplay`, `btnVal` variables **removed** from `onCropTypeChange()`

#### Application Timing card suppressed

When the application plan is showing (nRec \> 0 && fertN \> 0), the Application Timing card is hidden — it was redundant and conflicted with the crop-specific plan.

#### P/K flags suppressed for zero-P zero-K fertilizers

When `fertAlreadyZeroPK` is true (user already chose an N-only product), the P and K flag boxes are suppressed. They still appear for complete fertilizers when P or K is High/Very High.

#### Per sq. ft. application rate row

New result row: "Application rate per sq. ft." showing oz per sq. ft. and tbsp or tsp per sq. ft. based on bulk density. Practical guidance for gardeners applying to a raised bed.

#### gardenFertMode bug

`onGardenProductSelect()` must call `setGardenFertMode('product')` before `calcGarden()`. Without this, `gardenFertMode` stays `'npk'`, `productKey` is empty, and the selected product is ignored throughout the plan.

#### Sources confirmed by actual soil test reports

Both Rutgers (Lab 2016-55191 tomato, 2016-55189 garlic, 2016-55190 lettuce) and VCE (Lab 23-15911 vegetable garden) confirm:

- Preplant: 2 lbs N/1,000 sq. ft. (= 0.20 lbs/100 sq. ft.)  
- Midseason: 1 lb N/1,000 sq. ft. additional (from FS626)  
- "Except in high-organic matter soils" — OM credit fires when OM ≥ 5%

#### About tab sources reorganized

Five sections with clear headings. Two collapsibles:

- "9 crop-specific VCE publications" (426-series)  
- "UMD, Clemson, Rutgers, NC State & Mid-Atlantic Veg Guide" SPES-40A pinned at top with gold highlight and thanks language.

#### updateCropGuidancePanel cleanup

Old `CROP_DATA` table (preplant/sidedress/caution rows) removed from `updateCropGuidancePanel()`. Panel now shows feeding level \+ sidedress timing from `SIDEDRESS_GUIDE` only. No conflicting preplant amounts.

---

## Session Updates — May 25, 2026

### Mixed Bed support added

- `CROP_FEEDING_LEVELS`: `mixed` entry added — medium level, 0.20 lbs N/100 sq. ft., pH 6.5 (VCE Note 19 / SPES-687P)  
- `SIDEDRESS_GUIDE`: `mixed` entry added — `apps: []`, advisory note citing VCE 426-323, Rutgers FS626, Clemson HGIC. No fixed sidedress schedule — needs vary by crop in the bed  
- Mixed Bed option added to step 3 crop type dropdown and guidance panel dropdown, each in their own `Mixed` optgroup

### OM unit fix (garden tab)

Yellow OM advisory box now shows N release in **lbs/100 sq. ft. and lbs for user's bed** — consistent with all other garden tab result rows. Previous version used lbs/1,000 sq. ft., which was inconsistent with all other garden outputs.

### Source boundary clarification: lawn vs. garden OM

- **Rutgers FS626** is a vegetable garden bulletin — must never be cited in lawn context  
- **UMD Extension OM-to-N credit** (0.4 lbs N per 1% OM per 1,000 sq. ft.) is garden-context only in this project  
- **Lawn equivalent** is the clipping return credit: 0.5–1 lb N/year (VCE 430-011, SPES-384NP)  
- VCE grounds lawn N recommendations in grass species and WIN programme, not OM level (*Lawn Fertilization in Virginia*, SPES-334P: "the nitrogen requirements of turfgrass cannot be reliably evaluated by a soil test")  
- NDSU Extension / Soltanpour & Follett (2007) confirm the 0.4 lbs/1% OM figure is valid turfgrass science, but it is outside the project's VCE-primary source hierarchy for lawns and should not be added to the lawn calculator

### Lawn Soil Test Challenges document

`Soil_Test_Challenges_and_Solutions.docx` updated:

- Challenge 6 reframed from "Organic Matter Reducing the Nitrogen Need" → "Clipping Return Credit — A Hidden Nitrogen Source"  
- All references to UMD Extension OM formula and Rutgers FS626 removed from lawn document  
- Source: VCE 430-011 and SPES-384NP throughout

---

## Session Updates — June 3, 2026

### Source correction: calcium nitrate and blossom end rot

Blossom end rot in tomatoes and tip burn in leafy greens are calcium **uptake** disorders, not soil calcium deficiency. Primary causes are inconsistent watering and underdeveloped root systems in young transplants. Calcium nitrate is the preferred sidedress N source because it delivers nitrogen without adding excess P or K — not because it cures blossom end rot. Calcium nitrate provides direct corrective value only when the soil test shows **low calcium**. Updated in:

- CLAUDE.md NC State source row  
- README.md NC State supplementary source entry  
- Fun Facts document \#11

### SPES-40A citation confirmed correct

SPES-40A is the Excel spreadsheet (Wilson & Goatley). SPES-40P is the companion PDF user guide for that spreadsheet. All project documents correctly cite SPES-40A. No changes needed.

### Fun Facts document (\#2) — WIN clarification

SPES-40A does not include WIN% program detection. The calculator builds on SPES-40A by adding: WIN% Program 1/2/3 detection, clipping return credit, plain-English soil test interpretation, crop-specific garden sidedress plans, dual lab support (VCE and Waypoint), and mixed bed support.

### Fun Facts document — structural changes

- \#1 and \#12 merged into single card: "It replaces a stack of nearly 30 publications with one workflow"  
- Source count updated from "15" and "20+" to "nearly 30" (11 core VCE \+ 9 VCE crop guides \+ 9 supplementary \= \~29)  
- \#11 title changed to "Calcium nitrate: the right sidedress nitrogen for most vegetables"  
- \#11 body rewritten to lead with calcium nitrate rationale; blossom end rot demoted to afterthought with accurate framing  
- High-codepoint emoji (U+1F000 range) replaced with safe Dingbat symbols (U+2000–U+27FF) to prevent square box rendering in Word

### Documents produced this session

| Document | Description |
| :---- | :---- |
| `VCE_Calculator_Development_History.docx` | Full development history Feb–May 2026 |
| `Soil_Test_Challenges_and_Solutions.docx` | Lawn soil test challenges (7 challenges, lawn-only sources) |
| `Garden_Soil_Test_Challenges_and_Solutions.docx` | Garden soil test challenges (10 challenges) |
| `VCE_Calculator_User_Guide.docx` | Plain-language user guide, both lawn and garden |
| `VCE_Calculator_Fun_Facts.docx` | 11 highlights for new users |

### README.md corrections applied

- Heavy feeder N rate corrected: 0.30 → 0.20 lbs/100 sq. ft.  
- "Use recommended N" button reference removed (function was deleted)  
- Application plan architecture updated: old 35/65 split replaced with preplant-only \+ fixed sidedress  
- Mixed Bed added to feeding level list  
- NC State source corrected (blossom end rot framing)  
- Supporting documents section added

---

## Session Updates — June 5, 2026

### Flower support added to garden calculator

Annual flowers, perennial flowers, and roses added as crop types with full `CROP_FEEDING_LEVELS` and `SIDEDRESS_GUIDE` entries. See tables above.

**Key design decisions:**

- Annual flowers: 0.10 lbs N/100 sq. ft. preplant; one light mid-season app at half rate for heavy bloomers. Consistent with VCE Note 19 and UMD Extension (both specify 0.10 lbs N/100 sq. ft.)  
- Perennial flowers: 0.10 lbs N/100 sq. ft. early spring only; no sidedress; compost often sufficient for established beds (VCE Note 19, UMD, Rutgers soil test reports)  
- Roses: 0.20 lbs N/100 sq. ft. monthly March–August (VCE Note 19 explicit)  
- All flower types: amber caution box warning that excess N suppresses flowering — more consequential for flowers than vegetables  
- `SIDEDRESS_DEFAULT` fallback excluded for flower keys to prevent incorrect vegetable sidedress plan from appearing

**Step 3 crop selector and guidance panel** both updated with Flowers optgroup (Annual flowers, Perennial flowers, Roses).

**Timing cards** (annual and perennial) updated to be more precise; perennial card detects if rose selected and prompts for Step 3 accordingly.

### Cross-source survey: annuals, perennials, trees & shrubs

Survey of UMD Extension, Clemson HGIC, Rutgers NJAES, and NC State on flower fertilization. Findings:

**Annuals — all sources consistent with VCE Note 19:**

- UMD Extension: 0.10 lbs N/100 sq. ft.; organic matter (compost, mulch) may be sufficient; water after applying to wash off foliage  
- NC State: 2–3 lbs 10-10-10 per 100 sq. ft. without soil test (= 0.20–0.30 lbs N); slow-release total not to exceed 4–6 lbs N/1,000 sq. ft. seasonally; pH range 5.5–6.5 for bedding plants  
- Clemson: crop-level guidance (geraniums: 1 lb 10-20-10 per 100 sq. ft. \+ every 4–6 weeks); confirms excess N suppresses flowering

**Perennials — all sources consistent:**

- UMD Extension: 0.10 lbs N/100 sq. ft. spring; lightly fertilize if needed; repeat mid-summer only if growth weak or foliage pale; late-summer application for fall bloomers  
- Rutgers soil test reports: 1 lb N/1,000 sq. ft. (= 0.10 lbs/100 sq. ft.) spring, 4:1:2 N:P:K ratio, slow-release preferred; heavy feeders use 4:1:1  
- Both confirm established perennials need less than annuals; compost approach often adequate

**Trees & shrubs — gap in current calculator; VCE source material exists:**

- VCE **452-720 (Soil Test Note 20: Home Shrubs and Trees)** and **430-018 / HORT-120P (Fertilizing Landscape Trees and Shrubs)** exist but are not yet in the calculator  
- VCE **SPES-397** is the homeowner-friendly companion to 430-018  
- Clemson HGIC: 1–2 lbs N/1,000 sq. ft. fast-release; not exceeding 4 lbs annually; excessive N stimulates shoot growth, reduces flowering, increases pest pressure  
- NC State: same excess-N-suppresses-flowering caution; confirms overly succulent growth attracts aphids, scale, lace bugs  
- Rutgers: 4:1:2 N:P:K ratio for shrubs and small trees; same maintenance approach as perennial flowers  
- **Recommendation:** Trees and shrubs tab is a well-supported future addition. VCE Note 20 \+ 430-018 are the primary sources; Clemson, NC State, Rutgers all consistent.

**Bulbs:**

- UMD groups bulbs with perennials for fertilization purposes — treat as perennial flowers in the current calculator

**Source status for flowers:**

| Source | Annuals | Perennials | Trees/Shrubs |
| :---- | :---- | :---- | :---- |
| VCE Note 19 | ✅ primary | ✅ primary | ❌ (Note 20 exists, not yet in calculator) |
| UMD Extension | ✅ confirms 0.10 rate | ✅ spring-only/compost | — |
| Rutgers | — | ✅ 0.10 lbs/100 sq. ft. | ✅ consistent with Note 20 |
| Clemson HGIC | ✅ crop-level detail | — | ✅ 1–2 lbs N/1,000 sq. ft. |
| NC State | ✅ 0.20–0.30 without test; follow soil test | — | ✅ excess-N caution |

### Fun Facts document updated

- \#11 changed from calcium nitrate/blossom end rot to: *"Your Waypoint report's N recommendation may exceed Virginia's legal limit"* — a more practically important point for homeowners  
- Waypoint N recommendation can exceed VCE annual ceiling for cool-season grasses and zoysiagrass/centipedegrass; appropriate for bermudagrass but not for tall fescue (capped at 3.5 lbs N/1,000 sq. ft. per VCE 430-011, DCR 2014\)  
- Source tag: VCE 430-011, DCR 2014, Waypoint Agronomy Facts 8


---

## Session Updates — June 5, 2026 (continued)

### Issue 3: Centipede / Zoysia split

Zoysiagrass and centipedegrass were previously merged under a single `zoysia` key. They are now separate species with distinct data throughout.

**SPECIES_CONFIG changes:**

| Key | maxN | maxApp (P1/P2/P3) | Notes |
| :---- | :---- | :---- | :---- |
| `bermuda` | 4.0 | 0.9 / 1.0 / 1.5 | Unchanged |
| `zoysia` | 2.0 | 0.7 / 1.0 / 1.0 | Label changed from "Zoysiagrass / Centipedegrass" to "Zoysiagrass" |
| `centipede` | 1.0 | 0.5 / 0.5 / 0.5 | New — WIN% does not meaningfully change per-app limit for centipede; flat 0.5 lb cap all programs. Annual maxN subsequently corrected to 2.0 (June 10, 2026) — see below. |

**MAX_PRACTICAL_APPS changes:**

| Key | P1 / P2 / P3 | Window |
| :---- | :---- | :---- |
| `zoysia` | 3 / 3 / 2 | May/Jun/Jul |
| `centipede` | 2 / 2 / 2 | May/Jun only — low-N, slow-growing |

**HTML changes:**
- `warm-species` selector: three options (Bermudagrass/St. Augustine, Zoysiagrass, Centipedegrass)
- Reference table: separate rows for Zoysiagrass (1.0–2.0 lbs) and Centipedegrass (0.5–1.0 lbs)
- Static N hint updated: three species with separate ranges and both SPES-669 and SPES-670 cited
- Waypoint warning updated: "appropriate for bermudagrass but potentially too high for zoysiagrass and centipedegrass" with specific centipede guidance (0.75–1 lb every 6 weeks → ~3 lbs derived annual total vs. 1–2 lb VCE ceiling per Soil Test Note 18). Updated again June 10, 2026 — see session notes.
- Shade+clippings combo note: centipede threshold set at 0.5 lb vs zoysia 1.0 lb
- About tab source description updated to name centipede separately

**Source note:** VCE SPES-670 covers zoysiagrass/centipedegrass together without separating N ceilings. The centipede 0.5–1.0 lb range and the flat 0.5 lb per-application cap are grounded in agronomic principle (fertilizer-sensitive, slow-growing, thatch-prone). VCE 452-718 (Soil Test Note 18) is the best available VCE citation. Clemson HGIC confirms centipedegrass decline from excess thatch at >2 lbs N/1,000 sq. ft. — supporting the conservative ceiling.

---

### Issue 2: New vs. Existing Lawn (507 vs. 563)

A **Lawn Status** selector was added to the Soil Test tab, appearing alongside Grass Type whenever a lawn report type is active. Hidden for garden reports.

**New element:** `st-lawn-status-field` (div) containing `st-lawn-status` (select)
- Options: "Existing lawn" (default) / "New lawn (before seeding or sodding)"
- Fires `interpretSoilTest()` on change
- Hidden/shown in `onReportTypeChange()` alongside `st-crop-field`

**`interpretSoilTest()` changes:**
- Grass Type card retitled "Grass Type & Lawn Status"
- `statusLabel` appended to the value display
- Card body text branches on `isNewLawn`:
  - Cool/new: starter fertilizer, incorporation before seeding
  - Warm/new: lime and fertilizer incorporation before sodding/seeding
  - Existing: unchanged seasonal program descriptions

**`carryOverToCalculators()` changes:**
- `lawnStatus` read from `st-lawn-status`
- "Status: New lawn (pre-seeding)" or "Status: Existing lawn" added to the success bar description line
- New-lawn amber notice box appears in the success bar when `lawnStatus === 'new'`: reminds user to incorporate before seeding, use starter fertilizer
- Warm species carryover bug fixed: previously always set `warm-species` to `bermuda` for both cool and warm; now only sets it for `crop === 'warm'` (cool-season carryover leaves warm species at user's previous selection)

**Design note:** New vs. existing is surfaced as context and guidance only — it does not change the N calculations. VCE 430-011 does not prescribe different annual N totals for new vs. established lawns. The distinction matters most for incorporation timing and starter fertilizer, which are communicated in the interpretation card and the carry-over success notice.

---

### Flower support — groundwork (later superseded by full tab split)

Flower entries were added to `CROP_FEEDING_LEVELS`, `SIDEDRESS_GUIDE`, and `CROP_DATA` within `updateCropGuidancePanel()`. These entries remain active on the Vegetable Garden tab for mixed-bed contexts but the primary flower interface is now the dedicated Flower Garden tab (see below).

**CROP_FEEDING_LEVELS flower entries:**

| Key | level | nPer100 | pHTarget | Source |
| :---- | :---- | :---- | :---- | :---- |
| `annual` | light | 0.10 | 6.5 | VCE Note 19; UMD Extension |
| `perennial` | light | 0.10 | 6.5 | VCE Note 19; UMD Extension; Rutgers NJAES |
| `rose` | medium | 0.20 | 6.5 | VCE Note 19 |

**SIDEDRESS_GUIDE flower entries:**

| Key | apps | Note |
| :---- | :---- | :---- |
| `annual` | 1 app: 0.5 lbs N/1,000 sq. ft. mid-season before peak bloom | ⚠️ Excess N suppresses flowers. (VCE Note 19; UMD Extension) |
| `perennial` | `apps: []` — no sidedress | Established perennials; spring only; compost often sufficient. (VCE Note 19; UMD Extension; Rutgers NJAES) |
| `rose` | 2 apps: 1.0 lb N/1,000 sq. ft. after first and second bloom flushes | Stop all N by August 15. (VCE Note 19) |

`SIDEDRESS_DEFAULT` fallback is explicitly excluded for all three flower keys — prevents incorrect vegetable sidedress plan from appearing.

**`onCropTypeChange()` update:** When a flower key (`annual`, `perennial`, `rose`) is selected in step 3 and `gdn-type` is unset or set to a vegetable type, `gdn-type` auto-syncs to the flower key. Prevents vegetable logic running for flower selections.

---

## Session Updates — June 5, 2026 (Tab Split)

### Flower Garden tab — new dedicated tab

The calculator now has **7 tabs**: Soil Test Report | Cool-Season Lawns | Warm-Season Lawns | Lime | Vegetable Garden | Flower Garden | About & Instructions.

**Vegetable Garden tab** — renamed from "Vegetable & Flower Gardens". `gdn-type` selector reduced to Vegetable Garden and Mixed Bed only. Intro text directs users to the Flower Garden tab for flowers.

**Flower Garden tab** (`tab-flower`) — new dedicated tab with full calculator using `flr-` prefixed IDs throughout. No ID conflicts with the vegetable tab.

#### Flower Garden tab fields

| Step | Element | Notes |
| :---- | :---- | :---- |
| 1 | `flr-type` | Annual Flower Bed / Perennial Flower Bed / Rose Bed / Spring-Flowering Bulbs |
| 2 | `flr-length`, `flr-width`, `flr-area-direct` | Size with L×W or direct entry modes |
| 3 | `flr-n-rec` | **Optional** — falls back to research-based default if blank |
| 4 | `flr-p-rating` | VCE and Waypoint optgroups |
| 5 | `flr-k-rating` | VCE and Waypoint optgroups |
| 6 | `flr-fert-n/p/k`, `flr-product-select` | NPK entry or product picker |
| 7 | `flr-bed-status` | Established / New (preplant) — controls lime application limit |
| 8 | `flr-lime-rec` | Optional; Waypoint auto-converted |

#### Key design decisions

**N field is optional on flower tab.** When blank, `calcFlower()` uses `FLOWER_DEFAULTS[flowerType].nPer100` and displays a green "Using research-based default" notice. This serves casual users who don't have a soil test. Users with a soil test override by entering their N rec. This is a **flower-tab-only** feature — the vegetable tab still requires a soil test N rec.

**Default N rates (`FLOWER_DEFAULTS`):**

| Key | nPer100 | Primary sources |
| :---- | :---- | :---- |
| `annual` | 0.10 | VCE Note 19; UMD Extension (Care of Annuals and Perennials) |
| `perennial` | 0.10 | VCE Note 19; UMD Extension; Rutgers NJAES |
| `rose` | 0.20 | VCE Note 19 (explicit monthly March–August) |
| `bulb` | 0.13 | NC State spring bulb trials (4 lbs 9-9-6 per 100 sq. ft. = ~0.13 lbs N); Rutgers NJAES FS1220 |

**Bulb N rate derivation:** 4 lbs × 9% N = 0.36 lbs N per 100 sq. ft. — wait, corrected: 4 lbs × 0.09 = 0.36 lbs N per 100 sq. ft. This does not match the stated 0.13. Re-examined: 4 lbs of 9-9-6 per 100 sq. ft. → 4 × 0.09 = 0.36 lbs actual N per 100 sq. ft. **Correction:** the FLOWER_DEFAULTS `bulb` entry should be `nPer100: 0.36`, not 0.13. **Action required:** fix `FLOWER_DEFAULTS['bulb'].nPer100` from 0.13 to 0.36 in `index.html`.

**Application plan (`FLOWER_APP_PLAN`):**

Each flower type has a structured plan array used to build the application table. Bulbs have a "Stop after flowering" entry rendered as a red ⛔ no-fertilizer row — a prohibition, not an application step.

**Timing sections** — four separate timing blocks in `calcFlower()`, one per flower type. All source-cited inline.

#### Spring-flowering bulbs — critical rules

1. **Nitrogen is the primary nutrient need** — not phosphorus. Bone meal alone is insufficient. (NC State spring bulb trials, Dr. Paul V. Nelson)
2. **Apply at planting (fall) AND at emergence (spring, before leaves open)** — two applications per year
3. **Never fertilize after flowering** — encourages bulb rot and disease, shortens flower life. (Rutgers NJAES FS1220; NC State Extension)
4. **Fertilized bulbs performed significantly better than unfertilized** regardless of fertilizer method (NC State trials)

#### Source boundary for bulbs

VCE has no published home-garden N rate for spring-flowering bulbs. NC State and Rutgers NJAES are primary sources for bulb fertilization in this project. Both are consistent and appropriate for Virginia (comparable climate zone, mid-Atlantic context).

#### Carryover updates

`carryOverToCalculators()` now routes by garden type:
- `['annual','perennial','rose','bulb']` → Flower Garden tab (`flr-` fields, `calcFlower()`)
- `'vegetable'`, `'mixed'` → Vegetable Garden tab (`gdn-` fields, `calcGarden()`)
- Success bar destination button switches accordingly
- `flowerTypes` array hoisted above `if (isGarden)` block so it is in scope for the success bar

#### Soil Test tab updates

- `st-garden-type` selector: `bulb` (Spring-Flowering Bulbs) added alongside annual/perennial/rose/mixed/vegetable
- `gdnLabels` map in `interpretSoilTest()`: `bulb` added
- Garden type card routes flower types to flower tab (`goBtn('flower', ...)`) and vegetable/mixed to garden tab
- Lime action box text: dynamically selects "Flower Garden" or "Vegetable Garden" tab based on crop type

#### About tab updates

**New VCE source added:**
- Publication 426-200 (SPES-802P) — Annual Flowers: Culture and Maintenance. VCE. Confirms soil test as basis for annual flower fertilization rates.

**New supplementary sources section** — "Flower Garden Supplementary Sources" collapsible (`about-flower-sources-btn` / `about-flower-sources-body`):
- UMD Extension — Care of Annuals and Perennials (0.10 lbs N/100 sq. ft. for annuals and perennials; spring-only for perennials; compost alternative)
- Rutgers NJAES FS1220 — Spring Flowering Bulbs (no fertilizer after flowering; treat as perennials; divide when flowers decline)
- NC State Extension — Spring-Flowering Bulbs: Trials in North Carolina (Dr. Paul V. Nelson; N is primary nutrient; 4 lbs 9-9-6/100 sq. ft. trial rate; primary source for bulb default rate)
- NC State Extension — Add Flowering Bulbs in Your Garden This Fall (Forsyth County; confirms at-planting and at-emergence timing; no post-bloom fertilization)

`toggleAboutFlowerSources()` function added alongside `toggleAboutSuppSources()`.

About tab step 2 instructions updated to name both Vegetable Garden and Flower Garden tabs.

---

## Critical Implementation Rules (additions)

19. **Flower tab uses `flr-` prefix** for all element IDs — never reuse `gdn-` IDs in flower tab or vice versa  
20. **Flower tab N field is optional** — `calcFlower()` falls back to `FLOWER_DEFAULTS[flowerType].nPer100` when blank; this is intentional and unique to the flower tab  
21. **Bulb N default requires correction** — `FLOWER_DEFAULTS['bulb'].nPer100` should be 0.36 (4 lbs × 9% from NC State trial), not 0.13 (arithmetic error in initial implementation). Fix before next session.  
22. **Never fertilize bulbs after flowering** — this is a prohibition, not an option. Rendered as ⛔ red no-fertilizer row in the application plan  
23. **Spring bulb primary sources: NC State + Rutgers** — VCE is silent on bulb N rates at home garden scale; NC State and Rutgers NJAES FS1220 are the governing sources  
24. **`flowerTypes` array in carryover** must be hoisted above `if (isGarden)` block — it is used in the success bar destination button logic which executes after the block closes  
25. **`setFlowerFertMode('product')` must be called in `onFlowerProductSelect()`** before `calcFlower()` — same pattern as `onGardenProductSelect()`; without it, product selection is ignored

---

## Source hierarchy additions (flower context)

| Source | Used for |
| :---- | :---- |
| VCE Note 19 (SPES-687P) | Annuals (0.10 lbs N/100 sq. ft.), perennials, roses (monthly March–August), liming limits |
| VCE 426-200 (SPES-802P) | Annual flowers culture and maintenance; confirms soil test as fertilization basis |
| UMD Extension — Care of Annuals and Perennials | 0.10 lbs N/100 sq. ft. for annuals and perennials; compost alternative; spring timing; late-summer for fall bloomers |
| Rutgers NJAES FS1220 | Spring bulbs: no post-bloom fertilization; treat as perennials; divide when declining |
| NC State — Spring-Flowering Bulbs Trials | Bulb N rate (4 lbs 9-9-6 per 100 sq. ft.); N is primary nutrient (not P); two-application protocol |
| NC State — Forsyth County Bulb Guide | Confirms at-planting + at-emergence timing; no post-bloom |

**Source boundary:** Clemson HGIC has crop-level flower guidance (dahlias, hydrangeas, amaryllis) but no general home garden flower rate table — not used for rate calculations. NC State and UMD are consistent on 0.10 lbs N/100 sq. ft. for annuals/perennials; all sources agree roses need more frequent feeding.


---

## Session Updates — June 7, 2026

### Glossary tooltip system

A hover/tap definition system was added. Terms are underlined with a dotted green line; hovering (desktop) or tapping (mobile) shows a tooltip with a plain-English definition.

#### Architecture

**Single shared tooltip node** — one `<span class="term-tooltip">` appended to `<body>` on page load. Never inside a card. Uses `position: fixed` with coordinates calculated from `getBoundingClientRect()` on mouseenter/touchstart.

**Why fixed, not absolute:** Cards may have `overflow: hidden` or CSS `transform` that creates a stacking context and clips absolutely-positioned children. Fixed positioning is relative to the viewport and is never clipped by parent cards. (Original implementation used `position: absolute` inside the `.term` span and was clipped — corrected in the same session.)

**Term wrapping:** `applyGlossary(rootEl)` uses a `TreeWalker` to visit plain text nodes, skips nodes inside `SKIP_TAGS` (A, BUTTON, INPUT, SELECT, TEXTAREA, SCRIPT, STYLE, LABEL) and existing `.term` spans. Matches terms using regex with word boundaries. `GLOSSARY_FLAT` is sorted longest-phrase-first so "Water Insoluble Nitrogen" matches before "nitrogen". Definitions stored in `data-def` attribute on each `.term` span — not inside a child element.

**Placement logic (`showGlossaryTooltip`):**
- Measures tooltip dimensions by rendering off-screen first
- Prefers above the term; flips below if insufficient clearance
- Clamps left/right within viewport (8px margins)
- Recalculates `--arrow-left` CSS variable after horizontal clamp so arrow still points at the term
- Re-runs on `scroll` and `resize` events if a tooltip is open

**Touch support:** `touchstart` on `.term` toggles the shared tooltip open/closed. `touchstart` on `document` (when target is not `.term`) dismisses it.

**`MutationObserver` pattern:** Each dynamic output panel (soil test results, cool/warm/lime/garden/flower/shrub results, timing sections, hints) has an observer that calls `applyGlossary` after innerHTML changes. Static elements (field hints, field labels, note banners, About steps) get `applyGlossary` on `DOMContentLoaded`.

**`GLOSSARY_TARGETS` array** — IDs watched by MutationObserver:
`st-results-panel`, `cool-results-panel`, `warm-results-panel`, `lime-results-panel`, `gdn-results`, `gdn-timing`, `flr-results`, `flr-timing`, `flr-type-hint`, `gdn-crop-n-hint`, `shrub-results`, `shrub-timing`, `shrub-type-hint`, `cool-species-hint`, `warm-species-hint`, `cool-n-valid`, `warm-n-valid`

#### Starting glossary (15 terms)

WIN / Water Insoluble Nitrogen, Buffer Index, Buffer pH, base saturation, CEC / cation exchange capacity, pH, lime / liming, dolomitic / dolomitic lime, nitrogen, phosphorus / phosphate, potassium / potash, organic matter, preplant, sidedress / sidedressing, slow-release / controlled-release

**Adding new terms:** Add an entry to `GLOSSARY_ENTRIES` array — `{ terms: ['canonical term', 'alias'], def: 'definition string' }`. No other changes needed. Longest phrases go first in each `terms` array.

#### CSS classes

| Class | Purpose |
| :---- | :---- |
| `.term` | Inline span wrapping a matched glossary term; dotted green underline, `cursor: help` |
| `.term-tooltip` | Fixed-position shared tooltip node; `display: none` by default, `.visible` shows it |
| `data-arrow="up"` / `data-arrow="down"` | Set by JS to control CSS arrow direction |
| `--arrow-left` | CSS custom property set by JS to shift arrow after horizontal clamp |

---

### Shrubs & Trees tab (tab 7 of 8)

**New tab:** `tab-shrub`, button `data-tab="shrub"`, print class `printing-shrub`. `calcShrub()` called by `switchToTab()`.

#### Plant types (`SHRUB_PLANT_TYPES`)

Six types, two categories:

| Key | Label | N range (lbs/1,000 sq. ft.) | Default N | pH target | Primary source |
| :---- | :---- | :---- | :---- | :---- | :---- |
| `deciduous-shrub` | Deciduous shrub | 3–6 | 3 | 5.5–7.0 | VCE 430-018 |
| `evergreen-shrub` | Evergreen shrub | 1–3 | 2 | 5.0–6.5 | VCE 430-018 |
| `acid-shrub` | Acid-loving shrub | 1–2 | 1.5 | 4.5–6.0 | VCE 430-018; UMD Extension |
| `deciduous-tree` | Deciduous tree | 3–6 | 3 | 5.5–7.0 | VCE 430-018 |
| `evergreen-tree` | Evergreen tree | 1–3 | 2 | 5.0–6.5 | VCE 430-018 |
| `acid-tree` | Acid-loving tree | 1–3 | 2 | 4.5–6.0 | VCE 430-018 |

Default N uses the low end of each range — conservative default for home landscape. Users with a soil test override by entering their N recommendation.

#### Canopy-based area calculation

User enters canopy diameter (circular) or L×W (rectangular). Calculator doubles the area for application per VCE Note 20: "spread fertilizer evenly over an area twice the size of the plant's canopy as most of the smaller roots grow beyond the drip line." Direct area entry also available.

#### Turf adjacency (three outcomes)

| Selection | Behavior |
| :---- | :---- |
| No turf | Normal calculation |
| Partial overlap | Caps each application at 1.5 lbs N/1,000 sq. ft. (VCE 430-018); splits into multiple applications if annual rate exceeds cap |
| Fully adjacent | Advisory amber warning — VCE Note 20 states plants adjacent to fertilized lawn generally need no supplement |

#### "Do you need to fertilize?" health check

Opens the tab with a prominent amber box listing VCE Note 20's exact deficiency criteria (pale/small leaves, stunted growth, reduced buds, premature leaf drop). This is the most important guidance in Note 20 and is placed above the calculator fields.

#### Products (`SHRUB_PRODUCTS`)

8 products: Osmocote 18-6-12, 10-10-10, 12-4-8, Holly-tone 4-3-4, Azalea/Rhododendron 10-8-8, Ammonium sulfate 21-0-0, Urea 46-0-0, Calcium nitrate 15.5-0-0. Each has npk array, cupsPerLb, and a product-specific note displayed on selection.

#### Acid-loving plants — specific rules

- Use acid-forming or acid-specific fertilizer (ammonium sulfate, Holly-tone, azalea formula)
- Apply **after bloom**, not before — fertilizing during or before bloom can damage flower buds
- No lime — lime raises pH and harms acid-loving plants
- Iron chlorosis (interveinal yellowing) is the most common symptom in Virginia clay soils above pH 6.5 — iron chelate may provide faster relief than N fertilizer

#### No-fertilizer-at-planting rule (trees)

Documented in deciduous and evergreen tree timing guidance, sourced from UMD Extension: research shows nitrogen suppresses root establishment in newly planted trees; wait at least one full growing season.

#### Soil Test tab integration

- `st-garden-type` selector: all 6 shrub/tree types added as an `<optgroup>`
- `gdnLabels` map updated with all 6 keys
- `interpretSoilTest()` plant type card: routes shrub types to shrub tab via `goBtn('shrub', ...)`; card note warns that fertilization is only recommended with deficiency symptoms
- `isShrubType` derived from `shrubTypes` array (parallel to `isFlowerType`, `flowerTypes`)

#### Carryover

`shrubTypes` array added alongside `flowerTypes`. `isShrubCarry` routes to shrub tab — pre-fills `shrub-plant-type`, `shrub-p-rating`, `shrub-k-rating`. Success bar shows "Shrubs & Trees Calculator" button for shrub types.

#### About tab

**Three VCE sources documented:**
- Soil Test Note 20 (452-720 / SPES-336P) — governing source; all health-check and application rules
- Publication 430-018 (HORT-120P) — all N rate ranges; turf overlap cap; fertilizer ratio
- SPES-397 — simplified companion; 1 lb N/1,000 sq. ft. reference rate

**Supplementary sources collapsible** (`about-shrub-sources-btn` / `about-shrub-sources-body`):
- UMD Extension — Fertilizing Trees and Shrubs (no fertilizer at planting; 2–3 lbs max; shallow evergreen roots; acid-loving evergreens)
- Clemson HGIC — Fertilizing Trees & Shrubs (ANSI A300 2–4 lbs slow-release; active uptake budbreak to late summer)

`toggleAboutShrubSources()` added.

About tab step 2 instructions updated to name all three garden-type tabs (Vegetable Garden, Flower Garden, Shrubs & Trees).

---

### Tab nav overflow fix

**Problem:** 8 tabs overflowed the fixed-width nav container, clipping the rightmost tab ("About & Instructions").

**Fix applied to `.tab-nav` and `.tab-nav-inner`:**
- `overflow-x: auto` on `.tab-nav` — enables horizontal scroll
- `scrollbar-width: none` + `::-webkit-scrollbar { display: none }` — hides scrollbar chrome while keeping scroll functionality
- `min-width: max-content` on `.tab-nav-inner` — forces container to be exactly as wide as tabs need; prevents flex from squeezing or wrapping
- `flex-shrink: 0` on `.tab-btn` — prevents individual tabs from compressing
- Tab padding reduced: `14px 24px` → `14px 14px`
- Tab font reduced: `0.9rem` → `0.82rem`

**Pattern:** This is the correct approach for any nav with more tabs than fit at typical viewport widths. The scrollbar is hidden but functional — touch/trackpad users can still scroll. Do not remove `min-width: max-content` or tabs will wrap to a second line.

---

## Critical Implementation Rules (additions)

26. **Shrub tab uses `shrub-` prefix** for all element IDs — no overlap with `gdn-`, `flr-`, or other tab prefixes  
27. **Shrub tab N field is optional** — same as flower tab; falls back to `SHRUB_PLANT_TYPES[key].nDefault`  
28. **Application area = 2× canopy** per VCE Note 20 — this is calculated automatically in `calcShrubCanopy()`; if user enters area directly, they are responsible for doubling it (noted in field hint)  
29. **Turf overlap cap = 1.5 lbs N/1,000 sq. ft. per application** per VCE 430-018 — enforced automatically by `calcShrub()` when `shrub-turf` = `partial`  
30. **Acid-loving plants: no lime, apply after bloom** — enforced in timing guidance and product notes; ammonium sulfate and Holly-tone are the recommended product types  
31. **No fertilizer at planting for trees** — documented in timing guidance; sourced from UMD Extension research finding that N suppresses root establishment  
32. **Tab nav uses `overflow-x: auto` + `min-width: max-content`** — do not revert to fixed padding or remove these properties; with 8 tabs the nav will overflow at any viewport below ~1100px without them  
33. **`shrubTypes` array in carryover** must be declared alongside `flowerTypes` before the `if (isGarden)` block — both are used in the success bar destination button logic

---

## Source hierarchy additions (shrubs & trees)

| Source | Used for |
| :---- | :---- |
| VCE Note 20 (452-720 / SPES-336P) | All health-check rules; application area = 2× canopy; ≥50% WIN requirement; no late-season N; turf adjacency advisory |
| VCE 430-018 (HORT-120P) | All N rate ranges by plant type; turf overlap 1.5 lbs cap; 3-1-2 ratio recommendation; acid-shrub timing (after bloom) |
| VCE SPES-397 | 1 lb N/1,000 sq. ft. reference rate; product quantities table |
| UMD Extension — Fertilizing Trees and Shrubs | No fertilizer at planting; 2–3 lbs N max; shallow evergreen root caution; acid-loving evergreens list |
| Clemson HGIC — Fertilizing Trees & Shrubs | ANSI A300 2–4 lbs N/1,000 sq. ft. for slow-release; active uptake timing from budbreak |

**Source boundary:** WSU Extension EB1034 and ISA Arboriculture & Urban Forestry journal were found in research but not used — outside the regional land-grant hierarchy. UNH Cooperative Extension was found but not used for same reason. Missouri Extension (MU) not used. All rate decisions trace to VCE 430-018 as primary.


---

## Session Updates — June 10, 2026

### Centipede annual N ceiling corrected

**Problem:** The centipede annual N ceiling throughout the calculator was set to 0.5–1.0 lbs/1,000 sq. ft., sourced to SPES-669 and SPES-670. Research against the primary sources revealed this was incorrect.

**Primary sources confirmed:**
- Soil Test Note 18 (452-718, Goatley/Ervin/Heckendorn): "Centipedegrass and mature zoysiagrass perform best at 1 to 2 pounds N/1,000 square feet/year"
- SPES-669 (430-522): "Centipedegrass and zoysiagrass should receive only 1–2 lbs N/1,000 sq ft total"
- DCR 2014: does not set a separate centipede-specific ceiling below 1 lb; the 4 lb warm-season ceiling applies to bermudagrass/St. Augustine; centipede and zoysia are referenced in VCE publications at 1–2 lbs

**Corrections made to index.html (5 locations):**
1. Waypoint advisory text (line ~1213) — rewritten to cite Waypoint's actual centipede guidance (0.75–1 lb every 6 weeks through late summer, derived annual total ~3 lbs), compare against VCE 1–2 lb ceiling in Soil Test Note 18 (452-718). "Far too high for centipedegrass" removed — replaced with specific, sourced claim.
2. Reference table row (line ~1223) — centipede suggested annual total corrected from 0.5–1.0 to 1.0–2.0 lbs
3. Field hint (line ~1239) — centipede ceiling corrected from 0.5–1.0 to 1.0–2.0 lbs; citation updated to include Soil Test Note 18
4. About tab source description (line ~2201) — centipede annual range corrected from 0.5–1.0 to 1.0–2.0 lbs
5. JavaScript SPECIES_CONFIG `maxN` (line ~2478) — centipede `maxN` corrected from 1.0 to 2.0; warning now fires correctly at anything above 2.0 lbs

**Note on per-application cap:** The flat 0.5 lb per-application cap for centipede (all programs) is retained. The correction only affects the annual ceiling, not the per-application limit.

**Note on shade+clippings combo text:** One instance remains that says "for centipede, it may be well under 0.5 lb" — this is contextual (shade + clipping reductions applied to a 1.0 lb starting target), not a ceiling statement, and is arithmetically defensible. Left unchanged.

### Fun Facts document — Fact #1 and Fact #11 updated

**Fact #1:**
- "nearly 30 publications" → "more than 35 publications" (heading, body ×2, source footnote)
- "eleven core VCE publications" → "fourteen core VCE publications" (body ×2)
- "two lab-specific interpretation guides (VCE and Waypoint)" → "(VCE and Waypoint Analytical, a commercial soil testing laboratory)"
- Source footnote: "VCE primary (11 publications)" → "VCE primary (14 publications)"

**Fact #11:**
- Rewritten to acknowledge Waypoint does differentiate by grass type, but differentiation ≠ alignment with VCE ceilings
- Centipede now the headline example: Waypoint guidance (0.75–1 lb every 6 weeks) → derived ~3 lb annual total vs. VCE 1–2 lb ceiling (Soil Test Note 18)
- Tall fescue retained as secondary example (4.0 vs. 3.5 lbs)
- Sources confirmed: Soil Test Note 18 (452-718); Waypoint example report (LAWN-S3M-UnitsPPM.pdf)

### Source count

The calculator now draws on **more than 35 publications**. The previously stated "nearly 30" figure predates the shrubs & trees tab (3 new VCE sources) and other additions. Count confirmed by source table audit this session.

### VCE primary publication count

**14 VCE publications** (including SPES-40A). Previous "11" figure excluded SPES-40A and the three shrubs & trees sources (452-720/SPES-336P, 430-018/HORT-120P, SPES-397). Waypoint Agronomy Facts 8 and DCR 2014 are correctly excluded from the VCE count — Waypoint is a commercial laboratory, DCR is a state agency.

### Waypoint source clarification

Waypoint Analytical is a **commercial soil testing laboratory**, not a VCE publication or land-grant source. Agronomy Facts 8 (Waypoint, 2023) is cited for lab-specific interpretation guidance only. This distinction is now explicit in Fun Facts #1 and in the email to Dr. Goatley.

### Email to Dr. Goatley drafted

Full draft produced for review. Author: calculator developer (Master Gardener volunteer, Chesterfield County). Purpose: share tool, seek feedback and endorsement, invite collaboration. Key points:
- Builds on SPES-40A (Wilson/Goatley)
- Framed as "teaching tool disguised as a calculator" — flags stimulate reasoning, not just compliance
- Deployment plan: Help Desk volunteers first; resident release later
- Centipede/Waypoint claim verified against sources before inclusion; language is precise and defensible



### Bulb N rate and source update

**Problem:** The NC State Extension "Spring-Flowering Bulbs: Trials in North Carolina" page (`content.ces.ncsu.edu/spring-flowering-bulbs-trials-in-north-carolina`) is no longer available. Additionally, the bulb default N rate of 0.13 lbs/100 sq. ft. was an arithmetic error (it was calculated as if 9-9-6 had 3.25% N; the correct math is 4 lbs × 9% = 0.36 lbs, not 0.13).

**Replacement sources (both active NC State Extension pages):**
- Franklin County Center: `franklin.ces.ncsu.edu/2023/11/spring-flowering-bulbs` — explicit rate: 4 lbs of 10-10-10 per 100 sq. ft. at planting and at emergence. Also confirms Bulb Booster as alternative and pH target 5.8–6.5.
- Wayne County Center: `wayne.ces.ncsu.edu/news/plant-bulbs-this-fall-for-spring-flowers/` — confirms 10-10-10 for both slow-release-at-planting and quick-release-at-planting-plus-emergence options.

**Rate corrected:** `FLOWER_DEFAULTS['bulb'].nPer100` changed from `0.13` → `0.40` (4 lbs × 10% N from 10-10-10 per 100 sq. ft.).

**pH target corrected:** `pHTarget` for bulbs changed from `6.5` → `6.0` (Franklin County source specifies optimal pH 5.8–6.5; 6.0 is the appropriate midpoint for this range, slightly more acid than the 6.5 used for other flower types).

**All source citations updated** in: `FLOWER_DEFAULTS` note, `FLOWER_APP_PLAN` planting step note, `calcFlower()` timing section (at-planting, at-emergence, and stop-after-flowering steps), and About tab supplementary sources collapsible.

**About tab:** Dead NC State trials link replaced with two active Franklin County and Wayne County pages. Both pages documented with full source descriptions explaining what guidance came from each.

**Rutgers NJAES FS1220 retained** as a supporting source for the no-post-bloom-fertilization rule (that guidance is not present on the Franklin/Wayne pages but is well-sourced in FS1220).

**Critical rule 21 updated:** The previously noted "fix before next session" action item is resolved. The correct rate is 0.40 lbs N/100 sq. ft.

---

## Session Updates — June 10, 2026 (Conformance Audit, Round 1)

A full source-conformance and real-report validation pass was run against twelve de-identified soil test reports (VCE and Waypoint; lawn, vegetable, and flower contexts) supplied by the Help Desk. Each value was traced through the calculator's logic, against the cited source, and against each report's own lab recommendation. Two audit-planning documents and one findings document were produced (`Calculator_Conformance_Audit_Plan.md`, `Conformance_Audit_Findings_Round1.md`). Six corrections were made to `index.html`; all JS validated clean after each.

### Correction 1 — Waypoint "Optimum" mismapped to VCE "H−" (fixed)

`WAYPOINT_TO_VCE` maps Waypoint OP → VCE H−. The P and K interpretation branches then treated H− as "high to very high, plants do not respond, use zero-P." Result: a nutrient **at target** (Optimum) was reported as excess, and a genuinely Very-High Waypoint soil rendered identically to a merely-Optimum one — defeating the phosphorus-runoff environmental flag on every Waypoint report. The correctly-worded "Optimum" branch was dead code because OP never survived the remap.

**Fix:** added a leading `pRatRaw === 'OP'` / `kRatRaw === 'OP'` branch in both interpretations that renders "at target — maintain, no additional needed." Strengthened the genuine High/Very-High branch to name runoff risk explicitly. Fixed the rating pill to show the raw Waypoint rating (Optimum) instead of the mapped H−, and added human-readable labels (`pill()` LABELS map: VL→Very Low, LO→Low, ME→Medium, OP→Optimum, VH2→Very High, etc.). The fertilizer-rec engine and carry-over were intentionally left mapping OP→H− since both correctly yield "no additional P" (matching Waypoint's own rec of 0 at Optimum).

**Source confirmation:** VCE Soil Test Note 1 (452-701) states the 12–35 lb/A P range is rated "medium *or optimum*" — VCE treats optimum as the top of the adequate band, not excess. This validates routing Optimum to "maintain" rather than "high, do not apply."

### Correction 2 — Lawn N-rec not captured, so the ceiling check wasn't automatic (fixed)

The garden/flower tabs capture the report's N figure, but the lawn tabs did not — carry-over set P/K/species/size but left `cool-n-rate`/`warm-n-rate` blank. The VCE-ceiling warning only fired after the volunteer manually typed the figure into the lawn tab. This is the exact Fact #11 scenario; the live example is the Irma Arritt Waypoint report (N 4.0 on a Midlothian cool-season lawn, above the 3.5 tall-fescue ceiling).

**Fix:** added an optional `st-lawn-n` field on the Soil Test tab (lawn report types only; shown/hidden alongside crop and lawn-status fields). Added a new "Nitrogen Recommendation Check" interpretation card that fires when an N value is entered: cool-season checks against 3.5; warm-season flags that the figure suits bermuda (4.0 ceiling) but exceeds the 1–2 lb zoysia/centipede ceiling, prompting species confirmation. Both branches cite 430-011, DCR 2014, Soil Test Note 18, SPES-669. `carryOverToCalculators()` now passes the N value to `cool-n-rate` or `warm-n-rate` by grass type. The warning now appears at interpretation time. The Arritt report is now a clean end-to-end demonstration of the Fact #11 feature.

### Correction 3 — Waypoint garden lime not converted in the interpretation card (fixed)

The Soil Test interpretation card for **garden** lime treated the entered figure as lbs/100 sq. ft. regardless of lab. Waypoint garden reports give lime in lbs/**1,000**, so the Anderson flower report's 87 would have displayed as "87 lbs/100 sq. ft., 18 applications" — off by 10×. (The Garden tab itself was correct; it divides by 10 at `calcGarden`/`calcFlower`. Only the interpretation card was wrong.)

**Fix:** the garden lime card now detects `rt === 'waypoint-garden'`, converts to lbs/100 (÷10) before display and before computing the application split, and shows the conversion explicitly ("your report lists 87 lbs/1,000 sq. ft., which is 8.7 lbs/100"). Anderson 87 now reads 8.7 lbs/100 over 2 applications — consistent with the 2.5-tons-per-acre figure on the same report. **Lawn lime path confirmed correct** (both labs use lbs/1,000, no conversion, 50-lb-per-application split). No double-conversion on carry-over (raw value carries; calc converts once).

### Correction 4 — Conflicting Waypoint→VCE maps for Very Low (fixed)

Two maps disagreed: the local `waypointToVCE` in `onReportTypeChange` had `VL → 'L'` while the global `WAYPOINT_TO_VCE` had `VL → 'L-'`. This made the report-type round-trip unstable (VCE L− → switch to Waypoint → switch back landed on L, not L−).

**Fix:** local map corrected to `VL → 'L-'` to match the global map. Waypoint's lowest tier correctly maps to VCE's lowest (L−).

### Correction 5 — Extreme organic-matter advisory stated false precision (fixed)

The garden OM-to-N credit (`omVal * 0.4`, garden-only, ≥5% trigger) applied the linear UMD formula without bound. At the Anderson #3 bed (29.4% OM) it implied ~11.8 lbs N/1,000 sq. ft. of natural release — far beyond any crop's need — stated to two decimals. The math didn't error, but the precision was unwarranted at an OM level the formula isn't calibrated for.

**Fix:** above 15% OM, the advisory switches to a qualitative message ("releases more nitrogen than most vegetables require; sidedressing very unlikely to be necessary; monitor plant color") and notes the standard estimate is calibrated for ordinary soils and overstates release at this level — no precise figure shown. Below 15% (the realistic 5–11% high-OM cases), the precise figure displays as before. The 15% threshold is a judgment call, not a sourced boundary — replace if a VCE/UMD validity limit is found.

### Correction 6 — VCE Medium P/K bands confirmed conformant (no change)

Verified the displayed interpretation ranges against VCE Soil Test Note 1 (452-701):
- P Medium: **12–35 lb/A** ✅ exact
- K Medium: **76–175 lb/A** ✅ exact
- Ca Medium: **721–1,440 lb/A** ✅ exact
- Mg Medium: **73–144 lb/A** ✅ exact

No correction needed.

### Items confirmed conformant during the audit (no change)

- Per-application N caps: Waypoint's own "0.7 soluble / 0.9 slow-release per 30 days" language (Arritt report) matches the calculator's Program 1/2 cool-season caps exactly.
- OM credit trigger: fires at ≥5% (Snow 11.4%, Anderson 5.6%), correctly silent below (Stephens 4.4%, Shaw 2.9–3.8%); garden-only, never on lawn tabs.
- Garden melon sidedress: more conservative than the Waypoint report's 0.5–1.5 lb guidance — documented intentional deviation (VCE 426-406, Rutgers FS626), a teaching-moment candidate.

### Open items for future rounds

- **`NEED_RATIO` tables vs DCR +/− rule.** DCR Standards & Criteria specify: L−/M−/H− → use the highest value of the recommended range; L+/M+/H+ → use the lowest. The calculator's `NEED_RATIO` gradations should be verified against this rule (out of Round 1 scope).
- **Flower tab has no OM advisory.** The OM-to-N credit lives only in `calcGarden`, not `calcFlower`. Anderson #3 (flower report, 29.4% OM) run through the Flower tab shows no OM note. Lower priority — flower N rates are already minimal and excess N suppresses bloom — but a consistency candidate.
- **Phases 1–8 remaining checklist items** in `Calculator_Conformance_Audit_Plan.md` not yet exercised by the supplied reports (e.g. shrub/tree reports — none in the test set; lime CCE adjustment).

### Documents produced this session

| Document | Description |
| :---- | :---- |
| `Calculator_Conformance_Audit_Plan.md` | Tab-by-tab audit methodology and checklist |
| `Conformance_Audit_Findings_Round1.md` | Findings from the twelve-report validation pass |

---

## Session Updates — June 10, 2026 (Clipping & Shade Controls)

Following the conformance audit, two interactive site-adjustment controls were built on both lawn tabs (cool and warm). Both were previously **advisory text only** — the calculator told the user to manually reduce their N rate but did no arithmetic. The Fun Facts doc (#3) and the Goatley email both described an automatic clipping "toggle" that did not exist; these builds make those claims true. All JS validated clean after each edit.

### Clipping return credit — now an interactive toggle

**Before:** advisory paragraphs on both tabs instructing the user to "reduce your annual total by up to one-third." No control, no calculation.

**Built:**
- Checkbox `cool-clip-toggle` / `warm-clip-toggle` below the N-rate input on each tab.
- Helper `clipCredit(prefix, rawRate)` returns the reduction: **one-third of the target, capped at 1.0 lb/1,000 sq. ft.** The cap reflects VCE 430-011's actual figure (clippings return 0.5–1 lb N/year). Without it, a 4.0-lb bermuda target would over-credit at 1.33 lbs. With it, the one-third rule governs low targets and the 1.0-lb ceiling governs high ones.
- **Autoplan mode:** auto-reduces the effective rate; plan recomputes applications/per-app amounts from the reduced figure; shows a credit box explaining the adjustment.
- **Manual multi-slot mode:** does NOT auto-reduce user-entered slots (the user controls those); shows an informational note with the reduced target to aim for.
- **Ceiling check stays on the raw target** in both modes — a clipping credit cannot be used to justify exceeding the species N ceiling.

### Shade adjustment — 3-position control

**Before:** advisory text ("one-half to two-thirds as much nitrogen") on both tabs. No control.

**Source basis:** VCE 430-011 states heavily shaded grass needs "one-half to two-thirds as much nitrogen as grasses growing in full sun" — a **range, not a point value**. Clemson HGIC and Cornell corroborate. The source does not support proportioning by degree of shade or percent-of-day, so the control is a discrete 3-position choice the user judges, not a slider with interpolation.

**Built:**
- 3-position radio group (`cool-shade` / `warm-shade`): **Full sun (×1) / Some shade (×0.67) / Heavy shade (×0.5)** — the two reduction values are the exact ends of VCE's stated range, not an invented midpoint.
- The exact VCE 430-011 quote is displayed above the control so the user places themselves in the band.
- **Area note** (per Help Desk guidance): if a lawn is part sun / part shade, the user is told to run the shaded zone as a **separate calculation** using only its square footage — the reduction must not be applied to a whole mixed lawn. (Proportioning isn't supported by the guidance.)
- `shadeFactor(prefix)` reads the selected radio; `effectiveNRate(prefix, rawRate)` applies **shade first, then clipping credit on the shade-adjusted target** — matching the order in the advisory text.
- Warm-season control carries the 430-011 winterkill caution (avoid late-season N in shade).

### Fine fescue in heavy shade — caution note

VCE 430-011: fine fescue in heavy shade should be reduced even further, or applications omitted until fall leaf collection is finished. A warning note now fires in both autoplan and manual modes when species = `fine` AND heavy shade (×0.5) is selected. Silent for fine fescue in lighter shade/full sun and for other species in any shade.

### Revalidation against advisory-text worked examples

The combined shade + clipping math was checked against the examples already written into the advisory text — all matched exactly:
- Cool tall fescue 2.5 → 1.675 at ×0.67 (text: "1.67"); → 1.25 at ×0.5 (text: "1.25")
- Cool fescue 2.5, heavy shade + clippings → 0.83 (text range "0.8–1.1", at the ×0.5 end)
- Warm bermuda 3.0 → 2.01 at ×0.67 (text: "2.0"); → 1.5 at ×0.5 (text: "1.5")
- Warm bermuda 3.0, heavy shade + clippings → 1.0 (text range "1.0–1.3", at the ×0.5 end)

### Note on a syntax error caught in process

The fine-fescue `if` block was initially committed with an unclosed brace; the post-edit JS parse check caught it before output (it would have broken the entire script, not just the feature). Fixed and re-validated. Reinforces: run the script-parse check after every JS edit.

### Area carry-over — verified working (no change)

Confirmed `carryOverToCalculators()` reads `st-lawn-size` and sets `cool-lawn-size`, `warm-lawn-size`, `lime-lawn-size`, `gdn-area-direct`, and `flr-area-direct` (the latter two also switch to direct-area mode). Carry-over fires on the "Apply to Calculators" button. The button appears when a P/K rating and crop/grass type are set (`canCarryOver = (pRatRaw || kRatRaw) && (isGarden || crop)`); area is not part of that gate, so entering area alone (no ratings) does not surface the button — acceptable for normal soil-test use. A built-in guard warns the user if they open the carry-over bar without an area entered.

### Toggles/controls not wired to carry-over or sample loader

The clipping toggle and shade radios always start at their defaults (unchecked / full sun) — a safe opt-in default. They are not set by carry-over or the sample-report loader. If sample reports should demonstrate these features, that is a small future addition.

---

## Session Updates — June 10, 2026 (Conformance Audit, Round 2 — Cross-cutting Phases)

The audit plan was upgraded to v2 (`Calculator_Conformance_Audit_Plan_v2.md`) after Round 1 showed the original plan only knew how to hunt wrong *numbers* — but Round 1's two worst defects were a bad cross-system translation and a data-flow gap. v2 adds three cross-cutting phases (T: translations, U: units, D: data flow) plus process rules (regression loop, mandatory JS-parse check, required boundary testing). Round 2 executed those three phases. Findings in `Conformance_Audit_Findings_Round2.md`. One correction made; one issue flagged for decision.

### Correction 7 — Optimum fix was incomplete; downstream consumers still treated OP as "High" (fixed)

The Round 1 Optimum fix (Correction 1) corrected only the **interpretation card** (which reads `pRatRaw` directly). Carry-over still mapped Waypoint OP → VCE H−, so the garden, flower, and shrub tabs received "H−" in their rating dropdowns and every downstream consumer treated Optimum as genuine High:
- Garden "your soil tests **High** for phosphorus" tomato/pepper note fired (lines ~4789).
- Fertilizer-rec engine returned "Use a Zero Phosphorus Fertilizer" (P_REC['H−']).
- `NEED_RATIO['H−'] = 1` applied (same as genuine High).

This produced a **user-visible contradiction**: the interpretation card said "Optimum — at target, maintain" while the garden plan said "tests High, use zero-P," on the same report.

**Fix:** carry-over now translates Waypoint **OP → VCE M+** (not H−). M+ is the correct equivalent of "Optimum":
- P_REC[M+] = "not needed, but may be used" (at-target, not excess)
- NEED_RATIO[M+] = 1 (no shortfall)
- `pHigh` test (`['H-','H','H+','VH']`) is false for M+ → no false "tests High" note

Matches VCE Soil Test Note 1 ("12–35 lb/A P is rated medium **or optimum**" — Optimum belongs at the top of the adequate band, M+, not the excess band, H−). Implemented as a `carryMap()` helper in `carryOverToCalculators()`; the interpretation card (handles OP directly) is unchanged, so card and downstream now agree end-to-end. Verified all tiers: VL→L−, LO→L, ME→M, **OP→M+**, VH2→VH.

**Lesson:** a fix to an interpretation message must be traced to every consumer of the underlying value. The Optimum bug had two layers; Round 1 caught one. Phase T (trace every translation through every consumer) is what surfaced the second.

### Phase T (translations) — other results

- Local `waypointToVCE` and global `WAYPOINT_TO_VCE` confirmed identical (Round 1 VL fix holds).
- Waypoint→VCE→Waypoint round-trip fully stable (the trip that matters on report-type switching).
- VCE→Waypoint→VCE lossy for +/− variants — expected many-to-one collapse (9 tiers → 5), harmless for interpretation. Not a defect.
- Interpretation "Optimum" branch confirmed reachable; no other unreachable branches.

### Phase U (units) — results

- ✅ Lime lbs/1,000 vs lbs/100 vs tons/acre: Round 1 fix holds, no double-convert, Anderson report reconciles across all three.
- ✅ Garden ÷10, soluble salts dS/m→ppm (×640), injury thresholds: consistent.
- ⚠️ **FLAGGED FOR DECISION: "Waypoint ppm" reference ranges are VCE lb/A ranges ÷2, not Waypoint's actual bands.** The card-header "typical range" shows e.g. "P Medium: 6–18 ppm (Waypoint)" — which is just the VCE 12–35 lb/A ÷2. Waypoint uses Mehlich-3 (VCE uses Mehlich-1); the extractants differ, so Waypoint bands can't be derived by unit-converting VCE's. Agronomy Facts 8 gives Waypoint's own ranges (K is CEC-dependent: 95–215 ppm). **Lower severity** — interpretation is rating-driven, not value-driven, so the displayed range drives no calculation; it's a display-accuracy/traceability issue. **Options:** (a) use Waypoint's actual bands from Agronomy Facts 8 (noting K is CEC-dependent), or (b) relabel as "VCE equivalent in ppm" rather than implying they are Waypoint's thresholds. Needs a careful Agronomy Facts 8 read — flagged, not fixed blind.
- ✅ Canopy ×2 (shrubs) described correctly; not yet exercised (no shrub report).

### Phase D (data flow) — results

All handoffs ✅: the OP→M+ carry-over fix (above), the Round 1 lawn N-rec handoff, full carry-over completeness (area, P/K, species, lime rec/type, lawn status, N-rec), and safe defaults for the new clipping/shade controls (not set by carry-over or sample loader).

### Open items after Round 2

| Item | Status | Blocker |
| :-- | :-- | :-- |
| Waypoint ppm reference ranges | Flagged for decision | Needs Agronomy Facts 8 read + judgment (option a vs b) |
| `NEED_RATIO` vs DCR +/− rule | Not yet checked | Phase 8 task |
| Shrub/tree tab (Phase 7) + canopy ×2 validation | Unexercised | No shrub/tree report in the set |
| VCE garden/flower reports | Phases 5–6 validated via Waypoint only | No VCE garden/flower report supplied |
| Flower-tab OM advisory | Absent by design | Consistency decision pending |
| CCE adjustment (Lime tab) | Not exercised | No report exercised the CCE input |

### Documents produced this round

| Document | Description |
| :-- | :-- |
| `Calculator_Conformance_Audit_Plan_v2.md` | Upgraded plan with Phases T/U/D and process rules |
| `Conformance_Audit_Findings_Round2.md` | Round 2 findings (cross-cutting phases) |

---

## Session Updates — June 10, 2026 (Round 2 follow-ups: Waypoint ranges + NEED_RATIO)

### Correction 8 — Waypoint reference ranges now use Agronomy Facts 8, not VCE ÷2

Resolves the Phase U flagged item. The Soil Test card-header "typical range" for Waypoint reports previously showed VCE lb/A bands mechanically divided by 2 (e.g. "P Medium: 6-18 ppm (Waypoint)"), mislabeled as Waypoint's. Waypoint uses Mehlich-3; VCE uses Mehlich-1; the extractants differ, so VCE bands can't be unit-converted into Waypoint's.

**Investigation:** Agronomy Facts 8 publishes a K optimum band (CEC-dependent) and a Mg adequacy figure, but **no numeric P or Ca band**. So "use Waypoint's published numbers" was only partpossible. Decision (with user): show Waypoint's real numbers where they exist; be honest where they don't.

**Implemented (Waypoint display only; VCE display unchanged):**
- **K** — CEC-dependent optimum band selected live from the entered CEC (Agronomy Facts 8, Mehlich-3): CEC <5 → 95-115; 5-9.9 → 130-155; 10-14.9 → 155-190; 15+ → 175-215 ppm. Fallback "95-215 ppm (varies by CEC)" when CEC not entered. Updates live as CEC changes (interpretSoilTest re-runs on input).
- **P** — "use the rating bar on your Waypoint report (no numeric band published)" — Agronomy Facts 8 publishes no P ppm band, so no fabricated number.
- **Ca** — same rating-bar treatment (no published band); **Mg** keeps the published "≥64 ppm adequate."

**Note:** the displayed range drives no calculation (interpretation is rating-driven). This was a display-accuracy/traceability fix, not a math fix. Validated K-band selection against all real reports' CEC (Shaw 3.8 → 95-115; Snow 15.3/20.7 → 175-215; mid-range soils land correctly between). JS clean.

### Phase 8 check — NEED_RATIO vs DCR +/- rule (conformant, no change)

DCR Standards & Criteria: for soil-test modifiers, minus (L-/M-/H-) → use the HIGH end of the recommended range; plus (L+/M+/H+) → use the LOW end. The calculator's `NEED_RATIO` (P/K need multiplier) was checked against this:

```
L band:  L- = 3    L = 2.5   L+ = 2
M band:  M- = 2    M = 1.5   M+ = 1
H band:  H- = 1    H = 0.75  H+ = 0.5
VH = 0
```

Within every band, minus > mid > plus (monotonic decreasing) — consistent with the DCR rule (minus = more = high end; plus = less = low end). Deficiency gradient correct (most-deficient L- highest at 3; VH = 0 = no application). All **three** instances (autoplan line ~2758, multi-slot ~2980, product-rec ~3072) are byte-identical — no drift. **Conformant; no correction needed.**

### Open items after this round

| Item | Status | Blocker |
| :-- | :-- | :-- |
| Shrub/tree tab (Phase 7) + canopy ×2 validation | Unexercised | No shrub/tree report supplied |
| VCE garden/flower reports | Phases 5-6 via Waypoint only | No VCE garden/flower report supplied |
| Flower-tab OM advisory | Absent by design | Consistency decision pending |
| CCE adjustment (Lime tab) | Not exercised | No report exercised the CCE input |

All other audit items through Round 2 are ✅ resolved or documented intentional deviations.

---

## Session Updates — June 10, 2026 (Flower OM, CCE survey/validation, lime timing)

### Flower-tab OM advisory added

The organic-matter nitrogen advisory previously existed only in `calcGarden` (Round 1 open item). Added to `calcFlower` with **bloom-appropriate framing** rather than a copy of the vegetable version: because excess N suppresses flowering, the flower advisory leans toward "skip or minimize" instead of "you may need less." Thresholds match the garden tab (≥5% precise figure; ≥15% qualitative). At ≥15% it states additional N is very likely unnecessary and could reduce flowering; at ≥5% it tells the user to lean to the low end or skip. Sourced UMD Extension + VCE Note 19. JS clean.

### CCE adjustment — survey, validation, and gypsum guard

CCE can't come from a soil report (it's on the lime *product label*), so a materials survey was done instead. Document: `Liming_Materials_CCE_Survey.md`.

**Authoritative source found:** VCE 452-510 / SPES-158P, "Sources of Lime for Acid Soils in Virginia" (expert-reviewed Sept 2024). Gives CCE by material type (Table 1) and rate-adjustment factors (Table 2). Should be added to the About source list; it's the Virginia authority for CCE.

**Real garden-center CCE ranges:** pelletized ~100% (clusters 90-100); calcitic pulverized 80-100%; dolomitic 95-108% (exceeds 100); Virginia legal floor 85% to be sold as "Aglime." Burnt/hydrated reach 120-175% but aren't typical homeowner buys. **Gypsum (CaSO4) has zero CCE — does not raise pH, is not lime** (key Help Desk trap; sold next to lime, looks identical).

**Validation (5 product-driven cases, rec = 50 lbs/1,000):** the Lime tab formula `adjRate = limeRec * 100 / CCE` (line ~3182) exactly reproduces VCE 452-510 Table 2:
- 100% → 50.0 | 90% → 55.6 | 85% → 58.8 | 108% → 46.3 | 135% → 37.0 — ALL PASS.
- CCE > 100 correctly *reduces* the amount (dolomitic, hydrated). Conformant; no math correction.

**Improvements made (survey-driven):**
- CCE field hint rewritten with VCE 452-510 ranges (pelletized ~100%, calcitic 80-100%, dolomitic 95-108%) and a gypsum-is-not-lime warning; source cited; `max` raised 150→175 so burnt/quick lime isn't rejected.
- **Gypsum/low-CCE guard:** a warning fires in the result when CCE < 50, naming gypsum and telling the user to confirm their product is actually limestone.

### Pelletized-lime timing note added (NC State)

Research/source question: does pelletized lime change application timing? **Yes** — and the sources contradict the "pelletized is faster" marketing:
- **NC State (in source hierarchy):** "Pelleted lime comes into contact with fewer soil particles than finely ground lime. As a result, soil pH changes are slower with the pellets." Enhanced by tilling in after the pellets soften.
- **Iowa State / A&L (Jones & Mallarino 2018):** once slaked, pelletized tracks a 60-100 mesh grind — faster than coarse aglime but slower than pure CaCO3; reaction slows in cold/dry soil.
- **A&L:** pelletized reacts faster but runs out sooner — same total over years, applied at lower rates more frequently.

**Mechanism:** the pellet must absorb moisture and slake (revert to powder) before it reacts. This is moisture- and temperature-dependent, so timing matters.

**Added to Lime tab result:** a note that pelletized lime must slake before reacting (so it's slower to start and stalls in dry soil), should be applied when soil moisture is reliable (fall/early spring or before rain) not into a dry summer lawn, benefits from being worked into garden beds, and reacts-then-runs-out sooner (reinforcing the split-application logic). Attributed to NC State Extension + VCE 452-510. Note: VCE's own pubs emphasize CCE/fineness but I did not find VCE stating the timing differential explicitly — the timing finding is NC State (a Tier-2 Mid-Atlantic source in the hierarchy).

### Open items after this round

| Item | Status | Blocker |
| :-- | :-- | :-- |
| Shrub/tree tab (Phase 7) + canopy ×2 validation | Unexercised | No shrub/tree report supplied |
| VCE garden/flower reports | Phases 5-6 via Waypoint only | No VCE garden/flower report supplied |
| Add VCE 452-510 to About source list | Recommended | Minor — not yet done |

All other audit and enhancement items through this session are ✅ resolved or documented intentional deviations.

---

## Session Updates — June 10, 2026 (Fertilizer grades table — marketplace survey)

### Marketplace survey of high-N, low/zero-P lawn fertilizers

Surveyed real lawn fertilizers (retail + professional + organic) to populate the "Help me choose a fertilizer at the garden center" table, organized by the WIN threshold that drives program selection. Survey: `Lawn_Fertilizer_Product_Survey.md` (working reference, retains brand examples for traceability). Public-facing table extract: `Fertilizer_Grades_Table.md`.

**Design constraint (per user): NO brand names in the calculator.** Products are represented only by generic N-P-K + WIN profiles so residents can match what's on the shelf without endorsement. Confirmed zero brand strings in index.html after the edit.

### Common grades table rewritten (in the fert-chooser, both lawn tabs)

The old table showed nearly every grade as "0% WIN / P1" with two vague slow-release rows. Replaced with survey-grounded generic profiles:
- Quick-release zero-P maintenance grades that actually dominate big-box shelves: 28-0-3 to 32-0-4, 29-0-3 to 38-0-4, urea 46-0-0 (all P1).
- Four concrete slow-release zero-P profiles by chemistry: 25-0-5 methylene-urea/MESA (~50%), 32-0-10 poly-coated urea (50-65%), 39-0-0 ureaform (~70%+), 9-0-9 organic feather/blood meal (~85%+).
- Catch-all "any slow-release blend, WIN 15-49% of N" → P2.

**Critical correctness fix surfaced by the survey:** the table now states explicitly that **WIN must be read as percent of TOTAL NITROGEN, not percent of bag weight** — divide the label WIN figure by total N%. This is the #1 misclassification trap (e.g. a label's "0.6% WIN" on 24-N = 2.5% of N = P1, not slow-release). Header and footnote both spell out the unit. Lists the slow-release chemistries to look for (methylene urea, MESA, ureaform, coated urea, IBDU, protein organics). Footnote reinforces no-brands + label-is-authority, cited VCE 430-011 + Notes 17/18.

**Phosphorus exclusion preserved:** zero-P rows only for the maintenance/High-P case; starter grades (24-25-4, 21-22-4) noted as new-lawn-only because they're intentionally high-P; organic N sources that carry P (e.g. biosolid-based ~4% P2O5) flagged in the survey as disqualified when P tests High.

**Note for review:** high-WIN rows (≥50%) are labeled Program 3, consistent with the calculator's existing 3-program structure. The VCE source defines only the 15% (P1/P2) threshold; if Program 3 has its own defined WIN cutoff, confirm the ~50% products land in the intended program. JS validated clean.

### Documents produced this session

| Document | Description |
| :-- | :-- |
| `Lawn_Fertilizer_Product_Survey.md` | Full marketplace survey (with brand examples, for reference) |
| `Fertilizer_Grades_Table.md` | Brand-free grades table extract (matches the calculator) |

---

## Session Updates — June 10, 2026 (Program 3 verification — CORRECTION of an in-session error)

### What happened

While reviewing the fertilizer grades table, a question arose about whether the calculator's **Program 3** (the ≥50% WIN tier with a higher per-application cap) was sourced. Reading **only Soil Test Notes 17 and 18** — which describe just Programs 1 and 2 — led to an **incorrect conclusion that Program 3 was an unsourced invention exceeding the DCR ceiling.** A change was made to `detectProgram()` collapsing P3 into P2. **This was wrong and has been reverted.**

### The correct, source-verified position

The user supplied the full **VCE 430-011** PDF (SPES-334), which explicitly defines **THREE** programs in tables 2-4:
- **Program 1** (table 2): quick-release, **<15% WIN**
- **Program 2** (table 3): slowly available, **15-49% WIN**
- **Program 3** (table 4): majority slowly available, **≥50% WIN**

Direct quote: "Program 3 (table 4) details nitrogen fertility strategies that use fertilizer products with the majority (>50%) of nitrogen being from slowly available nitrogen sources." Footnotes confirm: "* ...15-49% slowly available... ** ...≥50% slowly available."

The Program 3 higher per-application cap (config uses 1.5 lb) is consistent with regional turf guidance — e.g. UT Extension states majority-slow-release (>50% WIN) products "may be applied at from 1 1/2 to 2 pounds of nitrogen per 1,000 square feet."

### Resolution

- `detectProgram()` **restored to the original three-program logic** (P1 <15, P2 15-49, P3 ≥50). Net change to the calculator from this whole exploration: **only an added source-citation comment**; the logic is exactly as it was. JS validated clean; all 30 Program 3 references intact.
- The fertilizer grades table built earlier (high-WIN rows labeled P3) was **correct all along** — no change needed.
- Public-facing docs (`Fertilizer_Grades_Table.md`, `Lawn_Fertilizer_Product_Survey.md`) correctly show Program 3 — no change needed.

### LESSON (important for future conformance work)

**Soil Test Notes 17 and 18 are ABRIDGED.** They describe only Programs 1-2. The authoritative source for the program structure is **VCE 430-011 itself** (which the Notes reference), and it defines all three programs. Do not treat the condensed Notes as complete. When a conformance question touches program structure or per-application caps, **430-011 is the source of truth**, not the Notes.

This also validates a process rule from the v2 audit plan: trace a figure to the *primary* publication, not a secondary/abridged one. The earlier centipede-ceiling work had the inverse lesson (don't trust the calculator's own internal text); this one is: don't trust an abridged note over the full publication.

---

## Session Updates — June 10, 2026 (Fertilizer table P-range expansion + README refresh)

### Fertilizer chooser expanded beyond zero-P

Per user direction, the "Help me choose a fertilizer at the garden center" table is no longer limited to zero-P grades. It now spans the full phosphorus range and is **organized by the soil's P rating** so a resident reads their interpretation and jumps to the matching group. Still brand-free (verified zero brand strings); real products converted to generic N-P-K + WIN profiles.

Three sections:
- **HIGH/VERY-HIGH P → zero-P** (runoff prevention): 28-0-3 to 32-0-4, 29-0-3 to 38-0-4, 46-0-0, plus the slow-release zero-P grades (32-0-6 ~30%, 24-0-12/24-0-11 25-49%, 25-0-5/32-0-10/39-0-0 50-70%+, 9-0-9 organic ~85%+).
- **MEDIUM P → low-P** (4-1-2 family): 16-4-8 / 20-5-10 / 24-6-12; 3-1-2 family 12-4-8 / 15-5-10. Program shown as "by WIN" since these come in both quick- and slow-release versions.
- **LOW P or NEW lawn → starter/high-P**: 10-10-10 / 12-12-12 balanced; 18-24-12, 18-24-6, 12-25-6, 24-25-4 starters; 5-10-5. Also "by WIN."

Footnote rewritten: apply P only when the soil test calls for it; starter grades on High-P soil waste money and pollute; WIN is % of total N not bag weight; "by WIN" means read the specific bag. Sources: real Mid-Atlantic products (The Mill, Lesco/SiteOne, Pro Trust, etc. — brands stripped); VCE 430-011, Notes 17/18. Standalone `Fertilizer_Grades_Table.md` rebuilt to match the new P-organized structure. JS clean.

### README refreshed to v1.7 (as styled HTML with color + emoji)

The uploaded `README.md` was at v1.6 and predated this session's work, with **stale/incorrect content**:
- Centipede listed as "1.0 lb ceiling, flat 0.5 lb cap, derived from agronomic principle" → corrected to **1.0–2.0 lb ceiling, cited to Soil Test Note 18 / SPES-669** (matches the calculator's maxN:2.0 and this session's centipede correction).
- Program table didn't cite 430-011 Tables 2–4 → now does (and notes Notes 17/18 are condensed).
- Missing all 1.7 features.

New `README.html` (HTML chosen so color renders; user requested emoji + color):
- Green/gold themed, hero header, callout boxes (new/note/warn/crit), emoji throughout.
- "What's new in 1.7" section: clipping toggle, shade control, expanded fertilizer chooser, lime improvements (CCE validation, gypsum guard, pelletized timing), conformance audit.
- Added VCE 452-510 to the source table; added the new supporting docs (fertilizer survey/table, CCE survey, audit plan/findings).
- Corrected warm-season table; cited program structure to 430-011.

Note: README.html is the refreshed deliverable; the original README.md (v1.6) is left as-is unless the user wants it replaced/converted. Version bumped 1.6 → 1.7 to reflect the feature additions; the calculator's <title> still reads v1.6 — **a future edit should bump the in-app version string to match.**

### Open items

| Item | Status | Blocker |
| :-- | :-- | :-- |
| Bump in-app version string (title) 1.6 → 1.7 | Recommended | Trivial; not yet done |
| Add VCE 452-510 to the in-app About source list | Recommended | Not yet done (README updated; calculator not) |
| Shrub/tree + VCE garden/flower report validation | Unexercised | Awaiting example reports |

---

## Session Updates — June 10, 2026 (Fertilizer table expanded to full P range; README rebuilt)

### Fertilizer grades table — added P2 grades, then expanded across the full phosphorus range

Two-step expansion of the "Help me choose a fertilizer at the garden center" table (both lawn tabs):

1. **Added concrete Program 2 grades (15-49% WIN)** from a marketplace search, brand-free: 32-0-6 (~30% coated urea), 24-0-12 / 24-0-11 (coated urea, often +iron, 25-49%). Previously P2 was only a generic catch-all row.

2. **Expanded beyond zero-P** (user: "we don't need to be limited to 0 P; there are low/lower-P products too"). Restructured the entire table to be organized by **phosphorus need**, matching the soil test's P rating so a resident reads their P result and jumps to the matching group:
   - **HIGH/VERY-HIGH P → zero-P** grades (the existing maintenance grades across P1/P2/P3).
   - **MEDIUM P → low-P** grades: 4-1-2 ratio family (16-4-8, 20-5-10, 24-6-12) and 3-1-2 family (12-4-8, 15-5-10).
   - **LOW P or NEW lawn → starter/higher-P** grades: balanced 10-10-10/12-12-12 and real starter grades (18-24-12, 18-24-6, 12-25-6, 24-25-4).

   Low-P and starter grades show program as **"by WIN"** rather than fixed P1/P2/P3, because these grades exist in both quick- and slow-release versions (verified in market) — the bag's WIN determines the program. Footnote reinforces: apply P only when the soil test calls for it; starter grades on High-P soil waste money and pollute. **Zero brand names confirmed** (grep clean). JS validated.

### Standalone doc updated

`Fertilizer_Grades_Table.md` rebuilt to match the new P-organized structure (three sections by P rating).

### README rebuilt as styled HTML (README.html) with corrections

The uploaded `README.md` was at v1.6 and contained a **stale centipede figure** ("1.0 lbs ... flat 0.5 lb per-app cap") — the 0.5 was the error corrected earlier this session. Rebuilt as `README.html` (HTML so it can carry color + emoji per user request), bumped to **v1.7**, with:
- **Centipede corrected** to 1.0-2.0 lbs, flagged with a "corrected v1.7" tag and a note that it was previously listed as 0.5-1.0 in error.
- **New v1.7 sections:** clipping return + shade site-adjustments, the expanded garden-center fertilizer table, the CCE/gypsum guard + pelletized-lime timing, the flower-tab OM advisory.
- **Source list:** added VCE 452-510 (lime sources) and UT Extension (Program 3 corroboration); noted 430-011 as authoritative for the 3-program structure and the Notes as condensed.
- **Conformance principle** callout: trace figures to the primary publication, not abridged Notes (the Program 3 lesson).
- Design: VCE-green/earth palette, Fraunces/Newsreader/IBM Plex Mono, color-coded callout cards, emoji as functional signposts.

### Still open (unchanged)

| Item | Blocker |
| :-- | :-- |
| Shrub/tree tab (Phase 7) + canopy ×2 validation | No shrub/tree report supplied |
| VCE garden/flower reports | No VCE garden/flower report supplied |

### Documents produced/updated this session

| Document | Status |
| :-- | :-- |
| `index.html` | Fertilizer table reorganized by P need |
| `README.html` | NEW — styled, v1.7, centipede corrected |
| `Fertilizer_Grades_Table.md` | Rebuilt to P-organized structure |
| `CLAUDE.md` | This entry |

---

## Session Updates — June 13, 2026 (Grass Seed Selection Assistant — standalone build)

### Plan revised to v2, then built standalone

Following four user decisions, the grass-seed-assistant plan was rewritten to v2 (`Grass_Seed_Selection_Assistant_Plan.md`) and then built as a self-contained HTML tool: `grass_seed_assistant.html`.

**The four decisions:**
1. **Build standalone first, then port into the calculator as a tab.** Logic is self-contained (driven by site/use questions, not soil-test data), so prove the question flow + engine + UI in isolation, then wire in. Logic kept in separated constants (`SPECIES`, `QUESTIONS`, `recommend()`) for a clean later port.
2. **Lead with cultivar PROPERTIES + real store-label literacy, NOT SPES-617 cultivar names.** Residents can't buy SPES-617 varieties (Bye/Hype/Navigator III) at a big-box store. SPES-617 is now a collapsible backstop only. Consumer content = (A) the properties that make a grass fit a site, (B) how to read a real bag.
3. **Include warm-season** as a real path (climate-change framing).
4. **Default to Chesterfield (Southern Piedmont); others selectable.**

### What the assistant does

- **7 tappable questions** with progress bar, in the calculator's visual identity (VCE-green/earth palette, Fraunces/Newsreader/IBM Plex Mono) so the port is seamless. Region defaults to Southern Piedmont; winter-color question auto-skips in the Mountains (warm-season not adapted there).
- **Recommendation engine = SPES-748 logic.** Validated across scenarios: tall fescue is the statewide default; fine fescue for shade; TF+KBG for high-traffic showcase/full-sun; warm-season (zoysia/bermuda/centipede/St. Augustine) opens when winter dormancy is acceptable in an adapted region.
- **Boundary fix during testing:** Coastal Plain + shade + dormant-OK now routes to St. Augustine (the shade-tolerant warm-season grass adapted to far-SE VA); the same case in the Piedmont stays cool-season (fine fescue), and Coastal + shade + wants-green also stays fine fescue. Implemented via `wantsWarm = ... && (a.sun !== 'shade' || coastal)`.
- **Output (shopping card):** recommended species/mixture + VCE rationale, property profile, what-to-look-for-on-the-bag, seed-quantity calculator (rate × area), planting timing, honest expectations ("eight turfgrasses, not very well"; winter dormancy; can't-seed warnings), hand-off to the calculator's fertilization tab + starter-fertilizer note, and the SPES-617 backstop in a `<details>`.
- **Rules baked in:** cool-season = always a blend/mixture (never single cultivar); warm-season = monoculture and several can't be seeded (St. Augustine = sod/plugs). Renovation-diagnosis reminder for overseed (430-520).

### Store-label literacy (the heart of decision 2)

Bag checklist teaches generic, brand-free tag-reading. Built iteratively from extension sources (MSU Extension bulletin most authoritative):
- Read the **back analysis tag**, not the front (front = marketing, back = lab report).
- **Blue certification tag** — certifies varietal authenticity (NOT germination/purity quality — phrased honestly). *(added after user noted it was missing)*
- Named **cultivars**, not just species.
- **Germination ≥85%** with **test date within 12 months** (drops ~5%/yr). *(test date added)*
- **Low inert/weed/other-crop.**
- **Coated-seed trap:** coating adds bag weight but isn't seed (counts as inert); a "10 lb" coated bag has less actual seed — compare pure-live-seed weight for big jobs. *(added)*
- **Pure Live Seed = pure% × germination%.**
- **Avoid:** Kentucky 31 (coarse forage grass; VCE steers to turf-type tall fescue) and annual-ryegrass-heavy mixes (die in a year).

### UI fix (user feedback via screenshot)

The region step had a floating "Chesterfield County is here ↑" caption that was confusing (highlighted text + up-arrow pointing at a box already reading "Southern Piedmont"). Removed it; instead the default dropdown option now reads "Southern Piedmont — incl. Chesterfield, Richmond area" inline. Option `value` stays plain "Southern Piedmont" so the engine still matches. (`.region-default` CSS now unused but harmless.)

### Status & open questions

- Standalone is a working proof; user likes it as a start. Not yet ported to the calculator (that's the deferred step 1 follow-up).
- Open (from the plan): warm-season depth (full parallel vs. cool-season-forward); whether to add a Virginia county→region lookup; patch/repair as its own flow; whether to add a brief VCE establishment how-to (seedbed prep, watering-in, first mow).

### Documents this session

| Document | Status |
| :-- | :-- |
| `grass_seed_assistant.html` | NEW — standalone selection assistant |
| `Grass_Seed_Selection_Assistant_Plan.md` | Rewritten to v2 (4 decisions) |

---

## Session Updates — June 14, 2026 (Grass Seed Assistant — print, diagnostic, tag diagram, refinements)

Continued work on the standalone `grass_seed_assistant.html`. All JS validated clean after each edit; zero brand names throughout (verified).

### Print feature
Added a "🖨️ Print my shopping list" button on the result screen (`window.print()`). Print stylesheet strips the hero/progress/quiz/buttons/footer and prints only the recommendation card with a print-only title. **Print-spacing fix (user screenshot showed 4 mostly-empty pages):** the cause was `page-break-inside:avoid` on whole sections (`.resblock`) forcing them to jump pages and strand white space. Removed section-level break rules; kept `break-inside:avoid` only on small units (property cards, checklist items, notes, diagnostic answer). Tightened print margins/spacing. Also hid the diagnostic picker buttons + "see all" table in print (interactive clutter), keeping only the selected answer. Note: at port time this would reconcile with the calculator's existing `printPlan()` convention.

### Renovation diagnostic (interactive "why did the lawn fail")
Replaced the static overseed note with an interactive troubleshooter: 8 tappable symptoms (shade/traffic/drainage/thatch/soil-pH/drought/pest/weeds) → likely cause + VCE fix, plus a "see all causes & VCE fixes" expandable table. Sourced from VCE 430-520 (Fall Lawn Care diagnostic framework) and EMG Handbook Ch. 11. **Trigger:** shows for project = overseed AND patch (extended to patch per user; heading/intro reworded for the bare-spot case); hidden for new lawns.

### Weed-control fix — corrected against the PMG (user asked "what does the PMG say")
Original text ("glyphosate per label, before soil prep") was incomplete. EMG Handbook Ch. 11 (which defers herbicide specifics to the PMG) specifies: start a non-selective herbicide **30–45 days before renovation** so there's time to **re-treat regrowth**; a single pass rarely kills bermudagrass/nimblewill; consult the PMG for product/rate. **PMG number verified:** the home-turf guide is **456-018, "Pest Management Guide: Home Grounds & Animals"** (product ENTO-634P, revised annually) — confirmed correct vs. 456-017 (Hort/Forest) and 456-016 (Field Crops), and confirmed the PMG actually covers turf weed control. Citation uses the full distinguishing title. **"Follow the label" added** to both pesticide-relevant diagnostic paths (weeds + insect/disease) — important because the label is legally binding and carries the planting-restriction interval that governs how soon you can seed after spraying.

### Store-label literacy additions
- Blue certification tag (certifies varietal authenticity, NOT germination/purity — phrased honestly). *Added after user noted it was missing.*
- Tag-location correction (user: tags are often sewn into the top seam): now "small bags (≤15 lbs) printed on back; larger bags sewn into top seam; jugs on side panel."
- Test date within 12 months (germination drops ~5%/yr).
- **Sample seed-tag diagram** in a boxed dropdown ("👀 Show me what a seed tag looks like") — brand-free annotated HTML tag with green/red callouts showing each field; `no-print`. Summary styled as a clear boxed button (green, bordered, chevron) per user request.

### Pure Live Seed vs. coated seed (user raised a real assumption question)
User asked whether seeding rates assume 100% pure live seed. They don't — VCE bulk-weight rates already assume normal good-quality bagged seed (typical germination/purity baked in). So PLS is a bag-comparison/quality lens, not a routine weight correction. Resolution: **PLS became a checklist item** (quality/value comparison); **coated-seed note moved to "How much to buy"** (it genuinely distorts seed-per-pound) with a clarifying line that the rate assumes uncoated seed. Also **darkened `.src` notes** (`--slate-light` → `--slate`, larger) — user reported they were unreadably light.

### Region label
Default option now reads "Southern Piedmont — incl. Chesterfield, Greater Richmond area." Earlier this session the confusing floating "Chesterfield County is here ↑" caption was removed in favor of this inline label (option `value` stays plain "Southern Piedmont" so the engine matches).

### Status
Standalone is feature-complete enough for review; not yet ported into the calculator (the deferred step-1 follow-up). Open plan questions remain: warm-season depth, county→region lookup, and whether to add a VCE establishment how-to (seedbed prep, watering-in, first mow).

---

## Session Updates — June 15, 2026 (Flower tab: lawn-alternative path context + first flower soil-report validation + 3 coded mods)

### Lawn-alternative / native groundcover path (grass_seed_assistant.html)
Added a 4th Q1 option "🌼 Replacing lawn with a groundcover" that short-circuits to renderAlternative() (skips the grass questions). Content from VCE 426-609 + EMG Ch. 11 (VCE endorses groundcovers over turf where grass struggles) + VCE/MG conversion steps. **NonEdu rule applied to sourcing:** removed Virginia Native Plant Society (not approved under any of the 5 situations) and removed specific species (green-and-gold/wild ginger/foamflower — from an MG web page, not citable); kept only VCE-cited Pennsylvania sedge. Resources box rebuilt with rule-compliant, correctly-scoped sources: VCE 426-609 + Extension/MG Help Desk; Plant Virginia Natives/Plant RVA Natives (Situation 1, lists+locator only); USDA NRCS Plants Database (Situation 2, native range); Lady Bird Johnson Wildflower Center (Situation 5, VA-applicable lists). **VNPS:** user argued it should qualify (agency-endorsed); held out pending explicit Extension Office approval per the rule's gray-area default, with a ready-to-paste code comment so it's a one-line add once blessed. PMG/label distinction fixed in the conversion steps too (PMG selects product; label governs rate/timing).

### First flower soil-report validation (Anderson + Armstrong)
Two Waypoint flower reports assessed (first flower-specific validation; Phases 5–6 were veg-only before). Anderson = 3 samples incl. 29.4% OM; Armstrong = 1 sample with full S3M micronutrient panel + sulfur rec. Findings doc: `Conformance_Audit_Findings_Flower.md`.

**Agronomy Facts 8 cross-check:** confirmed both reports are internally consistent with Waypoint AF8 (K CEC-bands, Mg saturation→dolomitic, K/Mg<0.33, high-P→zero, low-S→sulfate forms). The only Waypoint-vs-VCE divergences (K maintenance at Optimum; S as a nutrient) are philosophy differences, not errors — calculator resolves by following VCE for rates.

### Three flower-tab mods CODED (all in calcFlower, index.html, JS validated, tested vs all 4 samples)

**Mod 1 — lime type (the real defect):** flower lime block now reads st-mg-rating/st-ca-rating (normalized via WAYPOINT_TO_VCE) and branches per VCE Note 19: low Mg + lime → **dolomitic**; adequate Mg + lime → calcitic OK; no lime + low Mg → **1 lb Epsom salts/100 sq ft**; no lime + low Ca → **10 lb gypsum/100 sq ft**.

**Mod 2 — extreme-OM tier:** added ≥20% branch above the existing ≥15% (bed needs no amendment; micronutrient lock-up; 0.4 lb N/1%OM estimate overstates at this level). Parity with veg tab.

**Mod 3 — secondary nutrients (follow VCE, not Waypoint):** when P or K tests **Low/Medium only**, show VCE Note 19 organic-amendment materials (bone meal/rock phosphate for P; granite dust/greensand for K + wood-ash caveat). Critically, **nothing shows at Optimum/High** — the key divergence from Waypoint, which recommended 4.0 lb K₂O at Optimum on Armstrong. Sulfur = optional advisory only (S<10 ppm), framed honestly (Waypoint suggests it; VCE treats S as a pH tool; sulfate sources per AF8; follow label) — no fabricated VCE rate. Deliberately did NOT add micronutrient rate logic.

**Test results vs the 4 real samples:** Anderson #2 (low Mg)→dolomitic ✓; Anderson #1 (adequate Mg)→calcitic ✓; Anderson #2 (Low K)→materials shown ✓; Armstrong (Optimum K)→materials hidden ✓; Armstrong (S 9 ppm)→advisory shown ✓; Anderson (no S)→hidden ✓; Anderson #3 (29.4% OM)→extreme tier ✓; Armstrong (11.9%)→high tier ✓.

### Earlier this session (grass assistant, already built): print feature + print-spacing fix; interactive renovation diagnostic (8 symptoms→cause+VCE fix, "see all causes" table, triggers on overseed AND patch); PMG-corrected weed guidance (30–45 day window, PMG 456-018 verified, PMG-selects/label-governs); store-label additions (blue tag, top-seam location, test date, coated-seed); sample seed-tag diagram in boxed dropdown; PLS→checklist item + coated-seed→"how much to buy" + darkened .src notes; region label "Southern Piedmont — incl. Chesterfield, Greater Richmond area."

### Documents this session
| Document | Status |
| :-- | :-- |
| `index.html` | 3 flower-tab mods coded |
| `grass_seed_assistant.html` | lawn-alternative path + all earlier refinements |
| `Conformance_Audit_Findings_Flower.md` | NEW — 2-report findings, AF8 cross-check, VCE-sourced mods |
| `Grass_Seed_Selection_Assistant_Plan.md` | v2 (earlier) |

### Still open
- Flower mods are coded but **findings doc not yet marked "implemented"** (optional housekeeping).
- VNPS pending Extension Office approval (comment in place).
- Grass assistant not yet ported into the calculator as a tab.
- Shrub/tree tab (Phase 7) + canopy ×2 still unvalidated (no shrub/tree report supplied).

---

## Session Updates — June 15, 2026 (cont.) (Sulfur/Sodium fields, area hints, print on all tabs)

### Sulfur & Sodium fields added (fixing the "no sulfur showing" bug)
User reported sulfur never appeared for Waypoint flowers. Root cause: **there was no `st-s` input field in the form at all** — Mod 3's sulfur code read a nonexistent element (always null → 0 → advisory never fired). Sodium had the same gap. Per user direction ("the Waypoint flower data entry needs to include all fields Waypoint includes, and they all need to be in the assessment and recommendations"):
- Added **Sulfur (S)** and **Sodium (Na)** ppm + rating inputs to the soil-test micronutrient grid. Compared against the full Armstrong S3M report, S and Na were the only two Waypoint-reported fields the form lacked; everything else was already present.
- Wired both into `interpretSoilTest()`'s nutrients array so they get full interpretation cards: **Sulfur** — low S advises sulfate-form sources (gypsum/ammonium sulfate/potassium sulfate per AF8) with honest VCE framing (S mainly a pH tool for home gardens, correction optional); **Sodium** — normal = no action, high = soil-structure/drainage risk + gypsum-leaching correction (AF8).
- Added `sVal`/`naVal` declarations and included them in the `hasAny` data check.
- Updated the "Flower Garden Sample" prefill to the **real Armstrong full-panel report** (pH 6.4, P 12/ME, K 112/OP, Ca 2165, Mg 139, **S 9/L**, B 0.7, Cu/Fe/Mn/Zn all SUFF, **Na 19**, OM 11.9, lime 0) so clicking the sample now demonstrates the sulfur advisory firing. JS validated; S<10 ppm correctly fires the advisory.

### Mod A — nominal sq ft hints (area entry)
Added an italic helper note under all six area-entry boxes so the report can fire when exact size is unknown:
- Lawn tabs (cool/warm/lime): "Enter 1000 to see results per 1,000 sq. ft., then scale to your lawn."
- Garden/flower/shrub: "Enter 100 to see results per 100 sq. ft., then scale to your bed."
Matches how VCE expresses the rates (per 1,000 for lawns, per 100 for gardens) and teaches the unit basis.

### Mod B — Print on every tab
Print infrastructure already existed (`printPlan(prefix)` toggles a `printing-{tab}` body class; per-tab print CSS). Buttons existed on soil-test, cool, warm, lime. **Added Print Plan buttons to garden, flower, and shrub** (same "🖨 Print Plan" pattern, guarded by `if (html)` so they only show with results) and added the missing print-CSS lines so `#flr-results` and `#shrub-results` render when printing those tabs. All 8 tabs now printable.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | S/Na fields + interpretation; area hints; print buttons on all tabs |
| `CLAUDE.md` | this entry |

---

## Session Updates — June 15, 2026 (cont.) (Two bug fixes: carry-over routing + "Sufficient" rating)

### Bug 1 — Carry-over button routed flowers to Vegetable Garden
User screenshot: garden type "Annual Flower Garden" selected, but the post-carryover success box button said "Vegetable Garden Calculator." Traced it: the routing data was correct (`flowerTypes=['annual','perennial','rose','bulb']`, `crop` reads `st-garden-type`), but the old destBtns used a ternary that defaulted **anything** not explicitly shrub-or-flower to the vegetable button — including the case where the garden-type value read back empty at button-build time (which is what occurred). **Fix (in carryOverToCalculators, index.html):** rewrote the destBtns block to (a) re-read the garden type **live** at button-build time, (b) branch **explicitly** — flower types→Flower, vegetable/mixed→Vegetable, shrub types→Shrub, and (c) if the type is genuinely unspecified, offer **both** Vegetable and Flower buttons rather than silently defaulting to vegetable. Tested: annual/perennial→Flower ✓, vegetable→Vegetable ✓, shrub→Shrub ✓, empty→both ✓.

### Bug 2 — "Sufficient" rating doesn't exist on Waypoint
User: "Waypoint doesn't offer a Sufficient rating." Confirmed via Agronomy Facts 8 — Waypoint's scale is very low / low / medium / optimum / very high (no "Sufficient"). **Fix:** relabeled every micronutrient (and the new S/Na) rating dropdown option from "Sufficient / Optimum" → **"Optimum"**; fixed the two internal label maps (LABELS, ratLabels) and the "Target: Sufficient at correct soil pH" interpretation text → "Optimum." Kept the internal value code `SUFF` unchanged so interpretation logic still keys correctly — only user-facing labels changed. Zero "Sufficient" strings remain.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | carry-over routing hardened; "Sufficient"→"Optimum" labels |
| `CLAUDE.md` | this entry |

---

## Session Updates — June 15, 2026 (cont.) (VNPS approved under the NonEdu rule — EMG Handbook Ch. 19)

### Decision reversed with evidence: VNPS now qualifies (Situation 1)
Earlier this session VNPS was held OUT of the lawn-alternative resources box pending Extension Office approval, with the note that "agency partnership" does not satisfy a gate. User pushed on the agency-partnership angle; web search + the user-uploaded **VCE Extension Master Gardener Handbook, Chapter 19 (Virginia Native Plants)** resolved it decisively — but on a different (stronger) basis than agency partnership:
- Ch. 19's **Additional Resources lists "Virginia Native Plant Society: https://vnps.org/"** outright → the exact Situation 1 trigger ("a specific VCE publication has directed clients to them").
- Ch. 19's "Warning Internet Searchers" box places VNPS inside its trusted set **alongside .edu/.gov** sources.
- Ch. 19 documents a **direct Chesterfield link**: Ashley Moulton "formerly coordinated the Chesterfield Extension Master Gardener unit and serves on the boards of the Virginia Native Plant Society."
- **Scope limit preserved:** Ch. 19 uses VNPS for native-plant lists/education and its cultivar/nativar statement, but points to the Digital Atlas of the Virginia Flora / USDA for range/nativity. So VNPS is approved for native-plant lists + education, NOT as a range authority.
- The "agency partnership" argument was explicitly NOT the basis (it doesn't satisfy a gate); the EMG Handbook listing is.

### Changes made
1. **grass_seed_assistant.html** — added VNPS to the lawn-alternative "approved native-plant resources" box ("a VCE-recognized native-plant resource (listed in the VCE EMG Handbook) for native plant lists and education"); rewrote the code comment from "NOT included pending approval" to record the Situation 1 basis (Ch. 19 listing + Chesterfield personnel link + the not-agency-partnership note). JS validated; zero brand names.
2. **NonEdu_Full_Rule.md** (NEW writable copy in outputs; original upload is read-only) — added a VNPS entry under Situation 1, formatted to match the Plant Virginia Natives entry, citing the EMG Handbook Ch. 19 basis and the range/nativity scope limit. Confirmed no conflict with the "Never Acceptable" list (which only excludes nonprofits that don't meet one of the five situations — VNPS now does).

### Files
| Document | Status |
| :-- | :-- |
| `grass_seed_assistant.html` | VNPS added to resources box (Situation 1) |
| `NonEdu_Full_Rule.md` | NEW writable copy — VNPS added under Situation 1 |
| `CLAUDE.md` | this entry |

### Note
The original NonEdu rule remains at /mnt/user-data/uploads/NonEdu_Full_Rule_v3.md (read-only). The updated, authoritative copy is now /mnt/user-data/outputs/NonEdu_Full_Rule.md.

---

## Session Updates — June 15, 2026 (cont.) (NonEdu rule → Word document + markdown sync)

### Word version built
Formatted the NonEdu rule as a Word document: **NonEdu_Source_Guidelines.docx** (in outputs). Built with docx-js (read docx SKILL.md first), VCE palette (deep green 2F5233 / green 3E6B43 / gold 8A6418), Calibri, styled H1/H2/H3, centered title block, running header, footer with "Page X of Y", bulleted lists via LevelFormat.BULLET, ExternalHyperlinks throughout, a shaded Xerces "critical restriction" callout box, and a 5-row Quick Reference table with a green header row. 9 pages; validated (validate.py PASSED) and visually checked via PDF/JPEG render. Build script: /home/claude/build_rule.js.

### Four consistency fixes applied to BOTH the docx and the .md (now in sync)
While converting, found and fixed source-doc inconsistencies; then synced the markdown to match:
1. **Quick Reference Summary, Situation 1 line** — previously omitted VNPS; now lists it ("native plant lists, selection, and education only — not range/nativity"), matching the body entry.
2. **"Prince Georges County" → "Prince George County"** (line ~111).
3. **"iNaturist, Bug Guide" → "iNaturalist, BugGuide"** (never-acceptable list).
4. **"Pathway 5" → "Situation 5"** (3 occurrences) — standardized terminology to match the section headers.

### Authoritative copies (both in outputs, now consistent)
| Document | Status |
| :-- | :-- |
| `NonEdu_Full_Rule.md` | updated markdown — VNPS (Situation 1) + 4 consistency fixes |
| `NonEdu_Source_Guidelines.docx` | NEW formatted Word version — same content, VCE-styled |
| `build_rule.js` | docx-js build script (/home/claude) |

Note: the original upload /mnt/user-data/uploads/NonEdu_Full_Rule_v3.md remains read-only and is now stale; the outputs .md + .docx are the source of truth.

---

## Session Updates — July 6, 2026 (ADA / WCAG 2.1 AA compliance — critical tier)

### Context
Virginia Tech Policy 7215 requires WCAG 2.1 AA conformance for all digital content (effective April 24, 2026). Applied all 5 critical-tier fixes to `index.html`, plus VCE style guide fixes from the prior session.

### Changes made to index.html

**All VCE style guide fixes from June 19, 2026 session reapplied** (phosphorus, Dr. honorifics, numeral rules, italic→bold, nondiscrimination statement, commercial products disclaimer, AI disclosure).

**ADA Fix 1.1 — Form label association (WCAG 1.3.1, 4.1.2)**
- Added `for=` attribute to every `<label>` in the file (~65 static labels + 7 JS-generated slot labels)
- Covers all tabs: Soil Test, Cool-Season, Warm-Season, Lime, Vegetable Garden, Flower Garden, Shrubs & Trees
- Also cleaned up inline `style=` on sub-label `<span>` elements, replacing with `.st-label-sub` class

**ADA Fix 1.2 — Tab widget ARIA pattern (WCAG 4.1.2)**
- Added `role="tablist"` to `<nav>`, `role="tab"` + `aria-selected` + `aria-controls` + `tabindex` to each button
- Added `role="tabpanel"` + `aria-labelledby` to each panel div
- Refactored tab JS into `activateTab(tab)` function that manages ARIA state, tabindex, and page title
- Added arrow-key (Left/Right/Home/End) keyboard navigation between tabs
- Updated `switchToTab()` to delegate to `activateTab()` for ARIA consistency
- Page `<title>` now updates dynamically to reflect the active tab

**ADA Fix 1.3 — Live regions for dynamic results (WCAG 4.1.3)**
- Added `aria-live="polite" aria-atomic="false"` to all 7 result panels
- Added `debounce()` utility (300ms) wrapping `interpretSoilTest()` on `oninput` to prevent screen reader chatter
- Select `onchange` handlers remain immediate (no debounce needed)

**ADA Fix 1.4 — Heading hierarchy (WCAG 1.3.1)**
- Converted 23 `<div class="card-header">` elements to `<h3 class="card-header">`
- 1 card-header (soil test, with inline buttons) uses `role="heading" aria-level="3"` fallback
- Updated CSS selector to include `h3.card-header`
- Added `aria-hidden="true"` to 27 decorative emoji `<span class="icon">` elements in headings and buttons

**ADA Fix 1.5 — Color-only status communication (WCAG 1.4.1)**
- Updated `abox()` helper to add `role="note"` and a `.sr-only` status prefix ("Action needed:", "Monitor:", "Good:")
- Added `.sr-only` CSS utility class (visually hidden, screen-reader announced)
- Added `aria-hidden="true"` to decorative header badge and prefill button emoji

**Additional improvements included in this pass:**
- Skip navigation link (`<a class="skip-link">`) as first element in `<body>`, visible on focus
- `id="main-content"` on `<main>` element for skip link target
- Contrast fix: hint/meta text color overridden from `#8a9490` (~2.8:1) to `#5f6b6b` (passes 4.5:1 on white)

### Items deferred (Serious + Moderate tiers — not in this pass)
- `<fieldset>`/`<legend>` grouping for related input pairs (P value + P rating, etc.)
- External link `target="_blank"` warnings
- `aria-expanded` on measure/area toggles
- Minimum font-size audit (0.68rem → 0.75rem on range/summary labels)
- `aria-invalid` + `aria-describedby` for validation errors

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | VCE style fixes reapplied + 5 critical ADA fixes |
| `CLAUDE.md` | this entry |

---

## Session Updates — July 6, 2026 (cont.) (ADA Serious + Moderate tier)

### Changes made to index.html

**Fix 2.2 — Fieldset/legend grouping (WCAG 1.3.1)**
- Wrapped P value+rating, K value+rating, Ca value+rating, Mg value+rating pairs in `<fieldset class="st-fieldset">` with visually hidden `<legend>` (Phosphorus, Potassium, Calcium, Magnesium)
- Wrapped full micronutrient block in `<fieldset class="st-fieldset-block">` with visible legend replacing the old section-label div
- Added CSS: `display: contents` on fieldset preserves existing CSS Grid layout; legend uses sr-only pattern for nutrient pairs

**Fix 2.3 — External link warnings (WCAG 2.4.4, 3.2.2)**
- Added `<span class="sr-only"> (opens in new tab)</span>` before `</a>` on all 39 `target="_blank"` links
- Added `rel="noopener"` to all 39 external links (security best practice)

**Fix 3.2 — aria-expanded on toggle buttons (WCAG 4.1.2)**
- Added `aria-expanded="false"` and `aria-controls` to 8 static toggle buttons (measure, garden subsections, about source panels)
- Added same attributes to 1 JS-generated fert-chooser toggle button
- Updated all 9 toggle functions to sync `aria-expanded` with open/closed state via `setAttribute`

**Fix 3.3 — Minimum font-size floor (WCAG 1.4.4)**
- Raised all font-size values below 0.75rem (12px) to 0.75rem
- Affected: `.st-range-label` (was 0.68rem), `.st-summary-label` (was 0.7rem), `.st-summary-rating` (was 0.72rem), `.prog-badge` (was 0.72rem), various inline styles on table cells and labels
- Zero sub-0.75rem font sizes remain

**Fix 3.4 — Validation errors (WCAG 3.3.1)**
- Added `aria-describedby` linking cool/warm N-rate inputs to their validation output divs
- Added `role="alert" aria-live="assertive"` on validation divs so screen readers announce ceiling violations
- N-rate validation JS now sets `aria-invalid="true"` when exceeding the annual ceiling and removes it when within range

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | 5 serious+moderate ADA fixes applied (2.2, 2.3, 3.2, 3.3, 3.4) |
| `CLAUDE.md` | this entry |

---

## Session Updates — July 6, 2026 (cont.) (axe audit + fixes)

### Context
Ran axe-core (WCAG 2.0 AA + 2.1 AA + best-practice rules) via Puppeteer against the rendered HTML file.

### Initial audit result
- 42 rules passing
- 2 violations (5 elements with contrast failure, 1 heading-order issue)
- 1 incomplete (manual review needed for toggle-arrow contrast)

### Fixes applied

**Color contrast (WCAG 1.4.3)**
- `.st-prefill-btn` background: `var(--gold)` (#b8892a) → `#7a6518` (white text now passes 4.5:1)
- Flower Garden sample button inline background: `var(--gold)` → `#7a6518`
- Vegetable Garden sample button inline background: `#5a7a2e` → `#3d5a1a`
- `#st-area-hint` text color: `var(--gold)` → `#7a6518` (on white, passes 4.5:1)
- `#st-salts-hint` text color: `var(--slate-light)` → `#5f6b6b` (matches earlier override)
- `.st-placeholder` text color: added CSS rule with `#5f6b6b`

**Heading order (best-practice)**
- Soil test card-header `div[role="heading"]`: changed `aria-level="3"` → `aria-level="2"`
- Added visually hidden `<h2 class="sr-only">` to 7 other tab panels (cool, warm, lime, garden, flower, shrub, about) so heading hierarchy flows h1 → h2 → h3 in every tab

### Final audit result
- **0 violations**
- 42 rules passing
- 1 incomplete: toggle-arrow contrast (manual review — inherits from parent button, visually passes)

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | axe-core 0 violations achieved |
| `CLAUDE.md` | this entry |

---

## Session Updates — July 6, 2026 (cont.) (Lighthouse confirmation)

User ran Lighthouse in Chrome DevTools against the hosted site (lawncarecalc.github.io). Results:
- **Accessibility: 100**
- Best Practices: 100
- Performance: 91
- SEO: 90

README.md updated to include Lighthouse 100 alongside the axe-core 0-violation result.

### Files
| Document | Status |
| :-- | :-- |
| `README.md` | Lighthouse score added to Accessibility section |
| `CLAUDE.md` | this entry |

---

## Session Updates — July 6, 2026 (cont.) (IBM Equal Access violations fixed)

### Context
User ran IBM Equal Access Accessibility Checker (v4.0.24) against the hosted site on the Cool-Season Lawns tab. Found 11 violations. All 11 fixed.

### Fixes

**3 unlabeled selects (WCAG 4.1.2)**
- `cool-species`, `cool-p-rating`, `cool-k-rating`: converted `<span class="field-question">` to `<label for="..." class="field-question">` in the field-label divs
- Same fix applied proactively to warm-season equivalents (`warm-species`, `warm-p-rating`, `warm-k-rating`) and lawn-size inputs on both tabs

**4 contrast failures (WCAG 1.4.3)**
- Changed `--slate-light` CSS variable itself from `#8a9490` to `#5f6b6b` (passes 4.5:1 on white)
- This fixes all ~20 inline `color:var(--slate-light)` references across all tabs in one shot
- Removed the now-redundant per-selector override from the earlier pass

**3 ungrouped radio buttons (WCAG 1.3.1)**
- Wrapped cool-shade and warm-shade radio groups in `<fieldset class="st-fieldset-block">` with `<legend>` containing the "Is this area shaded?" prompt
- Legend styled with `float:left;width:100%` to preserve layout; radio container uses `clear:both`

**1 content outside landmark (WCAG 1.3.1)**
- Moved skip link from before `<header>` to inside it, so all content is within a landmark element

### Verification
- axe-core: still 0 violations, 42 rules passing
- All 11 IBM violations addressed

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | IBM Equal Access 11 violations fixed |
| `CLAUDE.md` | this entry |

---

## Session Updates — July 6, 2026 (cont.) (IBM Equal Access clean scan confirmed)

User re-ran IBM Equal Access Accessibility Checker (v4.0.24) against the updated hosted site on the Soil Test Report tab (full-page scan).

### Result
- **Violations: 0** (down from 11 in previous scan)
- Needs review: 72 (all manual confirmations — focus-visible, onchange behavior, heading suggestions)
- Recommendations: 8 (additional fieldset grouping, addEventListener preference)
- Elements without violations: **100%**

### Cumulative testing results
| Tool | Result |
| :-- | :-- |
| axe-core 4.x (Puppeteer) | 0 violations, 42 rules passing |
| Lighthouse | Accessibility **100** |
| IBM Equal Access Checker | 0 violations, 100% elements clean |

### Files
| Document | Status |
| :-- | :-- |
| `CLAUDE.md` | this entry |

---

## Session Updates — July 6, 2026 (cont.) (tab-switching bug fix)

### Bug
Clicking Lime, Vegetable Garden, Flower Garden, Shrubs & Trees, or About tabs did not show their panels.

### Cause
Unbalanced `<fieldset>`/`</fieldset>` tags. The warm-season shade radio group had a `</fieldset>` closing tag (line 1367) but its matching opening `<div>` was never converted to `<fieldset>`. The browser's HTML parser treated the orphan `</fieldset>` as closing a parent element, which swallowed all subsequent tab panels from the DOM tree.

### Fix
Converted the warm-season shade block's opening `<div>` to `<fieldset class="st-fieldset-block">` with a `<legend>`, matching the pattern already applied to the cool-season shade block. Fieldset count is now 7 open / 7 close (balanced).

### Verification
- Puppeteer tab test: all 8 tabs activate correctly
- axe-core: still 0 violations

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | warm-season fieldset mismatch fixed |
| `CLAUDE.md` | this entry |

---

## Session Updates — July 7, 2026 (Claude-in-Chrome accessibility audit findings fixed)

### Context
User had Claude in Chrome work through the manual Accessibility Testing Checklist. It found 5 code issues (plus 1 already-known toggle-arrow contrast item). All 5 fixed.

### Fixes

**Fix 1 — 13 unlabeled selects (WCAG 4.1.2, Critical)**
- Converted `<span class="field-question">` to `<label for="..." class="field-question">` on all unlabeled selects across Lime (`lime-type`), Vegetable Garden (`gdn-type`, `gdn-p-rating`, `gdn-k-rating`, `gdn-bed-status`), Flower Garden (`flr-type`, `flr-p-rating`, `flr-k-rating`, `flr-bed-status`), and Shrubs & Trees (`shrub-plant-type`, `shrub-turf`, `shrub-p-rating`, `shrub-k-rating`) tabs
- Also labeled 4 Lime tab number inputs (`lime-rec`, `lime-cce`, `lime-bag`, `lime-area`)

**Fix 2 — Heading hierarchy h1→h3 skip (WCAG 1.3.1, Moderate)**
- Added visually hidden `<h2 class="sr-only">` to all 8 tab panels (Soil Test Report, Cool-Season Lawns, Warm-Season Lawns, Lime Calculator, Vegetable Garden, Flower Garden, Shrubs and Trees, About and Instructions)
- These were present in an earlier build but were lost when starting from a fresh index.html copy during the IBM Equal Access fix pass

**Fix 3 — Skip link unreachable on first Tab (WCAG 2.4.1, Moderate)**
- Moved skip link from inside `<header>` back to before it — first focusable element on the page
- The IBM Equal Access scan had flagged it as "content outside landmark" so we moved it inside `<header>`, but that caused it to be bypassed by the browser's initial Tab focus order. Reverting fixes the skip-link reachability while accepting the IBM advisory

**Fix 4 — 🧪 emoji missing aria-hidden (WCAG 1.1.1, Minor)**
- Added `aria-hidden="true"` to the beaker emoji `<span class="icon">` in the soil test card header — the one emoji that was missed in the earlier bulk pass

**Fix 5 — Reflow at ~320px width (WCAG 1.4.10, Minor)**
- Added `@media (max-width: 400px)` breakpoint that collapses `.calc-layout` to `display: block`, `.st-field-grid` to single column, and `.npk-row` to vertical stack

### Verification
- axe-core: 0 violations, 42 rules passing
- Puppeteer tab test: all 8 tabs activate correctly
- Fieldsets: 7/7 balanced

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | 5 Claude-in-Chrome audit findings fixed |
| `CLAUDE.md` | this entry |

---

## Session Updates — July 7, 2026 (cont.) (WAVE report fixes)

### Context
User ran WAVE (WebAIM) accessibility scanner. Found 9 input errors, 18 select alerts (13 already fixed but not deployed; 5 new), 1 orphaned label, 2 table caption issues, plus advisory items (PDF links, JS jump menus).

### Fixes

**9 missing input labels (WAVE errors)**
- `lime-lawn-size`, `lime-rec`, `lime-cce`, `lime-bag-size`: lime tab field-question spans converted to `<label for="...">`
- `gdn-n-rec`, `gdn-lime-rec`: garden tab N and lime recommendation inputs labeled
- `flr-n-rec`, `flr-lime-rec`: flower tab N and lime recommendation inputs labeled
- `shrub-n-rec`: shrub tab N recommendation input labeled

**5 new select labels (WAVE alerts)**
- `gdn-crop-type`: field-question span converted to `<label for="...">`
- `gdn-product-select`, `flr-product-select`, `shrub-product-select`: no visible adjacent text, so `aria-label="Select a fertilizer product"` added
- 13 previously fixed selects confirmed present (lime-type, gdn-type, gdn-p/k-rating, gdn-bed-status, flr-type, flr-p/k-rating, flr-bed-status, shrub-plant-type, shrub-turf, shrub-p/k-rating)

**1 orphaned label**
- Label "Showing guidance for — change to browse other crops:" was missing `for="gdn-guidance-crop"` — added

**2 table caption issues**
- Two `<td colspan>` cells styled as section headers ("Major nutrients" and "Synthetic — from VCE garden report (exact)") converted to `<th scope="colgroup">` for proper semantic markup

### Not fixed (advisory, not violations)
- 5 PDF links: already have descriptive link text; PDFs themselves are external VCE publications
- 40 JS jump menus: onchange behavior is by design for a calculator; no context change occurs (only in-page results update)

### Verification
- axe-core: 0 violations
- All 8 tabs activate correctly

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | WAVE fixes: 9 input labels, 5 select labels, 1 orphaned label, 2 table captions |
| `CLAUDE.md` | this entry |

---

## Session Updates — July 7, 2026 (cont.) (WAVE label bug fix + PDF links + final score)

### Critical bug fix — span→label
The previous label fixes used `<span class="field-question" for="...">` instead of `<label class="field-question" for="...">`. The `for=` attribute is ignored on `<span>` elements — only `<label>` elements create programmatic associations. Fixed 23 instances across all tabs (19 simple + 4 with id attributes). Confirmed via browser console that all 9 WAVE-flagged inputs now resolve `querySelector('label[for="..."]')`.

### PDF link indicators
Added visible "(PDF)" text to all 5 PDF links in the About tab so users know the format before clicking. Screen readers now announce: "[title] (PDF) (opens in new tab)".

### WAVE score: 9.4/10
- 0 Errors, 0 Contrast Errors
- 45 Alerts remaining: 40 JS jump menu (by design — instant recalculation is the intended UX, aria-live regions handle screen reader announcements) + 5 PDF link alerts (now addressed with visible format indicator)
- Decision: JS jump menu alerts left as-is — adding Calculate buttons would degrade the calculator UX for all users to address an advisory, not a violation

### Cumulative testing results
| Tool | Result |
| :-- | :-- |
| axe-core 4.x | 0 violations, 42 rules passing |
| Lighthouse | Accessibility **100** |
| IBM Equal Access | 0 violations |
| WAVE | 0 errors, 0 contrast errors, 9.4/10 |

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | 23 span→label fix + 5 PDF indicators |
| `CLAUDE.md` | this entry |

---

## Session Updates — July 21, 2026 (Vegetable Garden Restructure, Part 1 — architecture groundwork + N-rule reversal)

### Context
Implementing a prepared "Vegetable Garden Restructure — Implementation Spec." This is the first of
what became a multi-session restructure (continued July 26–27).

### Soil Test tab — two-block input architecture (Option 4)
The soil test input fields are duplicated into two static, correctly-ordered blocks:
- `#st-block-vce` — fields ordered to match a VCE report (nutrients first, chemistry second)
- `#st-block-waypoint` — fields ordered to match a Waypoint report (chemistry first, nutrients interleaved)

`onReportTypeChange()` toggles `display` between them — no CSS `order`, no live DOM reorder, so tab
order and screen-reader order always match what's visually shown (WCAG 2.4.3). Each visible field
carries `data-canon` pointing at its hidden canonical counterpart in `#st-canonical-fields`.
`stSync(el)` syncs on every input/change; `stPushBlockToCanonical(blockId)` bulk-syncs after a
report-type switch or sample load. **Rule: all downstream logic reads ONLY canonical fields.**

### Nitrogen handling — rule reversed, with evidence
**Reversed:** "calculator requires a soil test" (N field removed for users without one) →
**Nitrogen is NOT a lab-measured parameter.** Nitrate-N is highly mobile and leaches within a day
or two of rain, so a snapshot measurement wouldn't stay accurate — neither VCE nor Waypoint
lab-measures it; the report's "N" figure is a generic crop-based recommendation, not a test result.

Consequence: N input is optional for vegetable/flower gardens. Blank → falls back to
`CROP_FEEDING_LEVELS[cropKey].nPer100`. Demoted from a numbered step to a collapsed override in
step 3, labeled "Have a different N recommendation? (rare — e.g. a private agronomist consult)."

Validated against: VCE Soil Test Note 19 (452-719), VCE 426-323, multiple Waypoint reports (N
figure identical regardless of soil chemistry), and Jim Myracle's VCE Lab 23-15911 vegetable
garden report.

### NUTRIENT_AMENDMENTS — individual nutrient corrections added
For vegetable/mixed gardens, a new Nutrient Status panel suggests single-nutrient corrections when
one nutrient is low but others adequate, so the user isn't forced to over-apply a blended
fertilizer. Three calc modes: `'flat'` (VCE Note 19 rates), `'target'` (synthetic products sized
from Waypoint's numeric target via guaranteed-analysis %), `'none'` (VCE names the product, no
rate). Lime-conditional logic on Ca/Mg entries (gypsum/Epsom salts) checks whether lime is already
being recommended first. S/Zn/Mn/Cu: "seldom a problem in Virginia soils" per VCE 426-323, no
home-garden rate published — stated honestly via `NUTRIENT_NO_RATE_NOTE` rather than fabricating one.

### Waypoint rating scale confirmed
5-level scale, no plus/minus: Very Low, Low, Medium, Optimum, Very High. No rating text printed on
the report itself — only a colored bar on a gradient. Dropdown values: VL, LO, ME, OP, VH2 (VH2 to
distinguish from VCE's VH). Confirmed against 14+ real uploaded Waypoint reports.

### New sources added
VCE 426-323 (SPES-803P), VCE 452-719 (SPES-687P) — both already in the Source Documents table
above. Garden Fertilizer Calculator (bulk density database) — **later superseded**; see July 26–27
sourcing audit, which found this and similar unnamed bulk-density charts don't meet the sourcing
standard and replaced them with Ohio State Ohioline / NMSU citations.

### Validated reports added
- Jim Myracle, Waypoint Report No. 26-188-0532, Sample "2-Vegetable Beds" (07/09/2026) — P Very
  High, K Low. The adequate-P/low-K case the Nutrient Status panel was built for.
- Jim Myracle, VCE Lab ID 23-15911, Sample "VEGGD" (2023) — all nutrients VH/SUFF, N-only
  recommended. Contains VCE's own cup conversions for 4 N products.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Two-block soil test architecture, N-rule reversal, NUTRIENT_AMENDMENTS added |
| `CLAUDE.md` | this entry |

---

## Session Updates — July 26–27, 2026 (Vegetable Garden Restructure, Part 2 — streamlining, app rename, report-type consolidation, tab gating, bulk-density sourcing audit, accessibility)

### Context
Continuation of the vegetable garden restructure, expanding into app-wide navigation and identity
changes. Sequenced: user requested vegetable garden first, then flower garden, then shrubs & trees
— flower and shrub restructuring have NOT started; only vegetable garden's calculator logic itself
was rebuilt. Navigation, naming, sourcing, and accessibility changes apply app-wide.

### Vegetable Garden — steps consolidated 7→4→3
Removed the blended N-P-K fertilizer picker (step 6), the P/K rating selects (auto-fill from Soil
Test tab now), the "Can't find the recommended grade?" substitution table, and the separate 9-field
Waypoint target grid (targets now inline per-nutrient). Merged what had become two near-duplicate
crop-guidance boxes into one (`renderCropInfoPanel()`), which also now **shows the actual
research-based N number** instead of just referencing it. Merged the two output cards ("Nitrogen
Application Plan" + "Nutrient Status") into one "Nutrient Application Plan" card, fixing a bug
where the Print Plan button was sandwiched between the two sections instead of after both. Garden
type (`gdn-type`, vegetable/mixed) removed — folded under vegetable, logic was identical for both.

**Dead code removed:** `CROP_DATA` + `CROP_GUIDANCE_MAP` (only 2 of CROP_DATA's 5 fields were ever
rendered; `SIDEDRESS_GUIDE` already covered every crop directly, and more completely — it has
potato/okra/sweet potato/asparagus entries CROP_DATA never had).

### Bulk density sourcing audit (significant)
The prior `BULK_DENSITIES` table cited "FAO Database," "Industry sources," and "Scientific
literature" — none of which are real, checkable citations, and none satisfy the non-.edu sourcing
rule. Corrected via live web research:
- **Now sourced:** Triple Superphosphate & Ammonium Nitrate ← Ohio State Ohioline FABE-550; Muriate
  of Potash, Elemental Sulfur, Langbeinite ← NMSU Cooperative Extension Guide H-119 (direct oz/cup
  figures)
- **No source found → weight-only:** Blood Meal, Feather Meal, Bone Meal, Rock Phosphate, Borax.
  One specific correction: bone meal's density had been mislabeled "Rutgers FS626" — FS626 only
  ever gave NPK ratios, never a bulk density.
- **Specific gravity removed as a user input entirely.** Initially added as a toggle alongside bulk
  density, then removed once evidence showed SDS Section 9 specific gravity reflects the pure
  crystal/absolute compound density, not the packaged granular form. Confirmed example: Southern
  Ag Sulfate of Potash SDS lists SG 2.66 (≈166 lbs/ft³ absolute crystal density) vs. the actual
  granular product's 75–81 lbs/ft³ loose bulk density — using the SDS value would understate
  volume by roughly half. Bulk density (lbs/ft³ or kg/m³) from the product label/technical data
  sheet is the only accepted density input now.

### Manganese guidance added (NC State Extension)
Mn moved from `NUTRIENT_NO_RATE_NOTE` (previously "no rate published") to real amendments, sourced
to NC State Extension (Torres Quezada, 2024): Manganese Sulfate flat rate (~0.05 lbs/100 sq ft,
scaled from 20–25 lbs/acre) + sized-to-target variant + Chelated Manganese for alkaline soils.
Similar target-calc amendments added for S (Elemental Sulfur, Gypsum), B (granular Borax), and Mg
(Epsom Salts sized-to-target).

### App renamed
"Lawn & Garden Calculator" / "VCE Lawn & Garden Care Calculator" → **"Soil Report Assistant"**,
tagline "No more guessing what to feed your lawn or garden." Updated in `<title>`, header `<h1>`,
header subtitle, dynamic per-tab `document.title`, and About tab `<h2>` (with a one-line VCE /
Chesterfield County attribution retained beneath it).

### Report-type question consolidated — one question, not two (SUPERSEDES the July 21 two-block
### section's report-type handling; the VCE/Waypoint block-switching mechanism is unchanged, only
### how "purpose" is captured changed)
Previously: `st-report-type` (lab, 4 values incl. `vce-garden`/`waypoint-garden`) + a separate
`st-garden-type` field asking vegetable/annual/perennial/rose/bulb/shrub-and-tree-subtypes. **Now:**
one `st-report-type` dropdown, 8 values (2 labs × 4 purposes: lawn/vegetable/flower/shrub),
grouped by lab. `st-garden-type` removed entirely. New helpers `soilTestPurpose()` and (rewritten)
`soilTestTargetTab()` derive everything downstream from the single value.

Went through two iterations before landing here: first tried grouping the old 12-value
`st-garden-type` list into three visually distinct optgroups (Vegetable/Flower/Shrub headers) —
correctly identified as still asking "what kind of test is this" in two places (report type, then
sub-type), since the sub-type chosen here also had to be re-asked on the destination tab (Flower
Garden's own annual/perennial/rose/bulb selector, Shrubs & Trees' own plant-type selector). Second
iteration collapsed `st-garden-type` to exactly 3 generic values (vegetable/flower/shrub) — better,
but still two separate dropdowns/questions. Final iteration merged lab + purpose into the single
8-value `st-report-type` dropdown, eliminating the second question entirely. **Mixed bed folded
into "Vegetable Garden"** at this same step (no separate value).

Sub-type detail (which flower type, which shrub/tree species) is asked exactly once now — on the
destination tab, not duplicated on the Soil Test tab. `carryOverToCalculators()` simplified
accordingly (no longer tries to pre-fill `flr-type`/`shrub-plant-type` from a Soil Test tab value
that no longer carries that detail).

### Tab navigation — hidden until unlocked (SUPERSEDES a same-session earlier "dimmed with lock
### icon" approach)
Calculator tabs are `display:none` until the Soil Test tab resolves a target
(`soilTestTargetTab()`) — not dimmed-but-visible as first implemented. Only ONE calculator tab is
ever visible at a time (Lime is the exception — purpose-agnostic, appears for any report with P/K
values). Tab bar reordered: **Soil Test Report, About & Instructions**, then calculator tabs — About
moved to position 2 (was last) so it's discoverable before any data entry. If the currently active
tab gets hidden out from under a user (they changed report type), they're redirected to Soil Test.
Warning banners that existed to catch users who'd reached a calculator tab without soil test data
("Before you start…", "No Soil Test tab data found yet…") were removed as redundant once this gate
existed — a "Need to see the instructions?" prompt (Yes/No, jumps to About) was added to the Soil
Test tab instead, as a positive on-ramp rather than a defensive warning.

### Accessibility fixes (real bugs, not just polish)
- **Confirmed root cause of a reported "tabbing skips things" bug:** the Soil Test card header
  used `<div role="heading">` and contained the sample-report buttons inside it. ARIA prohibits
  interactive content inside a heading role, and this caused Chrome to skip those buttons (and,
  separately, the "need instructions?" prompt) during Tab navigation. Fixed by moving the buttons
  into a sibling `role="toolbar"` element and removing `role="heading"` from the div.
- Hidden Soil Test field blocks (`st-block-vce`, `st-block-waypoint`, `st-canonical-fields`,
  lawn-specific fields) now carry `inert` when hidden, toggled alongside `display` by a
  `setVisible()` helper inside `onReportTypeChange()` — previously their inputs remained in tab
  order even while invisible.
- Arrow-key tablist navigation now filters to visible tabs only — previously it could try to focus
  a hidden (locked) tab and get silently rejected, breaking the rotation.
- Added `aria-label` to the dynamically-generated amendment-choice `<select>` (had no accessible
  name at all) and to the inline Waypoint target `<input>`s (visible `<label>` existed but wasn't
  programmatically associated — no `for=` possible since these are generated in an innerHTML
  string with no stable id per row).
- Shade radio buttons (cool/warm) given unique `id`s + explicit `<label for>` (previously
  unassociated).
- **Not verified — flagged, not claimed clean:** actual color-contrast ratios of the CSS custom
  properties against their backgrounds. Static analysis can't confirm WCAG contrast minimums; a
  browser-based tool (axe/Lighthouse) would be needed.

### `renderNutrientStatusPanel` signature changed
`renderNutrientStatusPanel(gardenType, area, pRating, kRating)` →
`renderNutrientStatusPanel(gardenType, area)` — P/K ratings read directly from the Soil Test tab's
canonical fields (`st-p-rating`/`st-k-rating`) inside the function now, matching how Ca/Mg/S/micros
already worked. Any code still calling the 4-arg version needs updating.

### Waypoint targets — from a separate grid to inline per-nutrient, backed by JS state
The 9-field target grid in step 3/4 is gone. Each nutrient's target is entered directly in that
nutrient's row in the results. Backed by `gdnTargets` (persistent JS object), not DOM element
values, because the input elements are generated dynamically inside
`renderNutrientStatusPanel()`'s innerHTML and don't exist yet when `prefillSampleReport()` tries to
populate them. `gdnSetTarget(key, val)` is the setter; `prefillSampleReport()` now assigns
`gdnTargets` directly and resets it on every sample load.

### Sample data updated for new report-type values
- Flower sample: `waypoint-garden` → `waypoint-flower`
- Waypoint veggie sample: `waypoint-garden` → `waypoint-vegetable`
- VCE veggie sample: `vce-garden` → `vce-vegetable`
- All `st-garden-type` keys removed from sample fields objects (field no longer exists)

### CLAUDE.md itself
This file was not updated during the July 21 session (an updates doc was prepared but never
merged) or during most of this session. Both are now merged in as of this entry — see all "changed
July 21," "changed/added July 26," and "REVERSED/SUPERSEDED" annotations throughout the document
above for exactly what moved.

### Open items / next steps
- Flower Garden tab restructure (per user's stated sequence: vegetable → flower → shrubs & trees)
- Shrubs & Trees tab restructure
- Color contrast verification via a real accessibility scanning tool (not yet re-run since the
  July 6–7 axe/Lighthouse/IBM/WAVE passes, which predate this session's markup changes)
- Consider whether Elemental Sulfur / Langbeinite (sourced via NMSU H-119 this session) should be
  added as selectable K/S amendment options — they're in `BULK_DENSITIES` but not yet wired into
  any dropdown

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Vegetable Garden streamlining, app rename, report-type consolidation, tab gating, bulk-density sourcing audit + specific-gravity removal, manganese guidance, accessibility fixes |
| `CLAUDE.md` | this entry — merges the July 21 updates doc and this session's changes into the master for the first time |

---

## Session Updates — July 27, 2026 (cont.) (Tab focus-order fix + critical `isGarden` substring bug from the report-type consolidation)

### Context
User reported "tabbing skips the sample reports and need instructions" on the Soil Test tab,
across two rounds of investigation. Static code analysis (checking for `role="heading"` violations,
`inert` handling, duplicate IDs, stray keydown listeners) repeatedly came up clean and did not
reproduce the bug. **Root cause was only found by live-testing the actual deployed site**
(https://lawncarecalc.github.io/lawncarecalculator.github.io/) with real simulated Tab keypresses
and inspecting `document.activeElement` after each one — this environment cannot reach a locally
sandboxed file from the real browser (file://, localhost, and data: URLs are all blocked from that
context), so a publicly reachable URL was necessary to actually catch this.

### Bug 1 — `btn-about` had `tabindex="-1"` (roving tabindex pattern)
Live test: Tab #1 correctly landed on "Soil Test Report," but Tab #2 skipped "About & Instructions"
entirely and landed on the first sample-report button instead. Cause: the tab bar used the standard
ARIA "roving tabindex" pattern for tab widgets — only the currently active tab keeps `tabindex="0"`;
all others get `tabindex="-1"`, with the expectation that arrow keys (not Tab) move between tabs.
This is spec-compliant per the WAI-ARIA APG Tabs pattern, but does not match ordinary user
expectation of sequential Tab reaching everything, and was the literal cause of the reported skip.

**Fix:** every visible, enabled tab button now keeps `tabindex="0"` regardless of active state, so
plain sequential Tab reaches every tab in the bar. Arrow-key navigation between tabs (added earlier
this session) is kept as an *additional* option, not the only path. Changed in three places:
`activateTab()` (no longer sets `tabindex="-1"` on deactivated tabs), `updateTabLocks()` (newly
unlocked tabs get `tabindex="0"` unconditionally, not only when active — two occurrences, calculator
tabs and Lime), and the static HTML for `btn-about` (`tabindex="-1"` → `"0"`, since it's always
visible from page load).

**Verified live** by patching the fix directly into the deployed page's console and re-running the
identical Tab-key sequence: Tab #2 now correctly lands on "About & Instructions."

### Not a bug — Safari default keyboard navigation
User separately reported the fix "not working in Safari" while confirming it worked in Chrome, and
separately confirmed Option+Tab worked in Safari. This is expected, long-standing Safari/macOS
behavior, not a code issue: Safari's default Tab key only moves between text fields and lists, not
buttons/links/custom widgets, unless the user enables "Full Keyboard Access" (Safari → Settings →
Advanced → "Press Tab to highlight each item on a webpage," or System Settings → Keyboard →
"Keyboard navigation"). Confirmed via live search rather than relying on memory (menu names shift
between macOS versions) — true since at least macOS Catalina, still true in current Safari/macOS.
Does not affect VoiceOver users, who have their own navigation model. `tabindex="0"` is still the
objectively correct code — it's what makes elements reachable once a Safari user enables the
setting, and is what Chrome/Firefox/Windows screen readers already rely on by default. No code
change was made or needed for this half of the report.

### Bug 2 — Critical: stale `rt.indexOf('garden') >= 0` checks from before the report-type
### consolidation (SUPERSEDES parts of the "Single Combined Report-Type Question" section above)
User reported the Flower Garden sample prefills the Soil Test tab but doesn't carry over to the
Flower Garden tab's own fields. Live-tested (not just read statically) by calling
`prefillSampleReport('garden')` then `carryOverToCalculators()` directly in the console on the
deployed site and inspecting `flr-p-rating`/`flr-k-rating`/`flr-lime-rec` afterward — confirmed all
stayed empty.

**Root cause:** two functions computed `isGarden` locally via `rt.indexOf('garden') >= 0` instead of
calling the shared `isGardenReport()` helper. That substring check was correct under the *old*
4-value report-type scheme (`vce-garden`, `waypoint-garden`) but the July 26 consolidation to 8
granular values (`vce-vegetable`, `waypoint-flower`, `vce-shrub`, etc.) means **none of the new
values contain the literal substring "garden" anymore** — so this check silently evaluated to
`false` for every vegetable/flower/shrub report, always, since that consolidation shipped.
`isGardenReport()` itself (the shared helper) had already been correctly updated at consolidation
time — these were two separate, local re-implementations of the same check that got missed.

**Affected functions (fixed — both now call `isGardenReport()`):**
- `carryOverToCalculators()` — was always taking the lawn carry-over branch regardless of actual
  report type, so `flr-*`/`gdn-*` fields never got P/K ratings, lime rec, or area size carried over
  for ANY garden-family report (vegetable, flower, or shrub) — not just flower.
- `interpretSoilTest()` — **the more significant half of this bug.** This is the function that
  builds every interpretation card on the Soil Test tab itself. Since the July 26 consolidation,
  it had been silently treating every vegetable/flower/shrub report as a lawn report for its own
  internal logic (card content, garden-specific messaging, etc.) — not just the carry-over step.
  This had been live and broken since the report-type consolidation shipped, undetected until this
  session.

**Verified live** for both the Flower Garden and Vegetable Garden sample paths: patched the fix
into the deployed page's console, re-ran `carryOverToCalculators()`, confirmed `flr-p-rating`
correctly resolves to "M", `flr-k-rating` to "M+", and `gdn-lime-rec` correctly carries "0" from
the Waypoint sample data.

### Lesson for future report-type-scheme changes
Any future change to the `st-report-type` value scheme must grep the whole file for **every**
place that inspects the raw string (`indexOf`, direct equality, etc.) rather than assuming the
shared helpers (`isGardenReport()`, `isWaypointReport()`, `soilTestPurpose()`) are the only call
sites — this session found two local re-implementations of the same check that had drifted out of
sync with the helper. `grep -n "indexOf('garden')\|indexOf(\"garden\")\|'vce-garden'\|'waypoint-garden'"`
across the whole file should be part of the verification checklist for any future report-type
scheme change, not just checking that the helper functions themselves were updated.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Tab-bar `tabindex` fixed (About & Instructions no longer skipped by sequential Tab); critical stale `isGarden` substring check fixed in `carryOverToCalculators()` and `interpretSoilTest()` |
| `CLAUDE.md` | this entry |

---

## Session Updates — July 27–28, 2026 (Manganese pH-threshold verification, application-method fix for small quantities, About tab bibliography additions)

### Context
User pointed out a manufacturer's product page (Greenway Biotech, chelated manganese EDTA) gives a
different pH crossover point than what's in the app, and separately raised that the app's
manganese sulfate flat rate (0.05 lbs/100 sq ft) computes to an amount that's genuinely too small
to broadcast evenly by hand on a typical small bed (e.g., ~0.02 lbs / ~2 tsp on a 40 sq ft bed).

### pH threshold cross-check (thorough multi-source search performed)
Compared the app's existing NC State-sourced guidance (Mn sulfate effective below ~6.8, sharp
availability drop above 7.5; switch to chelated above 7.0) against Greenway Biotech's page (sulfate
"unreliable" above 5.5; switch to chelated at 5.5; chelate itself stops working above 7.0).

Searched seven independent sources to adjudicate:
- **Cornell Nutrient Management Spear Program** (Factsheet 49): Mn most available pH 5–6.5; above
  6.5 could cause deficiency
- **University of Maryland Extension**: Mn less available above pH 6.5
- **Michigan State University Extension**: deficiency most likely above pH 6.5
- **University of Wisconsin–Madison** (A2526): toxicity below 5.5, deficiency risk rises toward
  neutral/alkaline
- **University of Delaware**: Manganese Availability Index formula (continuous decline with rising
  pH, not a hard cutoff)
- **Zubieta et al., 2025** — *Agrosystems, Geosciences & Environment* (University of Florida,
  peer-reviewed, open access, Wiley/ASA-CSSA): directly tested MnSO₄ vs. Mn-EDTA in the field;
  found **no yield or leaf-Mn difference between the two product forms**, and concluded foliar Mn
  generally isn't needed below soil pH 6.2
- **Purdue University Extension** (AY-276-W): states Mn-EDTA chelate is **not as effective** as Mn
  sulfate for foliar application tank-mixed with glyphosate — directly contradicts Greenway
  Biotech's claim that EDTA is "preferred for glyphosate mixes"

**Conclusion:** every neutral source clusters around pH 6.0–6.5 as the meaningful threshold — not
5.5. This matches the app's existing NC State-sourced guidance closely and does **not** support the
manufacturer's earlier crossover point. The manufacturer's pH claims are unattributed marketing
copy on the same page that does properly cite Delaware/Virginia/Cornell/Michigan State for a
different claim (field rates) — the pH thresholds themselves carry no citation. Combined with the
Purdue contradiction on a second specific technical claim (glyphosate compatibility), and the
inherent conflict of interest (a manufacturer's own product page recommending an earlier switch to
its pricier chelated product), the app's existing threshold was left unchanged as the better-
supported figure. **No source meeting this project's standard was found to justify changing it.**
Commercial/manufacturer sources remain excluded from this app's sourcing per existing policy —
this was a real-world test of that policy holding up under an actual disagreement, not just a
restatement of it.

### Application method for tiny quantities (the more actionable finding)
Separately searched for a legitimate source specifically for a manganese-sulfate-in-water soil
drench dilution rate (e.g., "X teaspoons per gallon"), since dry-broadcasting ~0.02 lbs of powder
over a 40 sq ft bed by hand is not practically achievable and risks patchy over/under-application —
worse for boron than manganese, given boron's narrow deficient-to-toxic margin.

**Result: no qualifying source found.** Every result for "manganese sulfate soil drench" was
commercial or unverified consumer content (succulentes.net, Alibaba/lifetips, BioLogix, BRANDT,
Sprinkler Warehouse, Facebook/Instagram posts, Greenway Biotech again) — the same "1–2 tsp/tbsp per
gallon" figure repeats across many of these, but repetition across non-authoritative sources does
not confer legitimacy under this project's rule, and no per-gallon concentration rate was added to
the app on that basis.

**The actual fix needed no new citation.** The insight: the *rate* (total weight of Mn needed) is
already correctly sourced (NC State) — what was missing was application *method* guidance, and a
water-dissolve method doesn't need its own separate sourced dilution ratio, because it isn't a new
dose — it's a more practical way to deliver the same already-correct total amount evenly.
Concentration in the water doesn't affect total Mn delivered to the bed; only total amount and
even distribution matter. This is supported by a legitimate, if general, source: a school/community
garden curriculum document, *Soil Amendments and Fertilizers*, hosted by **Hood College's Center
for Coastal and Watershed Studies** as part of their Farm to Fork/Food Systems Network (FFSN),
states plainly that a water-soluble fertilizer can be "dissolved in water... used as a foliar spray
or applied directly to soil" — confirming the general principle without needing a manganese-
specific rate. **Correction, logged so the mistake pattern is visible:** this was first attributed
to "Maryland Department of Agriculture" based on a search-result snippet, without navigating to the
actual URL. When later verified directly (a live HTTP fetch), that guessed `mda.maryland.gov` URL
404'd — the real, working document is the Hood College one above (confirmed via `fetch()` returning
HTTP 200, `content-type: application/pdf`). Both the About tab entry and the two inline code
citations (Manganese Sulfate, granular Borax) were corrected to the verified attribution. **Lesson:
always navigate to and verify a source URL directly before writing it into a citation — a search
snippet describing where a source is hosted is not the same as confirming the actual link
resolves.**

**Applied to both Manganese Sulfate entries** (flat and sized-to-target) in `NUTRIENT_AMENDMENTS.Mn`:
notes now recommend dissolving the calculated amount in 1–2 gallons of water and pouring evenly
over the bed instead of dry broadcast, citing the MD Dept. of Agriculture principle.

**Also applied to Boron** — user asked directly whether the same reasoning extends to Borax. It
does, and matters more there: boron has the narrowest deficient-to-toxic margin of any plant
nutrient (well-established across virtually every source on boron), so uneven dry distribution
risks a locally toxic patch even when the total amount is correct — dissolving isn't just more
convenient for boron, it's the safer method. The existing "Borax (liquid method)" entry already had
a real sourced rate (UMD Extension, 1 tbsp/gallon/100 sq ft) and needed no change. The **"Borax
(granular, weighed to target)"** entry — the one sized from a Waypoint numeric target, which is
often just a few grams — did not have this guidance and now does, with the boron-specific safety
reasoning made explicit in the note, plus a pointer back to the already-diluted liquid method as an
alternative for users who'd rather not weigh out a tiny dry quantity at all.

### Process note — a confirmation didn't actually get implemented
User said "yes" to the Manganese drench-method fix in an earlier turn this session; that turn's
response acknowledged the change but the actual code edit was never made. This was caught only
because implementing the parallel Boron fix required re-reading the current Manganese code first,
at which point the note text was found unchanged. **Lesson: verify a described change actually
landed in the file (grep for the new text) before treating a "yes" as done, not just after saying
so** — do not assume a conversational confirmation implies the corresponding tool calls occurred
unless independently checked.

### About tab bibliography — four sources added, one caught and corrected via direct URL
### verification (had been missing/wrong since first cited in code)
Cross-checked the About tab's Source Documents section against every citation string actually used
in the code (not just spot-checked) and found gaps:
- **NC State Extension — Torres Quezada, 2024** (manganese) — added to the existing "UMD, Clemson,
  Rutgers, NC State & Mid-Atlantic Veg Guide" collapsible, alongside the pre-existing generic NC
  State entry
- **Ohio State University Extension, Ohioline FABE-550** and **NMSU Cooperative Extension Guide
  H-119** — given their own new collapsible, "Bulk Density / Volume Conversion Sources," since
  they're a different kind of source (physical density data, not agronomic recommendations,
  neither from a Virginia/Mid-Atlantic institution) and needed their own framing note explaining
  the narrow exception under which they're cited
- **Hood College FFSN "Soil Amendments and Fertilizers"** (the drench-method source, see above) —
  added alongside the manganese entry. Caught and corrected mid-addition: initially written in as
  "Maryland Department of Agriculture" from a search snippet without checking the actual URL; a
  live `fetch()` verification found that guessed URL 404'd, and the real, working document
  (confirmed HTTP 200) turned out to be hosted by Hood College instead. Both the About tab entry
  and the two inline code citations were corrected to match.
- New JS function `toggleAboutDensitySources()` added, matching the existing per-section toggle
  pattern (`toggleAboutSuppSources()`, etc.)

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Manganese pH threshold verified against 7 independent sources (unchanged, now better-documented); drench-application guidance added to both Manganese Sulfate entries and the granular-target Borax entry; 4 sources added to About tab bibliography (one caught and corrected via direct URL verification after an initial wrong attribution) |
| `CLAUDE.md` | this entry |

---

## Session Updates — July 28–29, 2026 (Flower Garden single-nutrient system, Lime CCE absorbed into garden tabs, print-fix verification saga)

### Flower Garden gets a Complete/Individual fertilizer choice (Vegetable Garden does not)
User explicitly requested Flower Garden offer a choice between "Complete N-P-K Fertilizer" (the
existing blended picker, kept as-is, now the default) and "Individual N, P, K Fertilizers" (new —
mirrors Vegetable Garden's single-nutrient system). Vegetable Garden deliberately does NOT get
this choice; the two tabs are allowed to diverge here by explicit user decision.

**`renderNutrientStatusPanel()` generalized** — signature changed to
`renderNutrientStatusPanel(prefix, area, suppressPK)` (was `(gardenType, area)`). `suppressPK` is
true only in Flower Garden's Complete Fertilizer mode, where P/K rows show "Handled by your
Complete N-P-K Fertilizer selection above" instead of an independent amendment (avoiding
double-applying P/K that the blended product already supplies). Ca/Mg/S/micronutrients are
unaffected by the mode and always show.

**State namespacing** — `gdnTargets`, `gdnNutrientChoice`, `gdnCustomDensity` remain single shared
objects (no signature change to their setters), but every key used to address them is now prefixed
(`'flr:k2o'` vs `'gdn:k2o'`, `'flr:P:Bone Meal'` vs `'gdn:P:Bone Meal'`) so switching between a
Vegetable and Flower report in the same session can't leak one tab's entered Waypoint target or
organic/synthetic choice into the other. Verified directly: set a target under the `gdn` prefix,
confirmed it does not appear when rendering under the `flr` prefix.

New: `flowerFertilizerMode` (default `'complete'`), `setFlowerFertilizerMode(mode)`. New Flower
Garden HTML: Nitrogen Source dropdown (Individual mode only, same organic/synthetic-by-% options as
Vegetable Garden, no Note-19-flat-rate bypass — deliberately narrower scope). `calcFlower()`'s
fertN/fertP/fertK sourcing now branches on mode; everything downstream (quantity display,
application-plan table) is unchanged regardless of which mode supplied those three numbers.

**Removed from Flower Garden as redundant, now superseded by the shared panel:** the generic P/K
flag boxes (`P_REC`/`K_REC` messages), the "~10 lb bone meal or rock phosphate" VCE amendment note,
the raw-ppm sulfur advisory, and the "no lime but Ca/Mg low" Epsom-salts/gypsum branch. Kept: lime
quantity math and dolomitic-vs-calcitic guidance (genuinely lime-specific, not covered by the
nutrient panel).

Verified via simulation: Complete mode suppresses P/K correctly; Individual mode shows real
amendment choices (Bone Meal/Rock Phosphate, etc.); Manganese/other micronutrients show correctly
in both modes.

### Manganese note reworded to be crop-neutral (Flower Garden now shares this note with Vegetable
### Garden)
Previously framed entirely around vegetable crops ("scaled down from NC State's... vegetable-garden
guideline, tomatoes, peppers, brassicas"). Now explicitly separates the pH-availability
relationship (general soil chemistry, corroborated by Cornell/UMD/Michigan State — not crop-
specific) from the application *rate* (still vegetable-crop-derived, now explicitly flagged as "not
separately validated for ornamental plantings" rather than silently implied to apply equally).
Applied to both Manganese Sulfate entries and the Chelated Manganese entry.

**Citation caught and fixed again during this pass** (second time this project — see the July 27–28
entry for the first): a Cornell factsheet URL was added to the About tab, then verified directly
per the standing rule (never cite a URL without checking it resolves) — it 404'd. A second,
differently-pathed URL from a different search result ALSO came back as an error page (`text/html`,
empty title). Rather than keep guessing, converted to a plain-text citation with no link, matching
how University of Maryland and Michigan State were already listed (neither has a verified link
either — no link was fabricated for those, and none was fabricated here once the guessed ones
failed).

### Lime — CCE and bag-size absorbed into Vegetable Garden and Flower Garden directly; standalone
### Lime tab no longer serves garden purposes at all (SUPERSEDES the "Lime unlocks for any report"
### rule stated in the July 26–27 entry)
User pushed back on an initial fix that had only updated the standalone Lime tab's wording/units for
garden reports ("Lawns" → "Lawns/Gardens"). Correct diagnosis: Vegetable Garden and Flower Garden
already had their OWN inline lime sections, but those were less precise than the standalone tab —
`limeLbsTotal = limeRec * hundredths` with **no CCE adjustment at all** (silently assumed 100% CCE)
and no bag-count math, while the Soil Test tab's own advisory literally told garden users to *go
use the separate Lime tab* for that precision. Two calculators for one number, one of them worse,
is the actual problem — not the standalone tab's wording.

**Fix:** Vegetable Garden and Flower Garden both got CCE % and bag-size input fields, and their
inline lime math upgraded to the real formula: `limeAdjRate = (limeRec * 100) / limeCce`, per-
application splitting (5 lbs/100 sq ft established / 10 lbs/100 sq ft preplant, per VCE Note 19),
bag count. Verified the formula directly: 5 lbs/100 sq ft report figure at 80% CCE correctly
computes to 6.25 lbs/100 sq ft adjusted, needing 2 applications and 1 bag of 40.

**`updateTabLocks()` — Lime is no longer purpose-agnostic.** Previously unlocked for any report
with P/K values, regardless of purpose. Now: `soilTestPurpose() === 'lawn' || 'shrub'` only.
Vegetable/Flower Garden purposes no longer unlock the Lime tab at all — verified via simulation
across all four purposes (vegetable → Lime locked, flower → Lime locked, shrub → Lime unlocked,
lawn → Lime unlocked). Shrubs & Trees has no lime section of its own to absorb this into, so it
(like Lawn) still routes to the standalone tab.

**Pre-existing bug found and fixed while implementing this:** the Soil Test tab's own
interpretation cards (Lime Recommendation, Base Saturation, Buffer Index) treated ALL garden-family
purposes as one group. A **Shrubs & Trees** report with a lime recommendation was being labeled
"Vegetable Garden" and routed to the `garden` tab — which has no shrub-specific handling at all.
Fixed with a proper three-way branch (vegetable → Garden tab, flower → Flower tab, shrub → Lime
tab) and consolidated into one shared `limeGoBtn` variable (computed once, reused by all three
cards) so the routing can't drift out of sync between cards the way it just had.

### Timing-card print fix — a two-part debugging story worth recording in full
User reported the Timing of Applications section missing from printed Flower Garden plans, despite
the July 26–27 fix (`.timing-card` shown via print-media override) already being in the codebase.

**First verification attempt was itself wrong, and it's important to know why.** A substring check
(`rule.cssText.indexOf('printing-flower') >= 0 && rule.cssText.indexOf('timing-card') >= 0`) run
against the deployed site's stylesheet returned `true`, appearing to confirm the fix was live. It
was a false positive: the check ran against the *entire* `@media print` block's concatenated
`cssText` (since `CSSMediaRule.cssText` includes all nested rules as one string), which contains
both substrings *somewhere*, just not in the same rule. A second, more careful check — walking
`CSSStyleRule`-type rules specifically and checking each one's own `selectorText` — found only 2
rules mentioning `printing-flower` on the deployed site, and **the actual `.timing-card` override
rule was entirely absent**. The deployed site was running a version of `index.html` that predates
that fix.

**Root cause: a deployment gap, not a code bug.** This project's `index.html` is produced here and
the user deploys it to GitHub Pages separately — Claude has no push access. The fix was correct in
the working file the whole time; it just hadn't been pushed yet when first reported.

**User then pushed an update and reported the SAME issue persisting.** Re-ran the careful
(non-substring, per-rule) verification against the freshly deployed site with a cache-busting query
string and confirmed the rule genuinely is now present, confirmed no competing print-media rule
touches `.timing-card` besides the intended two, and computed the CSS specificity by hand
(override: 1 ID + 2 classes + 1 type vs. general suppressor: 1 class alone — override correctly
wins). The fix is confirmed live and correct as of this session.

**Lesson, added as a rule below:** when verifying whether a CSS/JS fix actually reached a deployed
site, check for the *specific* rule/behavior directly (walk parsed CSSOM rules by type and compare
selectors) — a broad substring match against a large concatenated block (e.g. a whole `@media`
block's `cssText`) can produce false positives when unrelated rules happen to share vocabulary.
Also: distinguish "is this fixed in the file I'm producing" from "is this fixed on the URL you're
looking at" — those are two different questions when the user has a separate deploy step.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Flower Garden Complete/Individual fertilizer mode toggle with shared, namespaced Nutrient Status panel; Manganese note reworded crop-neutral; Cornell citation corrected (unlinked, matching UMD/Michigan State) after a second broken-URL catch; CCE/bag-size lime calculation absorbed into Vegetable Garden and Flower Garden; Lime tab purpose-gated to Lawn/Shrub only; three-way lime-routing bug fixed on the Soil Test tab; Flower Garden's print output confirmed (via direct CSSOM inspection on the live deployed site, not just the local file) to correctly include its Timing of Applications section |
| `CLAUDE.md` | this entry |

---

## Session Updates — July 29, 2026 (cont.) (Print bug, part 3 — the actual root cause: incomplete `:not()` exclusion list)

### Context
After the July 28–29 fix was confirmed present and correctly winning the cascade on the deployed
site, the user reported the Timing of Applications section was *still* missing from Flower
Garden's printed output. The `.timing-card` override itself was not the problem — a third,
different bug was.

### The real bug
The "default print view" rule — the one that shows the Soil Test tab when no plan-specific print
is active — was:
```css
body:not(.printing-cool):not(.printing-warm):not(.printing-lime):not(.printing-garden) #tab-soiltest { display: block !important; }
```
**Missing `:not(.printing-flower)` and `:not(.printing-shrub)`.** This rule was written before
those two prefixes existed and never updated when they were added. Consequence: when printing
Flower Garden (`body.printing-flower`), this selector still matched (none of cool/warm/lime/garden
were present), so `#tab-soiltest` got `display: block !important` **at the same time** as
`#tab-flower` did from its own rule. Both tab panels' entire contents rendered into the same print
job — the Soil Test tab's own lengthy interpretation-card content most likely pushed Flower
Garden's later sections (including its Timing card, which itself was rendering correctly) onto
later pages that weren't reviewed. Same bug would affect Shrubs & Trees printing.

**Fix:** added the two missing exclusions. Verified: dumped every rule in the print media block
in exact source order (29 rules total) via the live deployed site, confirmed only one rule
addresses `#tab-soiltest`'s default visibility and it now excludes all six prefixes; confirmed the
fix doesn't regress the Soil Test tab's own print button (`printSoilTestResults()` → plain
`window.print()`, no class set at all — all six `:not()` conditions remain true when no class is
present, so that path is unaffected).

### Why this took three passes to find
1. First pass: confirmed the `.timing-card` override rule existed in the file — true, but
   irrelevant, since the site hadn't been redeployed yet (a deployment gap, not a code bug).
2. Second pass (after redeployment): confirmed the `.timing-card` override rule was live and
   correctly winning the cascade by specificity — also true, and still not the actual cause,
   because a *different* rule was additionally showing the wrong tab panel at the same time.
3. Third pass: only found by dumping literally every rule inside the print media block, in order,
   rather than just the rules directly relevant to the one element (`.timing-card`) already under
   suspicion. The bug was adjacent to, not inside, the thing being investigated.

**Lesson, added as a rule below:** when a specific override rule is confirmed correct in isolation
but the reported symptom persists, widen the investigation to every rule in the same media block —
a correct fix for one selector doesn't rule out an unrelated, adjacent rule causing the same
visible symptom by a different mechanism (here: showing an extra tab's content, not hiding the
target content).

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Fixed incomplete `:not()` exclusion list on the default print-view rule — Soil Test tab was printing simultaneously with Flower Garden (and would have with Shrubs & Trees) any time those were printed, most likely burying their own later sections including the Timing card |
| `CLAUDE.md` | this entry |






