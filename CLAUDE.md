# CLAUDE.md — VCE Lawn & Garden Care Calculator Project Context

Use this file to bring a new Claude session up to speed on the project.

---

## Project Overview

A single-file interactive HTML web calculator (`lawn_garden_calc_v1_5.html`) that helps Virginia homeowners interpret soil test results and calculate fertilizer and lime applications. Supports **VCE / Virginia Tech** and **Waypoint Analytical** reports for both **lawn** and **vegetable/flower garden** contexts.

**Primary audience:** Chesterfield County, Virginia (Zone 7b, Piedmont clay soils). Secondary: all of Virginia.

No server, no build step — single self-contained HTML file. Single-column responsive layout on all calculator tabs. Soil Test tab retains two-column `st-layout`.

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
| Rutgers NJAES FS626 | Organic fertilizer N% and release rates (Table 1); tomato sidedress schedule (Table 2); blood meal as medium-rapid; bat guano/bone meal/dried cow manure |
| NC State Cooperative Extension | Calcium nitrate as preferred sidedress N source — delivers N without adding excess P or K. Blossom end rot and tip burn are calcium *uptake* disorders primarily caused by inconsistent watering and underdeveloped root systems, not soil calcium deficiency. Calcium nitrate provides direct corrective value only when soil calcium is low. |
| Mid-Atlantic Commercial Veg Guide 2026/2027 | Per-crop pH targets (Table B-1); soil testing 1–3 years. **Commercial guide — principles only, not home garden rates** |
| SARE LS16-269 | Blood meal \>80% available N within 2–4 weeks in warm soil |
| GitHub Fertilizer Calculator | Bulk density data; Borax sodium accumulation note |

**Source policy:** VCE always primary. UMD and Clemson co-primary for home garden where VCE is silent. Rutgers FS626 and NC State supporting. Mid-Atlantic Veg Guide principles only. Never cite OSU, UNH, or non-regional extensions.

**Critical rule:** Never infer soil texture from CEC or Buffer Index values.

---

## File Structure

Single HTML file — all CSS, JS, HTML inline. No external dependencies except Google Fonts CDN.

### Tabs (6)

1. **Soil Test Report** (`tab-soiltest`) — interpretation cards, carry-over  
2. **Cool-Season Lawns** (`tab-cool`)  
3. **Warm-Season Lawns** (`tab-warm`)  
4. **Lime** (`tab-lime`)  
5. **Vegetable & Flower Gardens** (`tab-garden`)  
6. **About & Instructions** (`tab-about`)

### Key JavaScript Functions

| Function | Purpose |
| :---- | :---- |
| `interpretSoilTest()` | All soil test cards — string concatenation only, no backticks |
| `calcMulti(prefix)` | Custom plan engine for cool/warm |
| `calcAutoplan(prefix)` | Auto plan — no cap at 4 apps |
| `calcCool()` / `calcWarm()` | Route to auto or custom |
| `calcLime()` | Lime calculator — writes to `lime-results-panel` |
| `calcGarden()` | Garden calculator — preplant summary \+ SIDEDRESS\_GUIDE-based application plan with volumetric output |
| `onCropTypeChange()` | Step 3 crop change: updates hint (feeding level \+ pH), syncs `gdn-guidance-crop`, calls `updateCropGuidancePanel()` and `calcGarden()` |
| `useRecommendedN(cropKey)` | Pre-fills N rec field from CROP\_FEEDING\_LEVELS |
| `updateCropGuidancePanel()` | Renders crop-specific guidance in collapsible — reads from `gdn-guidance-crop` (not step 3\) |
| `fmtMeasure(lbs, cupsPerLb)` | tsp / tbsp / cup fractions based on bulk density |
| `detectProgram(fertN, winLbs)` | P1/P2/P3 WIN branch |
| `setPlanMode(prefix, mode)` | Toggle auto/custom |
| `printPlan(prefix)` | Always use this — never call window.print() directly |
| `onReportTypeChange()` | Switches scales, units, labels; calls calcGarden() for garden reports |
| `carryOverToCalculators()` | Copies soil test values to calculators; uses setTimeout |
| `prefillSampleReport(type)` | Types: 'lawn', 'garden' (flower), 'veggie' |
| `onGardenProductSelect()` | Fires when product dropdown changes — **must call `setGardenFertMode('product')` before `calcGarden()`** or product info is ignored |
| `useRecommendedN()` | **REMOVED** — calculator requires a soil test |

