# CLAUDE.md — VCE Lawn & Garden Care Calculator Project Context

Use this file to bring a new Claude session up to speed on the project.

---

## Project Overview

A single-file interactive HTML web calculator (`lawn_garden_calc_v1_4.html`) that helps Virginia homeowners interpret soil test results and calculate fertilizer and lime applications. It supports reports from both **Virginia Cooperative Extension (VCE) / Virginia Tech** and **Waypoint Analytical**, for both **lawn** and **vegetable/flower garden** contexts.

No server, no build step — single self-contained HTML file.

---

## Source Documents

All calculations, thresholds, and interpretation language must be grounded in these sources. Do not infer or add content beyond what they support.

| Publication | Title | Authors |
| :---- | :---- | :---- |
| SPES-40A | Spreadsheet-Based Calculator for Lawn Fertilizer and Lime Applications in Virginia | Chantel Wilson (VSU); Michael Goatley Jr. (VT) |
| 430-011 / SPES-334P | Lawn Fertilization in Virginia | Goatley, Cataldi, Chalmers, Hall, Schmidt — VCE 2021 |
| 430-520 / SPES-223P | Fall Lawn Care | Goatley, Askew, McCall — VCE 2025 |
| 452-717 / SPES-306P | Soil Test Note 17: Lawn Fertilization for Cool-Season Grasses | Goatley, Ervin, Heckendorn — VCE 2021 |
| 452-718 / SPES-305P | Soil Test Note 18: Lawn Fertilization for Warm-Season Grasses | Goatley, Ervin, Heckendorn — VCE 2021 |
| 452-719 / SPES-687NP | Soil Test Note 19: Vegetable and Flower Gardens | VCE |
| 452-701 / SPE-605NP | Soil Test Note 1: Explanation of Soil Tests | Maguire, Heckendorn — VCE 2024 |
| Agronomy Facts 8 | Soil Test Interpretation: Terms and Definitions | Large / Ruiz Jr. — Waypoint Analytical 2023 |
| DCR 2014 | Virginia Nutrient Management Standards and Criteria | Virginia DCR (Tables 2-2 and 2-3) |

**Critical rule:** Never infer soil texture (sandy/clay) from CEC or Buffer Index values.

---

## File Structure

Single HTML file — all CSS, JS, and HTML inline. No external dependencies except Google Fonts CDN.

### Tabs (6)

1. **Soil Test Report** (`tab-soiltest`) — enter report values, get interpretation cards, carry over to calculators
2. **Cool-Season Lawns** (`tab-cool`) — species-aware fertilizer calculator with two-mode application planner
3. **Warm-Season Lawns** (`tab-warm`) — species-aware fertilizer calculator with two-mode application planner
4. **Lime** (`tab-lime`) — lime calculator with CCE adjustment
5. **Garden & Flowers** (`tab-garden`) — fertilizer and lime calculator for vegetable and flower gardens (Note 19)
6. **About & Instructions** (`tab-about`) — source docs, attributions, how-to

### Key JavaScript Functions

