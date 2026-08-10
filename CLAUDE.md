# CLAUDE.md — Soil Test Report Assistant Project Context

Use this file to bring a new Claude session up to speed on the project.

---

## Project Overview

A single-file interactive HTML web calculator (`index.html`) — named **"Soil Test Report Assistant"** (renamed again August 2, 2026 — see dated entry below)
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

**Versioning convention (added August 9, 2026):** the version badge in the header (bottom-right of
the title bar, `v#.# · date`) uses a rolling single-digit minor number: 0 through 9, then the whole
number increments and the minor digit resets — `n.9` is followed by `n+1.0`, never `n.10`. This
matters because `n.10`/`n.11` sorts and reads inconsistently next to single-digit values. **Bump
this on every `index.html` change, in every session, no exceptions** — this convention was broken
for two versions (v6.10, v6.11) before being caught and corrected to v7.2 in this session; those two
numbers should never be reused or referenced as if they were valid.

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
3. **Cool-Season Lawns** (`tab-cool`) — hidden until a lawn report + Cool grass type entered. Includes inline CCE-adjusted lime calculation (July 31).
4. **Warm-Season Lawns** (`tab-warm`) — hidden until a lawn report + Warm grass type entered. Includes inline CCE-adjusted lime calculation (July 31).
5. **Lime** (`tab-lime`) — hidden until a **Shrubs & Trees** report has P or K values entered. As of July 31, this is the only remaining purpose that routes here; Cool/Warm Lawns, Vegetable Garden, and Flower Garden all do lime math on their own tab now.
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
| `calcLime()` | Standalone Lime calculator — writes to `lime-results-panel`. **Now only serves Shrubs & Trees reports** (July 31). Still uses its own internal lime math (not yet refactored to `calcLimeForBed()` since that tab is approaching retirement for all but Shrub). |
| `calcLimeForBed(limeRec, cce, areaUnits, maxPerApp, bagSize)` | **(added July 31)** Shared lime math — CCE-adjusted rate, total lbs, applications needed, lbs per app, bags needed. Used by `calcGarden()`, `calcFlower()`, and `renderLimeForLawn()`. Caller passes everything in a consistent basis (Garden/Flower: lbs/100 sq ft, areaUnits = area/100, maxPerApp = 5 or 10; Lawns: lbs/1,000 sq ft, areaUnits = lawnSize/1000, maxPerApp = 50). The function itself is unit-agnostic. |
| `renderLimeForLawn(prefix)` | **(added July 31)** Dedicated lime display for Cool/Warm Lawns — reads from `{prefix}-lime-rec`, `{prefix}-lime-cce`, `{prefix}-lime-bag-size`, `{prefix}-lime-type`, `{prefix}-lawn-size`; writes to `{prefix}-lime-display`. Called by `calcCool()`/`calcWarm()` regardless of auto/custom plan mode, since lime is independent of the N-P-K plan. |
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
| 🌿 Vegetable Garden Sample (Waypoint) | Waypoint vegetable | waypoint-vegetable | P Very High (394 ppm), K Low (100 ppm) — the exact adequate-P/low-K case the Nutrient Status panel was built to handle. Sets `gdnTargets` (K2O 2.0, S 0.13, B 0.04, Mn 0.05) directly, not DOM fields |
| 🌿 VCE Vegetable Garden Sample | VCE vegetable | vce-vegetable | *(Added July 21)* Sample "VEGGD". All nutrients VH/SUFF, N-only fertilizer recommended, lime 3 lbs/100 sq ft. Contains VCE's own cup conversions for 4 N products — demonstrates the report's own math matches CROP_FEEDING_LEVELS defaults exactly |

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
31. **(Added July 30)** When a routing/labeling bug tied to purpose (vegetable/flower/shrub/lawn) is found and fixed in one card, `grep` the whole file for the same raw pattern (e.g. `isGarden ? 'garden' : ...`) before considering it resolved — do not assume inspection caught every instance. This exact bug (a card using a simple `isGarden` check instead of the three-way vegetable/flower/shrub split) was fixed for three cards in one session and found again, missed, in a fourth (the pH card) the next session
32. **(Added July 30)** Live user-simulation testing (actually operating the deployed app via the browser tool, reading every explanation as a first-time user would, not just checking navigation) surfaces bugs that code review does not. This session's most significant find — a legacy P/K flag system still actively contradicting the new single-nutrient system for certain Nitrogen Source choices (Fish Meal, Bat Guano) — was invisible to static review and had gone undetected through several prior sessions' worth of smoke-testing, because every Nitrogen Source tried previously happened to be 0% P/K. When removing code found this way, check immediately whether anything else in the same function depends on variables the removed block declared — a genuine regression (breaking the still-valid tomato/pepper N-timing split) was introduced and caught only because a live-patch test threw a `ReferenceError`, not because of prior inspection
33. **(Added August 1)** `index.html` carries a version tag — a `<meta name="app-version">` in `<head>` and a small visible `v{X}.{Y} · {date}` tag in the top-right of the site header (marked `no-print`). **Bump both on every single update to `index.html`, no exception, even a one-line fix.** This exists specifically to solve the recurring "is the live site actually running my latest fix" problem that came up repeatedly before this convention existed (the print-CSS saga, the Google/Bing verification confusion) — a live fetch of the deployed page can now check the version tag directly instead of needing to grep for a specific recent change each time. Current: 2.1 (2026-08-01).

---

## Attributions

- **Chantel Wilson** — Assistant Professor and 4-H STEAM Extension Specialist, Virginia State University  
- **Michael Goatley Jr.** — Professor and Extension Specialist, Virginia Tech

Virginia Cooperative Extension is a partnership of Virginia Tech, Virginia State University, USDA, and local governments.

---

## Files

| File | Description |
| :---- | :---- |
| `index.html` | Main application — **Soil Test Report Assistant** (renamed August 2, 2026 from "Soil Report Assistant"; that itself was renamed July 26, 2026 from `lawn_garden_calc_v1_5.html` / "VCE Lawn & Garden Care Calculator") |
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

Both Rutgers (real tomato, garlic, and lettuce reports) and VCE (a real vegetable garden report) confirm:

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

The garden/flower tabs capture the report's N figure, but the lawn tabs did not — carry-over set P/K/species/size but left `cool-n-rate`/`warm-n-rate` blank. The VCE-ceiling warning only fired after the volunteer manually typed the figure into the lawn tab. This is the exact Fact #11 scenario; the live example is a real Waypoint report (N 4.0 on a cool-season lawn, above the 3.5 tall-fescue ceiling).

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
figure identical regardless of soil chemistry), and a real VCE Lab vegetable garden report.

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
- A real Waypoint vegetable garden report, Sample "2-Vegetable Beds" — P Very
  High, K Low. The adequate-P/low-K case the Nutrient Status panel was built for.
- A real VCE vegetable garden report, Sample "VEGGD" — all nutrients VH/SUFF, N-only
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
"Lawn & Garden Calculator" / "VCE Lawn & Garden Care Calculator" → "Soil Report Assistant" → **"Soil Test Report Assistant"**,
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

---

## Session Updates — July 29, 2026 (cont. 2) (Print Plan button relocated after the Timing card — four tabs)

### Context
Even after the print output itself was confirmed correct (both the `.timing-card` override and the
`:not()` exclusion-list bugs from the two prior entries), the user flagged a UX problem: the
"Print Plan" button visually sits at the bottom of the results card, immediately followed by a
*separate* Timing of Applications/Application Timing card. That placement makes the button look
like it only covers the box it's physically inside, even though it has always covered the Timing
card too — a correct behavior that reads as suspicious due to layout alone.

### Scope check done before fixing
Grepped every tab for this pattern rather than fixing only where reported. Confirmed it's universal
across **Vegetable Garden, Flower Garden, Lime, and Shrubs & Trees** — all four are single-column
layouts with a results card ending in a Print Plan button, immediately followed by a separate
`.timing-card`. **Cool-Season and Warm-Season Lawns were checked and found structurally
different** — a two-column layout where the Print Plan button lives in the *left* (input) column's
custom-plan mode, not stacked directly above the *right* column's results-then-Timing-card
sequence. Deliberately left unfixed this pass; flagged to the user as a related but different
problem needing its own approach, not silently bundled into this fix or silently ignored.

### Fix
Moved each of the four tabs' Print Plan button to sit **after** that tab's Timing card, so it
visually reads as covering everything above it (which it always did).

- **Vegetable Garden, Flower Garden** — these already used a static `<div id="{prefix}-print-btn-
  wrap">` pattern (from earlier session work); just relocated the wrapper's HTML position to after
  the Timing card. No JS changes needed — `calcGarden()`/`calcFlower()` already toggled this
  wrapper's visibility correctly regardless of its position in the DOM.
- **Lime, Shrubs & Trees** — these built their Print Plan button as part of a JS-generated HTML
  string appended directly into the results panel's `innerHTML` (no static wrapper existed). Real
  rewiring needed: removed the inline `html += '<button ...>'` append in both `calcLime()` and
  `calcShrub()`; added a new static `#lime-print-btn-wrap` / `#shrub-print-btn-wrap` div after each
  tab's Timing card in the HTML; added show/hide logic at the end of each calc function (and in
  Lime's early-return "no input yet" branch, which needed to explicitly hide the wrapper too, since
  that branch returns before reaching the end-of-function show logic).

### Verification
- Confirmed via `grep` that each wrapper now has exactly one occurrence, correctly positioned.
- Simulated `calcLime()` directly: wrapper shows (`display: ''`) with valid input, hides
  (`display: 'none'`) when the lawn/garden size is cleared — both directions confirmed.
- For `calcShrub()`: confirmed by direct inspection (rather than a full simulation, given the
  function's length and number of dependencies) that the `shrubHasContent` flag is captured using
  the exact same condition the old inline check used, and that `html` is not reassigned between
  where the flag is captured and where it's read — so the flag can't go stale.
- Full HTML/JS validation clean; no new orphaned `getElementById` references beyond the
  pre-existing, already-documented harmless set.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Print Plan button moved to after the Timing card on Vegetable Garden, Flower Garden, Lime, and Shrubs & Trees; Lime and Shrub's buttons converted from inline JS-appended HTML to a static wrapper with proper show/hide logic. Cool/Warm Lawns identified as having a related but structurally different issue, intentionally not addressed this pass. |
| `CLAUDE.md` | this entry |

---

## Session Updates — July 30, 2026 (Live user-simulation evaluation pass — found and fixed one active fertilizer-advice bug, several content/copy issues, and a recurring routing-bug class)

### Context
User asked Claude to "wear the shoes of a user" — actually operate the deployed app end-to-end via
the browser tool (not reason about the code) and evaluate every explanation encountered, not just
navigation. This is the same technique used for the July 28–29 print-button work, now applied
specifically to *content correctness*, not just navigation flow. It found a materially more
significant bug than any of the wording issues.

### Most significant finding: a dead-looking legacy P/K flag system was still active in
### `calcGarden()`, giving contradictory single-nutrient-era advice
While reading Vegetable Garden's live output with a Fish Meal nitrogen source selected (P rated
Very High), a box appeared reading **"Phosphorus: Use a Zero Phosphorus (P) Fertilizer"** —
directly alongside the new Nutrient Application Plan's own correct "Adequate — no addition needed"
guidance for the same nutrient. This old `pkHtml`/`P_REC`/`K_REC` block predates the July 21–28
single-nutrient restructure and was never removed. It didn't fire during earlier smoke-testing
because every Nitrogen Source tried up to that point (Calcium Nitrate, Urea, etc.) happens to be
0% P/K, which coincidentally kept the block's `!fertAlreadyZeroPK` guard false. **Fish Meal and Bat
Guano are NOT 0% P/K** (Fish Meal is 10-6-2), so selecting either un-suppressed it — a real,
reachable, contradictory-advice bug, not dead code.

**Fixed:** removed the entire legacy `pkHtml`/tomato-pepper-split-note/`P_REC`/`K_REC` block from
`calcGarden()`. **A genuine regression was introduced and caught immediately while doing this**:
a separate, still-valid piece of logic a few lines earlier (VCE Note 19's "split preplant N in
half when P or K rates High/Very High for tomato/pepper" — a nitrogen *timing* rule, unrelated to
the P/K amendment system) depended on the same `pHigh`/`kHigh` variables the removed block
declared. Restored a clean, correctly-sourced `pHigh`/`kHigh` computation (reading directly from
`st-p-rating`/`st-k-rating` via `WAYPOINT_TO_VCE`) in the right place, and verified both things at
once via a live patch-and-test on the deployed site: the "zero fertilizer" message is gone, and the
tomato/pepper split still fires correctly (`pHigh=true kHigh=true`, split logic confirmed).
Also removed now-orphaned `pRating`/`kRating` variable declarations left unused after the block's
removal.

### Recurring bug class: cards using a simpler `isGarden` check instead of the three-way
### vegetable/flower/shrub routing (SUPERSEDES the assumption, from the July 29 entry, that all
### affected cards had been found)
The July 29 fix corrected Lime Recommendation, Base Saturation, and Buffer Index to route/label
correctly per purpose (vegetable → Garden tab, flower → Flower tab, shrub → Lime tab) instead of
lumping all garden-family purposes together. **The Soil pH card had the identical bug and was
missed in that pass** — found this session via the user pointing at stale-looking "go to lime
calculator" text and asking for it to be removed, which led to checking every remaining
`goBtn(isGarden ? ...)` pattern rather than just the one instance mentioned. Fixed by moving the
shared `limeGoBtn` variable (computed once) to before the pH card instead of after it, so the pH
card now reuses the same correctly-routed variable instead of an independent, drift-prone
`isGarden`-only check. **Lesson: when a routing/labeling bug is found and fixed in N places, grep
for the same raw pattern (`isGarden ? 'garden' : ...` etc.) across the whole file rather than
assuming every instance was caught by inspection** — this is the second time in as many sessions a
bug was fixed in some places but not found everywhere it existed until a later prompt surfaced it.