---

## Vegetable & Flower Gardens Tab

### Field numbering

1. Garden type  
2. Bed size  
3. Crop selector (`gdn-crop-type`) — syncs collapsible, shows N rate hint in both units  
4. N recommendation  
5. P rating  
6. K rating  
7. Fertilizer  
8. Lime recommendation

### Report type and N/lime units

| Report type | N unit | Lime unit | calcGarden() handling |
| :---- | :---- | :---- | :---- |
| vce-garden | lbs/100 sq. ft. | lbs/100 sq. ft. | direct |
| waypoint-garden | lbs/1,000 sq. ft. | lbs/1,000 sq. ft. | ÷ 10 before calculating |

### CROP\_FEEDING\_LEVELS — seasonal N rates

| Level | Rate | Crops |
| :---- | :---- | :---- |
| Heavy | 0.20 lbs/100 sq. ft. \= 2 lbs/1,000 sq. ft. | Tomato, pepper, potato, broccoli, cabbage, corn, beet, spinach, onion, okra |
| Medium | 0.20 lbs/100 sq. ft. \= 2 lbs/1,000 sq. ft. | Leafy greens, lettuce, cucumber, squash, melon, sweet potato, asparagus |
| Light | 0.10 lbs/100 sq. ft. \= 1 lb/1,000 sq. ft. | Beans/peas, carrot, root crops |
| Mixed | 0.20 lbs/100 sq. ft. \= 2 lbs/1,000 sq. ft., pH target 6.5 | Mixed bed (vegetables & flowers) — no fixed sidedress schedule; advisory note only |
| Annual flower | 0.10 lbs/100 sq. ft., pH 5.5–6.5, `flowerCaution: true` | Annual flowers — preplant from soil test; light mid-season at half rate for heavy bloomers only |
| Perennial flower | 0.10 lbs/100 sq. ft., pH 6.5, `flowerCaution: true` | Perennial flowers — early spring only; no sidedress; compost often sufficient |
| Rose | 0.20 lbs/100 sq. ft., pH 6.5, `flowerCaution: true`, `roseMonthly: true` | Roses — monthly March–August per VCE Note 19 |

### Application plan architecture (current)

**Key principle:** Step 4 N rec \= **preplant amount only** — entered exactly as shown on the soil test report. Sidedress amounts are **additional** fixed applications from crop research, not a split. This matches VCE and Rutgers soil test reports (2 lbs N/1,000 sq. ft. preplant \+ separate midseason). This calculator requires a soil test — it does not provide N rates for users without one.

**`SIDEDRESS_GUIDE` data object** — 20 crops \+ 3 flower types:

- `apps: [{n: lbs actual N/1,000 sq. ft., trigger: timing string}]`  
- `note` — source-grounded caution with citation  
- Carrots: `apps: []` — no standard sidedress  
- `SIDEDRESS_DEFAULT`: 1.0 lb N/1,000 sq. ft. at 3–4 weeks for unlisted **vegetable** crops only

**Flower entries in SIDEDRESS\_GUIDE:**

| Key | apps | Note |
| :---- | :---- | :---- |
| `annual-flower` | 1 app: 0.5 lbs N/1,000 sq. ft. at mid-season peak bloom, half preplant rate | Wash fertilizer off foliage; excess N suppresses flowers. *(VCE Note 19\)* |
| `perennial-flower` | `apps: []` — no sidedress | Established perennials; early spring only; compost often sufficient; late-season N causes frost damage. *(VCE Note 19\)* |
| `rose` | 5 apps: 0.5 lbs N/1,000 sq. ft. each for April, May, June, July, August | Monthly March–August per VCE Note 19 |