| Function | Purpose |
| :---- | :---- |
| `interpretSoilTest()` | Builds all soil test interpretation cards — zero backtick template literals, all string concatenation |
| `calcMulti(prefix)` | Custom plan engine for cool/warm tabs — processes up to 4 manual application slots |
| `calcAutoplan(prefix)` | Auto plan engine — divides annual N target equally across minimum applications needed, no cap at 4 |
| `calcCool()` / `calcWarm()` | Route to calcAutoplan or calcMulti depending on planMode[prefix] |
| `calcLime()` | Lime calculator logic |
| `calcGarden()` | Garden & Flowers calculator logic (Note 19) |
| `detectProgram(fertN, winLbs)` | Three-way WIN branch: returns program 1/2/3 and label |
| `setPlanMode(prefix, mode)` | Switches between 'auto' and 'custom' modes; pre-populates custom from auto on switch; shows/hides timing card |
| `prePopulateCustom(prefix)` | Fills custom plan slots from auto plan inputs when user switches to custom mode |
| `addAppSlot(prefix)` / `removeAppSlot(prefix, id)` | Add/remove manual application slots (max 4) |
| `renderAppSlots(prefix)` | Renders application slot HTML |
| `fertChooserHTML(prefix)` | Generates collapsible fertilizer chooser HTML — dynamic P/K recommendation based on current ratings |
| `toggleFertChooser(prefix)` | Expands/collapses the fertilizer chooser section |
| `printPlan(prefix)` | Adds printing-cool or printing-warm class to body, calls window.print(), removes class — ensures correct tab prints |
| `onReportTypeChange()` | Switches rating scales, salt units, lime labels, Buffer Index/pH label, crop/garden-type visibility, carry-over routing |
| `onLabSourceChange()` | Legacy alias for onReportTypeChange() |
| `setGardenSizeMode(mode)` | Toggles garden bed size between L x W and direct area entry |
| `setGardenFertMode(mode)` | Toggles garden fertilizer between N-P-K entry and product selector |
| `onGardenProductSelect()` | Fills product details when a garden product is chosen |
| `calcGardenDimensions()` | Auto-calculates area from L x W inputs |
| `setSaltUnit(unit)` | Auto-switches ppm/dS/m label and placeholder based on report type |
| `carryOverToCalculators()` | Copies soil test values into all relevant calculator tabs; uses setTimeout to defer calc calls |
| `prefillSampleReport(type)` | Loads sample report: 'lawn' or 'garden'. Never writes st-lawn-size |
| `switchToTab(tab)` | Tab navigation — re-runs calc on reveal |
| `getReportType()` / `isGardenReport()` / `isWaypointReport()` | Report type helpers |
| `fmtVolume(cups)` | Converts decimal cup value to human-readable volume string |
| `fmt(n, dec)` | Number formatter — returns '-' for NaN/null/Infinity |

### Helper functions inside interpretSoilTest()

Defined locally right after `var cards = [];`. Must always be present:

    card(icon, title, range, target, valDisplay, whatMeans, whyMatters, action, extraBtns)
    abox(cls, txt)       // action box
    goBtn(tab, lbl)      // navigate-to-calculator button
    pill(r)              // rating pill

---

## Soil Test Tab — Report Type Selector

| Option value | Lab | Context | Lime unit | Carry-over to | pH target | OM target |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| vce-lawn | VCE / Virginia Tech | Lawn | lbs/1,000 sq. ft. | Cool + Warm + Lime | 5.8-6.8 | 0.5-2.5% |
| waypoint-lawn | Waypoint Analytical | Lawn | lbs/1,000 sq. ft. | Cool + Warm + Lime | 5.8-6.8 | 0.5-2.5% |
| vce-garden | VCE / Virginia Tech | Garden | lbs/100 sq. ft. | Garden & Flowers | 6.0-6.8 | 5-10% |
| waypoint-garden | Waypoint Analytical | Garden | lbs/100 sq. ft. | Garden & Flowers | 6.0-6.8 | 5-10% |

**Carry-over bar behavior:**
- Appears as soon as P or K rating AND crop/garden type are entered — area not required to show bar
- Amber warning inside bar if area is blank; amber hint below area field hides once value entered
- Lawn reports carry to ALL three tabs (Cool, Warm, Lime)
- DOM writes deferred via setTimeout(..., 0) before calc calls — do not remove this

**Buffer Index / Buffer pH:** label switches automatically — VCE = "Buffer Index", Waypoint = "Buffer pH"

**Soluble Salts unit:** auto-switches ppm (VCE) / dS/m (Waypoint) — manual toggle buttons were removed

---

## Cool and Warm Season Calculator Tabs — Architecture (v1.4)

### Two-mode planner

Both tabs have a toggle: **"Build a plan for me"** (default) / **"Custom plan"**.