### Vegetable-specific language leaking into Flower Garden's shared nitrogen-source data
Flower Garden's "Individual N, P, K Fertilizers" mode (added July 28) reuses the same
`GARDEN_PRODUCTS` object Vegetable Garden uses for its Nitrogen Source dropdown. Three entries had
vegetable-crop-specific examples that don't make sense to a Flower Garden user: Calcium Nitrate
("blossom end rot in tomatoes and tip burn in cole crops"), Blood Meal ("effective as a sidedress
for warm-season crops... tomatoes, corn, peppers"), Fish Emulsion ("good choice for early-season
cole crops and root vegetables"). All three generalized to be crop-neutral while keeping the
genuinely useful, non-crop-specific parts (soil-temperature release behavior, etc.).

### Blossom end rot / tip burn causal claim was overstated (user's own science critique, not just
### a wording preference)
User flagged that describing calcium nitrate as reducing blossom end rot in tomatoes "stretches
the science" — correct: BER and tip burn are primarily calcium-**uptake** disorders driven by
inconsistent watering and root development, not usually a true soil calcium shortage; added
calcium only helps reliably when soil calcium itself tests low. Fixed in **three** places that made
the same overreach: the Calcium Nitrate product note itself, the Clemson HGIC bibliography
description, and the NC State bibliography description. **Left unchanged, deliberately:** the
Nutrient Deficiency Symptoms Reference table's mention of "blossom end rot in tomatoes" as a visual
*symptom* of calcium deficiency — that one already correctly hedges ("Properly limed soils usually
supply adequate calcium") and isn't making a treatment-efficacy claim the other three were.

### Minor content/copy fixes found via direct reading
- **Wrong emoji**: Shrubs & Trees' "Soil pH target" line used `&#127789;` — decoded and confirmed
  this is literally the hot dog emoji (🌭), not a rendering artifact. Replaced with a thermometer
  (`&#127777;`).
- **Redundant nutrient-name repetition**: every card offering a P/K recommendation box prepends a
  bold "Phosphorus:"/"Potassium:" label via the *calling* code, but the shared `P_REC`/`K_REC`
  message text *also* repeated the nutrient name ("Phosphorus: Phosphorus (P) is not needed...").
  Fixed at the data level (all `P_REC`/`K_REC` entries), not per call site, since all four call
  sites shared the same redundant pattern.
- **ALL-CAPS shade question** (Cool/Warm Lawns): the "Is this area shaded?" legend was rendering in
  full uppercase — traced to a shared CSS class (`fieldset.st-fieldset-block > legend`) designed
  for short section labels (its original, correct use: the "Micronutrients" section header) but
  reused here for a long conversational paragraph, inheriting `text-transform: uppercase`
  unintentionally. Fixed with a targeted inline `text-transform:none` override on just these two
  instances (Cool and Warm), leaving the shared class and its original usage untouched.

### Flagged, not yet acted on (subjective content/design calls, not bugs — presented as options)
- pH, Buffer Index, and Lime Recommendation cards on the Soil Test tab all independently give
  overlapping "go apply lime" guidance: could strip the diagnostic cards' (pH, Buffer Index) action
  buttons and leave Lime Recommendation as the single actionable destination, or leave as-is since
  each answers a genuinely different question.
- Base Saturation card is thin — mostly defers to "look at pH/lime instead" — could be shortened to
  a single line rather than its current multi-paragraph structure, without claiming more precision
  than VCE's own treatment of base saturation (background info) supports.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Removed an actively-firing legacy P/K flag system from `calcGarden()` that contradicted the new Nutrient Application Plan for certain Nitrogen Source choices; restored the still-valid tomato/pepper N-timing split logic that briefly broke during that removal; fixed the pH card's lime-routing bug (same class as the July 29 fix, missed in that pass); de-vegetable-ified three shared nitrogen-source notes now used by Flower Garden; corrected an overstated blossom-end-rot/calcium causal claim in three places; fixed a wrong emoji and an ALL-CAPS CSS bug; removed redundant nutrient-name repetition in P/K recommendation text |
| `CLAUDE.md` | this entry |

---

## Session Updates — July 30, 2026 (cont.) (Fertilizer-chooser relocation on Cool/Warm Lawns, pH/Buffer Index action buttons removed, About-tab Step 1 reformatted as a bulleted list)

### Fertilizer-chooser button relocated (Cool-Season and Warm-Season Lawns)
User flagged (with a screenshot of the deployed site) that "Help me choose a fertilizer at the
garden center" sat disconnected above the entire Application Plan section, rather than near the
N%/P%/K%/WIN% fields it's meant to help with. Moved `#cool-fert-chooser` / `#warm-fert-chooser`
from before the Application Plan / mode-toggle block to immediately after the auto-mode ("Build a
plan for me") WIN% input, before the inline result. Scoped to auto mode only, matching what the
screenshot showed — not duplicated into Custom mode's multi-slot builder, which asks for N/P/K per
slot in a different shape; flagged to the user as a follow-up if wanted there too.
`fertChooserHTML()`'s insertion logic (`document.getElementById('cool-fert-chooser').outerHTML =
...`) needed no change — same id, just relocated in the DOM tree, verified exactly one instance of
each id remains.

### pH and Buffer Index cards' "go to Lime Calculator" buttons removed (Soil Test tab)
Implements option (a) from the July 30 assessment of the three overlapping lime-related cards —
proposed earlier in the same session but not actually acted on until the user pointed out the
button was still there. pH and Buffer Index are now pure diagnostic cards (what's wrong, why it
matters) with no action button; Lime Recommendation remains the single card offering "go
calculate your lime," now the one clear destination instead of three competing ones. Base
Saturation's button was deliberately left in place — it was not part of this specific proposal;
still flagged separately as a candidate for the same treatment if wanted.

**Process note:** this was presented as an open option and the user was asked to choose; when they
responded, only the pH card's separate routing bug got fixed (see prior entry) and option (a)
itself was never actually implemented, despite having been described as if it might be. Confirm an
approved change actually landed (grep for it) rather than assuming a related fix in the same
turn covered it — this is the same class of gap as the "said yes, didn't implement" mistake from
the July 27–28 Manganese session, now recurring in a different form (partial implementation
mistaken for complete, rather than a skipped implementation).

### About tab — Step 1 reformatted as a bulleted list
Step 1 of the universal on-ramp ("Enter your report") was one dense paragraph covering five
distinct actions (select report type, enter size, enter every value, the P/K-before-continuing
gotcha, click Continue). Converted to a `<ul>` with one bullet per action, keeping the bolded
"Enter your report." lead-in and the bolded P/K-gotcha sentence intact. Steps 2 and 3 are short
enough as single sentences and were left as prose.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Fertilizer-chooser collapsible relocated to after the WIN% field on both lawn tabs' auto-plan mode; pH and Buffer Index cards' Lime Calculator action buttons removed per the approved option (a); About tab Step 1 reformatted as a bulleted list |
| `CLAUDE.md` | this entry |

---

## Session Updates — July 30, 2026 (cont. 2) (Color contrast bug found via WAVE, fixed, then systematically swept across all restructure-era markup)

### Context
User reported WAVE contrast errors on two card header subtitles ("(Vegetable Garden tab)" on the
Single-Nutrient Amendment Philosophy card, "(Lawn tabs only)" on the WIN & Nitrogen Programs card —
both added during the July 26–29 About tab rewrite). This is exactly the kind of regression the
July 6–7 accessibility audit's automated scores could not have caught, since neither card existed
yet at that point — see the standing warning already in the README's Accessibility section.

### Root cause, confirmed by computing the actual ratio rather than assuming
Both subtitles used `color: var(--slate-light)` (#5f6b6b) against the dark green `.card-header`
background (`--green-deep`, #1a3d1f). Computed via the real WCAG relative-luminance formula (not
eyeballed): **2.2:1**, against the 4.5:1 minimum required for this text size. The `--slate-light`
token has an existing code comment noting it was "darkened from #8a9490 for WCAG AA contrast" —
but that adjustment was made for use against *light* backgrounds (cream/white), and got reused here
against a dark one by mistake. Grepped the whole file for the same pattern
(`card-header"><span` combined with a `color:` style) and confirmed these were the only two
instances — not a wider pattern in the new markup.

**Fix:** switched both to `--green-pale` (#d4edda), an existing token already in the palette rather
than introducing a new one-off color. Recomputed: **9.78:1**.

### Full systematic sweep of restructure-era markup (not just the two reported instances)
Rather than stop at the reported bug, computed actual contrast ratios for every distinct
color-on-background pairing introduced or touched during the July 21–30 restructure, using the
real WCAG formula (including proper alpha-blending for any semi-transparent color, e.g. the tab
bar's `rgba(255,255,255,0.55)` inactive state — blended against its background before computing,
not treated as if it were an opaque color):

| Element | Ratio |
| :-- | :-- |
| Sample report buttons (4 background variants) | 5.67 – 9.98 |
| P/K recommendation boxes (`.rec-p`/`.rec-k` adequate/low/zero states) | 4.76 – 9.78 |
| `.warning-badge` (red on pink) | 4.76 |
| `.note-banner` (brown on gold) | 6.23 |
| Bulk-density widget / `.lime-notes` box | 5.88 |
| Organic/Synthetic badges (Nutrient Status panel) | 5.65 – 11.14 |
| Complete/Individual & auto/custom mode toggle buttons (`.st-unit-btn`, active + inactive) | 6.41 – 6.42 |
| Main tab bar — active, inactive (alpha-blended), hover (alpha-blended) | 4.84 – 9.23 |
| `.results-card .card-header` (lighter green variant) with white text | 6.42 |

All pass. Closest margins: the red-on-pink warning badge (4.76:1) and the inactive tab bar text
(4.84:1, the alpha-blended one) — both clear the 4.5:1 minimum but with little room, worth
rechecking if either color or background changes in a future edit. No other instance of the
reused-wrong-context color-token pattern that caused the original bug was found.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Fixed contrast failure on two card-header subtitles (`--slate-light` → `--green-pale`); systematically verified contrast (computed, not assumed) across every other color pairing introduced in the July 21–30 restructure — all pass |
| `CLAUDE.md` | this entry |

---

## Session Updates — July 31, 2026 (Lime absorbed into Cool/Warm-Season Lawns, Lime tab now Shrub-only, shared calcLimeForBed function, navigation cleanup)

### Context
User proposed either (a) adding bottom-of-tab navigation links between Cool/Warm and Lime, or
(b) absorbing lime calculations into Cool/Warm directly and eliminating the Lime tab for lawn
purposes — and asked Claude's point of view. Claude recommended option (b), on the grounds that
it's the same architecture already built for Vegetable Garden and Flower Garden and solves the
same underlying problem ("two calculators for one number" is worse than one, regardless of how
well you navigate between them), plus recommended factoring the now-four-times-duplicated lime
math into one shared function while in there. User agreed.

### Shared `calcLimeForBed(limeRec, cce, areaUnits, maxPerApp, bagSize)` — one formula, four
### callers (SUPERSEDES the three separate copies mentioned in earlier entries)
Extracted the CCE-adjusted-rate + total-lbs + apps-needed + bags-needed math into a single
shared function used by Vegetable Garden, Flower Garden, Cool-Season Lawns, and Warm-Season
Lawns — was previously copy-pasted three times (Garden, Flower, and the standalone Lime tab's
`calcLime()`) with a fourth about to be written. The function is caller-agnostic:
`calcLimeForBed(60, 80, 5, 50, 40)` = 60 lbs/1,000 sq ft report figure, 80% CCE, 5 × 1,000 sq ft
units, 50 lbs max/app, 40 lb bags → adjRate 75.0, totalLbs 375.0, 2 applications, 10 bags.
Verified the formula directly with both a lawn test case and a garden test case to confirm the
same function works in both unit bases. `calcGarden()` and `calcFlower()` refactored to call it
(their inline math removed); `renderLimeForLawn()` was built using it from the start.

### Cool-Season and Warm-Season Lawns — lime calculated directly, no separate tab
Added Step 6 to both tabs: lime recommendation (lbs/1,000 sq ft), lime type
(Agricultural/Dolomitic), CCE %, and bag size — matching the Vegetable Garden and Flower Garden
pattern. `renderLimeForLawn(prefix)` computes and displays lime results inside the existing
results card (separate from the N-P-K plan, since lime is independent of auto/custom plan mode),
using `calcLimeForBed()` in the lawn basis (lbs/1,000 sq ft, 50 lbs/1,000 sq ft max per
application per VCE 430-011). Wired into both `calcCool()` and `calcWarm()`, called regardless
of plan mode.

**Implementation note — a structural mistake made and caught mid-edit:** the first attempt at
inserting Cool tab's lime fields accidentally deleted the "Build a plan for me" toggle button
from the Application Plan section (the `str_replace` old-string was too broad and consumed the
next block's opening lines). Caught immediately via an HTML balance check showing only one of the
two toggle buttons remaining, and fixed before continuing. The same edit for Warm tab was done
more carefully as a result (a narrower, more precisely-bounded replacement string) and landed
cleanly on the first try.

### `updateTabLocks()` — Lime tab now Shrub-only (SUPERSEDES the "Lawn + Shrub" rule from July 29)
Previously: `limePurpose === 'lawn' || limePurpose === 'shrub'`. Now: `limePurpose === 'shrub'`
only. Lawn purposes no longer unlock the Lime tab at all. Only Shrubs & Trees still relies on the
standalone Lime tab for its lime math (Shrubs & Trees has no lime section of its own to absorb
this into, and VCE actively discourages lime for many shrub/tree species — building inline lime
math there is a genuinely separate decision from the other four tabs).

### Interpretation card "Open Calculator" buttons — removed for lawn purposes
Removed the "Open Cool-Season/Warm-Season Calculator" buttons from the Phosphorus, Potassium,
Grass Type & Lawn Status, and Nitrogen Recommendation Check interpretation cards. The single
"Continue to [X] Calculator" carry-over banner plus the new bottom-of-tab navigation links are the
intended navigation path now. **Carefully preserved** the garden-routing button on the Phosphorus
and Potassium cards (`isGarden ? goBtn('garden',...) : ''`) — those weren't part of this request.

Updated the Lime Recommendation card's lawn branch: no longer shows "Open Lime Calculator" /
routes to the standalone Lime tab; action text now says "Enter your product's CCE and bag size on
the Cool-Season or Warm-Season Lawn tab."

Updated the shared `limeGoBtn` variable: Lawn purposes produce no button (lime is on their own
tab); Shrub still routes to the Lime tab; Vegetable/Flower still route to their own tabs. This
affects the pH, Buffer Index, Base Saturation, and Lime Recommendation cards simultaneously.

### Bottom-of-tab navigation links added
"← Back to Soil Test Report" button added at the bottom of Cool-Season Lawns, Warm-Season Lawns,
and the Lime tab — styled consistently, hidden from print output via `no-print`.

### About tab instructions updated
- Cool-Season Lawns: now shows 9 numbered steps (was 4) including lawn size, lime as step 6,
  and the application plan as steps 7–9.
- Warm-Season Lawns: same structure, matching Cool.
- Lime: updated to say "Only appears for Shrubs & Trees reports" (was "Lawn and Shrubs & Trees").

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Lime CCE-adjusted calculation absorbed into Cool/Warm-Season Lawns via shared `calcLimeForBed()` (refactored Garden/Flower to use the same function); Lime tab gated to Shrub-only; four lawn "Open Calculator" buttons removed from interpretation cards; Lime Recommendation card's lawn branch updated; bottom-of-tab nav links added to Cool/Warm/Lime; About tab instructions updated for all three |
| `CLAUDE.md` | this entry |
| `README.md` | Updated tabs table (Cool/Warm now mention inline lime; Lime tab described as Shrub-only); Lime & CCE section updated to reflect Shrub-only scope and shared function |

---

## Session Updates — July 31–August 1, 2026 (Cool/Warm duplicate-plan bug, versioning convention, comprehensive click-through test plan, two more `isGarden`-lumping fixes)

### Cool/Warm-Season Lawns — Auto mode duplicated the entire application plan on screen
User found this by using the app normally (not a code-review find): the inline area under the
N-P-K/WIN inputs and the separate "Your Application Plan" card both showed the identical full
table simultaneously. Root cause: `calcAutoplan()` built one `planHtml` string and wrote it into
*both* `resultEl` (`{prefix}-auto-result`, left column) and `panelEl`
(`{prefix}-results-panel`, right column), with a code comment ("Write to right panel (print
only)") describing an older architecture where the right panel was apparently meant to be
print-only/hidden on screen — but it had since become a normal, always-visible card, and the
dual-write was never updated to match. A second, orphaned Print Plan button (embedded in
`resultEl`'s assignment) existed alongside the one already moved to sit after the Timing card in
the July 29 fix.

**Fix:** `resultEl` now gets only a brief one-line summary (grade + program badge + warnings);
the full table exists exactly once, in `panelEl`. Removed the orphaned embedded print button.
Verified by patching the corrected function into the live deployed page and confirming the inline
area no longer contains a `<table>` element while the results panel still does. Checked
`calcMulti()` (Custom mode) for the same pattern — confirmed its inline per-slot results and its
results-panel rollup are genuinely different content (individual slot numbers vs. a
season-cumulative table), not a duplicate, so no fix needed there.

### Versioning convention established (see rule 33)
Added `<meta name="app-version">` to `<head>` and a small visible `v{X}.{Y} · {date}` tag in the
top-right of the site header (`no-print`). Current: 2.1 (2026-08-01). Exists specifically to let
a live-fetch check confirm whether a deploy has actually landed, without needing to grep for a
specific recent change each time — a problem that came up repeatedly this project (the print-CSS
saga, the Google/Bing verification confusion). **Must be bumped on every future `index.html`
change, no exception.**

### Comprehensive click-through test plan created
`Click_Through_Test_Plan.md` — built from the actual bug patterns found across this whole
project (duplicate content rendering, mode-locked buttons, missing carry-over, incomplete
`isGarden`-based purpose routing, misused shared CSS/color tokens, cross-context leaked wording,
incomplete print exclusion lists, generic-vs-specific threshold mismatches), each generalized into
a checklist of where else in the app the same shape of bug could be hiding, followed by an
exhaustive per-tab walkthrough and cross-cutting checks. Structured to be worked through
repeatedly as the app changes, not a one-time checklist.

### Two more `isGarden`-lumping routing bugs found (SUPERSEDES the assumption that the July 30
### pH-card fix and the three-card fix from July 29 caught every instance)
Running the test plan's own Pattern D check (`grep -n "isGarden ?"` across the whole file, rather
than trusting prior inspection) found two more real instances of the same bug class already fixed
three times this project:
- **pH card's action text** (not the trailing button, which was already fixed) said "use the
  Garden Calculator" for *any* `isGarden` report — mislabeling Flower Garden and incorrectly
  pointing Shrubs & Trees at a tab that has nothing to do with lime for that purpose. This is a
  different piece of the pH card than the `limeGoBtn` fix from July 30 — that fixed the trailing
  button, this fixes inline text constructed earlier in the same card's logic.
- **Phosphorus and Potassium cards' own buttons** (`pCropBtn`/`kCropBtn`) still routed every
  `isGarden` report to `'garden'` (Vegetable Garden), regardless of whether the actual report was
  vegetable, flower, or shrub. Fixed with the same three-way `crop`-based split used elsewhere;
  Shrub now correctly gets "Open Shrubs & Trees Calculator" instead of being silently absorbed
  into the vegetable-only routing.

Verified via simulation: all four purposes (vegetable/flower/shrub/lawn) now produce the correct
button label and destination for both cards.

**Lesson already written as rule 31, reconfirmed by this find:** a routing bug fixed "in the
cards I looked at" is not the same as fixed everywhere it exists. The grep-first approach (Pattern
D in the new test plan) found these two in under a minute; they had survived two prior fix passes
that relied on inspection instead.

### Live re-verification of prior fixes (all confirmed still holding)
- Cycled through **all 17** Vegetable Garden Nitrogen Source options (including the 5 Note-19
  flat-rate variants) checking for the old contradictory "zero-phosphorus fertilizer" message —
  none found, July 30 fix holds comprehensively, not just for the two options originally
  spot-checked.
- Cycled through all 12 Flower Garden Individual-mode Nitrogen Source options checking for
  vegetable-specific language (tomato, pepper, cole crop, etc.) — none found.
- Checked the Nutrient Status panel's amendment notes on Flower Garden for the same leakage —
  none found.
- Confirmed Vegetable Garden and Flower Garden have no separate inline-result div architecture
  (unlike Cool/Warm) — Pattern A structurally cannot occur there, by design, not just by luck.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Fixed Cool/Warm Auto-mode duplicate application-plan rendering and an orphaned second Print Plan button; added app-version meta tag and visible header version tag (2.1, 2026-08-01); fixed pH card's action text and P/K cards' own buttons, which still lumped vegetable/flower/shrub together after two prior fix passes |
| `Click_Through_Test_Plan.md` | New — comprehensive pattern-based + per-tab click-through test plan |
| `CLAUDE.md` | this entry |

---

## Session Updates — August 1, 2026 (cont.) (Executing the test plan: Lime tab's Timing card was never included in print, keyboard/Shrub walkthrough clean)

### Print-matrix check (Pattern H) found a real, previously undiscovered bug
Ran a systematic check — not just re-confirming the five tabs already fixed, but building the full
cascade table for all six — and found that **Lime was never added to the `.timing-card` print
override list**, even though it has its own Timing & Application Notes section like every other
tab. The July 26–27 fix that made this override list exist in the first place covered Cool, Warm,
Garden, Flower, and Shrub; Lime was missed at that time and stayed missed through every later
"Timing card doesn't print" investigation this project, because those investigations were all
triggered by reports about Flower Garden specifically and never widened to check Lime too.

**Fix:** added `body.printing-lime #tab-lime .timing-card` to the existing override rule.
Verified via the same cascade-table method used to confirm the other five (walking the live
parsed CSSOM rather than assuming) — all six tabs now correctly include their own Timing card in
print, confirmed via direct rule inspection rather than visual print-preview.

### Print-matrix and keyboard regression check — everything else confirmed clean
- Built a full six-tab table confirming each `printing-X` class shows exactly one tab panel with
  no overlap and no Soil Test Report bleed-through — the July 29 `:not()` exclusion fix holds
  correctly for all six, not just the two that had been specifically reported broken.
- Re-ran the July 27 tab-focus-order keyboard check (Tab #2 → "About & Instructions") against the
  current deployed site including the new header version tag — confirmed no regression; the
  version tag `<div>` isn't natively focusable and doesn't affect Tab order.

### Shrubs & Trees walkthrough — clean, no new bugs found
Full walkthrough with an acid-loving shrub (azalea/rhododendron category) and a Soil Test tab
lime recommendation entered on the same report. Confirmed: the tab correctly shows "No lime —
lime raises pH and will harm acid-loving plants" despite a general lime figure being present on
the report (matching the documented July 31 design intent for the Lime Recommendation card's
shrub branch); the thermometer emoji fix (from the July 30 evaluation pass) displays correctly;
no redundant P/K nutrient-name repetition. Shrubs & Trees remains the one tab still on the
pre-restructure P/K-entry pattern (manual selects, not auto-filled from the Soil Test tab) —
confirmed this is a known, already-flagged gap, not a new one.

**One methodology note worth keeping:** an early attempt to test this same walkthrough used an
invalid dropdown value (`'azalea'` instead of the real option value `'acid-shrub'`), which silently
left the field blank rather than erroring — a reminder that a live-simulation test needs to verify
the *actual* option values from the markup before assuming a plausible-looking value will work,
same discipline as reading real code rather than guessing at API shapes.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Added Lime tab to the `.timing-card` print override list (v2.2, 2026-08-01) — the sixth tab, missed in every prior pass at this specific fix |
| `CLAUDE.md` | this entry |

---

## Session Updates — August 1, 2026 (cont. 2) (Test plan continued after v2.2 deploy confirmed — Vegetable Garden, Cool lime math, mobile width: all clean)

### Deploy confirmation via the new version tag — working as intended
Fetched the live site fresh (no-cache) and confirmed `app-version` reads `2.2 (2026-08-01)` and
the Lime `.timing-card` fix's exact code comment is present — the version tag did exactly the job
it was built for, first real use.

### Vegetable Garden — full crop-type cycle and Nutrient Application Plan hand-verification
Cycled all 24 crop-type options (including the legacy flower entries retained in the dropdown) —
no `NaN`/`undefined`, every crop returns distinct, sensible guidance-panel content. Then ran a full
Nutrient Application Plan with P Low / K Very High / Ca Optimum / Mg Low / Mn Low and hand-checked
every computed number: Bone Meal 20.00 lbs (10 lbs/100 sq ft flat rate × 2 for a 200 sq ft bed),
Epsom Salts 2.00 lbs (1 lb/100 sq ft × 2), Manganese Sulfate 0.10 lbs (0.05 × 2) — all correct. K
Very High and Ca Optimum both correctly show "Adequate — no addition needed." Confirmed the
tomato/pepper N-timing split note ("apply only half now... High/Very High P or K") correctly fires
given the Very High K rating — this is the exact logic that was carefully preserved during the
July 30 legacy-code removal, still working correctly under real numbers.

### Cool-Season Lawns lime math — hand-verified correct
40 lbs/1,000 sq ft report figure, 90% CCE, 8,000 sq ft lawn, 50 lb bags → adjusted rate 44.4
(40 ÷ 0.90), total 355.6 lbs (44.4 × 8), 1 application (44.4 is under the 50 lb/1,000 sq ft cap),
9 bags (⌈355.6 ÷ 40⌉). Every step matches `calcLimeForBed()`'s formula exactly.

**Correction, August 4, 2026:** this entry originally said "8 bags (⌈355.6 ÷ 50⌉)" — dividing by
50 (the per-application lbs cap) instead of 40 (the actual bag size), an arithmetic slip made when
this was first hand-verified, not a code bug. Re-checked independently during the calculation audit
prompted by the target-conversion bug (see that entry) and corrected here. The code itself
(`Math.ceil(totalLbs / bagSize)`) was always correct; only this documented "golden number" was
wrong. Recorded as its own lesson: even a hand-verification step needs to be checked against the
right inputs, and a "verified" number in this file should be re-derivable by someone else, not just
trusted because it's labeled verified.

### Mobile-width check — no overflow found, but width achieved wasn't the one requested
Resized to 380×800; the actual viewport reported was 500px wide (browser minimum constraint in
this environment, not something adjustable from here). At the 500px width actually achieved, no
element's `scrollWidth` exceeded the viewport — no horizontal overflow found. **This does not
fully substitute for a genuine ~380px check** — flagged as an open item, not silently claimed as
complete, since the app has its own `@media (max-width: 400px)` reflow rule that this test never
actually got narrow enough to exercise.

### Net result this round: no new bugs found
After two consecutive rounds that each found a real bug (the P/K/pH routing fix, then the Lime
timing-card fix), this round's checks — Vegetable Garden's full crop cycle, its Nutrient
Application Plan math, and Cool-Season's lime math — came back clean. Recorded as a genuine clean
result, not a gap in testing effort: each check was a real computation or content generation,
verified against hand-arithmetic or direct inspection, not a superficial "the page loaded" check.

### Open items remaining in the test plan
- Flower Garden's own full field-by-field pass (Vegetable Garden's was completed; Flower Garden's
  crop-type cycle and Complete-mode math not yet hand-verified)
- A genuine ~380px mobile-width check (this round's attempt topped out at 500px)
- Print-preview visual confirmation (this project has relied on CSSOM rule inspection throughout,
  which is more reliable for confirming *what the rules say* but has never been cross-checked
  against an actual rendered print preview image)

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | No changes this round — verification only |
| `CLAUDE.md` | this entry |

---

## Session Updates — August 1, 2026 (cont. 3) (Flower Garden's full field-by-field pass — clean)

### Flower Garden — all 4 flower types, both fertilizer modes, mode-toggle stability
- Cycled all 4 flower types (annual/perennial/rose/bulb) in Complete mode with a fertilizer grade
  entered — no NaN/undefined; N defaults confirmed exact matches to documentation (0.10/0.10/0.20/
  0.40 lbs/100 sq ft respectively).
- Hand-verified Spring-Flowering Bulbs' full output: N rate 0.4 ÷ 10% N fertilizer = 4.00 lbs/100
  sq ft, × 1.5 (150 sq ft bed) = 6.00 lbs — correct.
- Confirmed Complete mode's P/K suppression message ("Handled by your Complete N-P-K Fertilizer
  selection") displays correctly, and that Mg (not suppressed by mode, only lime-conditional) still
  shows a real amendment: 1 lb/100 sq ft × 1.5 = 1.50 lbs Epsom Salts — correct, and correctly
  un-suppressed by lime since the lime type entered was Agricultural, not Dolomitic.
- Switched to Individual mode: confirmed Phosphorus correctly un-suppresses and computes 10 lbs/
  100 sq ft × 1.5 = 15.00 lbs Bone Meal — correct.
- **Toggled Complete ↔ Individual four times in a row**, ending in each mode, and confirmed no
  state corruption either direction — P/K correctly re-suppress going back to Complete, correctly
  show real amendments going back to Individual, every time.
- Lime math hand-verified: 5.0 lbs/100 sq ft report figure ÷ 80% CCE = 6.25 (shown 6.3), × 1.5 =
  9.375 total (shown 9.4), ⌈6.25/5⌉ = 2 applications (established-bed limit), ⌈9.375/40⌉ = 1 bag —
  all correct. Also confirmed the dolomitic-lime recommendation correctly triggers given the
  Mg-Low rating entered, independent of which lime type was originally selected.

**No new bugs found.** This completes both halves of the Vegetable Garden / Flower Garden
field-by-field pass from the test plan's Part 2 (Vegetable Garden done in the prior entry, Flower
Garden here) — both single-nutrient systems, and Flower Garden's additional mode toggle, are
confirmed working correctly under real hand-checked numbers, not just "no error was thrown."

### Remaining open items in the test plan
- A genuine ~380px mobile-width check (still blocked by this environment's resize floor)
- Print-preview visual confirmation (still only verified via CSSOM rule inspection, never an
  actual rendered image)
- Cool/Warm Custom-mode (multi-slot) full walkthrough — Auto mode was covered by the duplicate-plan
  bug fix and its verification; Custom mode's season-summary math hasn't been independently
  hand-checked the way Auto mode's has

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | No changes this round — verification only |
| `CLAUDE.md` | this entry |

---

## Session Updates — August 1, 2026 (cont. 4) (Real-phone testing found what desktop simulation couldn't; Start Over feature added)

### "Start Over" feature added
User reported no way to clear the app and switch report purposes (e.g. lawn → flower garden)
without closing and reopening it entirely. Added a "🔄 Start Over" button to the Soil Test tab's
sample-report toolbar. Deliberately implemented as a confirm-then-full-reload
(`window.location.href = window.location.pathname`, stripping any query string) rather than
manually enumerating and clearing every field and JS state object across six tabs — the user had
already confirmed a close-and-reopen gives a genuinely clean slate, and a reload reproduces that
exact result with certainty, without the risk of missing a field or state variable (the same risk
class this whole test-plan effort keeps finding elsewhere). Verified end-to-end on the live site:
filled Flower Garden completely, triggered the reset, confirmed landing back on Soil Test Report
with Flower Garden's data cleared and that tab re-locked.

### Real-phone testing (not desktop simulation) found a genuine mobile layout bug this session's
### own testing had flagged as a blind spot
This desktop environment could not get its browser viewport below ~500px width no matter what was
requested (confirmed twice, down to a 320px request still yielding 500px) — flagged explicitly in
the prior entry as leaving a real 400–500px gap untested. User switched to an actual phone and
found it immediately: **the Soil Test tab's own two-column grid (`.st-layout`) has no mobile
reflow rule at all**, unlike `.calc-layout` (used by every calculator tab), which already collapses
to single-column under `@media (max-width: 400px)`. In portrait orientation on a real phone, the
Soil Test tab's interpretation cards render squeezed into the ~42%-width right column and get
their text clipped mid-word — confirmed via the user's own screenshots. Landscape orientation
(effectively a wider viewport, closer to what could be tested here) showed no problem, exactly
matching what this environment's own 500px-floor testing had found.

**Root cause, once identified:** `.st-layout` is a separate, distinctly-named CSS class from
`.calc-layout` — same two-column grid concept, different tabs (Soil Test vs. every calculator
tab). The "Reflow fix: single column at very narrow widths (WCAG 1.4.10)" block that fixed
`.calc-layout` simply never included `.st-layout`, because it was written for the calculator tabs
specifically and the Soil Test tab's parallel two-column layout wasn't checked against the same
fix at the time.

**Fix:** added the identical `display: block !important` / `width: 100% !important` treatment for
`.st-layout` to the same existing `@media (max-width: 400px)` block `.calc-layout` already uses —
same breakpoint value, since the user's own report confirms that threshold already works
correctly for `.calc-layout` on this exact device.

**Checked for the same gap elsewhere before considering this closed:** grepped for every other
two-column/multi-column grid layout in the file. Found `.leftover-grid` is dead CSS (no `class=
"leftover-grid"` anywhere in the actual markup) and the newer lime-field two-column grids (Lime
type + CCE%, added this session to Cool/Warm/Garden/Flower) are inline-styled `1fr 1fr` layouts —
deliberately left untouched, since the user explicitly confirmed Cool/Warm "render well including
the application plans" on the same real device, meaning those specific grids are not currently
broken and don't need a proactive fix invented for them.

**This is the clearest demonstration yet of why the test plan calls for real-device testing, not
just desktop viewport resizing** — this exact gap was flagged as an open item in the prior entry,
and the fix was found within one round of switching to an actual phone.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Added "Start Over" button (confirm + full reload) to the Soil Test tab; fixed `.st-layout`'s missing mobile reflow rule — the Soil Test tab's two-column grid had no `@media (max-width: 400px)` collapse, unlike every calculator tab's `.calc-layout` (v2.4, 2026-08-01) |
| `CLAUDE.md` | this entry |

---

## Session Updates — August 1, 2026 (cont. 5) (Master Gardener survey link added to all six calculator tabs — a real prefix-mismatch bug found only through live debugging, not through static review or isolated simulation)

### Feature: dismissible survey prompt on every calculator tab
Ahead of a broader Master Gardener rollout, added a dismissible callout — "📋 Help us improve
this tool — take a 2-minute survey" with a "Take Survey" link (`https://virginiatech.questionpro.com/calculatortool`)
and a "No thanks" dismiss button — positioned after Print Plan, before "Back to Soil Test Report,"
on all six calculator tabs (Cool, Warm, Lime, Vegetable Garden, Flower Garden, Shrubs & Trees).
Shown only once real results exist (same condition as the Print Plan button), dismissible per tab
(not globally — a user can legitimately complete two separate tasks, e.g. a lawn report and a
separate vegetable garden report, in one sitting, and dismissing on one shouldn't hide it on the
other), and dismissal is session-only (no localStorage, matching the rest of this app).

**Discovered while adding this: three tabs (Vegetable Garden, Flower Garden, Shrubs & Trees) were
missing "Back to Soil Test Report" entirely.** The July 31 session that added this link only
touched Cool, Warm, and Lime. Added the missing link to the other three at the same time, since
the survey feature's placement depends on it existing.

### A real, shipped bug found only through live debugging — not the isolated JS simulation
Built `updateSurveyPrompt(prefix, shouldShow)` and `dismissSurvey(prefix)` as small shared
functions, and verified the *logic* with a clean Node.js simulation (shows/hides/persists/
per-tab-independent — all passed). That simulation used made-up, self-consistent prefix names
(`'cool'`, `'warm'`, etc.) and never caught the actual defect, because the defect wasn't in the
logic — it was a **string mismatch between the calling convention and the real element IDs**:

- Vegetable Garden's tab prefix is `gdn` everywhere in this codebase (`gdn-crop-type`,
  `gdn-lawn-size`, etc.) — but the new code called `updateSurveyPrompt('garden', ...)` and
  `dismissSurvey('garden')`, constructing the DOM lookup `'garden-survey-prompt'`, which does not
  match the actual element `id="gdn-survey-prompt"`.
- Flower Garden has the identical pattern: internal prefix `flr`, but the new code used
  `'flower'`.
- Cool, Warm, Lime, and Shrub were unaffected only because those four tabs' internal element
  prefixes happen to exactly equal the JS-level word used to call the functions — the bug was
  invisible on 4 of 6 tabs purely by coincidence of naming, and would have shipped completely
  silent on the two that abbreviate their prefix.

**How this was actually found:** live-testing in the browser kept showing the prompt as `none`
regardless of what should have made it show. Ruled out, in order: the function logic itself
(correct, confirmed via isolated expression evaluation), the `surveyDismissed` state (correctly
`false`), duplicate DOM IDs (only one element existed), and cross-`javascript_exec`-call context
loss (state and functions both persisted correctly across calls). The actual proof came from
writing a version of the function that *returns* whether it found an element at all — it returned
`'NO ELEMENT'`. That is the exact bug: `getElementById('garden' + '-survey-prompt')` legitimately
finds nothing, because no such ID exists.

**Also worth recording:** `file://` navigation was tried as a way to test the real local file
directly (rather than approximating it via injection) and doesn't work — the browser being
controlled is the user's own machine via the Chrome extension, not this sandbox's filesystem, so
local paths aren't reachable that way. The eventual fix came from extracting the *actual* current
`calcGarden()` function from the real file and injecting that exact code (the same proven
technique used earlier this session for the `calcAutoplan()` duplication-bug verification) rather
than a hand-approximated version — which is precisely what surfaced the real prefix string used in
the shipped code, instead of whatever prefix I assumed while manually testing.

**Fix:** changed both calls and the dismiss buttons' `onclick` attributes to use `'gdn'`/`'flr'`
(matching the real element IDs) instead of `'garden'`/`'flower'`, and renamed the corresponding
keys in the `surveyDismissed` state object to match. Re-verified with the real, corrected
`calcGarden()` logic injected live: shows on first calculation, hides on dismiss, **stays hidden
through a subsequent recalculation** (the one behavior an isolated simulation can't meaningfully
test when the actual bug is a string/ID mismatch rather than a logic error).

**Lesson for future work in this codebase:** when a tab's internal element-ID prefix differs from
the natural English word used to describe it (`gdn`≠garden, `flr`≠flower — a naming inconsistency
that predates this session and exists throughout the file), any new shared function taking a
`prefix` argument for that tab must be called with the *actual* ID prefix, not the descriptive
name — and this class of mismatch will not show up in a logic-only simulation that doesn't use the
real ID strings. Grep for the real `id="..."` values before wiring up a new cross-tab shared
function, rather than assuming the prefix used elsewhere in a conversation (like `'garden'`
earlier in this same conversation, referring to the report *purpose*) is also the right DOM prefix.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Added dismissible Master Gardener survey prompt to all six calculator tabs (after Print Plan, before Back to Soil Test Report); added the missing "Back to Soil Test Report" link to Vegetable Garden, Flower Garden, and Shrubs & Trees (a gap from July 31); found and fixed a real `'garden'`/`'gdn'` and `'flower'`/`'flr'` prefix mismatch that would have made the survey prompt permanently non-functional on exactly those two tabs (v2.6, 2026-08-01) |
| `CLAUDE.md` | this entry |

---

## Session Updates — August 2, 2026 (Tomato/pepper "split preplant N in half when P/K test High" rule retired — not a bug fix, an architectural decision, reached after tracing a wording complaint all the way back to source conflict)

### How this started
User reported the red warning text on Vegetable Garden's tomato/pepper preplant step was confusing.
Investigation initially found a real, narrower bug: Step 1's "Amount for your bed" column was
showing the *full* unsplit preplant total while the adjacent text said "apply only half now" — no
way to tell half of what from that row alone. That narrower fix (documented in the same day's
earlier entry, now superseded below) halved the displayed Step 1 amount to match the instruction
and rewrote the text to state the reasoning plainly.

### The question that reopened it
User then asked a good follow-up: does this imply the *full* amount would be applied at preplant
if P/K weren't High? Confirmed yes, and directly against the primary source this time (VCE
452-719 / SPES-687P, fetched and read in full, not assumed):

> "Tomatoes, Green Peppers, Lima Beans – If the garden area has been liberally fertilized in the
> past and the soil tests high or very high for phosphate and potash, for best results apply
> one-half the recommended amount of fertilizer before planting and the remaining half after
> fruit set. Too much fertilizer applied early in the spring for these vegetables will encourage
> vegetative growth and reduce fruit set."

**Also found while reading the primary source, not yet acted on then:** VCE's own list of crops
this applies to is "Tomatoes, Green Peppers, **Lima Beans**" — the app's code only ever checked
`cropKey === 'tomato' || cropKey === 'pepper'`. Lima Beans has never been included. Flagged to the
user as an open item; complicated by the fact that the app's crop dropdown has only a generic
"Beans & peas" option, not a specific Lima Beans entry, so a correct fix means adding a new crop
entry, not just adding a string to an array. **Still open — not resolved by this session's later
decision, since the split rule this crop list fed into no longer exists (see below).**

### The bigger question: is VCE's rule even the right rule to be citing here at all?
User then asked whether "fertilizer" in the VCE passage means a blended product (10-10-10) or an
N-only source like calcium nitrate — a genuinely important distinction given this calculator's
architecture. Read the full VCE document and confirmed: **it means a blended product.** Signals in
the text itself: the line immediately above the exception says "broadcast the recommended amount
of fertilizer" (describing the single blended grade a soil test report recommended in VCE's
original paradigm); the document points to a "Fertilizer Substitution Table" (only meaningful for
a specific N-P-K grade, not a pure N source); and the same document's separate "Organic
Fertilizers" section explicitly treats N, P, K, Ca, and Mg as individually-sized components as an
*alternative* to "the Fertilizer Recommendation on your Soil Test Report" — a contrast that only
makes sense if the main recommendation is one blended product.

At this point a citation-accuracy fix was proposed (make the note transparent that this was an
*adaptation* of VCE's blended-product guidance to a single-nutrient system, not a literal
restatement) — this fix was **not implemented**, since the next exchange overtook it entirely.

### Sourcing detour: user recalled "UMD says full amount at planting + half at fruit set" —
### turned out to be Rutgers, not UMD
User asked to check CLAUDE.md first, suspecting this had come up before — searched thoroughly,
found related-but-different content (the already-documented Rutgers FS626-sourced normal
tomato sidedress schedule: 2 lbs/1,000 sq ft preplant + two 1.0 lb sidedress steps) but no prior
resolution of this exact question. Searched UMD Extension's actual tomato guidance directly and
found it **did not match** what the user described — UMD's general consumer guide says the
opposite (avoid heavy pre-plant N, use a starter amount, sidedress after fruit set), and a
different UMD-affiliated source described a half/half split that would have matched VCE, not "full
amount at planting." Reported the conflict honestly rather than picking one. User then corrected:
they'd meant **Rutgers**, not UMD — "we at one point used the Rutgers recommendation."

Fetched Rutgers FS626 (njaes.rutgers.edu/FS626/) in full. Confirmed: Table 2 lists tomatoes as
"1.0 lbs at first bloom followed 4 weeks later with another 1.0 lbs" — exactly matching what's
already coded — and Rutgers frames all sidedress N as **supplemental**, additional to whatever the
soil-test fertilizer recommendation already provided. **Critically: nowhere in the Rutgers
document does a P/K-based split-preplant exception exist at all.** Rutgers' entire framework is:
apply the full preplant amount once, then add Table 2's fixed supplemental sidedress — no
exception for P/K level.

### The actual decision (user's reasoning, not a citation resolution)
User then made the point that actually resolves this, and it isn't about which source wins:

> "We have structured the vegetable garden calculator around the gardener applying individual
> N-P-K components as well as micronutrients as needed. The quantity of each component to be
> applied is calculated separately. The VCE guidance is for complete or blended fertilizers wherein
> it makes sense to reduce N application to avoid over use of P or K. Applying individual
> components avoids this problem entirely."

This is correct and decisive: VCE's split-preplant rule exists *specifically* because a blended
product forces N and P/K to move together — reducing the dose is the only way to avoid
over-applying P/K that's already High/Very High, and N gets reduced as an unavoidable side effect.
This calculator's single-nutrient architecture removes that coupling by design: nitrogen is a
separate, N-only product; P and K are each sized independently by the Nutrient Application Plan's
own section (skipped entirely when already Adequate/High, per `renderNutrientStatusPanel()`).
There is no mechanism by which applying more nitrogen causes over-application of phosphorus or
potassium in this system. VCE's stated reason for the split does not transfer.

**Decision: the P/K-High split-preplant rule is retired for tomato/pepper.** Every crop, tomato and
pepper included, now always gets the full preplant amount followed by the standard
`SIDEDRESS_GUIDE`-based supplemental schedule (Rutgers FS626-sourced), regardless of P or K rating.
This is not "Rutgers overrides VCE" — it's that VCE's rule was never really about nitrogen timing
in the first place; it was a workaround for a blended-fertilizer constraint that no longer exists
in this tool.

### Implementation
Removed `pRatForSplit`/`kRatForSplit`/`pHigh`/`kHigh`/`pkSplitApplies`/`ppHighPKNote` entirely from
`calcGarden()`. Step 1 (Preplant) unconditionally shows the full `lbsTotal`; the sidedress branch
(`if (guide.apps.length > 0)`) unconditionally runs the standard schedule with no P/K-based
branching. Confirmed no other code in `calcGarden()` depended on the removed variables. **Left
untouched, correctly out of scope:** `fertChooserHTML()` (the Lawn tabs' "help me choose a
fertilizer" helper) has its own, unrelated `pHigh`/`kHigh` locals — Lawn still recommends one
blended N-P-K product, so VCE's original reasoning genuinely still applies there; this is not the
same situation as Vegetable Garden and was correctly left alone.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Retired the VCE Note 19 P/K-High split-preplant rule for tomato/pepper entirely — every crop now always gets the full preplant amount + standard Rutgers-sourced supplemental sidedress, regardless of P/K level. This supersedes the same-day earlier fix that had corrected the display bug in that rule, which is now moot since the rule itself is gone. (v3.0, 2026-08-02) |
| `CLAUDE.md` | this entry |

### Still open
- **Lima Beans** are named by VCE alongside tomatoes/peppers but have never been in this app's
  crop-check logic — moot for *this* rule now that it's retired, but Lima Beans may still warrant
  its own crop entry (distinct from the generic "Beans & peas") for its own feeding-level/sidedress
  data independent of this decision. Not addressed this session.

---

## Session Updates — August 2, 2026 (cont.) (Vegetable Garden intro copy — added a single-nutrient lead-in, then removed a stale sourcing sentence)

### Lead-in paragraph added (v3.1)
User asked for a few lead-in sentences at the top of the Vegetable Garden tab explaining the
benefit of single-component fertilization — specifically that different vegetable varieties have
very different nitrogen needs, and a complete N-P-K fertilizer's fixed ratio means matching one
nutrient's need almost always over- or under-supplies the other two. Proposed two draft lengths;
user chose the longer one. Added directly above the tab's existing sourcing sentence, so the tab
now opens with *why single-nutrient fertilization works this way*, then *what it's sourced from*.

### Stale sourcing sentence removed (v3.2)
User flagged the sentence right after it — "Based on VCE Soil Test Note 19 (SPES-687P). P, K, Ca,
Mg, S, and micronutrient ratings carry over automatically from the Soil Test tab — nothing to
re-enter." — as old copy from an earlier version of the calculator, inaccurate now that more
micronutrients are individually carried over and handled than this vague "and micronutrient
ratings" catch-all phrase implies. Removed entirely (not reworded) per the request. The tab now
opens with only the new single-nutrient lead-in paragraph before Step 1 (bed size).

**Note:** Flower Garden has its own, separate sourcing sentence ("Based on VCE Soil Test Note 19
[...], VCE Publication 426-200 [...], UMD Extension, Rutgers NJAES, and NC State Extension...") —
correctly left untouched, since the user's request was specific to Vegetable Garden and that
sentence wasn't flagged as inaccurate.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Vegetable Garden tab intro rewritten: added single-nutrient-fertilization lead-in paragraph, removed a stale/inaccurate sourcing sentence about which values carry over (v3.2, 2026-08-02) |
| `CLAUDE.md` | this entry |

---

## Session Updates — August 2, 2026 (cont. 2) (App renamed again — "Soil Report Assistant" → "Soil Test Report Assistant")

### Rename
User requested changing the name to "Soil Test Report Assistant" (inserting "Test"). Found and
updated all four instances in `index.html`: the `<title>` tag, the header `<h1>`, the About tab's
hero `<h2>`, and the JS that constructs each tab's dynamic `document.title`. Confirmed zero
remaining instances of the old name (case-insensitive check too) and confirmed no other string
elsewhere in the file referenced it. Tagline ("No more guessing what to feed your lawn or garden")
unchanged. v3.3.

Then updated `README.md` (1 instance — the top-level title) and this file (4 instances — the
top-level title, the intro paragraph, the Files table's `index.html` entry, and the rename-history
line) to match, rather than leave the reference docs out of sync with the app itself — the same
category of drift this project has repeatedly caught in the other direction (docs describing
something the app no longer does). Preserved rename history rather than overwriting it: the app
has now been renamed twice ("VCE Lawn & Garden Care Calculator" → "Soil Report Assistant" on July
26, 2026 → "Soil Test Report Assistant" on August 2, 2026), and both this file's intro and its
Files table now say so explicitly instead of only showing the current name.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Renamed "Soil Report Assistant" → "Soil Test Report Assistant" in all four instances (title tag, header, About tab heading, dynamic per-tab title) (v3.3, 2026-08-02) |
| `README.md` | Title updated to match |
| `CLAUDE.md` | this entry; title, intro, and Files table updated to match, with rename history preserved |

---

## Session Updates — August 2, 2026 (cont. 3) (Favicon added — a wheelbarrow icon, and a pre-existing conflicting placeholder found and removed)

### Favicon conversion
User supplied a wheelbarrow graphic (green bucket, black wheel/handle, white background,
2000×2000 PNG) and asked for it to become the site's favicon. Processed with Pillow: made the
white background transparent, cropped to the actual artwork's bounding box (the original had a
lot of empty margin that would have made the icon look tiny at favicon scale), then padded back a
small deliberate margin before squaring it off.

**Checked legibility at real size before finalizing**, rather than assuming a detailed image would
downsize cleanly — rendered the 16×16 and 32×32 outputs at actual pixel scale (upscaled with
nearest-neighbor for inspection, not smoothed) and viewed them directly. The wheel and green
bucket shape hold up clearly at both sizes; the thin diagonal handle line gets faint at 16×16,
expected for a thin-line element at that scale, but the icon still reads as itself.

### Embedded as a data URI, not a separate file — and a real conflict found while doing it
Consistent with this project's single-self-contained-HTML-file design (no external assets), the
favicon is embedded directly as `data:image/png;base64,...` in two `<link>` tags — 32×32 for
browser tabs, 180×180 `apple-touch-icon` for iOS home-screen bookmarking (relevant given the
Master Gardener rollout is mobile-facing).

**While inserting these, found the file already had an older placeholder favicon** — a small green
leaf icon (likely auto-generated at some earlier point, never previously noticed or documented) —
sitting via two separate `<link rel="icon">` / `<link rel="shortcut icon">` tags further down in
`<head>`, after the `<title>` tag. Left in place, this would have meant two competing favicon
declarations in the same document with unpredictable results depending on which one a given
browser honored. Removed the old pair entirely so there's exactly one, unambiguous favicon
declaration now. This predates any documented entry in this file — it's unclear when it was added
or by whom; noting its removal here for the record since nothing else does.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Wheelbarrow favicon added as embedded data URI (32×32 `icon`, 180×180 `apple-touch-icon`); removed a previously-undocumented placeholder leaf favicon that would have conflicted with it (v3.4, 2026-08-02) |
| `CLAUDE.md` | this entry |

---

## Session Updates — August 2–3, 2026 (Catch-up entry: v3.5 through v4.2 — second-tier dead-code check, meta description, app rename, nutrient reorder, nitrogen sourcing, Lime/Plant Type button cleanup, Lime card rewording, Flower Garden lime-type reconciliation, Zn/Cu/B/P/Mg amendments)

This entry covers eight versions' worth of work that landed without an intervening CLAUDE.md
update — recorded here together, in order, rather than left undocumented.

### v3.5 — Second-tier dead-code check (28 single-reference functions): clean, no changes
Ran the "count == 2" bucket from the dead-code audit process (functions referenced exactly once
elsewhere, deliberately not auto-flagged as suspicious the way zero-reference functions were).
Checked all 27 remaining candidates individually — every one had a genuine call site (an
`onclick`/`onchange` attribute, or in `watchTarget`'s case, a legitimate nested-helper pattern
inside `applyGlossaryToStatic`). Verdict: clean, nothing removed. Logged as a real result in its
own right — confirmation that treating single-reference functions differently from zero-reference
ones (per the original audit design) was the right call, not just excess caution.

### v3.6 — Meta description added
Proposed four length-checked candidates (~150–168 chars), user chose the one leading with the
user's actual action ("Enter your VCE or Waypoint soil test results...") and naming all four
garden types explicitly rather than collapsing to "gardens." Added to `<head>`.

### v3.7 — Vegetable Garden nutrient list reordered to match Waypoint's report order; Calcium
### removed entirely
User request: reorder the Nutrient Application Plan's P/K/Other Nutrients section to N, P, K, Mg,
S, B, Cu, Mn, Zn, Fe (Waypoint's own sequence) and drop Calcium, since Lime (covered in its own
section above) already addresses it. `renderNutrientStatusPanel()` is shared between Vegetable
Garden and Flower Garden — user confirmed applying to both rather than only the tab they'd
originally named. Reordered the `nutrients` array, removed the Ca entry (confirmed no separate
amendment-data structure existed for it, so nothing else was orphaned), and rewrote the section's
intro paragraph to state both the new order and the Ca exclusion explicitly instead of leaving
stale wording ("All ratings (P, K, Ca, Mg, S...)").

### v3.8 — Nitrogen's "not soil-tested" explanation now leads with VCE's own quoted language
Following the Note 1 (452-701) research, added *"No soil test is performed for nitrogen because
this element is too mobile in the soil for laboratory results to be useful"* — VCE's own words,
verified directly from the primary source, not a paraphrase — to all 7 places the app explains why
N isn't derived from a soil test: 6 field hints (Vegetable Garden and Flower Garden, VCE and
Waypoint variants each) plus the Soil Test tab's "Nitrogen Recommendation Check" card, which
previously stated the VCE-vs-Waypoint difference without explaining why. Existing practical
elaboration (leaching within a day or two of rain) kept as supporting detail after the sourced
statement, not replaced.

### v3.9 — Lime Recommendation and Plant Type & Fertilizer Program cards' navigation buttons
### removed (completing a cleanup started in an earlier session)
User reported these two buttons "reappeared" on the Soil Test tab; investigation found neither had
actually regressed — the Lime Recommendation card's button was deliberately kept during the
pH/Buffer Index cleanup ("the one card with an actionable destination"), and the Plant Type card
had been explicitly scoped out during the P/K card cleanup ("outside the scope of what you
flagged"). User confirmed finishing the job: removed both, across all purpose branches (Lime
Recommendation: vegetable/flower, shrub, lawn already clean; Plant Type: vegetable/flower/shrub).
Cleaned up three now-orphaned variables left behind (`destTabForLime`, `destTab`, `destBtn`) rather
than leave dead assignments next to the dead-code audit work from the same week. Confirmed
`goBtn()`/`limeGoBtn` still legitimately needed by Base Saturation, correctly out of scope.

### v4.0 — "Lime for Your Bed" card reworded; lime type carried over for Vegetable Garden
User found the card's phrasing confusing: *"Total: 0.4 lbs in 1 application of up to 5 lbs/100 sq.
ft. (established bed limit)"* — one sentence mixing the actual amount to apply with an unrelated
per-application safety ceiling, with no clear signal which number meant what. Rewritten as a direct
instruction ("Apply **0.4 lbs** of lime to your bed") followed by a separate clarifying line
explaining the cap only when relevant. Applied to both Vegetable Garden and Flower Garden's
identical cards. Also found and fixed a real content gap while in there: Vegetable Garden's inline
lime card never read `st-lime-type` at all, unlike the Soil Test tab's own Lime Recommendation
card — added it.

### v4.1 — Flower Garden's lime-type guidance reconciled with the report's own stated type
### (not just inferred from Mg)
Follow-up question: since dolomitic lime was specified on a report, could that be carried over to
Flower Garden's card too? Flower Garden already had a *smarter* type suggestion than Vegetable
Garden's (inferring dolomitic specifically when Mg tests Low, rather than just echoing the report)
— rather than replace that with a naive echo of `st-lime-type`, reconciled the two signals: report
type is the authoritative source when given, but the two can genuinely disagree (report says
Agricultural/calcitic while Mg still rates Low), which is surfaced as an explicit warning rather
than silently resolved either direction. Simulated all six practical combinations (Dolomitic/
Agricultural/unstated × Mg Low/adequate) to confirm no contradictory message in any case.

### v4.2 — Zinc and Copper amendments added (previously nonexistent); Boron/Phosphorus placement
### notes added; Magnesium product options expanded
User forwarded a real Waypoint report showing the lab's own report
notes name specific products and give numeric targets for nutrients the app was not actually using:
`Zn: []` and `Cu: []` were completely empty in `NUTRIENT_AMENDMENTS` — Low ratings for either
nutrient fell through to "VCE publishes no specific home-garden product or rate," which is true of
VCE, but the *Waypoint* report the user was looking at explicitly says "broadcast zinc sulfate" /
"broadcast copper... using copper sulfate" and gives an exact numeric target right there on the
page the app already reads P/K/Mg/S/Mn targets from.

Verified elemental percentages directly rather than compute from memory alone:
- Zinc Sulfate has two common commercial forms with meaningfully different concentrations —
  monohydrate (35–36% Zn) and heptahydrate (20–22% Zn) — confirmed across multiple independent
  retail/industrial sources; added both as separate entries since the app can't know which form a
  user's product label states.
- Copper Sulfate Pentahydrate is consistently 25% Cu across every source checked — simpler, one
  entry.
- Magnesium Oxide: garden-grade product listings consistently show 55–57% Mg (vs. ~60% for
  chemically pure MgO) — added at 56%.
- K-Mag / Sul-Po-Mag: confirmed via multiple sources to be a **combined** K+Mg+S product
  (langbeinite, ~22% K₂O, ~11% Mg, ~22% S), not a Mg-only source as the name might suggest —
  flagged this explicitly in its own note, recommending it specifically when K and/or S are *also*
  low, and steering away from it (toward Epsom salts/Mg oxide) when K already rates Adequate/High,
  so choosing it for Mg alone doesn't silently over-supply potassium.

New entries sourced to **Waypoint Analytical's own report guidance**, not VCE, since VCE genuinely
publishes no rate for Zn/Cu — kept the citation honest about which lab's guidance is being used
rather than attributing it to VCE. Added the same "may be applied more efficiently in a band near
the plant" placement tip (from the same Waypoint report) to all three Phosphorus entries, and an
explicit "do not concentrate in a band near the plant" warning to both Boron entries — the
existing Boron notes already recommended dissolve-and-pour methods specifically because of boron's
narrow toxicity margin, so this makes an already-implied precaution explicit rather than adding a
new idea.

**Found and fixed a real pre-existing inconsistency while wiring the new Mg entries in:** the
target-based "Epsom Salts (sized to report target)" option was missing the
`limeConditional`/`dolomiteOnly` flags its flat-rate sibling correctly has. Since
`supersededByLime` is evaluated against whichever amendment option is currently *selected* in the
dropdown (not once per nutrient), switching between the two Epsom Salts variants would have given
different "your lime already covers this" behavior for the literal same product depending only on
which sizing method was chosen. Added the missing flags so all four Mg options (flat Epsom salts,
target Epsom salts, Mg oxide, K-Mag) behave consistently.

Verified the target-calc formula (`lbsProduct = (target * hundredths) / (a.pct / 100)`) produces a
sane real-world amount using the actual report's own Zn target — came out to roughly a quarter
ounce for a 100 sq ft bed, consistent with how small the existing Mn/B corrections already are in
this app, not an outlier.

**Still open:** a second request from the same message — displaying computed application amounts
in lbs+oz instead of decimal lbs, and confirming volume already mostly uses `fmtMeasure()`'s
existing tsp/tbsp/fractional-cup logic — is paused pending the user's answer on scope (computed
amounts only, vs. also the abstract per-100-sq-ft rate labels). Roughly 40–46 call sites identified
via `fmt(...) + 'lbs'`-pattern search as candidates once scope is confirmed; no changes made yet.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Eight versions of accumulated work (v3.5–v4.2) documented in this single catch-up entry — see above for the full breakdown of each |
| `CLAUDE.md` | this entry |

---

## Session Updates — August 3, 2026 (cont.) (Instructions cleanup — a stale gotcha removed, sample buttons relabeled, a navigation button added to the How to Use card)

### v4.3 — Removed an instruction that described a scenario which can no longer happen
User flagged a specific line in the universal on-ramp instructions ("Enter at least your P and K
values before trying to continue... clicking it early just leaves you on this tab") as no longer
valid. Verified why before removing it, rather than deleting on request alone: this instruction was
warning about the Plant Type & Fertilizer Program card's premature "Continue" button — a button
that appeared before P/K was entered and silently did nothing if clicked. That button was removed
entirely in the v3.9 cleanup (same week). With no premature button left to click, the scenario the
instruction described can't occur anymore, so the warning itself is now describing a problem that
doesn't exist. Confirmed no other place in the About tab repeats the same now-stale gotcha before
removing it.

Also this version: added a "Pre-fill with Example Reports:" caption above the sample-report button
row (previously the four sample buttons plus Start Over sat directly below the card header's
divider with no label explaining what they were), and renamed all four sample buttons for
consistency and clarity about which lab each one represents: "Lawn Sample" → "Lawn-VCE", "Flower
Garden Sample" → "Flower Garden - Waypoint", "Vegetable Garden Sample (Waypoint)" → "Vegetable
Garden-Waypoint", "VCE Vegetable Garden Sample" → "Vegetable Garden-VCE". Restructured the
surrounding markup so the `role="toolbar"` wraps only the buttons themselves, with the new caption
sitting outside it as a heading rather than inside the toolbar region — slightly better
accessibility structure than before, not just a visual change.

### v4.4 — "Back to Soil Test Report" button added to the About tab's "How to Use This Calculator"
### card
Every calculator tab already has this exact button at the bottom (added earlier this project);
the About tab's own instructions card didn't. Added the same button, same wording, same
`activateTab('soiltest')` call — proposed reusing the established phrase rather than the user's
suggested alternative wording, specifically so this reads as the same action already used
everywhere else in the app rather than introducing new phrasing for an identical action.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Removed a stale "P/K before continuing" instruction (the scenario it warned about no longer exists); added "Pre-fill with Example Reports:" caption and renamed all four sample buttons (v4.3); added "Back to Soil Test Report" button to the How to Use This Calculator card, matching the wording already used on every calculator tab (v4.4) |
| `CLAUDE.md` | this entry |

---

## Session Updates — August 4, 2026 (CRITICAL FIX — Waypoint numeric target amendments were calculating 10x too much product)

### The bug
User submitted a screenshot from real use: Waypoint report P₂O₅ target of 4.5 (lbs/1,000 sq. ft.,
per both the report and the field's own label), an 870 sq. ft. bed, Triple Superphosphate (0-46-0)
selected — app showed **85.11 lbs**. Verified by hand before responding: the mathematically correct
amount is **8.51 lbs**. Exactly a factor of 10 off.

**Root cause:** in `renderNutrientStatusPanel()`'s `calc === 'target'` branch, the user-entered
Waypoint target value was read with `parseFloat(targetRaw)` and used directly, with no unit
conversion, in a formula (`(target * hundredths) / (a.pct / 100)`) where `hundredths` (`area/100`)
assumes every other quantity in the function is already in a lbs/100 sq. ft. basis. The target
field is *always* a Waypoint value (VCE reports use the separate flat-rate path instead, never
`calc:'target'`), and Waypoint reports state this figure in lbs/1,000 sq. ft. — the same
lbs/1,000-to-lbs/100 conversion already applied elsewhere in this codebase for other Waypoint
figures (N recommendation, lime recommendation) was simply never applied here.

**Scope of impact:** every nutrient that can use a Waypoint numeric target — Phosphorus,
Potassium, Magnesium, Sulfur, Zinc, Copper, Manganese, Boron — on both Vegetable Garden and Flower
Garden, since `renderNutrientStatusPanel()` is shared between them. This has been live since the
inline Waypoint-target-entry feature was first built earlier this same session; not something that
predates this project's more recent work, but real nonetheless, and exactly the kind of dosing
error this app exists to prevent rather than cause.

### The fix
One-line change at the point the target is parsed:
```js
var target = targetRaw ? ((parseFloat(targetRaw) || 0) / 10) : 0;
```
No other call site needed changing, since every downstream calculation already correctly assumes a
lbs/100 sq. ft. basis — the bug was purely in the unit of the input, not the formula that consumes
it. Verified: (a) this is the only place this exact target-parsing pattern exists in the file (no
second copy sharing the same bug), (b) the *other* `target` variable in the codebase
(`soilTestTargetTab()`, used for tab-routing) is a completely unrelated naming coincidence, not a
second instance of the same issue, and (c) re-running the exact numbers from the user's screenshot
through the corrected formula produces exactly 8.51 lbs.

### Process note
This was found through real use, not a code-review pass — the same pattern as several of this
project's most consequential bugs (the Cool/Warm duplicate-plan bug, the Lima Beans/Rutgers sourcing
questions). A user actually entering their own real report's numbers and checking the output
against hand arithmetic caught something that static review of the formula, in isolation, would
likely have missed, since the formula itself is correct — the bug was entirely in what unit its
input was actually in.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | **Fixed a 10x overdose bug** in Waypoint-target-based nutrient amendments (P, K, Mg, S, Zn, Cu, Mn, B) on Vegetable Garden and Flower Garden — the target value was used without converting from the report's lbs/1,000 sq. ft. to the lbs/100 sq. ft. basis the rest of the formula assumes (v4.5, 2026-08-04) |
| `CLAUDE.md` | this entry |

---

## Session Updates — August 4, 2026 (cont.) (Executing the Calculation Audit Plan — one real dosing gap fixed, one documentation error corrected, one syntax error caught by validation, one ambiguous label clarified)

### Boron liquid-method: real missing calculation, not just missing wording
Part 1 of the audit plan led to checking whether the Boron liquid-dilution note ("1 tbsp per
gallon of water, applied per 100 sq. ft.") was actually being scaled to the user's bed size. It
wasn't — it used `calc:'none'`, a flat unscaled note, meaning anyone with other than exactly
100 sq. ft. had to do the scaling themselves. The generic `calc:'none'` wrapper text ("no specific
rate published") was also factually wrong for this entry specifically, since UMD does publish a
rate — it just wasn't being applied. Added a new `calc:'liquid'` type that scales tbsp and gallons
to the user's actual bed size like every other amendment on the tab. Verified: 300 sq ft → 3.0 tbsp
in 3.0 gallons; 100 sq ft → 1.0 tbsp in 1.0 gallon.

### A documentation error in this file, found and corrected
Re-verifying the Lime golden test case from an earlier entry (40 lbs/1,000 sq ft, 90% CCE,
8,000 sq ft, 40 lb bags) produced 9 bags, not the "8 bags" previously recorded here. Traced the
discrepancy: the original hand-check divided 355.6 by 50 (the per-application lbs cap) instead of
40 (the actual bag size) — an arithmetic slip in the original verification, not a code bug. The
formula (`Math.ceil(totalLbs / bagSize)`) was always correct. Corrected the earlier entry in place
rather than leave a wrong "verified" number standing, and flagged it as its own lesson: a number
labeled verified in this file should be re-derivable by someone else, not trusted because of the
label.

### A real syntax error introduced and caught by validation, not shipped
While clarifying the WIN% field label to specify "the bag's Guaranteed Analysis," the JS-generated
version of this label (used for Custom-mode application slots) used a literal apostrophe inside a
single-quoted JS string (`'...bag's Guaranteed Analysis...'`), which prematurely closed the string
and threw a syntax error that would have broken the entire app. Caught immediately by the
post-edit `node --check` validation step (not by inspection), fixed with a proper `\u2019`
character instead of a literal apostrophe. The two *other* occurrences of the same clarified text
were untouched by this issue, since they're static HTML label text, not JS string content — a good
reminder that the same-looking text can be safe or unsafe entirely depending on what's holding it.

### WIN% field label clarified — a real risk, not a code bug
Hand-verified `detectProgram()`'s WIN%/Program classification against realistic fertilizer label
examples (29-3-4 with a 4.5%-of-product WIN figure → 15.5% of nitrogen → Program 2, matching VCE
430-011's 15–49% band; straight urea → Program 1). The formula is dimensionally correct, converting
a bag's raw "WIN % of total product" figure (how real Guaranteed Analysis labels state it) into
VCE's "WIN % of nitrogen" criterion. But the field label just said "WIN % (if listed on bag)" with
no indication of *which* of those two numbers to enter — a user who assumed the field wanted an
already-computed "% of my nitrogen that's slow-release" value, rather than the bag's raw printed
figure, would get a silently wrong Program classification with no way to notice. Clarified all
three occurrences to specify "the bag's Guaranteed Analysis... not a percentage you calculate
yourself."

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Boron liquid method now properly scaled to bed size (new `calc:'liquid'` type, replacing the flat, unscaled `calc:'none'` note); WIN% field label clarified in all three locations (v4.7, 2026-08-04) |
| `Calculation_Audit_Plan.md` | Part 1 fully checked off with findings recorded; Part 2's Lime and WIN% golden numbers added, including the bag-count correction |
| `CLAUDE.md` | this entry; corrected an arithmetic error in an earlier entry's "verified" lime bag count (8 → 9) |

---

## Session Updates — August 4, 2026 (cont. 2) (Calculation Audit Plan, continued — Part 2 and Part 3, all clean, including a self-caught false alarm)

Continued executing the audit plan into the remaining Part 2 items and the first Part 3 item. Every
check this round came back correct — a genuinely clean result, verified independently rather than
assumed, including one case where the discrepancy turned out to be in the auditor (this session),
not the app.

- **Cool/Warm auto-plan** (tall fescue, 5,000 sq ft, 3.0 lb N target, 32-0-8, no WIN): 5
  applications, 46.875 lbs total product — confirmed two independent ways (the app's own formula
  chain, and a from-scratch total-N-needed-for-the-whole-lawn calculation), both landing on the
  same number.
- **Shrub canopy area**: standard circle-area formula, 2× canopy doubling matches VCE Note 20.
- **Shade + clipping combination**: confirmed shade applies first (multiplicatively), clipping
  credit is computed from the already-shaded value (not the original), then subtracted — and this
  reproduced the exact 0.8–1.1 lb range already documented earlier this session for the same
  example, a successful *re*-verification rather than a first-time check.
- **`fmtMeasure()` tsp/tbsp/cup transitions**: first hand-check appeared to disagree with the app
  (1.6 tbsp expected, 1.5 shown). Before flagging it, re-read the actual current function instead
  of trusting memory — found I'd recalled an *older* version's rounding rule (nearest 0.1 tbsp)
  that no longer matches the current implementation (nearest 0.5 tbsp, matching real
  measuring-spoon increments). All four spot-checked values confirmed correct once verified against
  the actual current code. Recorded deliberately as its own lesson: a hand-calculation that
  disagrees with the app isn't automatically proof the app is wrong — the assumption doing the
  verifying needs the same scrutiny as the thing being verified.
- **Cross-tab consistency for `renderNutrientStatusPanel()`**: verified live on the deployed site,
  not assumed from shared code — identical inputs on Vegetable Garden and Flower Garden (P Low, K
  Medium, Mg Low, 200 sq ft, Calcium Nitrate) produced the identical 2.00 lbs Epsom Salts amount on
  both tabs.

**Still open:** Cool/Warm custom-plan (multi-slot) season totals — the one remaining Part 2 item —
plus the rest of Part 3 (`calcLimeForBed()` called identically from all four tabs that share it)
and all of Part 4 (extra scrutiny on this session's newest code: Zn/Cu, Mg oxide/K-Mag, the
reordering work, lime-in-lawns).

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | No changes this round — verification only |
| `Calculation_Audit_Plan.md` | Part 2 nearly complete (only custom-plan season totals remain); Part 3's first item verified |
| `CLAUDE.md` | this entry |

---

## Session Updates — August 4, 2026 (cont. 3) (Calculation Audit Plan — completed Parts 2, 3, and 4)

Completed the remaining items in the audit plan. Working environment reset partway through this
session (the `/home/claude/work` directory was cleared) — recovered cleanly from the persisted
files in `/mnt/user-data/outputs/`, confirmed the restored `index.html` matched the last exported
v4.7 exactly before continuing, no work lost.

- **Cool/Warm custom-plan season totals**: verified a 2-slot scenario by hand. **Caught my own
  arithmetic error mid-check** — expected the wrong K total by conflating N-delivered-per-1,000-sq-ft
  with product-delivered-per-1,000-sq-ft (two different bases). Redid the derivation correctly and
  confirmed the app was right the first time. This is the second time this same failure mode (my
  own hand-verification being wrong, not the app) showed up in this audit — worth treating as a
  standing risk in this process itself, not a one-off.
- **`calcLimeForBed()` cross-tab consistency**: the browser tool timed out mid-check, so pivoted to
  direct simulation instead — arguably the more rigorous method anyway, since it isolates exactly
  what needed checking (whether each tab's surrounding code derives equivalent arguments from
  equivalent real-world inputs) without depending on a live page. Verified the same real-world
  scenario (40 lbs/1,000 sq ft, 100% CCE, 1,000 sq ft, 40 lb bags) produces the same real-world
  total (40 lbs, 1 bag) whether computed via the Lawn tab's native basis or the Garden tab's —
  confirming physical agreement across genuinely different unit conventions, which is the
  meaningful version of "consistency" here, not a naive same-inputs check.
- **Part 4 (newest-code scrutiny)**: assessed rather than re-derived from scratch — Zn/Cu/Mg
  additions were already sourced and verified at build time earlier this session; the nutrient
  reordering was confirmed to be array-order-only (amendments key off nutrient symbol, not
  position); lime-in-lawns was already hand-verified when built, and the one place that original
  verification was actually wrong (the bag count) was the same error already caught and fixed
  earlier in this same audit. Recorded as "substantially covered by build-time verification, now
  confirmed to have held up" rather than claiming a fresh check that would have just re-derived the
  same conclusion.

### Overall audit status: complete
Every item across all four parts of `Calculation_Audit_Plan.md` is now checked. Net result: one
real, fixed dosing gap (Boron liquid method), one corrected documentation error (lime bag count),
one clarified ambiguous field label (WIN%), one caught-before-shipping syntax error, and two
instances of the auditor's own hand-verification being wrong rather than the app — all recorded in
the plan document itself as the actual outcome, not just "everything passed."

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | No changes this round — verification only |
| `Calculation_Audit_Plan.md` | All four parts fully checked off with findings recorded |
| `CLAUDE.md` | this entry |

---

## Session Updates — August 4, 2026 (cont. 3) (Calculation Audit Plan — remaining items closed out; browser tool outage handled by falling back to direct code extraction)

Closed out the plan's remaining open items: Nitrogen preplant amount (tomato, 32-0-8, 200 sq ft →
1.25 lbs, cross-checked independently), Bone Meal flat-rate multiplication, a second target-based
amendment number (Copper Sulfate), and `calcLimeForBed()`'s cross-tab consistency — verified that
the *same real-world scenario* produces the same real-world total whether expressed in the Lawn
tab's native basis or the Garden tab's, since a naive "same raw inputs" test doesn't apply across
tabs that use genuinely different native units.

**Tool outage handled without stopping the audit:** the browser tool became unresponsive partway
through this pass. Rather than treat that as blocking, continued verifying against the actual
current code via direct function extraction and Node.js execution (same technique used earlier
this session to catch the duplicate-plan bug), which still tests the real implementation, just
without live browser interaction. The one place this left a real gap: the sidedress-schedule check
for corn/cucumber/squash was done via internal-consistency reasoning against the app's own
feeding-level data rather than re-fetching Rutgers FS626 directly — flagged explicitly in the plan
document as a weaker verification than the rest, not silently treated as equivalent.

**A genuine observation surfaced, not clearly a bug:** corn (heavy feeder) and cucumber (medium
feeder) both total exactly 4.0 lbs N/1,000 sq ft across the season — corn front-loads it into one
larger sidedress application, cucumber splits the same total into two smaller ones. The
heavy/medium classification doesn't show up as strict total-N ordering in this pairing. Recorded
as a flagged pattern for a future primary-source re-check, not resolved either way.

**Net status:** every item across all four parts of the Calculation Audit Plan is now checked off.
Total findings from the full audit: one critical dosing bug (the original 10x target-conversion
error), one genuine missing calculation (Boron liquid method not scaling to bed size), one
ambiguous field label with real silent-error potential (WIN%), one documentation error in this
file's own prior "verified" numbers (lime bag count), one syntax error introduced and caught by
validation before shipping, and one flagged-but-unresolved pattern worth a future look
(corn/cucumber N totals). Five of six required an actual fix; all are in `index.html` v4.7 or this
document.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | No further changes this round |
| `Calculation_Audit_Plan.md` | All four parts fully checked off; net assessment recorded |
| `CLAUDE.md` | this entry |

---

## Session Updates — August 4, 2026 (cont. 4) (Maintenance Fertilizing & Retesting card added; nutrient rating dropdowns corrected for both labs)

### "Maintenance Fertilizing & Retesting: Years 2–3" card added to the About tab
Followed up on the earlier years-2/3 research thread (Chesterfield county agent's guidance, VCE
Soil Test Note 1 / 452-701, VCE Soil Test Note 17 / 452-717's "Lawn Maintenance" section, and DCR's
Nutrient Management Regulations) by turning the discussion into a new card, positioned above "Soil
Test Ratings Explained." Deliberately written to distinguish what's directly sourced from what the
calculator is reasoning through in the absence of specificity, rather than hedge defensively:

- **Nitrogen** — apply every year, no exception, for all three garden types; directly stated
  (Note 1: no soil test is performed for N at all).
- **Lawns** — correct P/K/lime once per current test, hold 2–3 years, don't repeat annually;
  directly stated (Note 17's "Lawn Maintenance" section is the clearest source found on this whole
  question). The Very-High/no-fertilizer-recommended case gets a 1-year retest instead of the full
  2–3, and applying P when already High/Very High is a defined regulatory limit, not just advice
  (DCR Nutrient Management Regulations).
- **Vegetable and flower gardens** — same pattern applied by inference, explicitly labeled as such:
  no garden-specific equivalent to Note 17 was found, and the general Note 1 policy ("may be used
  for two to three years") is itself ambiguous between "reapply annually" and "correct once, hold"
  — resolved by reasoning that 452-701 is likely describing repeat-use for replanted/harvested
  crops while Note 17's lawn-specific language addresses turf's different removal pattern. Named
  the harvest-removal difference explicitly as the one real point of uncertainty, rather than
  smoothing it over.

**Consistency pass across the app:** found four other places (Base Saturation's card, the P/K
"Optimum" messages, and the Flower/Garden fertilizer-chooser tool) stating "retest in 3–4 years"
with no independent source of their own for that number — aligned all four to "2–3 years" to match
the new card's sourced language. Checked pH cards and the Lime Recommendation card too; both
already consistent.

Title later revised at user request to **"Maintenance Fertilizing & Retesting: Years 2–3."**

**Still open:** the two Google Docs (Warm/Cool Season Guides) the county agent specifically
referenced remain inaccessible — both returned "Permission denied" via direct URL and export
attempts, not a format issue but a sharing-settings issue. The garden section of the new card is
flagged as inference specifically because these two documents, if accessible, might resolve that
ambiguity directly rather than leave it as a reasoned extension.

### Nutrient rating dropdown scales corrected for both labs — a real, wide-reaching accuracy bug
User asked to check all nutrient dropdowns against real report formats, having noticed Waypoint's
options looked wrong. Confirmed against a real Waypoint report (used earlier this
session): every nutrient row uses the same 5-category scale (Very Low/Low/Medium/Optimum/Very
High) — but the app only offered this full scale for P/K/Ca/Mg. Sulfur, Boron, Copper, Iron,
Manganese, and Zinc were collapsed to 4 categories ("Low/DEF" merging Very Low+Low, "High/Very
High" merging High+Very High) — meaning a user with that exact real report (which rates both Boron
and Copper "Very Low" on both samples) had no way to enter what it actually said.

**Checking the VCE side surfaced a second, separate bug in the opposite direction.** Three
independent sources — VCE's own "Your Soil Test Report Simplified" (SPES-384), Piedmont Master
Gardeners, and a JCC Extension guide — all confirm VCE actually rates these same six nutrients on
just **two** categories: Sufficient or Deficient. The app was showing 4 categories on the VCE side
too. So the fix went both directions: **VCE narrowed to 2 categories (Deficient/Sufficient);
Waypoint expanded to the full 5** — for Zn, Mn, Cu, Fe, and B. Sulfur got the same 5-category
Waypoint expansion but no VCE optgroup added, since Sulfur has no VCE input pathway in this app at
all (confirmed by checking — there's no `st-s-rating-vce` field anywhere).

Replicated the exact working pattern already used for Calcium and Magnesium's canonical fields
(two `<optgroup>`s: "VCE / Virginia Tech" and "Waypoint Analytical") rather than inventing a new
structure — Magnesium's canonical field additionally had a third "VCE special" optgroup for
DEF/SUFF as a rare edge case on an otherwise L-/L/L+-graded nutrient, which clarified that DEF/SUFF
is the *primary* VCE scheme for the six micronutrients rather than a special case, the way it is
for Mg.

**Verified architecturally safe, not just visually correct, before calling it done:**
- Traced how `n.rating` is actually consumed in `renderNutrientStatusPanel()` — only ever through
  `nutrientRatingStatus()` for a binary low/adequate check, never displayed as raw text anywhere,
  so no separate display-label mapping was needed for the new codes.
- Found `nutrientRatingStatus()` was missing `'DEF'` from its low-set entirely — a real gap that
  would have silently misclassified an actual VCE "Deficient" rating. Fixed, and also removed
  redundant duplicate entries ('L'/'M'/'H' appeared twice) while confirming P/K/Ca/Mg's and
  Sodium's existing codes were unaffected by the cleanup.
- Confirmed `stSync()` (the function that copies a lab-specific dropdown's selection into its
  canonical counterpart) is fully generic — just copies `.value` with no hardcoded dependency on
  specific codes — so the new value schemes sync correctly with no special-casing required.
- Searched the sample-report prefill data and found six stale values still using the old collapsed
  codes (`'L'`, `'M'`, `'H'`) that no longer exist as valid options on the updated dropdowns —
  fixed by mapping each to its most faithful new-scheme equivalent (L→LO, M→ME, H→VH2) based on
  what the old collapsed label represented. This is an inference from the old code's meaning, not a
  re-check against the original source reports, and is noted as such.
- Hand-verified all 17 possible rating codes (old and new, across every nutrient) classify
  correctly via `nutrientRatingStatus()`.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Added "Maintenance Fertilizing & Retesting: Years 2–3" card to the About tab; aligned four other "retest in 3–4 years" mentions to "2–3 years" (v4.8–v4.9); corrected the rating scale for Zn/Mn/Cu/Fe/B (VCE: 2 categories; Waypoint: 5 categories) and Sulfur (Waypoint: 5 categories, no VCE path); fixed a missing `'DEF'` classification in `nutrientRatingStatus()`; corrected six stale sample-report codes (v5.0, 2026-08-04) |
| `CLAUDE.md` | this entry |

---

## Session Updates — August 4–5, 2026 (Catch-up: v5.1–v5.6 — sample-data SUFF bug, two new Waypoint lawn samples, PII scrub, favicon swap, and a substantially deeper Maintenance & Retesting card)

### v5.1 — Second wave of the same sample-data bug, found by the user post-deployment
After v5.0 shipped the Waypoint rating-scale fix, user deployed it and reported blank rating
dropdowns on the Waypoint Vegetable Garden sample (screenshot showed Cu/Fe/Mn rated "-"). Root
cause: the v5.0 sample-data cleanup had only caught the *obviously* invalid leftover codes ('L',
'M', 'H' — which don't exist in any current scheme) but missed `'SUFF'`, which is still a real,
valid code elsewhere (VCE side, canonical field) but is **not** part of the new 5-category Waypoint
scheme (VL/LO/ME/OP/VH2) — so any `-wp` field still holding `'SUFF'` silently failed to select
anything. Found 6 more instances this time via exhaustive validation (extracted and checked every
single Waypoint/VCE rating assignment in the file against its actual valid option list) rather than
searching for specific known-bad strings again, since that narrower method is exactly what missed
this the first time. Verified live: reproduced the user's exact blank-dropdown bug on the deployed
site, then confirmed the dropdown correctly accepts `'OP'` once corrected.

### v5.2 — Two new real Waypoint Lawn sample reports added (Cool and Warm Season)
User provided two real Waypoint lawn reports from the same property (front yard / back yard,
tested separately) — one explicitly cool-season (report comments reference bluegrass/fescue/
ryegrass Fall timing), one explicitly Zoysiagrass (warm-season). Extracted the printed numeric
values directly; for the bar-chart-based ratings (which can't be read pixel-precisely from a
scanned image), proposed best-effort inferences from the printed fertilizer recommendation itself
(a $0 P₂O₅ rec implies Optimum-or-above; a nonzero K₂O rec implies correction needed) and flagged
the uncertainty explicitly rather than guess silently. **User corrected two of the inferred
ratings** (Cool: Ca → Medium, not the initially inferred Optimum; Warm: Ca → Optimum, not the
initially inferred Very High) — both now reflect the user's own read of the actual shaded bars, not
the inference. New buttons: "Lawn-Waypoint (Cool Season)" / "Lawn-Waypoint (Warm Season)";
existing "Lawn-VCE" relabeled "Lawn-VCE (Warm Season)" for consistency, since that sample is also
warm-season. The warm-season sample's report N figure (5.0 lbs/1,000 sq ft) is a genuinely useful
test case for the existing Nitrogen Recommendation Check card: it exceeds VCE's own 1–2 lb ceiling
for zoysiagrass specifically, even though it's within the general warm-season range — confirmed the
card's existing logic (conservative, phrased "if your lawn is zoysiagrass...") correctly fires on
this exact scenario.

### v5.3 — Resident-identifying information scrubbed from the entire codebase
User pointed out the two new lawn samples were a real resident's front/back yard and asked that no
identifying information be left in the code. Search turned up far more than the two new samples —
**six different sample reports across most of this project's history** had real names, towns, or
report/client ID numbers embedded in code comments (a flower sample, both vegetable garden
samples, both new lawn samples, and a Rutgers citation with specific lab reference numbers).
Scrubbed all of them, in `index.html` and `CLAUDE.md` both — not just names and addresses, but also
the specific report/lab ID numbers themselves, since those are unique identifiers tied to real
submissions that could in principle be cross-referenced back to a real person given lab database
access, even without a name directly attached. Replaced each with a generic description that keeps
whatever made the sample agronomically useful (the specific ratings, the report type, the lab)
without any residual thread back to whose soil it was.

### v5.4 — Favicon replaced with a user-supplied, better-packaged .ico
User uploaded a proper multi-resolution `.ico` (16×16, 32×32, 48×48, all with alpha) — a cleaner
source than needing to generate one from a flat image again. Extracted each native embedded frame
individually (not just one image scaled to different sizes) for the 32px favicon; upscaled the 48px
frame with LANCZOS resampling for the 180px apple-touch-icon, since 48px is the largest size
available in the source. Flagged the resolution ceiling honestly rather than pretend it's not a
tradeoff — the design's bold, flat-colored style upscales cleanly, but a higher-resolution source
would still be preferable for a sharper home-screen icon if one exists.

### v5.5–v5.6 — Maintenance & Retesting card substantially deepened, then reordered
Extended the years-2/3 research with a comparative read of five real soil reports (VCE and
Waypoint, lawn and garden) plus both labs' own paper intake forms (Waypoint's Soil Sample
Information Sheet; VCE's 452-125). This surfaced a distinction sharper than "Waypoint is more
specific": it's about **where crop-specificity enters the pipeline**. Waypoint's intake form lets a
submitter select the exact vegetable or turf type by name (individual codes for tomatoes, peppers,
lima vs. snap beans; Zoysiagrass Lawn vs. Bermudagrass Athletic Field vs. Bermudagrass Fairway), so
the report itself already reflects what's planted. VCE's intake form distinguishes cool- from
warm-season for lawns but offers **only one generic code for all vegetable gardens** — no way to
specify what's actually growing — which is the direct, traceable cause of why VCE's vegetable
garden report comes back as one general nitrogen-only recommendation rather than a crop-specific
one. This reframes what this calculator's own per-crop N defaults and sidedress schedules
(`CROP_FEEDING_LEVELS`, `SIDEDRESS_GUIDE`) actually do: they're not just "more detail than VCE
gives" — they're specifically filling the exact gap created by VCE's own intake form having no
crop-specific code to select in the first place.

Added a summary table at the top of the card (Nitrogen / P&K / Lime / sourcing-confidence rows,
lawns vs. gardens) and rewrote the Nitrogen prose section to carry the intake-form-specificity
point through in full, rather than leave the table as the only place it appears. Left the P&K and
Lime prose sections unchanged after checking them against the new research — they're specifically
about the correct-once-hold retesting pattern, which this round's research didn't touch.

**Card reordered** to sit above "Single-Nutrient Amendment Philosophy" (previously the other way
round) — swapped as complete HTML blocks via exact string boundaries, verified the swap was lossless
(pre- and post-swap total file length identical) rather than trusting a visual check alone. Confirmed
the one internal cross-reference to the Single-Nutrient card from earlier on the page ("see the card
below") still correctly says "below," since it sits earlier in the page than both swapped cards and
was unaffected by their reordering relative to each other.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Six stale `'SUFF'`-on-Waypoint sample codes fixed (v5.1); two new real Waypoint Lawn samples added, one existing sample relabeled for consistency (v5.2); all resident-identifying information scrubbed from code comments across six sample reports (v5.3); favicon replaced with a user-supplied multi-resolution `.ico` (v5.4); Maintenance & Retesting card given a summary table and a substantially rewritten Nitrogen section reflecting the intake-form specificity research (v5.5); card reordered above Single-Nutrient Amendment Philosophy (v5.6) |
| `CLAUDE.md` | this entry; resident-identifying information also scrubbed from this file's own history (six references across five entries) |

---

## Session Updates — August 5–7, 2026 (WIN calculation explained in the About tab; a VCE-report display bug found via user screenshot and fixed for both garden tabs)

### v5.7 — "Understanding WIN & Nitrogen Programs" card now explains the calculation itself, not
### just the resulting thresholds
The existing card already stated the three program thresholds (<15%, 15–49%, ≥50% WIN) and their
per-application caps, but never explained *how* a user gets their own WIN% in the first place —
which specific number to enter, or what it's measured against. Added two new subsections before
the program boxes:
- **What to enter**: the raw Water Insoluble Nitrogen figure exactly as printed on the bag's
  Guaranteed Analysis (expressed as % of total product, same basis as the main N% figure) — not a
  pre-computed "% of my nitrogen" value, which is a distinct number a user could easily produce
  instead. States the actual formula (`WIN% of nitrogen = (label WIN ÷ label Total N) × 100`) with
  a worked example (29-3-4, 4.5% WIN → 15.5%, landing in Program 2), and what happens if the field
  is left blank (defaults to Program 1, the conservative choice).
- **Why the program matters**: connects WIN% to the practical consequence (fewer total
  applications, not just gentler release) before the program boxes give the exact numbers.

Also added one line to the existing closing note: Soil Test Notes 17/18 (the shorter,
consumer-facing lawn publications) only describe Programs 1–2 in condensed form — the full
three-program structure and exact thresholds come from the fuller source, VCE 430-011. Explains why
Program 3 appears in this calculator even though the more commonly-cited Notes don't spell it out.

### v5.8 — "Waypoint report target" input field was showing on VCE reports, where it can never
### apply — found via user screenshot, fixed for both Vegetable Garden and Flower Garden at once
User showed a VCE vegetable garden entry where every nutrient row in the Nutrient Application
Plan displayed a "Waypoint report target (lbs/1,000 sq. ft.)" input field — nonsensical for a VCE
report, which doesn't publish this kind of number. Root cause: the field was rendered
unconditionally, with the code's own comment explicitly acknowledging "VCE reports never populate
this (leave blank)" — the wrong call; it should never have rendered for VCE users rather than sit
there permanently empty and irrelevant. Fixed using the existing `isWaypointReport()` helper
(reads `st-report-type`, already used elsewhere in the app) to hide the field entirely for VCE
reports. Verified the underlying amendment-selection logic doesn't depend on the field being
visible — `targetDriven` is computed from the stored value alone, which is correctly empty/zero
whether the field was hidden (VCE) or just left blank (Waypoint) — so no downstream behavior
changed, only the confusing, always-inapplicable input.

**User also asked a substantive research question this prompted**: does VCE actually publish
P/K/micronutrient guidance by rating for vegetable gardens? Checked the actual
`NUTRIENT_AMENDMENTS` data rather than assume: **yes for P, K, and Mg** — VCE Note 19 gives flat
rates for each (Bone Meal/Rock Phosphate for P; Granite Dust/Greensand/Wood Ash for K; Epsom Salts
for Mg), already implemented as `calc:'flat'` entries that fire regardless of whether a Waypoint
target is entered. **No for S, B, Cu, Mn, Fe, Zn** — VCE's own rating for these is simply
"sufficient or deficient" with no corrective rate attached (confirmed earlier this session against
VCE's own SPES-384 and two independent Extension sources); this calculator's amendment options for
these six are sourced from elsewhere (UMD, NC State, Rutgers, or Waypoint's own report guidance for
Zn/Cu specifically), not VCE. This means the screenshot's "Adequate" readings for P/K/Mg were very
likely correct output reflecting genuinely adequate entered ratings, not a symptom of the display
bug — the two issues (a confusing always-shown field, and what VCE does or doesn't publish) were
separate findings from the same conversation, not the same bug.

**Confirmed the fix covers Flower Garden too**, not just Vegetable Garden, without a separate
change: both tabs call the exact same shared `renderNutrientStatusPanel()`, and `isWaypointReport()`
reads from the single canonical `st-report-type` field both tabs carry over from — there's no
tab-specific copy of report-type detection that could have gone out of sync.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Added a "how to calculate your own WIN%" section (formula, worked example, blank-field default) to the About tab's WIN card, plus a Notes-17/18-vs-430-011 sourcing clarification (v5.7); hid the "Waypoint report target" input field for VCE reports in `renderNutrientStatusPanel()`, fixing both Vegetable Garden and Flower Garden at once since they share the function (v5.8) |
| `CLAUDE.md` | this entry |

---

## Session Updates — August 7, 2026 (cont.) (Sulfur's "not entered" message was actively wrong for VCE reports — fixed)

### v5.9 — "Fill out the Soil Test tab" implied there was something to fill out; for Sulfur on a
### VCE report, there isn't
Following directly from the v5.8 fix, user provided a real VCE lab report showing its actual Lab
Test Results columns (P, K, Ca, Mg, Zn, Mn, Cu, Fe, B, Soluble Salts) — no Sulfur column at all,
confirming what the earlier intake-form research already implied (VCE's routine panel, per
Publication 452-125, lists exactly those nine values plus estimated CEC — no sulfur, and no
separate sulfur test offered as an add-on anywhere on the form either, unlike Waypoint's explicit
S2M/S3M sulfate-sulfur tier). The generic "Not entered — fill out the Soil Test tab to see a
recommendation here" message fires for any nutrient with no rating entered, regardless of report
type — for Sulfur specifically on a VCE report, this is actively misleading, since it implies the
data exists somewhere and the user just needs to go enter it, when in fact there's no way to ever
obtain a sulfur result through VCE's routine service at all.

Added a specific case: when `n.key === 'S'` and the report isn't Waypoint, show "Not tested —
sulfur isn't part of VCE's routine soil test panel. (VCE Publication 452-125)" instead. Left the
generic message unchanged for every other case — including Sulfur on a Waypoint report, where
"fill out" remains accurate, since sulfur is a real, orderable add-on tier there, not something
structurally unavailable the way it is for VCE.

**Privacy note carried forward correctly**: the real VCE report used to confirm this bug contains
the same resident's name scrubbed from the codebase earlier this session (v5.3). Checked the new
code comment before committing it — describes the finding ("a real VCE lab report with no S
column") without reintroducing the name, consistent with that earlier scrub rather than working
around it.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Sulfur's "not entered" message on VCE reports replaced with an accurate "not tested by VCE's routine panel" message, cited to VCE 452-125; Waypoint's version of the message left unchanged, since it's still accurate there (v5.9, 2026-08-07) |
| `CLAUDE.md` | this entry |

---

## Session Updates — August 7–8, 2026 (cont.) (v6.0–v6.5: a second VCE-target-message leak, Sulfur removed entirely for VCE, onboarding text reconciled with the Retesting card, a second rating-dropdown audit round, the actual "lime dropdown" request correctly identified and resolved, and Soluble Salts given a rating dropdown)

### v6.0 — The "enter its Waypoint report target" instruction leaked through a second, separate
### code path — found via user screenshot showing it on Phosphorus specifically
The v5.8 fix hid the Waypoint-target *input field* for VCE reports, but a separate piece of code
generating the *instructional text* telling users what to do still unconditionally said "enter its
Waypoint report target in this row" — pointing users at an input that no longer existed on the
page for them. Categorized every nutrient's amendment options by calc type to find every reachable
instance: Sulfur, Zinc, and Copper were the worst cases (every option for each is target-only, no
flat-rate fallback), meaning *every* VCE user who ever saw a Low rating on any of those three hit
this exact dead end, not just occasionally. Fixed the shared branch once
(`isWaypointReport() ? [original message] : "VCE publishes no specific rate... start at your
product's label rate"`), verified empirically for S/Zn/Cu specifically (not just P, the one in the
screenshot), and swept the whole file for a second copy of the same phrase — found none.

### v6.1 — Two more items from the same conversation
1. **A remaining "Open Vegetable Garden Calculator" button**, on Base Saturation's card
   (`limeGoBtn`) — missed during the original button-removal cleanup since it wasn't explicitly
   flagged at the time. Removed, and `goBtn()` itself removed too once confirmed it had no other
   callers left anywhere in the file.
2. **Sulfur removed entirely from the Vegetable/Flower Garden nutrient list for VCE reports** —
   not just given an accurate "not tested" message (v5.9's fix), but not shown as a row at all,
   per explicit user request. Filtered out of the `nutrients` array itself
   (`if (!isWaypointReport()) nutrients = nutrients.filter(...)`), which made the v5.9 message
   branch for this case unreachable — removed that too rather than leave confirmed-dead code
   sitting next to the change that caused it.

### v6.2 — Onboarding Step 3 reconciled with the Maintenance & Retesting card
Found to be stating a flat, outdated rule ("all recommendations valid for up to three growing
seasons") that no longer matched the more precise card built earlier this session — missing the
1-year-retest exception and lumping nitrogen in with fertilizer/lime as if it followed the same
multi-year cycle. Rewritten to summarize the actual current rule accurately while staying brief,
and pointed to the full card rather than duplicate it.

### v6.3 — Second rating-dropdown audit round: found and removed Magnesium's unsourced "VCE
### special: DEF/SUFF" option
User asked for a thorough check of the nutrient rating dropdowns (a continuation of the Zn/Mn/Cu/
Fe/B/S work from earlier). Catalogued and cross-checked all 28 dropdowns (10 nutrients × VCE/
Waypoint/canonical variants) against confirmed real-report formats. Found one real issue:
Magnesium's canonical dropdown had a "VCE special: DEF/SUFF" option with no sourcing comment —
directly contradicted by a real VCE report reviewed earlier this session, which rated Magnesium
"VH" on the standard macronutrient scale, not DEF/SUFF (that scale is confirmed for the actual
micronutrients, not for Mg). Also inconsistent with Calcium, which has identical defensive code
(`caLow` checking for `'DEF'`) but never had the corresponding dropdown option — same unverified
pattern, only one of the two was ever reachable. Removed the option and the now-fully-unreachable
`'DEF'` checks in both `mgLow` and `caLow`.

### v6.4 — The actual "lime dropdown" request, correctly identified after an initial misread
User clarified that "the lime dropdown on the instructions page" reviewed at the start of this
session referred to a specific collapsible ("🪨 Lime") inside the About tab's "How to Use This
Calculator" card — one of six per-tab guide toggles (Cool, Warm, Lime, Garden, Flower, Shrub) — not
the Soil Test tab's rating `<select>` elements the v6.3 audit had covered. Confirmed directly: zero
`<select>` elements exist anywhere in the About tab. Went through all six collapsibles line by line
against current app behavior. Found real drift in three places, all the same root cause: Vegetable
Garden's and Flower Garden's descriptions still listed **Calcium** as part of the nutrients
"auto-filled" alongside P/K/Mg/S/micronutrients — inaccurate since Ca was deliberately removed from
that shared panel back in v3.7 (handled by the Lime section instead). Notably, the same outdated
claim was sitting on the **live Flower Garden tab itself** (the text directly above the Nitrogen
Source dropdown in Individual mode), not just the About page — actively telling users something
untrue about what they were about to see. Fixed all instances found (live tab text, its code
comment, both About-page descriptions, and one more stale code comment describing the panel's
contents found via a follow-up grep) rather than stopping at the first match.

### v6.5 — Soluble Salts given a VCE rating dropdown, matching every other value on the page
User noted Soluble Salts was the one field with no rating dropdown at all (numeric ppm/dS-m input
only), and that VCE 452-701 does describe a rating scale for it. Re-fetched the primary source
directly to confirm rather than assume: the document's own abbreviation list states **"EH =
Excessively High (soluble salt test only)"** — confirming salts use the standard L/M/H/VH scale
plus one category unique to this measurement. Matches a real VCE report reviewed earlier this
session, which printed a rating ("L") in that exact column alongside every other nutrient. The
source gives no precise numeric boundaries for L/M/H/VH/EH (unlike its P/K/Ca/Mg medium-range
figures) — only the 844 ppm injury threshold already used in the app's own interpretation logic —
so the dropdown is for data entry (let the user enter exactly what their report says, same pattern
as every other field), not a new independent scoring system.

Added: a VCE-side rating dropdown (L/M/H/VH/EH); a canonical field shown only for VCE reports
(toggled via the existing `setSaltUnit()` function, extended rather than duplicated — no confirmed
Waypoint equivalent, so left numeric-only there); the entered rating now displays as a pill on the
interpretation card. **Found and fixed while wiring this in**: the shared `pill()` styling
function had no case for `'EH'` at all — would have silently rendered with the same neutral styling
as "Medium," understating exactly the result that most needs a visible warning. Added `'EH'` as its
own case using the existing `pill-warn` class (confirmed it exists before relying on it) with the
full "Excessively High" label. Added plausible ratings to two existing VCE sample datasets based on
where their printed ppm values fall relative to the confirmed 844 ppm threshold — flagged as
inference in the code, not a re-confirmed literal value from those original reports.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Fixed a second Waypoint-target-message leak affecting P/K/Mg/S/Zn/Mn/Cu/B (v6.0); removed Base Saturation's last "go to calculator" button and the now-callerless `goBtn()`; removed Sulfur entirely from the VCE-side garden nutrient list (v6.1); reconciled onboarding Step 3 with the Retesting card (v6.2); removed Magnesium's unsourced DEF/SUFF dropdown option (v6.3); fixed a real Calcium-list inaccuracy on the live Flower Garden tab and both Garden/Flower About-page guides (v6.4); added a VCE Soluble Salts rating dropdown, sourced to 452-701, plus an `'EH'` case for the shared rating-pill styling (v6.5) |
| `CLAUDE.md` | this entry |

---

## Session Updates — August 8, 2026 (v6.6: new VCE master recommendation guidebook found — cross-checked against the app, five edits made)

### v6.6 — User found VCE's "Soil Test Recommendations for Virginia" (Maguire & Heckendorn, July
### 2026) — the actual master document behind every crop-code recommendation on a real VCE report
Read the full 110-page PDF (pdftotext + targeted section review: Home Lawns/Gardens/Shrubs
crop-code tables, Secondary Nutrients, Micronutrients, Raising Soil pH with Lime). Cross-checked
against current app content rather than assuming anything changed.

**Confirmed, no change needed:**
- Sulfur is genuinely absent from VCE's recommendation list ("more research is needed before this
  element can be put on the recommendation list") — backs the v5.9/v6.1 decision directly.
- Cool/warm-season per-application N caps (0.7 lb / 0.9 lb) match the source's own Note 17/18
  table column headers exactly.
- Zn/Mn deficiencies are VCE-documented only for field crops (corn/small grains/sorghum;
  soybeans/peanuts) — not home lawn/garden — matching this calculator's own earlier conclusion
  that its Zn/Mn amendments are sourced elsewhere, not from VCE.

**New information found, not previously in the app — five edits made:**
1. **Lime trigger threshold + previous-lime credit** — VCE only recommends lime once pH is 0.2
   units or more below target (0.1 for new turf establishment; 0.50 T/A minimum), and credits
   75%/50%/25%/0% of lime applied 1–6/7–12/13–18/18+ months ago. Added as a new paragraph in the
   "Maintenance Fertilizing & Retesting" About-tab card, with a one-line pointer added to the
   shorter "🪨 Lime" collapsible so both entry points connect.
2. **Molybdenum** — VCE does recommend it (alfalfa/soybeans/some vegetables, triggered below pH
   5.8) but publishes no home-garden rate; added a short explainer to the "Single-Nutrient
   Amendment Philosophy" card on why this tab has no separate Mo amendment (the lime already
   recommended elsewhere removes the low-pH trigger condition in practice).
3. **Copper (Soil Test tab interpretation card)** — tightened `st-cu`'s `lowMsg` from "rare in
   Virginia gardens" to the source's actual, stronger statement: "not recommended for any Virginia
   crop."
4. **Copper (Garden/Flower amendment note)** — this is the one place the app actually computes and
   offers a copper application (Waypoint-only; VCE reports never reach this branch since VCE gives
   no Cu rate). Added an explicit note that this option follows Waypoint's methodology, not VCE's,
   since the two labs genuinely disagree here — VCE's position isn't just "no published rate," it's
   a stated non-recommendation.
5. **New source entry** — added the guidebook itself to the About tab's Source Documents list,
   in a new "📘 VCE General & Lime Publications" section placed near the top (alongside SPES-40A)
   since, like that document, it isn't specific to any one tab.

**Not fully resolved:** the official garden N-P-K crop-code table (*221–*225) gives synthetic
complete-fertilizer combinations that weren't cross-checked gram-for-gram against this app's
organic single-nutrient amendments (bone meal, granite dust, etc.), since those are sourced from a
different publication (Note 19) not reprinted in this master document. Left as a flagged gap rather
than guessed at.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Added new VCE general/lime source entry to About tab (Source Documents list); added lime-trigger-threshold + previous-lime-credit paragraph to the Retesting card, with a cross-reference from the Lime collapsible; added a molybdenum explainer to the Single-Nutrient Amendment Philosophy card; tightened Copper's Soil Test tab interpretation message; added a VCE-vs-Waypoint divergence note to the Copper garden amendment (v6.6) |
| `CLAUDE.md` | this entry |

---

## Session Update — August 8, 2026 (v6.7: WAVE accessibility scan — fixed the one real error)

User ran the WAVE browser extension against the live page (after enabling "Allow access to file
URLs," since WAVE can't inspect a file:// page without that permission). Result: 199 Features, 80
Structure, 138 ARIA, 9.3/10 AIM Score, **1 Error, 0 Contrast Errors, 76 Alerts**.

**The 1 Error — "Empty table header" — was real and is now fixed.** The "Maintenance Fertilizing
& Retesting: Years 2–3" card's comparison table (Lawns vs. Vegetable & Flower Gardens) had an empty
`<th></th>` corner cell, and its row labels (Nitrogen / Phosphorus & Potassium / Lime / How
well-sourced is this?) were plain `<td><strong>` rather than proper row headers — meaningless to a
screen reader announcing that column. Fixed: corner cell now carries a visually-hidden "Category"
label (`<th scope="col"><span class="sr-only">`), the three column headers got explicit
`scope="col"`, and the four row labels became `<th scope="row">`. That reuses the `.fert-grade-table
th` selector, which was styled for dark-green thead headers — added a scoped
`.fert-grade-table tbody th` rule so row headers keep the original bolded/plain-background look
instead of turning dark green, and extended the existing `thead`/`nth-child(even)` selectors to
cover `th` alongside `td` so striping and border rules still apply consistently.

The 76 Alerts weren't reviewed in this pass — WAVE alerts are "check this, it might be fine"
flags, not confirmed errors, and the ones visible in the user's screenshot (redundant link text,
link-to-PDF, JavaScript jump menu, possible list) are common on content-heavy sites and often
non-issues on inspection. Left for a future pass if requested rather than acted on here.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Fixed WAVE's one flagged Error: empty table header + missing row headers on the Retesting card's comparison table, with a matching CSS fix so the new `<th scope="row">` cells don't inherit the dark-green thead styling (v6.7) |
| `CLAUDE.md` | this entry |

---

## Session Update — August 8, 2026 (v6.8: two user-reported bugs on Waypoint Flower Garden — both fixed)

User reported two issues via screenshots, both on the Flower Garden tab with a Waypoint report:

### Bug 1 — Soil Test tab lime label wrong for Waypoint gardens
The lime recommendation label/placeholder logic (in the report-type change handler) branched only
on `isGarden`, always showing "lbs / 100 sq. ft." for any garden report. That's correct for VCE
gardens, but Waypoint garden reports print lime on the same 1,000 sq. ft. basis as lawns — the
`isWaypoint` flag needed for this was already computed one line below and simply wasn't being used.
Fixed: label/step/placeholder now key off `isGarden && !isWaypoint`.

### Bug 2 — Boron/Manganese (and in fact every nutrient) "locked" on Flower Garden tab
Root cause: `gdnSetNutrientChoice()`, `gdnSetTarget()`, and `gdnSetDensity()` — the three functions
that handle changing a nutrient's amendment dropdown, entering a Waypoint numeric target, or
entering a custom bulk density inside the shared Nutrient Status panel — all unconditionally called
`calcGarden()` (the **Vegetable Garden** tab's recalc function), regardless of which tab the control
actually lived on. State updated correctly either way (the state objects are keyed by
`'prefix:nutrient'`, e.g. `flr:Mn`), but on the Flower Garden tab this re-rendered the hidden
Vegetable Garden panel instead of the visible Flower Garden one — so any change looked like it had
no effect. Fixed all three functions to split the prefix off the state key and dispatch to
`calcFlower()` when `prefix === 'flr'`, `calcGarden()` otherwise. Confirmed the only two prefixes
that ever call `renderNutrientStatusPanel()` are `gdn` and `flr`, so no other tab is affected.
`onCropTypeChange()`, `setGardenSizeMode()`, and `calcGardenDimensions()` were left alone — they
operate on `gdn`-only elements with no Flower Garden equivalent, so always calling `calcGarden()`
there is correct.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Fixed Waypoint-garden lime label basis (100 vs. 1,000 sq. ft.); fixed `gdnSetNutrientChoice`/`gdnSetTarget`/`gdnSetDensity` re-rendering the wrong tab's panel on Flower Garden (v6.8) |
| `CLAUDE.md` | this entry |

---

## Session Update — August 8, 2026 (v6.9: Base Saturation %H mini-calculator, Option B)

Following up on the Base Saturation discussion: a real user filling out the Waypoint block has no
way to find "Base Saturation" on their report, since Waypoint reports print %H (Hydrogen
Saturation) in the %Saturation table instead — Base Saturation = 100 − %H, but nothing told the
user that, and no field existed to do the arithmetic for them.

**Built Option B (mini in-field calculator) rather than just a hint.** Added a %H input beneath
Waypoint's Base Saturation field: enter %H as printed on the report, and `calcBaseSatFromH()`
computes and fills the real Base Saturation field automatically, then syncs it to the canonical
field via the existing `stSync()` path exactly as if the user had typed the result in directly.

**Accessibility, since this needed to stay ADA-compliant:** the %H input has its own `<label for>`
(not just a visual caption); `aria-describedby` links it to both the instructional text above and
the result region below; the result region uses `aria-live="polite"` specifically because setting
another field's `.value` via JS never fires a native change event and would otherwise be silently
invisible to a screen reader — the live region is the only way a non-sighted user learns the
calculation ran and what it produced. Kept plain semantic inputs throughout (no custom widgets),
so keyboard operation needs nothing extra.

**Prefill traceability fix, same root issue as the earlier conversation:** the 'veggie' sample
previously hardcoded `'st-basesat-wp':'100'` with no comment showing where 100 came from — it was
computed by hand off-report (100 − the report's own H% of 0.0), same math a real user would now do
through the new calculator, just never documented. Replaced with `'st-basesat-h-helper':'0.0'`
(the number actually printed on the report) plus a call to `calcBaseSatFromH()` after the field
loop, so the prefill now demonstrates the same calculator a real user relies on instead of
silently pre-computing the answer.

**Also expanded the Soil Test tab's intro line** ("Fields below are ordered to match the layout of
each lab's report.") to add "Leave fields blank where values don't appear on your report." —
directly addresses the fact that several fields (Buffer pH/Index, Base Saturation, etc.) are
correctly blank on many real reports and aren't all mandatory just because they're in the grid.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Added %H-to-Base-Saturation mini-calculator (Waypoint block only) with full label/aria-describedby/aria-live wiring; fixed the 'veggie' prefill's undocumented Base Saturation value to route through the new calculator instead; expanded the Lab Test Results intro line to mention leaving fields blank (v6.9) |
| `CLAUDE.md` | this entry |

---

## Session Update — August 9, 2026 (v6.10: garden-aware P/K card wording; removed legacy "Plant Type & Fertilizer Program" card; investigated Sodium report)

### Investigated — Sodium showing "Very Low"
User reported the Sodium rating showing "Very Low" on the Waypoint vegetable prefill, despite the
Na dropdown only ever offering two options (Normal/Low, High/Very High — no "Very Low" choice
exists). Simulated the exact prefill against the live code in a headless DOM (jsdom) rather than
guessing from static reads, and it correctly renders "54 ppm — Optimum" — did not reproduce.
No code path exists that could reach "Very Low" for Na given its rating can only ever be '', 'SUFF',
or 'H'. The user's own attached report shows a plain gray, uncolored bar for the Sodium row (unlike
every other nutrient's colored 5-zone bar) — Waypoint's own convention for "informational value, no
graded scale applies," consistent with the app's 2-option design. Could not reach Waypoint's
published documentation directly to confirm further (Chrome extension not connecting this
session). Left open — asked user to confirm they're on the latest version and, if it still
reproduces, to send a screenshot.

### Fixed — Phosphorus/Potassium cards prescribed lawn-style advice for garden reports
The Soil Test tab's Phosphorus and Potassium interpretation cards gave identical advice regardless
of report type — e.g. "Use a complete fertilizer containing phosphorus (e.g. 10-10-10, 12-4-8)" —
even though the Vegetable Garden tab has no blended-fertilizer picker at all (removed in an earlier
session; it only offers individual single-nutrient amendments), and Flower Garden's default mode is
also individual-nutrient. Fixed both cards' Low/Medium/High/Optimum branches to check `isGarden`:
garden reports now point to "the Vegetable Garden or Flower Garden tab" for the actual calculated
amount instead of naming a fertilizer grade; lawn reports keep the original advice unchanged (still
correct there, since Cool/Warm-Season lawn calculators do use a fertilizer-grade picker). Checked
for the same issue elsewhere — the Ca/Mg card was already fine (gypsum-based advice, not
fertilizer-grade). Verified both branches via jsdom simulation: garden P (Very High) → "No
[amendment] needed... skips phosphorus automatically"; garden K (Low) → "calculated on the
Vegetable Garden or Flower Garden tab"; lawn P (Optimum) → unchanged original wording.

### Removed — "Plant Type & Fertilizer Program" card
User feedback: leftover from an earlier version of the app, adds nothing the carry-over bar /
"Continue to [X] Calculator" button and bottom-of-tab navigation don't already say more usefully.
Removed the entire `isGarden` branch of the "Grass / Garden Type" card block (covered vegetable,
flower, and shrub crop types alike, all built from the same code path). Kept the lawn-side "Grass
Type & Lawn Status" card as-is — genuinely distinct content (new-lawn establishment guidance,
seasonal fertilizing windows, starter-fertilizer note) the garden version never had. Required
collapsing `if (crop) { if (isGarden) {...} else {...} }` into `if (crop && !isGarden) {...}` and
removing one now-orphaned closing brace. Verified via simulation: garden reports no longer contain
"Plant Type" anywhere in the results panel; lawn reports still show "Grass Type & Lawn Status"
correctly.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Made Phosphorus/Potassium Soil Test tab cards garden-aware (no more fertilizer-grade advice for garden reports); removed the "Plant Type & Fertilizer Program" card entirely (all garden crop types); Sodium "Very Low" report investigated but not reproduced (v6.10) |
| `CLAUDE.md` | this entry |

---

## Session Update — August 9, 2026 (v6.11: resolved the Sodium "Very Low" confusion — report UX gap, not an app bug)

User clarified the actual source of confusion: their real Waypoint report shows a plain gray bar
for Sodium sitting near the "Very Low" end of the shared color-bar chart (the same chart width used
for every nutrient row), so a user naturally goes looking for a "Very Low" option in the app's Na
Rating dropdown — and can't find one, since Waypoint doesn't actually grade sodium on that 5-level
scale (only Normal/Low vs. High/Very High, per the dropdown's two real options). This reads as "the
app is missing a choice" when the real issue is that Waypoint's own report visually implies a
rating that was never actually assigned.

Added a hint directly under the Na Rating dropdown (Waypoint block only — VCE reports don't test
sodium at all, confirmed no VCE-side Na field exists) explaining that the gray bar's left-side
position is a chart-width artifact, not a real "Very Low" rating, and to pick based on the bar's
color/general position or leave it blank if unsure. Checked whether the canonical `st-na-rating`
field (inside the hidden `#st-canonical-fields` mirror) also needed this — confirmed it's
`display:none`/`aria-hidden`/`inert`, purely an internal sync target never seen by a user, so no
duplicate hint needed there.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Added an explanatory hint under the Waypoint Na Rating dropdown clarifying that the report's gray bar position isn't a real rating (v6.11) |
| `CLAUDE.md` | this entry |

---

## Session Update — August 9, 2026 (v7.2: corrected versioning convention break)

User flagged that v6.10 and v6.11 broke the project's established versioning pattern — the minor
number has always rolled 0–9 then incremented the whole number (e.g. v5.9 → v6.0), never gone to
double digits. Corrected: v6.11 → **v7.2** (v6.9 → 7.0, 7.1, 7.2 covers the three version bumps that
happened this session — P/K card + Plant Type card removal, the Sodium hint, and this fix itself).
Added an explicit standing rule to this file's Project Overview section (see "Versioning
convention" above) and to the version badge's own `title` tooltip in `index.html`, so this doesn't
drift again. v6.10 and v6.11 are retired — they should never be referenced as valid versions.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Version badge corrected to v7.2; tooltip now states the versioning convention explicitly (v7.2) |
| `CLAUDE.md` | Added standing versioning-convention rule to Project Overview; this entry |

---

## Session Update — August 9, 2026 (v7.3: shortened Sodium hint per user request)

User asked to remove one sentence from the Na Rating field hint added in v6.11 — specifically the
"Sodium's bar on your report is usually plain gray... not an actual rating" framing. Removed;
the hint now reads: "Waypoint doesn't grade sodium on that 5-level scale, only Normal/Low vs.
High/Very High — pick whichever matches your bar's color and general position, or leave this blank
if you're unsure."

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Shortened the Na Rating field hint (v7.3) |
| `CLAUDE.md` | this entry |

---

## Session Update — August 9, 2026 (v7.4: pH card now cross-references Buffer Index)

User spotted an apparent self-contradiction: the pH card's "ideal range" Action said "No lime action
needed," while the Buffer Index card directly below it (same report) said "Moderate lime
requirement." Not actually a bug — pH is the current reading, Buffer Index measures the acid
reserve that determines real lime need even when current pH looks fine — but shown back-to-back
with no cross-reference, it read as the app contradicting itself.

Changed the pH card's Action text for both the "ideal range" (6.0/5.8–6.8, action-good) and "near
neutral" (6.8–7.0, action-monitor) buckets to point the user at the Buffer Index/Buffer pH card,
hedged as "if your report includes" one since it's an optional field and isn't always entered/shown.
Replaced the previous "Continue monitoring with periodic soil tests" line, which wasn't tied to any
specific citation — just the app's own synthesized text.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | pH card's "ideal range" and "near neutral" Action text now cross-reference Buffer Index/Buffer pH instead of a generic "keep retesting" line (v7.4) |
| `CLAUDE.md` | this entry |

---

## Session Update — August 9, 2026 (v7.5: same pH/Buffer-Index cross-reference fix, extended to Base Saturation & Acidity)

User caught the identical contradiction one card down: Base Saturation & Acidity's "good" bucket
(Acidity ≤ 20%) said "No corrective action needed... Continue monitoring with periodic soil
tests," while the Buffer Index card directly above it can independently say "Moderate lime
requirement" for the same report — same root cause as the v7.4 pH card fix (a good current reading
doesn't mean no lime is needed; Buffer Index/pH measures the acid reserve that actually determines
that). Applied the identical fix and wording: now points to Buffer Index/Buffer pH, hedged the same
way since it's an optional field. The middle bucket (20–40% Acidity) already referenced "if lime is
recommended on your report," so didn't need the change. Grepped for any other remaining instances
of the old "Continue monitoring with periodic soil tests" phrasing — none found; this was the last
one.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Base Saturation & Acidity card's "good" Action text now cross-references Buffer Index/Buffer pH, same as the pH card (v7.5) |
| `CLAUDE.md` | this entry |

---

## Session Update — August 9, 2026 (v7.6: audit for the same isGarden-mislabels-Shrub bug class — found and fixed 4 more instances)

User asked whether more issues like the pH/Buffer-Index contradiction existed. Systematically grepped
every `isGarden ?` branch and every `abox('action-good'...)` call. Found the pH/Buffer-Index/Base
Saturation issue was a symptom-level fix (v7.4/v7.5) of a broader, pre-existing bug class the code's
own comments already named: **`isGarden` is true for vegetable, flower, AND shrub reports**
(`isGardenReport()` returns true for all three), so any text branching only on `isGarden` — without
also checking `crop === 'shrub'` — silently mislabels Shrub & Trees reports with vegetable/flower-
specific language. This exact bug class had already been fixed once for the pH card's destination
button (July-something session, per the comment at the top of the pH card block) but was reintroduced
by this session's own earlier P/K card fix, and was never applied to two more cards.

**Found and fixed 4 instances**, all newly discovered or reintroduced this session:

1. **Phosphorus/Potassium cards (self-introduced bug)** — my own fix two turns ago said "calculated
   on the Vegetable Garden or Flower Garden tab" for ALL garden reports including Shrub & Trees,
   which routes to a different tab that doesn't do soil-test-rating-triggered P/K correction at all
   (shrub fertilization is symptom-triggered only). Added `isVegFlowerGarden` / `isShrubReport`
   split (mirroring the existing `phDestName` 3-way pattern) across all four rating buckets for both
   nutrients, with shrub-specific language pointing to symptom-based fertilization on the Shrubs &
   Trees tab instead.
2. **Micronutrients summary card intro paragraph** — said "For vegetable and flower gardens..." for
   Shrub reports too. Added a `crop === 'shrub'` branch with shrub-appropriate framing (deficiencies
   uncommon, fertilization only on visible symptoms, consult VCE for species-specific guidance).
3. **Micronutrients card's "Target: Optimum at correct soil pH (6.0-6.8)" line** — same issue,
   falsely implied a single numeric pH target applies to all shrub species. Changed to "Optimum pH
   varies by species — check your specific plant's requirements" for shrub, since no sourced
   shrub-general pH target exists anywhere in the codebase to substitute (species vary too widely —
   azaleas ~4.5–5.5 vs. most other woody ornamentals). Did not touch the underlying `phLow` bucket
   threshold logic (still 6.0, same as garden) since changing functional thresholds needs a real
   source, not just a text fix.
4. **The main Soil pH card itself** — TARGET label ("Gardens: 6.0-6.8"), "why it matters" paragraph,
   and both the "acidic" and "near neutral" bucket messages all said "vegetable and flower gardens"
   or "garden plants" for Shrub reports. Fixed all four spots: TARGET label now shows "Varies by
   species" for shrub; why-it-matters paragraph now explains species vary widely and specifically
   flags acid-loving plants (azaleas/rhododendrons, ~4.5–5.5) as needing to check their own
   requirements rather than assume a general target.

**Checked but left alone:** the Soluble Salts card's `isGarden ?` branch (adds seedling/
transplanting caution text) — for shrub reports this adds mildly imprecise wording (new shrub
plantings aren't quite "seedlings"), but doesn't misroute anywhere or state anything factually
wrong, so it's a much lower-severity style issue than the four fixed above. Left as a minor open
item rather than fixed speculatively.

**Verification:** simulated a Waypoint Shrub & Trees report (jsdom, real functions, not guessing)
with pH 5.5 / P Low / K Optimum. Confirmed: P card action correctly says "Established shrubs and
trees rarely need direct correction... See the Shrubs & Trees tab" (not the garden-tab text);
pH card TARGET line shows "Varies by species"; pH why-it-matters includes the azalea/acid-loving
note; zero remaining instances of "vegetable and flower gardens" or "garden plants" language
outside the static, intentionally-generic pH glossary tooltip (which correctly stays general since
it's not report-specific).

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Fixed 4 instances of the isGarden-mislabels-Shrub bug class: P/K cards, Micronutrients summary intro + target-pH line, and the main Soil pH card (TARGET label, why-it-matters text, acidic/near-neutral bucket messages) (v7.6) |
| `CLAUDE.md` | this entry |

---

## Session Update — August 9, 2026 (v7.7: lime action wording standardized; Action box removed from genuinely non-actionable buckets)

### 1. Lime Recommendation card wording, all three variants
Changed "Use the [X] tab to calculate lime for your specific bed size, including CCE and bag size"
to "...calculate the quantity of lime required for your specific bed size adjusted for CCE and bag
size" per user request. Applied with appropriate wording to all three Lime card variants:
Vegetable/Flower Garden (routes to that tab), Shrub & Trees (routes to the standalone Lime
Calculator, unchanged since shrub has no lime section of its own), and Lawn (routes to
Cool-Season/Warm-Season Lawn tab, replacing the older, more verbose "Enter your product's CCE and
bag size..." phrasing with the same standardized wording).

### 2. Removed Action box from genuinely non-actionable buckets: Soil pH, Base Saturation & Acidity, Buffer Index
User asked to remove the Action element entirely from these three card types where no action can
be taken as a result of the test. Interpreted narrowly (confirmed with user before implementing):
this means the specific "good" bucket within each card, not the whole card type, since all three
do drive real action in their other buckets (acidic pH, high acidity, low buffer index all still
call for lime).
- **Soil pH** — removed the Action box for the "ideal range" bucket (pH 6.0/5.8–6.8). The Buffer
  Index cross-reference added in v7.4 is preserved but moved into the "why it matters" prose
  instead of a styled Action box, appearing only when pH is actually in that ideal range.
- **Base Saturation & Acidity** — same treatment for the Acidity ≤20% bucket; same v7.5
  cross-reference moved into prose, conditional on `acPct <= 20`.
- **Buffer Index** — removed the Action box for the ≥6.5 bucket ("Relatively low total acidity").
  This one's previous text ("Apply per your recommendation") was circular anyway — the actual
  action lives on the separate Lime Recommendation card. Replaced with a plain-prose note in "why
  it matters" pointing there instead, conditional on `bi >= 6.5`.
- Confirmed via `card()`'s own logic that passing an empty string for `action` correctly omits the
  entire Action wrapper `<div>` rather than rendering an empty styled box.
- Left the action-monitor and action-needed buckets on all three cards untouched — those give real,
  specific guidance (do this / don't do that / monitor this) and aren't "no action" cases.

**Verification:** ran a full jsdom simulation (VCE Lawn, pH 6.3 / Buffer Index 6.62 / Base Sat
96.9%) confirming zero `st-action-box` elements render on any of the three cards at those values,
while the Buffer Index cross-reference text still appears in the pH card's body. Separately
verified all three Lime card variants (Vegetable, Shrub, Lawn) render the new wording correctly.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Standardized Lime Recommendation Action wording across Vegetable/Flower, Shrub, and Lawn variants; removed the Action box from the non-actionable bucket of Soil pH, Base Saturation & Acidity, and Buffer Index cards, folding the retained cross-reference content into prose (v7.7) |
| `CLAUDE.md` | this entry |

---

## Session Update — August 10, 2026 (v7.8: removed the Action box entirely from Soil pH, Base Saturation & Acidity, and Buffer Index — all buckets)

User followed up on v7.7 with screenshots showing several buckets still had an Action box (pH's
acidic and near-neutral buckets, Buffer Index's moderate bucket) and asked to go further: remove
the Action box from **every** bucket of these three cards, since the only real actionable output
(exact amount, bag count, CCE-adjusted schedule) lives on the separate Lime Recommendation card —
having pH, Base Saturation, and Buffer Index each repeat their own "apply lime" instruction is
redundant with that card and risks looking contradictory if wording ever drifts between them.

Agreed with the reasoning and implemented, with one exception: the pH card's alkaline bucket
mentions sulfur as an option to *lower* pH, which isn't covered anywhere on the Lime Recommendation
card (that card only ever handles raising pH) — preserved that as prose in the result text rather
than dropping it, just unstyled as a plain sentence instead of a colored Action box.

**pH card** — removed `phAction` entirely (all 5 buckets: strongly acidic, acidic, ideal, near
neutral, alkaline). Folded the substantive content that used to live in each Action box into the
"Your result" (`phMsg`) sentence instead: acidic/strongly-acidic buckets now end with "see the Lime
Recommendation card for your exact amount and schedule"; alkaline bucket keeps the sulfur mention
inline. Removed the now-unused `phDestName` variable (was only referenced by the deleted action
text).

**Base Saturation & Acidity** — removed `bsAction` entirely (all 3 buckets). Replaced with a `bsExtra`
string appended to the why-it-matters paragraph: >40% and 20–40% buckets point to the Lime
Recommendation card; ≤20% keeps the existing Buffer Index cross-reference from v7.5.

**Buffer Index** — removed `biAction` entirely (all 3 buckets, low bucket already done in v7.7).
Moderate and high buckets now fold their content into `biMsg` ("see the Lime Recommendation card
for your exact amount...").

**Verification:** ran jsdom simulations matching all four scenarios shown in the user's screenshots
(pH 6.3/BI 6.23 lawn; pH 5.5/BI 6.23 lawn; pH 6.3/BI 6.32/BaseSat 96.9% VCE vegetable; pH 7.0/
BaseSat 100% Waypoint vegetable) — zero `st-action-box` elements in all four. Also tested a
high-acidity scenario (pH 4.8, BI 5.8, BaseSat 55%) to confirm the "needed" content survived as
prose rather than being silently lost — confirmed present in each card's result text.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Removed the Action box entirely from all buckets of Soil pH, Base Saturation & Acidity, and Buffer Index; substantive content preserved as plain prose, redirecting to the Lime Recommendation card for the actual actionable numbers (v7.8) |
| `CLAUDE.md` | this entry |

---

## Session Update — August 10, 2026 (v7.9: removed Action boxes from CEC/Organic Matter/Soluble Salts; redesigned Calcium & Magnesium card)

### Principle established this session
User articulated the underlying rule behind the last several rounds of card edits: **an "Action:"
box should only exist where it transcribes or directly derives from an action a lab actually
produced** — Waypoint's own nutrient-addition table plus its explanatory comments, or VCE's text
recommendation tied to a measured rating — not wherever the app has independently synthesized
"here's what I'd do" from a raw measurement using its own thresholds. Audited every remaining
`abox()` call against this test (full breakdown given to user in prior turn) before touching
anything.

### Removed — CEC, Organic Matter, Soluble Salts (failed the test)
None of these three cards' Action content is transcribed from either lab's own printed
recommendation — checked the actual attached Waypoint report's Comments section directly and
confirmed it says nothing about OM or salts specifically. All three "Action:" boxes removed
(all buckets, both lawn and garden variants where applicable):
- **CEC** — dropped the "consider slow-release Program 2 fertilizer" prescription (unsourced,
  app-invented); left the moderate/high buckets' plain-prose "CEC is an estimation" note untouched
  since it was never styled as an Action box in the first place.
- **Organic Matter** — dropped all compost/topdressing prescriptions; kept the SPES-384/Note 19
  citations, moved into the why-it-matters paragraph as plain sourced fact rather than an
  instruction.
- **Soluble Salts** — kept the 844/640 ppm thresholds themselves (these genuinely are VCE-sourced,
  per Soil Test Note 1 / 452-701, already cited elsewhere in the app) but dropped the specific
  remediation instructions ("water thoroughly to leach," "delay transplanting," etc.) since those
  aren't transcribed from Note 1's own text — added the citation directly to the card body instead
  of only in a separate field hint.

### Redesigned — Calcium & Magnesium
User's specific ask: the card should *explain* what agricultural vs. dolomitic lime actually are
when the report recommends one (since that lime-type field is printed directly on the report —
VCE's "Lime Type Recommended," Waypoint's comments — so explaining it passes the sourcing test),
and should tell the user to check the CCE and lime type carefully when shopping, since products
vary. Rewrote all four branches (Mg low, Dolomitic recommended, Agricultural recommended, Ca low
with no lime) with real definitions instead of jumping straight to prescriptive language, added a
shared shopping-tip paragraph (check the label for type + CCE, since a lower-CCE bag needs more
material), and moved everything out of `abox()` into plain why-it-matters prose — consistent with
the same treatment given to the other six cards, since the real actionable quantity still belongs
to the separate Lime Recommendation card. Dropped the specific "gypsum, 10 lbs per 100 sq. ft."
figure from the Ca-low-no-lime branch (flagged last turn as borderline) since that number isn't
tied to either report's own printed recommendation — kept the qualitative fact (gypsum supplies
calcium without changing pH, cited VCE 426-323) without inventing a report-unsourced rate.

**Verification:** jsdom simulation with pH 6.3, CEC 2 (low), OM 1.0% (low), Salts 900ppm
(elevated), Ca 400/Low, Mg 50/Low, Dolomitic lime, lime rec 50 lbs — confirmed exactly **one**
remaining `st-action-box` on the page (the Lime Recommendation card, which correctly still passes
the test), down from what would have been 5+ under the old logic. Separately tested the
Agricultural-lime branch of the Ca/Mg card to confirm both explanatory paths render correctly.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Removed Action boxes from CEC, Organic Matter, and Soluble Salts (all buckets); rewrote the Calcium & Magnesium card to explain agricultural/dolomitic lime with a CCE shopping tip instead of prescriptive action language, moved out of the Action-box styling entirely (v7.9) |
| `CLAUDE.md` | this entry |

---

## Session Update — August 10, 2026 (v8.0: Copper description reframed; Lime card redesigned to a single consistent unit)

### 1. Copper (Cu) description — was alarming regardless of actual reading
The Cu row's italic note ("Deficiency most likely on sandy, low-organic or highly organic soils")
always displayed regardless of the user's actual ppm value or rating — so someone with a genuinely
high/adequate copper reading (per user's real report) still saw what read as an active deficiency
warning. Reframed to lead with VCE's actual stance (uncommon, no routine recommendation for any
crop) so the same risk-factor information now reads as background context rather than a live
concern tied to their specific number.

### 2. Lime Recommendation card (Vegetable/Flower Garden and Shrub & Trees, Waypoint only) — redesigned to one consistent unit
Previously led with the converted 100-sq.-ft. figure and buried the report's own printed number in
a parenthetical: "0.3 lbs/100 sq. ft. (your report lists 3 lbs/1,000 sq. ft., which is 0.3
lbs/100 sq. ft.)" — then the body text switched back to the 100-sq.-ft.-basis VCE Note 19 quote
("never apply more than 5 lbs per 100 sq. ft."), so the card used two different units in two
different places. User proposed showing the report's own printed number as the single header
figure, and re-expressing the Note 19 threshold in that same unit rather than switching mid-card.
Implemented, with one correction: 5 lbs/100 sq. ft. converts to **50 lbs/1,000 sq. ft.** (×10), not
0.5 as initially suggested — flagged and corrected before implementing rather than reproducing the
arithmetic error. VCE reports (which already give lime in the 100-sq.-ft. basis, matching Note 19
natively) were untouched — no conversion was ever needed there. The underlying application-count
math (`limeRec100`/`limeMaxPer`) is unchanged; only the displayed wording was redirected to stay in
one unit.

**Verification:** jsdom simulation matching the exact screenshot scenario (Waypoint vegetable,
lime rec 3 lbs/1,000 sq. ft., Cu 4.1 ppm) — Lime card now reads "3 lbs / 1,000 sq. ft." in the
header and "never apply more than 50 lbs per 1,000 sq. ft." in the body, both in the report's
native unit; Copper card shows the revised neutral framing.

### Files
| Document | Status |
| :-- | :-- |
| `index.html` | Reframed Copper's always-visible description to lead with VCE's rarity/no-recommendation stance instead of an unconditional deficiency warning; redesigned the Waypoint Vegetable/Flower Garden and Shrub & Trees Lime Recommendation cards to display in one consistent unit (the report's own printed basis) instead of switching between 100- and 1,000-sq.-ft. mid-card (v8.0) |
| `CLAUDE.md` | this entry |