**`SIDEDRESS_DEFAULT` fallback exclusion** — flower crop keys (`annual-flower`, `perennial-flower`, `rose`) bypass `SIDEDRESS_DEFAULT` entirely. Without this, they would incorrectly receive the generic vegetable sidedress plan (1.0 lb N at 3–4 weeks).

**Flower caution box** — amber advisory box appears in the application plan header whenever a flower crop type is selected: *"Avoid excessive nitrogen — promotes vegetative growth at the expense of blooms."* Source: VCE Note 19\. `isFlowerType` detection: `['annual-flower','perennial-flower','rose'].indexOf(cropKey) >= 0 || gardenType === 'annual' || gardenType === 'perennial'`

**Sidedress product logic (`useUserProduct`):**

- Zero-P/K product selected (`fertAlreadyZeroPK`): use user's product throughout — consistent  
- Complete fertilizer (10-10-10, 5-10-5): default to calcium nitrate for sidedress  
- `fertAlreadyZeroPK = (fertP === 0 && fertK === 0)`

**`gardenFertMode`** — global var, default `'npk'`. **`onGardenProductSelect()` must call `setGardenFertMode('product')` before `calcGarden()`** — otherwise productKey stays empty and all product info is ignored (caused calcium nitrate to always appear regardless of selected product).

**Application Timing card** — `display:none` when `nRec > 0 && fertN > 0`. Only shown when inputs incomplete.

**P/K flags** — suppressed when `fertAlreadyZeroPK`. Also suppressed for tomato/pepper (handled in plan).

**OM credit (garden only)** — when `st-om` ≥ 5%: yellow notice showing `omVal * 0.4` lbs N/1,000 sq. ft. natural release, converted to lbs/100 sq. ft. and lbs for user's actual bed. Source: UMD Extension. **Not applicable to lawn tabs** — VCE does not ground lawn N recommendations in OM level; lawn equivalent is the clipping return credit (VCE 430-011, SPES-384NP: 0.5–1 lb N/year, up to one-third of seasonal requirement). Never cite Rutgers FS626 or UMD OM formula in lawn context.

**Per sq. ft. application rate row** — `lbsPerHundred / 100 * 16` \= oz/sq. ft.; converted to tbsp or tsp via bulk density. Allows gardeners to measure directly over the bed.

**`CROP_FEEDING_LEVELS` `nPer100`** — **0.20 for heavy feeders, 0.20 for medium, 0.10 for light** (lbs/100 sq. ft. \= preplant amount). Validated against VCE Lab 23-15911 and Rutgers reports 2016-55189/55190/55191. Old 0.30 heavy feeder value was total seasonal N — incorrect for this field.

**Step 3 crop hint** — shows feeding level, target pH, and prompt to enter soil test N in step 4\. No N amounts shown. `useRecommendedN()` removed — calculator requires soil test.

### Organic product sidedress logic

**Fast-release organics** (`fastOrganic: true` — blood meal, fish meal, fish emulsion, bat guano) \+ warm-season crops: can sidedress (soil warm enough for microbial release)

**Fast-release organics \+ cool-season crops** OR **slow-release organics**: all preplant

**Warm-season crops:** tomato, pepper, potato, corn, squash, cucumber, melon, okra, beans, sweetpotato

### Vegetable guidance collapsible

- `gdn-guidance-crop` selector — synced from step 3 but independently browsable  
- `updateCropGuidancePanel()` reads from `gdn-guidance-crop`, renders feeding level \+ sidedress timing from SIDEDRESS\_GUIDE \+ note  
- Old CROP\_DATA preplant/sidedress/caution table removed — was conflicting with the application plan  
- General timing rule and banding note always visible below selector

### GARDEN\_PRODUCTS — key fields

All products: `name`, `npk[N,P,K]`, `cupsPerLb`, `organic`, `fastOrganic`, `source`, `note19Rate`, `note`, `liquid`