**Build a plan for me (auto mode):**
- User enters fertilizer N-P-K and WIN%
- `calcAutoplan(prefix)` detects program, calculates minimum applications needed (no cap at 4), divides N equally
- Results render **inline** directly below the grade inputs — not in the right column
- If more than 4 applications needed, amber warning suggests switching to slow-release (Program 2/3)
- Right column card (`results-card`) is hidden on screen, visible only when printing

**Custom plan mode:**
- Up to 4 manual slots, each with N-P-K, WIN%, N per application, month
- Pre-populated from auto plan inputs when user switches to custom mode
- Timing card shown in custom mode, hidden in auto mode (timing is in the plan table)
- Season summary writes to right column card for printing

**Print plan:**
- `printPlan(prefix)` adds `printing-cool` or `printing-warm` class to body before `window.print()`
- CSS shows only the target tab when these classes are present
- Without these classes, print defaults to soil test report (existing behaviour preserved)
- Print button appears in both auto and custom modes

### N rate guidance table (static, in Step 3)

Both tabs show a guidance table above the N rate input field. Table-first layout: the user reads the table to choose a rate, then enters it in the subordinate input field below. Contains:
- Suggested Annual Application Total by lawn situation
- Max per application by program (P1/P2/P3)
- Minimum applications needed
- Clipping recycling note (up to 1/3 N reduction per 430-011)
- Shade adjustment note (1/2 to 2/3 N rate for heavy shade per 430-011)
- Timing guidance: "SON" for cool-season (430-520); April–August 15 + fall bermudagrass program for warm-season (430-520)

### Fertilizer chooser (collapsible)

Between K rating field and Application Plan on both tabs. Collapsed by default. Contains:
- Plain-language explanation of N-P-K percentages
- Dynamic P/K recommendation driven by current ratings (updates when ratings change)
- Quick-release vs slow-release explainer with WIN instructions
- Common grades at a glance table (grades from 430-011 Table 1 + common retail)
- Disclaimer: calculator does not endorse specific brands

### Species config (SPECIES_CONFIG object)

    tall:    maxN:3.5, maxApp:{1:0.7, 2:0.9, 3:1.5}  — Tall fescue / Bluegrass / Ryegrass
    fine:    maxN:2.0, maxApp:{1:0.7, 2:0.9, 3:1.0}  — Fine-leaf fescue
    bermuda: maxN:4.0, maxApp:{1:0.9, 2:1.0, 3:1.5}  — Bermudagrass / St. Augustinegrass
    zoysia:  maxN:2.0, maxApp:{1:0.7, 2:1.0, 3:1.0}  — Zoysiagrass / Centipedegrass

### WIN / Program Detection (3-way per 430-011)

    >= 50% WIN  → Program 3 (majority slowly available)
    >= 15% WIN  → Program 2 (slowly available)
    <  15% WIN  → Program 1 (quickly available)

### P/K Flags

NEED_RATIO = {L-:3, L:2.5, L+:2, M-:2, M:1.5, M+:1, H-:1, H:0.75, H+:0.5, VH:0}
Flag fires when total P applied > NEED_RATIO[rating]

### Lime Calculator

Applications = ceil(adjusted_rate / 50), max 50 lbs/1,000 sq. ft. per app.
CCE adjustment: adjusted_rate = recommended_lbs x (100 / CCE%)

---

## Garden & Flowers Calculator (Note 19)

Lime limits: 5 lbs/100 sq. ft. established, 10 lbs/100 sq. ft. preplant.
Sidedress: 1 lb 10-10-10 per 100 sq. ft. of row, ~1 month after planting (vegetable/mixed only).
Bed size: L x W mode or direct area entry (for irregular beds).
Fertilizer: N-P-K entry or product selector.

GARDEN_PRODUCTS volume data (cups/lb): nitrate-soda 1.75, calcium-nitrate 2.0, ammonium-sulfate 2.5, urea 2.5, 10-10-10 1.75, 5-10-5 1.75, blood-meal 2.75, fish-meal 2.5, soybean-meal 2.0, cottonseed-meal 2.25, feather-meal 3.0, poultry-manure 1.75.
Synthetic volumes from VCE Note 19 (exact). Organic volumes from bulk density data (flagged as estimates).

