# 🌱 VCE Lawn & Garden Care Calculator

![Version](https://img.shields.io/badge/version-1.7-2c5f3e) ![Build](https://img.shields.io/badge/build-single%20HTML%20file-3d8b5f) ![Sources](https://img.shields.io/badge/built%20from-VCE%20publications-b8862f) ![Region](https://img.shields.io/badge/region-Virginia%20%C2%B7%20Zone%207b-33688f)

An interactive web tool for Virginia homeowners to interpret soil test results and calculate fertilizer and lime needs for **lawns, vegetable gardens, flower beds, and landscape shrubs and trees** — built entirely from official Virginia Cooperative Extension publications and peer-reviewed regional research.

> 🗂️ Single self-contained HTML file. No server, no build step, no external dependencies except Google Fonts.

---

## 🧪 Overview

The calculator accepts soil test reports from two labs and adjusts rating scales, units, and interpretation notes automatically when you select your lab:

> 🏛️ **VCE / Virginia Tech Soil Testing Laboratory** — reports in lb/A (P, K) and lbs/1,000 sq. ft. (lawn lime) or lbs/100 sq. ft. (garden lime).

> 🔬 **Waypoint Analytical** — reports in ppm (P, K, micronutrients), dS/m (salts), and lbs/1,000 sq. ft. (all lime). Rating bands use Waypoint's own published values from Agronomy Facts 8.

---

## 📋 The Eight Tabs

| | Tab | What it does |
| :-- | :-- | :-- |
| 🩺 | **1. Soil Test Report** | Interprets every value — pH, Buffer Index, P, K, Ca, Mg, organic matter, salts, CEC, base saturation, lime, micronutrients — each with a plain-English card, rating pill, and action. **Apply to Calculators** pre-fills the other tabs. |
| ❄️ | **2. Cool-Season Lawns** | Tall fescue, bluegrass, ryegrass, fine fescue. Up to 4 custom application slots, each with its own N-P-K and WIN%. Includes clipping-return and shade adjustments. |
| ☀️ | **3. Warm-Season Lawns** | Bermuda, St. Augustine, zoysia, centipede — distinct N ceilings per species. Clipping and shade controls; no nitrogen after August 15. |
| 🪨 | **4. Lime** | Lime quantities adjusted by product CCE and bag size. Schedules multiple applications, warns on gypsum, explains pelletized-lime timing. |
| 🥬 | **5. Vegetable Garden** | 20 crops with preplant N rates and separate sidedress schedules. Organic-matter nitrogen credit for high-OM beds. |
| 🌸 | **6. Flower Garden** | Annuals, perennials, roses, spring bulbs. Nitrogen field optional (research-based defaults). Bloom-aware advisory for high-OM beds. |
| 🌳 | **7. Shrubs & Trees** | Six plant types. Fertilize only on signs of deficiency. Application area = twice the canopy. |
| 📖 | **8. About & Instructions** | Source documentation, WIN/program guide, VCE-vs-Waypoint rating comparison, step-by-step usage. |

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

> ⚠️ **Reading WIN correctly** — Program is set by WIN as a **percent of total nitrogen**, not percent of bag weight: divide the label's WIN figure by the total N%. A bag with 24% N and "0.6% WIN" is 0.6 ÷ 24 = 2.5% of N → Program 1.

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

## 🪨 Lime & CCE &nbsp; `enhanced v1.7`

The Lime tab adjusts the recommended amount by the product's **Calcium Carbonate Equivalent (CCE)**, validated against **VCE 452-510**: the adjustment factor is simply 100 ÷ CCE.

> 🚫 **Gypsum is not lime** — gypsum (calcium sulfate) has a CCE of zero and does not raise pH. The Lime tab warns if a near-zero CCE is entered.

> 💧 **Pelletized lime timing** — the pellet must absorb moisture and slake before it reacts, so apply it when soil moisture is reliable (fall/early spring or before rain), not into a dry summer lawn. For beds, work it in.

---

## 🌸 Flower Garden Defaults

The nitrogen field is **optional** — research-based defaults are used when left blank.

| Type | Default N rate | Key timing rule |
| :-- | :-- | :-- |
| Annual flowers | 0.10 lbs/100 sq. ft. preplant | Optional half-rate mid-season |
| Perennial flowers | 0.10 lbs/100 sq. ft. spring only | Compost often sufficient once established |
| Roses | 0.20 lbs/100 sq. ft. monthly | March–August; stop by August 15 |
| Spring-flowering bulbs | 0.40 lbs/100 sq. ft. | At planting + at emergence; **never after flowering** |

> 🌼 **High organic matter** — because excess nitrogen suppresses bloom, high-OM beds get a flower-specific advisory to lean toward the low end of any nitrogen rate, or skip it.

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

- 🌿 **UMD Extension** — vegetable N rates by feeding level; organic-matter N credit; annual/perennial flower care; tree & shrub guidance
- 🌿 **Clemson HGIC** — sidedress guidance; calcium nitrate; tree & shrub timing (ANSI A300)
- 🌿 **Rutgers NJAES** — FS626 organic fertilizer release rates & sidedress amounts; FS1220 spring bulbs
- 🌿 **NC State Extension** — calcium nitrate rationale; blossom-end-rot framing; spring bulb rates; **pelletized-lime timing**
- 🌿 **UT Extension** — Program 3 (>50% WIN) application-rate corroboration
- 🌿 **Waypoint Agronomy Facts 8** — rating labels, units, Buffer pH terminology, K optimum bands by CEC

---

## ⚖️ Source Policy

VCE is always primary. UMD Extension and Clemson HGIC are co-primary where VCE is silent. Rutgers NJAES and NC State are supporting sources. Sources outside the Mid-Atlantic land-grant network are not used.

> 📐 **Conformance principle** — trace every figure to the **primary** publication, not a secondary or abridged one. The condensed Soil Test Notes (17/18) describe only Programs 1–2; the full **430-011** defines all three. When program structure or per-application caps are in question, 430-011 is the source of truth.

---

## ⚠️ Limitations

- **Requires a soil test** for lawn and vegetable calculators. Flower and shrub/tree tabs offer research-based defaults when no test is available.
- **Lawn N cannot be estimated from a soil test** — VCE 430-011 is explicit. The N figure on a lawn report is a research-based guideline, not a measured deficiency.
- **Healthy shrubs and trees do not need fertilizer** — VCE Note 20 is explicit.
- **Recommendations are valid for ~3 years** — retest every 3–4 years for lawns, 2–3 for active vegetable beds.
- **Soil texture is never inferred** from CEC or Buffer Index values.
- **Virginia soils and climate** — primary audience is Chesterfield County and the Piedmont clay belt (Zone 7b); recommendations are appropriate statewide.

---

## 🗂️ Supporting Documents

| Document | Description |
| :-- | :-- |
| `CLAUDE.md` | Development context for AI-assisted sessions — implementation, source boundaries, critical rules, session log |
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

Virginia Cooperative Extension is a partnership of Virginia Tech, Virginia State University, the U.S. Department of Agriculture, and local governments.

> 🌱 *This calculator is not an official VCE product. It is a homeowner tool built from VCE publications for personal use.*
