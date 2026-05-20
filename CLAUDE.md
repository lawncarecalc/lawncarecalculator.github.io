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
| University of Maryland Extension | N rates by feeding level (0.10/0.20/0.30 lbs/100 sq. ft.); liquid Borax method; OM-to-N credit; fish emulsion in cool soils |
| Clemson HGIC | 35% preplant / 65% sidedress split; sandy soil flag; calcium nitrate as preferred sidedress |
| Rutgers NJAES FS626 | Organic fertilizer N% and release rates (Table 1); tomato sidedress schedule (Table 2); blood meal as medium-rapid; bat guano/bone meal/dried cow manure |
| NC State Cooperative Extension | Calcium nitrate reduces blossom end rot and tip burn |
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
| Heavy | 0.30 lbs/100 sq. ft. \= 3 lbs/1,000 sq. ft. | Tomato, pepper, potato, broccoli, cabbage, corn, beet, spinach, onion, okra |
| Medium | 0.20 lbs/100 sq. ft. \= 2 lbs/1,000 sq. ft. | Leafy greens, lettuce, cucumber, squash, melon, sweet potato, asparagus |
| Light | 0.10 lbs/100 sq. ft. \= 1 lb/1,000 sq. ft. | Beans/peas, carrot, root crops |

### Application plan architecture (current)

**Key principle:** Step 4 N rec \= **preplant amount only** — entered exactly as shown on the soil test report. Sidedress amounts are **additional** fixed applications from crop research, not a split. This matches VCE and Rutgers soil test reports (2 lbs N/1,000 sq. ft. preplant \+ separate midseason). This calculator requires a soil test — it does not provide N rates for users without one.

**`SIDEDRESS_GUIDE` data object** — 20 crops:

- `apps: [{n: lbs actual N/1,000 sq. ft., trigger: timing string}]`  
- `note` — source-grounded caution with citation  
- Carrots: `apps: []` — no standard sidedress  
- `SIDEDRESS_DEFAULT`: 1.0 lb N/1,000 sq. ft. at 3–4 weeks for unlisted crops

**Sidedress product logic (`useUserProduct`):**

- Zero-P/K product selected (`fertAlreadyZeroPK`): use user's product throughout — consistent  
- Complete fertilizer (10-10-10, 5-10-5): default to calcium nitrate for sidedress  
- `fertAlreadyZeroPK = (fertP === 0 && fertK === 0)`

**`gardenFertMode`** — global var, default `'npk'`. **`onGardenProductSelect()` must call `setGardenFertMode('product')` before `calcGarden()`** — otherwise productKey stays empty and all product info is ignored (caused calcium nitrate to always appear regardless of selected product).

**Application Timing card** — `display:none` when `nRec > 0 && fertN > 0`. Only shown when inputs incomplete.

**P/K flags** — suppressed when `fertAlreadyZeroPK`. Also suppressed for tomato/pepper (handled in plan).

**OM credit** — when `st-om` ≥ 5%: yellow notice showing `omVal * 0.4` lbs N/1,000 sq. ft. natural release. Source: UMD Extension, confirmed by Rutgers FS626 reports.

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
- Clipping recycling credit: 0.5–1 lb N per year (SPES-384)  
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