---

## Sample Report Pre-fill

prefillSampleReport('lawn'): pH 5.5, K Low, lime 60 lbs, warm-season.
prefillSampleReport('garden'): pH 5.9, OM 8.8%, salts 1216 ppm, lime 5 lbs, vegetable (real VCE Lab 23-15911).
Neither sample writes st-lawn-size. Area field is explicitly cleared on load.

---

## Known Issues / Technical Debt

### Remaining gap: Shade adjustment (static guidance only)
Per 430-011, heavy shade lawns need only 1/2 to 2/3 the N rate. Currently a static callout. Two planned enhancements deferred from v1.4:
1. **Dynamic minimum-applications calculation** — live result based on user's actual N total and program
2. **Shade checkbox** — auto-reduces suggested N range display when checked

### Remaining gap: N rate not carried from Soil Test tab
N rate from Waypoint report not captured or carried. The N rate guidance table helps users translate a Waypoint recommendation into a VCE-compliant starting point in the meantime.

### Critical: Unicode in JS strings
Never use literal Unicode/emoji in JS string literals. Use HTML entities (&#9888; &#10003; etc.). Literal special characters cause silent parse errors in Safari.

### Critical: Template literals
All calculator functions must use zero backtick template literals — all string concatenation.

### Critical: carryOverToCalculators timing
DOM writes and calc calls separated by setTimeout(..., 0). Do not remove.

### Critical: canCarryOver must remain in interpretSoilTest
The canCarryOver check and carryBar.style.display call live at the bottom of interpretSoilTest(), just before the summary bar render. Has been accidentally dropped in past sessions — always verify if carry-over bar stops appearing.

### Critical: printPlan class cleanup
printPlan(prefix) adds a class to body before print and removes it after. If window.print() is ever called without going through printPlan, the soil test page will print instead of the plan. Never call window.print() directly from plan print buttons.

### Critical: numApps must not be capped in calcAutoplan
The auto plan calculator must not cap numApps at 4. Capping causes nPerApp to silently exceed the per-application limit. The warning for >4 applications handles user communication instead.

### HTML Structure
The st-layout grid requires exactly 2 direct children. A missing closing div collapses the grid.

### Helper Functions Must Be Present
card(), abox(), goBtn(), pill() are defined locally inside interpretSoilTest. Verify after any automated block replacement.

---

## Style & Language Rules

1. Never infer soil texture from CEC or Buffer Index.
2. Only use thresholds explicitly stated in source documents.
3. All dynamic result sentences preceded by bolded "Your result:".
4. Action boxes use abox(). Must be a genuine action, not a caveat.
5. Non-action caveats use plain p with Note: label.
6. "Why it matters" kept to one sentence, sourced from VCE.
7. No "Mehlich" in user-facing text.
8. No user names or lab IDs in user-visible text.
9. Use "plant health" / "your plants" language so text works for both lawn and garden contexts.
10. Organic volume estimates always flagged. Synthetic VCE Note 19 volumes are exact.
11. Never recommend specific brand names — use NPK ratios and WIN percentages only.
12. "Applications" not "trips" when describing fertilizer frequency.

---

## Attributions

- **Chantel Wilson** — Assistant Professor and 4-H STEAM Extension Specialist, College of Agriculture, Virginia State University
- **Michael Goatley Jr.** — Professor and Extension Specialist, School of Plant and Environmental Sciences, Virginia Tech

Virginia Cooperative Extension is a partnership of Virginia Tech, Virginia State University, the U.S. Department of Agriculture, and local governments.

---

## Files

| File | Description |
| :---- | :---- |
| `lawn_garden_calc_v1_4.html` | Main application — current version |
| `CLAUDE.md` | This file — project context for AI-assisted development |
| `README.md` | User-facing documentation |
