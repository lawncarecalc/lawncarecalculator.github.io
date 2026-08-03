# 🌱 Soil Test Report Assistant

![Version](https://img.shields.io/badge/version-2.0-2c5f3e) ![Build](https://img.shields.io/badge/build-single%20HTML%20file-3d8b5f) ![Sources](https://img.shields.io/badge/built%20from-VCE%20publications-b8862f) ![Region](https://img.shields.io/badge/region-Virginia%20%C2%B7%20Zone%207b-33688f)

> **No more guessing what to feed your lawn or garden.**

An interactive web tool for Virginia homeowners to interpret soil test results and calculate fertilizer and lime needs for **lawns, vegetable gardens, flower beds, and landscape shrubs and trees** — built entirely from official Virginia Cooperative Extension publications and peer-reviewed regional research.

> 🗂️ Single self-contained HTML file. No server, no build step, no external dependencies except Google Fonts.

---

## 🧪 Overview

The calculator accepts soil test reports from two labs. **One question** on the Soil Test tab — "what is this report for?" — tells the app both the lab (VCE / Virginia Tech or Waypoint Analytical) and the purpose (lawn, vegetable garden, flower garden, or shrubs & trees), and every rating scale, unit, and interpretation note adjusts automatically from that single answer.

> 🏛️ **VCE / Virginia Tech Soil Testing Laboratory** — reports in lb/A (P, K) and lbs/1,000 sq. ft. (lawn lime) or lbs/100 sq. ft. (garden lime).

> 🔬 **Waypoint Analytical** — reports in ppm (P, K, micronutrients), dS/m (salts), and lbs/1,000 sq. ft. (all lime). Rating bands use Waypoint's own published values from Agronomy Facts 8.

**The tool is gated by design.** Only the Soil Test Report and About & Instructions tabs are visible when you first open it — every calculator tab is hidden until you've entered a report and disclosed its purpose. This reflects a deliberate philosophy: you shouldn't be able to apply fertilizer without a soil test telling you your starting point. Once you answer that one question, the single matching calculator tab appears (Lime appears alongside Lawn or Shrubs & Trees reports specifically, since lime math applies to either).

---

## 📋 The Tabs

Tab bar order: **Soil Test Report, About & Instructions** (always visible), then six calculator tabs that appear one at a time as your soil test discloses its purpose.

| | Tab | What it does |
| :-- | :-- | :-- |
| 🩺 | **Soil Test Report** | Interprets every value — pH, Buffer Index, P, K, Ca, Mg, organic matter, salts, CEC, base saturation, lime, micronutrients — each with a plain-English card, rating pill, and action. One combined question ("what is this report for?") determines lab, units, and which calculator tab appears. **Continue to [X] Calculator** pre-fills that tab. |
| 📖 | **About & Instructions** | Universal on-ramp (how the gating works), a per-tab mini-guide for each calculator, a dedicated explainer for the Vegetable Garden tab's single-nutrient philosophy, source documentation, and the WIN/program guide. |
| ❄️ | **Cool-Season Lawns** | Tall fescue, bluegrass, ryegrass, fine fescue. Up to 4 custom application slots, each with its own N-P-K and WIN%. Includes clipping-return and shade adjustments. Full CCE-adjusted lime math built in. |
| ☀️ | **Warm-Season Lawns** | Bermuda, St. Augustine, zoysia, centipede — distinct N ceilings per species. Clipping and shade controls; no nitrogen after August 15. Full CCE-adjusted lime math built in. |
| 🪨 | **Lime** | For **Shrubs & Trees** reports only — Cool/Warm-Season Lawns, Vegetable Garden, and Flower Garden all calculate lime directly on their own tab now. Lime quantities adjusted by product CCE and bag size; schedules multiple applications; warns on gypsum. |
| 🥬 | **Vegetable Garden** | Single-nutrient system: pick a crop to see feeding level, target pH, research-based N default, and sidedress timing together; choose a nitrogen source (organic or synthetic, never a blended N-P-K product); phosphorus, potassium, calcium, magnesium, sulfur, and micronutrients each get their own amendment — auto-filled from the Soil Test tab, with an organic/synthetic choice per nutrient and full CCE-adjusted lime math built in. |
| 🌸 | **Flower Garden** | Choose **Complete N-P-K Fertilizer** (one blended product, the default) or **Individual N, P, K Fertilizers** (single-nutrient, same system as Vegetable Garden). Annuals, perennials, roses, spring bulbs. Nitrogen field optional (research-based defaults). Full CCE-adjusted lime math built in. |
| 🌳 | **Shrubs & Trees** | Six plant types. Fertilize only on signs of deficiency. Application area = twice the canopy. Lime, when needed, uses the standalone Lime tab. |

---

## ❄️ Cool-Season Lawn Limits

Annual N ceilings and per-application limits follow **VCE 430-011 (Tables 2–4)** and **DCR 2014**.

| Grass | Annual N ceiling | P1 /app | P2 /app | P3 /app |
| :-- | :-- | :-- | :-- | :-- |
| Tall fescue / bluegrass / ryegrass | 3.5 lbs/1,000 sq. ft. | 0.7 | 0.9 | 1.5 |
| Fine-leaf fescue | 2.0 lbs/1,000 sq. ft. | 0.7 | 0.9 | 1.0 |

🍂 Primary fertilization window: **September through November**.

---

## ☀️ Warm-Season Lawn Limits

| Grass | Annual N ceiling | Notes |
| :-- | :-- | :-- |
| Bermudagrass / St. Augustinegrass | 4.0 lbs/1,000 sq. ft. | Highest-N warm-season grasses |
| Zoysiagrass | 1.0–2.0 lbs/1,000 sq. ft. | Per Soil Test Note 18 / SPES-669 |
| Centipedegrass | **1.0–2.0 lbs/1,000 sq. ft.** ✳️ | Most fertilizer-sensitive grass in Virginia |

> ✳️ **Corrected in v1.7:** centipedegrass was previously listed as 0.5–1.0 lb in error. The VCE annual ceiling is **1.0–2.0 lbs** (Soil Test Note 18 / SPES-669).

> 🛑 **Hard cutoff:** no nitrogen after **August 15** on any warm-season grass. Late-season nitrogen invites winterkill — especially in shade.

---

## 🍃 Site Adjustments &nbsp; `new in v1.7`

Both lawn tabs now adjust the nitrogen plan for two real-world conditions, each grounded in **VCE 430-011**.

> ♻️ **Clipping return** — returning clippings recycles nitrogen. Toggle it on and the calculator reduces your annual target by up to one-third, capped at 1 lb/1,000 sq. ft. — the amount clippings actually return.

> ☁️ **Shade** — a three-position control (full sun / some shade / heavy shade) applies VCE's stated range: heavily shaded grass needs one-half to two-thirds the nitrogen of full sun. Shade reduction applies first, then clippings. Mixed-shade lawns should run the shaded zone as a separate calculation.

---

## 🛒 Choosing a Fertilizer at the Garden Center &nbsp; `expanded v1.7`

The lawn tabs include a **brand-free** reference table that matches commercial grades to your soil's phosphorus rating. Read your P result (Low / Medium / High) and jump to the matching group, then match the N-P-K and WIN on any bag to the closest row. Full table in [`Fertilizer_Grades_Table.md`](Fertilizer_Grades_Table.md).

> ⚠️ **Reading WIN correctly** — Program is set by WIN as a **% of total nitrogen**, not % of bag weight: divide the label's WIN figure by the total N%. A bag with 24% N and "0.6% WIN" is 0.6 ÷ 24 = 2.5% of N → Program 1.

<details>
<summary>📊 <strong>Grades by phosphorus need</strong> (click to expand)</summary>

**If soil tests HIGH / VERY HIGH for P — choose zero-P (prevents runoff):**

| Grade | WIN (% of N) | Program |
| :-- | :-- | :-- |
| 28-0-3 to 32-0-4 | 0–14% | P1 |
| 46-0-0 (urea) | 0% | P1 |
| 32-0-6 (coated urea) | ~30% | P2 |
| 24-0-12 / 24-0-11 | 25–49% | P2 |
| 25-0-5 / 32-0-10 / 39-0-0 | 50–70%+ | P3 |
| 9-0-9 (organic) | ~85%+ | P3 |

**If soil tests MEDIUM for P — a little P is fine:**

| Grade | WIN (% of N) | Program |
| :-- | :-- | :-- |
| 16-4-8 (or 20-5-10, 24-6-12) | varies | by WIN |
| 12-4-8 / 15-5-10 | varies | by WIN |

**If soil tests LOW for P, or NEW lawn — choose higher-P (starter):**

| Grade | WIN (% of N) | Program |
| :-- | :-- | :-- |
| 10-10-10 / 12-12-12 | 0% | P1 |
| 18-24-12 (starter) | 0–50% | by WIN |
| 18-24-6 / 12-25-6 / 24-25-4 | 0–50% | by WIN |

🌊 Apply P only when your soil test calls for it. Starter/high-P grades on High-P soil waste money and run off into waterways. No brands endorsed — the bag's guaranteed-analysis label is always the authority.

</details>

---

## 🔢 Nitrogen Programs (WIN%)

Per **VCE 430-011, Tables 2–4**. The full publication defines three programs; the condensed Soil Test Notes 17/18 describe only the first two.

| Program | WIN% of total N | Per-app ceiling | Notes |
| :-- | :-- | :-- | :-- |
| 🟡 **Program 1** | < 15% | Lower (0.7 cool) | Quick-release; more applications needed |
| 🟢 **Program 2** | 15–49% | Medium (0.9 / 1.0) | Slow-release component on the bag |
| 🔵 **Program 3** | ≥ 50% | Higher | Majority slow-release; fewest applications |

WIN is listed on the fertilizer bag. If no WIN is listed, assume Program 1 — unless the bag names sulfur- or polymer-coated urea, which counts as slowly available.

---

## 🪨 Lime & CCE

Lime quantities are adjusted by the product's **Calcium Carbonate Equivalent (CCE)**, validated against **VCE 452-510**: the adjustment factor is simply 100 ÷ CCE.

> 🔀 **Lime now lives on each tab that needs it, not a separate tab.** The standalone **Lime tab** only appears for **Shrubs & Trees** reports. Cool-Season Lawns, Warm-Season Lawns, Vegetable Garden, and Flower Garden each do the complete CCE-adjusted calculation on their own tab instead — enter your product's CCE and bag size right there, no need to visit a separate tab. The underlying math is factored into a single shared `calcLimeForBed()` function so every tab uses the same formula.

> 🚫 **Gypsum is not lime** — gypsum (calcium sulfate) has a CCE of zero and does not raise pH. Every lime calculator warns if a near-zero CCE is entered.

> 💧 **Pelletized lime timing** — the pellet must absorb moisture and slake before it reacts, so apply it when soil moisture is reliable (fall/early spring or before rain), not into a dry summer lawn. For beds, work it in.

---

## 🥬 Vegetable Garden

Based on **VCE 452-719 / SPES-687P (Soil Test Note 19)** and **VCE 426-323 / SPES-803P (Fertilizing the Vegetable Garden)**, supplemented by UMD Extension, Clemson HGIC, Rutgers NJAES FS626, NC State Extension, Ohio State University Extension, and NMSU Cooperative Extension (see Primary Sources below).

### A single-nutrient system, not a blended fertilizer

Vegetable crops vary widely in how much nitrogen they need — a heavy feeder like tomatoes or corn requires several times more than a light feeder like beans or carrots — but a complete N-P-K fertilizer locks all three nutrients into one fixed ratio, so applying enough of it to meet a crop's nitrogen need almost always over- or under-supplies phosphorus and potassium at the same time. Rather than recommending one N-P-K product for the whole bed, this tab addresses each nutrient that's actually low on its own — VCE Note 19's own approach. Pick a crop and one merged panel shows its feeding level, target soil pH, research-based nitrogen default, and sidedress timing together. Choose a nitrogen source (organic or synthetic, always single-nutrient). Phosphorus, potassium, calcium, magnesium, sulfur, and every micronutrient (zinc, manganese, copper, iron, boron) then each get their own row in the results — rating and amount pulled automatically from the Soil Test tab, with a choice between an organic and a synthetic source wherever both exist, so you're never forced to over-apply one nutrient to correct another. Lime is calculated on this same tab, CCE and bag size included.

If you have a Waypoint report, its "SOIL FERTILITY GUIDELINES" numeric target for any nutrient can be entered directly in that nutrient's own row for a precise amount — sized even when the rating comes back adequate, since Waypoint's target is a maintenance figure, not just a deficiency flag. VCE reports don't print an equivalent number, so those fall back to VCE Note 19's rating-based flat rates instead.

> ⚖️ **Tomatoes and peppers always get the full preplant nitrogen amount, regardless of P/K test level.** VCE Note 19 calls for splitting a *complete fertilizer* in half when soil already tests High/Very High in phosphorus or potassium — the only way to avoid over-applying P/K from a blended product is to reduce the whole dose, nitrogen included. That constraint doesn't exist here: nitrogen is its own separate product, and phosphorus/potassium are each already sized independently (and skipped entirely when adequate) by this tab's own single-nutrient system. So the preplant amount is never split — every crop gets the full amount, then the standard Rutgers FS626 sidedress schedule on top, same as every other crop on this tab.

| Feeding level | Crops |
| :-- | :-- |
| **Heavy feeders** | Tomatoes, peppers & eggplant, potatoes, sweet corn, broccoli & cauliflower, beets & Swiss chard, spinach, onions/garlic/shallots |
| **Medium feeders** | Leafy greens (kale, collards, mustard), lettuce, cucumbers, squash & pumpkins, melons, sweet potatoes, asparagus |
| **Light feeders** | Beans & peas, carrots, root crops (radishes, turnips, parsnips) |

### Sidedress timing

The calculator applies VCE's three-to-four-week timing rule: a nitrogen application has its greatest effect three to four weeks after it is applied. Sidedressing too early pushes vegetative growth at the expense of flowering and fruiting. Crop-specific notes include:

- **Tomatoes & peppers** — sidedress after first fruit set; avoid heavy N before flowering.
- **Potatoes** — excess N promotes vining over tuber development.
- **Sweet corn** — sidedress when plants reach 12 inches.
- **Cucumbers & squash** — sidedress one week after blossoming; repeat three weeks later.
- **Melons** — sidedressing generally not recommended.

### Nitrogen sources

Both synthetic and organic sources are available. Calcium nitrate (15.5-0-0) is the preferred synthetic sidedress product — it supplies calcium alongside nitrogen, which helps prevent calcium-related disorders in sensitive crops (blossom end rot and tip burn are primarily caused by inconsistent watering rather than a true soil calcium shortage, so this helps most reliably when soil calcium itself tests low). Organic options include blood meal (medium-rapid release), fish meal, feather meal (slow release), soybean meal, cottonseed meal, poultry manure, and bat guano. VCE Soil Test Note 19's own flat rates (e.g. 5 lbs blood meal per 100 sq. ft.) are offered as a bypass that skips the percentage calculation entirely.

### Volume estimates and bulk density

Where a product's bulk density is backed by a source meeting this project's sourcing standard (see Primary Sources), the calculator shows both weight and a cups/tablespoons volume estimate. Where no such source exists, it shows weight only and invites you to enter your own product's bulk density (lbs/ft³ or kg/m³, from the label or technical data sheet) for an estimate — **not** the specific gravity from an MSDS/SDS, which reflects the pure crystal or absolute compound density rather than the packaged granular form (confirmed with a real product: a Sulfate of Potash SDS lists SG 2.66 ≈ 166 lbs/ft³ absolute crystal density, while the actual granular product is 75–81 lbs/ft³ loose — using the SDS figure would understate the correct volume by roughly half).

---

## 🌸 Flower Garden

For annual beds, perennial borders, rose gardens, and spring-flowering bulbs. The nitrogen field is **optional** — research-based defaults are used when left blank.

| Type | Default N rate | Key timing rule |
| :-- | :-- | :-- |
| Annual flowers | 0.10 lbs/100 sq. ft. preplant | Optional half-rate mid-season |
| Perennial flowers | 0.10 lbs/100 sq. ft. spring only | Compost often sufficient once established |
| Roses | 0.20 lbs/100 sq. ft. monthly | March–August; stop by August 15 |
| Spring-flowering bulbs | 0.40 lbs/100 sq. ft. | At planting + at emergence; **never after flowering** |

> 🌼 **Avoid excess nitrogen** — it produces lush foliage at the direct expense of blooms.

### Choose how you fertilize

Unlike Vegetable Garden, Flower Garden offers a choice:

- **Complete N-P-K Fertilizer** *(default)* — one blended product supplies nitrogen, phosphorus, and potassium together. Enter a grade directly or pick a common product.
- **Individual N, P, K Fertilizers** — the same single-nutrient system as Vegetable Garden: pick a nitrogen source on its own, and phosphorus/potassium/calcium/magnesium/sulfur/micronutrients each get their own amendment in the results, auto-filled from the Soil Test tab.

In Complete Fertilizer mode, the phosphorus and potassium rows in the results show that they're being handled by the blended product instead of an independent recommendation — so you're never told to add P or K twice.

Lime, in either mode, uses the same CCE-adjusted calculation as Vegetable Garden — enter your product's CCE and bag size directly on this tab.

---

## 🌳 Shrubs & Trees

Based on **VCE Soil Test Note 20 (SPES-336P)** and **VCE 430-018 (HORT-120P)**.

> ✅ **Fertilize only on signs of deficiency.** Healthy plants — and plants next to a regularly fertilized lawn — typically need no supplement.

| Type | N range (lbs/1,000 sq. ft.) | pH target |
| :-- | :-- | :-- |
| Deciduous shrub | 3–6 | 5.5–7.0 |
| Evergreen shrub | 1–3 | 5.0–6.5 |
| Acid-loving shrub (azalea, rhododendron, camellia…) | 1–2 | 4.5–6.0 |
| Deciduous tree | 3–6 | 5.5–7.0 |
| Evergreen tree | 1–3 | 5.0–6.5 |
| Acid-loving tree (pin oak, red maple…) | 1–3 | 4.5–6.0 |

🌲 **Area:** enter canopy diameter or L×W — fertilizer is applied to twice the canopy area, since feeder roots extend well past the drip line (Note 20). **Turf adjacency:** overlap with a fertilized lawn caps each application at 1.5 lbs N/1,000 sq. ft. (430-018).

---

## 🌡️ How to Get a Soil Test

> 🏛️ **VCE / Virginia Tech Soil Testing Laboratory** — forms and sample boxes at your local Extension office. Mail to 145 Smyth Hall (MC 0465), 185 Ag Quad Ln, Blacksburg VA 24061. Fee (in-state): $10 routine, $4 organic-matter add-on. More at [soiltest.vt.edu](https://soiltest.vt.edu).

> 🔬 **Waypoint Analytical** — submit form at [waypointanalytical.com](https://www.waypointanalytical.com). Richmond lab: 7621 Whitepine Road, Richmond VA 23237 · 804-743-9401. Test codes: S1M (lawn) or S3M (garden, includes micronutrients).

🍂 Sample in fall or early spring for the most accurate results. Don't sample when soil is extremely wet. Take 10–12 sub-samples per area and mix before submitting.

---

## 📚 Primary Sources

<details>
<summary>🌿 <strong>VCE Core Publications</strong> (click to expand)</summary>

| Publication | Title |
| :-- | :-- |
| 430-011 / SPES-334P | Lawn Fertilization in Virginia **(authoritative for the 3-program structure)** |
| 430-018 / HORT-120P | Fertilizing Landscape Trees and Shrubs |
| 430-520 / SPES-223P | Fall Lawn Care |
| 430-522 / SPES-669P | Maintenance Calendar for Warm-Season Turfgrasses |
| 430-523 / SPES-670P | Maintenance Calendar for Cool-Season Turfgrasses |
| 452-717 / SPES-306P | Soil Test Note 17 — Cool-Season Grasses *(condensed)* |
| 452-718 / SPES-305P | Soil Test Note 18 — Warm-Season Grasses *(condensed)* |
| 452-719 / SPES-687P | Soil Test Note 19 — Vegetable and Flower Gardens |
| 452-720 / SPES-336P | Soil Test Note 20 — Home Shrubs and Trees |
| 452-701 / SPE-605NP | Soil Test Note 1 — Explanation of Soil Tests |
| 452-510 / SPES-158P | Sources of Lime for Acid Soils in Virginia `added v1.7` |
| 426-323 / SPES-803P | Fertilizing the Vegetable Garden |
| 426-200 / SPES-802P | Annual Flowers: Culture and Maintenance |
| SPES-384NP | Your Soil Test Report Simplified |
| DCR 2014 | Virginia Nutrient Management Standards and Criteria |

Plus the per-crop 426-series vegetable guides (tomatoes, potatoes, sweet corn, brassicas, leafy greens, cucurbits, root crops, beans, alliums).

</details>

**Supplementary regional sources** — used only where VCE is silent; all from land-grant Cooperative Extension programs and consistent with VCE on material points:

- 🌿 **UMD Extension** — vegetable N rates by feeding level; organic-matter N credit; annual/perennial flower care; tree & shrub guidance; general water-soluble-fertilizer application method
- 🌿 **Clemson HGIC** — sidedress guidance; calcium nitrate; tree & shrub timing (ANSI A300)
- 🌿 **Rutgers NJAES** — FS626 organic fertilizer N% and release rates (NPK content only — not a bulk-density source); FS1220 spring bulbs
- 🌿 **NC State Extension** — calcium nitrate rationale; blossom-end-rot framing; spring bulb rates; pelletized-lime timing; manganese application rates and pH-availability guidance (Torres Quezada, 2024 — vegetable-crop-specific rate, cited as the closest sourced figure available, not separately validated for ornamentals)
- 🌿 **Cornell Nutrient Management Spear Program, University of Maryland Extension, Michigan State University Extension** — independently corroborate the manganese pH-availability threshold (~6.5) as general soil chemistry, not tied to any one crop
- 🌿 **UT Extension** — Program 3 (>50% WIN) application-rate corroboration
- 🌿 **Waypoint Agronomy Facts 8** — rating labels, units, Buffer pH terminology, K optimum bands by CEC
- 🌿 **Hood College Center for Coastal and Watershed Studies (FFSN)** — general principle that a water-soluble fertilizer can be dissolved in water and applied to soil in place of a dry broadcast (used for small-quantity micronutrients like manganese and boron, where the calculated amount is often too little dry material to spread evenly by hand)

**Bulk density / volume conversion sources** — a narrow exception to the policy below, used only for physical density data (converting a weight into a cups/volume estimate), never for an agronomic rate or recommendation:

- 🌿 **Ohio State University Extension, Ohioline FABE-550** — bulk density for triple superphosphate and ammonium nitrate
- 🌿 **NMSU Cooperative Extension, Guide H-119** — direct oz/cup bulk density for muriate of potash, elemental sulfur, langbeinite

---

## ⚖️ Source Policy

VCE is always primary. UMD Extension and Clemson HGIC are co-primary where VCE is silent. Rutgers NJAES and NC State are supporting sources. Sources outside the Mid-Atlantic land-grant network are not used, **except** for bulk-density/volume-conversion data specifically (Ohio State, NMSU above) — a narrow exception for physical measurements where no closer regional source publishes the equivalent figure, not a general policy change for agronomic recommendations. Where no source meeting this standard exists for a product's bulk density, the calculator shows weight only rather than an estimated volume, and never accepts an MSDS/SDS specific gravity as a substitute (see Vegetable Garden section above).

> 📐 **Conformance principle** — trace every figure to the **primary** publication, not a secondary or abridged one. The condensed Soil Test Notes (17/18) describe only Programs 1–2; the full **430-011** defines all three. When program structure or per-application caps are in question, 430-011 is the source of truth.

---

## ⚠️ Limitations

- **The tool is gated by design** — every calculator tab is hidden until you enter a soil test report and disclose its purpose on the Soil Test tab. You cannot reach a lawn, garden, or shrub calculator without a soil test's starting point; this is intentional, not a bug.
- **Lawn N cannot be estimated from a soil test** — VCE 430-011 is explicit. The N figure on a lawn report is a research-based guideline, not a measured deficiency. The same is true for vegetable and flower gardens — the nitrogen field is optional and falls back to a research-based default for your crop/flower type when left blank.
- **Healthy shrubs and trees do not need fertilizer** — VCE Note 20 is explicit.
- **Recommendations are valid for ~three years** — retest every 3–4 years for lawns, 2–3 for active vegetable beds.
- **Soil texture is never inferred** from CEC or Buffer Index values.
- **Virginia soils and climate** — primary audience is Chesterfield County and the Piedmont clay belt (Zone 7b); recommendations are appropriate statewide.
- **Flower Garden's "Complete Fertilizer" mode is not available on Vegetable Garden** — this is a deliberate difference between the two tabs, not an inconsistency to be fixed; Vegetable Garden is single-nutrient only.

---

## ♿ Accessibility

The calculator targets **WCAG 2.1 AA** conformance, the standard required by Virginia Tech Policy 7215 and ADA Title II (effective April 24, 2026).

> ⚠️ **The specific counts and automated-tool results below are from the July 6–7, 2026 audit and predate the July 21–29 restructure** (single-nutrient system, tab gating, report-type consolidation, Flower Garden's mode toggle, and related markup changes). The underlying practices remain in place and new instances of each pattern were applied to new markup as it was built, but the exact figures (23 headers, 39 links, etc.) and the axe/Lighthouse scores have not been re-run against the current build. Treat this section as "what the approach has been," not a current scorecard, until a fresh automated pass is run.

### What was done

- **Form labels** — every `<label>` is programmatically associated with its input via `for`/`id` pairing, including dynamically generated fields (application slots, per-nutrient amendment rows, inline Waypoint targets).
- **Tab widget** — full ARIA tab pattern (`role="tablist"`, `role="tab"`, `role="tabpanel"`, `aria-selected`, `aria-controls`). Every visible tab keeps `tabindex="0"` so plain sequential Tab reaches all of them — an earlier "roving tabindex" design (only the active tab in the Tab sequence, others reachable only by arrow key) was tried, found to cause a real, confirmed "Tab skips the next tab" bug via live testing, and reverted. Arrow-key navigation (Left/Right/Home/End) remains available as an additional way to move between tabs, filtered to only the tabs currently visible.
- **Live regions** — result panels use `aria-live="polite"` so screen readers announce updated calculations. Soil test input is debounced at 300ms to prevent announcement chatter.
- **Heading hierarchy** — card-header divs converted to semantic `<h3>` elements; visually hidden `<h2>` added to each tab panel; decorative emoji marked `aria-hidden="true"`. Interactive elements (e.g. sample-report buttons) are never placed inside a `role="heading"` element — this caused a real, confirmed focus-skip bug in Chrome and was fixed by moving the buttons into a sibling `role="toolbar"` region.
- **Color independence** — action boxes include screen-reader-only status prefixes ("Action needed:", "Monitor:", "Good:") so status is conveyed by text, not color alone.
- **Fieldset grouping** — related input pairs (P value + P rating, K, Ca, Mg) wrapped in `<fieldset>` with `<legend>`; micronutrient block grouped with a visible legend.
- **Hidden fields removed from tab order** — form blocks that are hidden until a report type is selected (e.g. the VCE/Waypoint field layouts, lawn-specific fields) carry `inert` alongside `display:none`, so their inputs can't be reached by keyboard while invisible.
- **External links** — `target="_blank"` links include a screen-reader-only "(opens in new tab)" notice and `rel="noopener"`.
- **Toggle buttons** — collapsible-section buttons have `aria-expanded` and `aria-controls`, synced in JavaScript on every open/close.
- **Contrast** — text is designed to pass 4.5:1 minimum contrast ratio against its background. One real failure from this gap was found and fixed July 30, 2026 (two card-header subtitles reused a color token designed for light backgrounds against a dark one, actual ratio 2.2:1) — every other color pairing introduced since the restructure was then checked by computing actual WCAG ratios and all pass, closest margins ~4.76–4.84:1. This was a manual, targeted check, not a full automated re-run — see warning above.
- **Font-size floor** — no text smaller than 0.75rem (12px).
- **Validation** — N-rate inputs linked to validation output via `aria-describedby`; ceiling violations set `aria-invalid="true"` and announce via `role="alert"`.
- **Skip link** — hidden "Skip to main content" link appears on first Tab keypress.

### Testing

Automated (July 6–7, 2026, predates the restructure — see warning above): **axe-core 4.x** via Puppeteer — 0 violations, 42 rules passing. **Lighthouse** — 100 Accessibility. See [`Accessibility_Testing_Checklist.md`](Accessibility_Testing_Checklist.md) for the full manual testing plan.

**WAVE re-scan (July 2026, current build):** 0 errors, 0 contrast errors, AIM Score 9.3/10. 60 alerts, all in two accepted, deliberate categories — "JavaScript jump menu" (every `onchange`-triggered select recalculates instantly rather than waiting for a submit button, by design, for the instant-feedback UX this tool depends on; mitigated via `aria-live` regions rather than adding confirm buttons to ~55 dropdowns) and "Link to PDF document" (external VCE publication links, which already carry a visible "(PDF)" indicator).

---

## 🗂️ Supporting Documents

| Document | Description |
| :-- | :-- |
| `CLAUDE.md` | Development context for AI-assisted sessions — implementation, source boundaries, critical rules, session log |
| `Accessibility_Testing_Checklist.md` | 34-item manual testing plan for WCAG 2.1 AA — keyboard, screen reader, visual, and automated tool checks |
| `Fertilizer_Grades_Table.md` | Brand-free garden-center grades table, organized by phosphorus need |
| `Lawn_Fertilizer_Product_Survey.md` | Full marketplace survey behind the grades table |
| `Liming_Materials_CCE_Survey.md` | CCE values for garden-center liming materials (validates the Lime tab) |
| `Calculator_Conformance_Audit_Plan_v2.md` | Audit methodology with translation / unit / data-flow phases |
| `Conformance_Audit_Findings_Round1.md` / `Round2.md` | Findings from validating against real soil test reports |
| `VCE_Calculator_Fun_Facts.docx` | Highlights for new users |
| `README.html` | Styled (color) version of this README for hosted use |

---

## 🙏 Attributions

- **Chantel Wilson** — Assistant Professor and 4-H STEAM Extension Specialist, Virginia State University
- **Michael Goatley Jr.** — Professor and Extension Specialist, Virginia Tech

Virginia Cooperative Extension is a partnership of Virginia Tech, Virginia State University, the U.S. Department of Agriculture (USDA), and local governments, and is an equal opportunity employer. For the full nondiscrimination statement, please visit ext.vt.edu/accessibility.

**Disclaimer:** Commercial products are named in this publication for informational purposes only. Virginia Cooperative Extension does not endorse these products and does not intend discrimination against other products that also might be suitable.

**Declaration of AI assistance:** During the preparation of this tool, the author(s) used Claude (Anthropic) to assist with code generation, content drafting, and document synthesis. After using this tool, the author(s) reviewed and edited the content as needed and take full responsibility for the content of this publication.

> 🌱 *This calculator is not an official VCE product. It is a homeowner tool built from VCE publications for personal use.*