| Product | fastOrganic | Notes |
| :---- | :---- | :---- |
| Blood meal (\~13-0-0) | true | Medium-rapid in warm soil (\>60°F); slow in cool soil |
| Fish meal (\~10-6-2) | true | Moderate-fast in warm soil |
| Fish emulsion (\~5-1-1) | true | Liquid; fast even in cool soil |
| Bat guano (\~10-4-2) | true | Medium-rapid |
| Feather/soybean/cottonseed/poultry/bone/dried cow | false | Preplant only |

Cottonseed meal corrected to **7-3-2** per Rutgers FS626.

### fmtMeasure(lbs, cupsPerLb)

- ≥ 4 cups → cups to nearest half  
- 0.5–4 cups → cups as Unicode fractions  
- 1–16 tbsp → tablespoons  
- \< 1 tbsp → teaspoons  
- Always flagged as approximate

---

## Soil Test Report Tab

### Report type options

| Value | Lab | Context | Lime unit | Carry-over |
| :---- | :---- | :---- | :---- | :---- |
| vce-lawn | VCE | Lawn | lbs/1,000 sq. ft. | Cool \+ Warm \+ Lime |
| waypoint-lawn | Waypoint | Lawn | lbs/1,000 sq. ft. | Cool \+ Warm \+ Lime |
| vce-garden | VCE | Garden | lbs/100 sq. ft. | Garden |
| waypoint-garden | Waypoint | Garden | lbs/1,000 sq. ft. | Garden |

### Sample report buttons (PII-free)

| Button | Type | Key values |
| :---- | :---- | :---- |
| 📋 Lawn Sample | VCE warm-season | pH 5.5, K Low, lime 60 lbs |
| 🌸 Flower Garden Sample | Waypoint annual flowers | pH 5.2, P Low, K Optimum, OM 5.6%, lime 87 lbs/1,000 sf, agricultural lime |
| 🌿 Vegetable Garden Sample | Waypoint vegetable | pH 7.1, P/K/Ca Very High, OM 11.4%, no lime |

Micronutrient prefill values must use `L`, `M`, `SUFF`, `H` — not Waypoint keys (ME, OP, VH).

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
- Zoysiagrass/centipedegrass annual N: **1–2 lbs** (not 1–1.5 lbs) per SPES-669  
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
14. `showCropGuidance()` is removed — use `updateCropGuidancePanel()`  
15. Soil testing: "3–4 years" lawns; "every 2–3 years" active vegetable beds  
16. Never recommend brand names — NPK ratios and WIN % only  
17. `onGardenProductSelect()` must call `setGardenFertMode('product')` before `calcGarden()` — without this, selected product is completely ignored and calcium nitrate appears in sidedress steps regardless  
18. This calculator requires a soil test — do not add N rate suggestions for users without one; `useRecommendedN()` has been removed for this reason

---

## Attributions

- **Chantel Wilson** — Assistant Professor and 4-H STEAM Extension Specialist, Virginia State University  
- **Michael Goatley Jr.** — Professor and Extension Specialist, Virginia Tech

Virginia Cooperative Extension is a partnership of Virginia Tech, Virginia State University, USDA, and local governments.

---

## Files

| File | Description |
| :---- | :---- |
| `lawn_garden_calc_v1_5.html` | Main application |
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
| `centipede` | 1.0 | 0.5 / 0.5 / 0.5 | New — WIN% does not meaningfully change per-app limit for centipede; flat 0.5 lb cap all programs |

**MAX_PRACTICAL_APPS changes:**

| Key | P1 / P2 / P3 | Window |
| :---- | :---- | :---- |
| `zoysia` | 3 / 3 / 2 | May/Jun/Jul |
| `centipede` | 2 / 2 / 2 | May/Jun only — low-N, slow-growing |

**HTML changes:**
- `warm-species` selector: three options (Bermudagrass/St. Augustine, Zoysiagrass, Centipedegrass)
- Reference table: separate rows for Zoysiagrass (1.0–2.0 lbs) and Centipedegrass (0.5–1.0 lbs)
- Static N hint updated: three species with separate ranges and both SPES-669 and SPES-670 cited
- Waypoint warning updated: "appropriate for bermudagrass but too high for zoysiagrass, and far too high for centipedegrass"
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

