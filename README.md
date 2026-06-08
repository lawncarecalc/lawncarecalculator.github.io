# VCE Lawn & Garden Care Calculator

**Version 1.6 — June 2026**

An interactive web tool for Virginia homeowners to interpret soil test results and calculate fertilizer and lime needs for lawns, vegetable gardens, flower beds, and landscape shrubs and trees. Built entirely from official Virginia Cooperative Extension publications and peer-reviewed regional research.

Single self-contained HTML file. No server, no build step, no external dependencies except Google Fonts.

---

## Overview

The calculator accepts soil test reports from two labs:

- **VCE / Virginia Tech Soil Testing Laboratory** — reports in lb/A (P, K) and lbs/1,000 sq. ft. (lawn lime) or lbs/100 sq. ft. (garden lime)  
- **Waypoint Analytical** — reports in ppm (P, K, micronutrients), dS/m (salts), and lbs/1,000 sq. ft. (all lime)

Rating scales, units, and interpretation notes adjust automatically when you select your lab.

---

## Tabs

### 1\. Soil Test Report

Interprets every value on your soil test report — pH, Buffer Index/Buffer pH, P, K, Ca, Mg, organic matter, soluble salts, CEC, base saturation, lime recommendation, and micronutrients (Zn, Mn, Cu, Fe, B). Each measurement gets its own interpretation card with a plain-English explanation, a rating pill, and a specific action recommendation.

**New vs. existing lawn:** Select whether your sample was taken before seeding/sodding or for an existing lawn. The interpretation card adjusts its guidance accordingly.

**Garden and plant type:** Select vegetable garden, flower bed type, or shrub/tree type. The interpretation card routes you to the appropriate calculator tab and adjusts its guidance for that plant category.

Once values are entered, click **Apply to Calculators** to pre-fill area size, P/K ratings, lime recommendation, plant type, and lime type into the relevant calculator tabs automatically.

### 2\. Cool-Season Lawns

For tall fescue, Kentucky bluegrass, perennial ryegrass, and fine-leaf fescue. Calculates fertilizer quantities for up to 4 custom application slots per season. Each slot accepts its own N-P-K grade and WIN% (Water Insoluble Nitrogen), enabling mixed programs.

Annual N ceilings and per-application limits follow VCE Publication 430-011 and DCR 2014:

| Grass | Annual N ceiling | P1 max/app | P2 max/app | P3 max/app |
| :---- | :---- | :---- | :---- | :---- |
| Tall fescue / bluegrass / ryegrass | 3.5 lbs/1,000 sq. ft. | 0.7 | 0.9 | 1.5 |
| Fine-leaf fescue | 2.0 lbs/1,000 sq. ft. | 0.7 | 0.9 | 1.0 |

Primary fertilization window: September through November (SON framework).

### 3\. Warm-Season Lawns

For bermudagrass, St. Augustinegrass, zoysiagrass, and centipedegrass. Three separate species with distinct N ceilings:

| Grass | Annual N ceiling | Notes |
| :---- | :---- | :---- |
| Bermudagrass / St. Augustinegrass | 4.0 lbs/1,000 sq. ft. |  |
| Zoysiagrass | 2.0 lbs/1,000 sq. ft. |  |
| Centipedegrass | 1.0 lbs/1,000 sq. ft. | Most fertilizer-sensitive grass in Virginia; flat 0.5 lb per-app cap all programs |

Hard cutoff: no nitrogen after August 15 on any warm-season grass.

### 4\. Lime

Calculates lime product quantities from the lbs/1,000 sq. ft. recommendation. Enter lawn size, product CCE, and bag size. Schedules multiple applications automatically when single-application limits are exceeded.

### 5\. Vegetable Garden

For vegetable beds and mixed beds (vegetables with flowers). Based on VCE Soil Test Note 19 (SPES-687P) and VCE Publication 426-323.

Crop types with N rates and sidedress schedules for 20 crops. The N recommendation from your soil test is the preplant amount only — sidedress amounts are calculated separately.

### 6\. Flower Garden

For annual beds, perennial borders, rose gardens, and spring-flowering bulbs. **The nitrogen field is optional** — research-based defaults are used when left blank.

| Type | Default N rate | Key timing rule |
| :---- | :---- | :---- |
| Annual flowers | 0.10 lbs/100 sq. ft. preplant | Optional half-rate mid-season |
| Perennial flowers | 0.10 lbs/100 sq. ft. spring only | Compost often sufficient for established beds |
| Roses | 0.20 lbs/100 sq. ft. monthly | March–August; stop by August 15 |
| Spring-flowering bulbs | 0.40 lbs/100 sq. ft. | At planting (fall) \+ at emergence (spring); **never after flowering** |

### 7\. Shrubs & Trees

For landscape shrubs and trees. Based on VCE Soil Test Note 20 (SPES-336P) and VCE Publication 430-018 (HORT-120P).

**Fertilization is only recommended when plants show signs of deficiency.** Healthy plants, and plants adjacent to a regularly fertilized lawn, typically need no supplement.

Six plant types:

| Type | N range (lbs/1,000 sq. ft.) | pH target |
| :---- | :---- | :---- |
| Deciduous shrub | 3–6 | 5.5–7.0 |
| Evergreen shrub | 1–3 | 5.0–6.5 |
| Acid-loving shrub (azalea, rhododendron, camellia…) | 1–2 | 4.5–6.0 |
| Deciduous tree | 3–6 | 5.5–7.0 |
| Evergreen tree | 1–3 | 5.0–6.5 |
| Acid-loving tree (pin oak, red maple…) | 1–3 | 4.5–6.0 |

**Area calculation:** Enter canopy diameter or L×W — the calculator automatically applies fertilizer to twice the canopy area, as feeder roots extend well beyond the drip line (VCE Note 20).

**Turf adjacency:** If the application area overlaps a fertilized lawn, each application is capped at 1.5 lbs N/1,000 sq. ft. to avoid turf burn (VCE 430-018). Fully adjacent plantings are flagged as likely needing no supplement.

### 8\. About & Instructions

Source documentation, WIN/program guide, rating scale comparison (VCE vs. Waypoint), and step-by-step usage instructions.

---

## Glossary Tooltips

Terms throughout the calculator that users may need defined — WIN, Buffer Index, CEC, pH, preplant, sidedress, and others — are underlined with a dotted green line. Hover (desktop) or tap (mobile) to see a plain-English definition. Tooltips are positioned using fixed viewport coordinates and are never clipped by card boundaries.

**Current glossary terms:** WIN / Water Insoluble Nitrogen, Buffer Index, Buffer pH, base saturation, CEC / cation exchange capacity, pH, lime / liming, dolomitic lime, nitrogen, phosphorus / phosphate, potassium / potash, organic matter, preplant, sidedress / sidedressing, slow-release / controlled-release.

---

## Nitrogen Programs (WIN%)

| Program | WIN% on bag | Per-application ceiling | Notes |
| :---- | :---- | :---- | :---- |
| Program 1 | \< 15% WIN | Lower | Quick-release; requires more applications |
| Program 2 | 15–49% WIN | Medium | Slow-release component listed on bag |
| Program 3 | ≥ 50% WIN | Higher | Majority slow-release; fewer applications needed |

WIN is always listed on the fertilizer bag label. If no WIN is listed, assume Program 1\.

---

## How to Get a Soil Test

**VCE / Virginia Tech Soil Testing Laboratory**

- Forms and sample boxes: your local Virginia Cooperative Extension office  
- Mailing address: 145 Smyth Hall (MC 0465), 185 Ag Quad Ln, Blacksburg VA 24061  
- Fee (in-state): $10 routine; $4 organic matter add-on  
- More information: [soiltest.vt.edu](https://soiltest.vt.edu)

**Waypoint Analytical**

- Submit form: [waypointanalytical.com](https://www.waypointanalytical.com)  
- Richmond lab: 7621 Whitepine Road, Richmond VA 23237 · 804-743-9401  
- Test codes: S1M (lawn) or S3M (garden, includes micronutrients)

Sample in fall or early spring for most accurate results. Do not sample when soil is extremely wet. Take 10–12 sub-samples per area and mix before submitting.

---

## Primary Sources

### VCE Core Publications

| Publication | Title |
| :---- | :---- |
| 430-011 / SPES-334P | Lawn Fertilization in Virginia |
| 430-018 / HORT-120P | Fertilizing Landscape Trees and Shrubs |
| 430-520 / SPES-223P | Fall Lawn Care |
| 430-522 / SPES-669P | Maintenance Calendar for Warm-Season Turfgrasses |
| 430-523 / SPES-670P | Maintenance Calendar for Cool-Season Turfgrasses |
| 452-717 / SPES-306P | Soil Test Note 17 — Cool-Season Grasses |
| 452-718 / SPES-305P | Soil Test Note 18 — Warm-Season Grasses |
| 452-719 / SPES-687P | Soil Test Note 19 — Vegetable and Flower Gardens |
| 452-720 / SPES-336P | Soil Test Note 20 — Home Shrubs and Trees |
| 452-701 / SPE-605NP | Soil Test Note 1 — Explanation of Soil Tests |
| 426-200 / SPES-802P | Annual Flowers: Culture and Maintenance |
| 426-323 / SPES-803P | Fertilizing the Vegetable Garden |
| 426-418 / SPES-795P | Tomatoes |
| 426-413 / SPES-794 | Potatoes, Peppers and Eggplant |
| 426-405 / SPES-780P | Sweet Corn |
| 426-403 / SPES-792P | Cole Crops or Brassicas |
| 426-408 / SPES-785P | Leafy Green Vegetables |
| 426-406 / SPES-779P | Cucumbers, Melons and Squash |
| 426-422 / SPES-789P | Root Crops |
| 426-402 / SPES-676NP | Beans |
| 426-411 / SPES-788P | Onions, Garlic and Shallots |
| SPES-384NP | Your Soil Test Report Simplified |
| SPES-397 | Fertilizing Landscape Trees and Shrubs — Basic |
| DCR 2014 | Virginia Nutrient Management Standards and Criteria |

### Supplementary Regional Sources

Used to supplement VCE where VCE is silent. All are from land-grant university Cooperative Extension programs and are consistent with VCE on all material points.

**Vegetable Garden**

- UMD Extension — N rates by feeding level; organic matter N credit; fish emulsion in cool soils  
- Clemson HGIC — Sidedress product guidance; calcium nitrate as preferred sidedress N source  
- Rutgers NJAES FS626 — Organic fertilizer N% and release rates; crop-specific sidedress amounts  
- NC State Cooperative Extension — Calcium nitrate rationale; blossom end rot framing  
- Mid-Atlantic Commercial Veg Guide 2026/2027 — Per-crop pH targets (principles only)

**Flower Garden**

- UMD Extension — Care of Annuals and Perennials (0.10 lbs N/100 sq. ft.; spring timing; compost alternative)  
- Rutgers NJAES FS1220 — Spring Flowering Bulbs (no post-bloom fertilization; treat as perennials)  
- NC State Extension (Franklin County) — Spring Flowering Bulbs: 4 lbs 10-10-10/100 sq. ft. at planting and at emergence; pH target 5.8–6.5  
- NC State Extension (Wayne County) — Plant Bulbs This Fall: confirms 10-10-10 for both slow-release and quick-release fertilization options

**Shrubs & Trees**

- UMD Extension — Fertilizing Trees and Shrubs (no fertilizer at planting; 2–3 lbs N max; shallow evergreen roots)  
- Clemson HGIC — Fertilizing Trees & Shrubs (ANSI A300 standard; active uptake timing)

### Lab Reference

- Waypoint Analytical — Agronomy Facts 8 (rating labels, dS/m units, Buffer pH terminology)

---

## Source Policy

VCE is always primary. UMD Extension and Clemson HGIC are co-primary for topics where VCE is silent. Rutgers NJAES and NC State are supporting sources. The Mid-Atlantic Commercial Veg Guide is cited for principles only — not rates. Sources outside the Mid-Atlantic land-grant network are not used.

**Source boundaries by topic:**

- Lawn N rates: VCE 430-011 only  
- Warm-season grass ceilings: VCE SPES-669/670 (centipedegrass cap derived from agronomic principle; VCE 452-718 is best available VCE citation)  
- Spring-flowering bulbs: NC State Extension (Franklin County \+ Wayne County) \+ Rutgers NJAES FS1220 (VCE is silent at home-garden rate level). Rate: 4 lbs 10-10-10 per 100 sq. ft. \= 0.40 lbs N per application.  
- Shrub/tree N rates: VCE 430-018 as primary  
- Flower N rates: VCE Note 19 as primary; UMD Extension confirms

---

## Limitations

- **Requires a soil test** for lawn and vegetable calculators. Flower and shrub/tree tabs provide research-based defaults when no soil test is available.  
- **Virginia soils and climate** — Primary audience is Chesterfield County and the Piedmont clay belt (Zone 7b). Recommendations are appropriate statewide.  
- **Lawn N cannot be estimated from a soil test** — VCE 430-011 is explicit on this. The N recommendation on a lawn soil test report is a research-based guideline, not a measured deficiency.  
- **Healthy shrubs and trees do not need fertilizer** — VCE Note 20 is explicit. The Shrubs & Trees tab opens with this guidance prominently displayed.  
- **Recommendations are valid for 3 years** — Retest every 3–4 years for lawns, every 2–3 years for active vegetable beds.  
- **Soil texture is not inferred** — The calculator never infers sandy, clay, or loam classification from CEC or Buffer Index values.

---

## Supporting Documents

| Document | Description |
| :---- | :---- |
| `CLAUDE.md` | Development context for AI-assisted sessions — technical implementation details, source boundaries, critical rules |
| `VCE_Calculator_Development_History.docx` | Full development history February–May 2026 |
| `VCE_Calculator_User_Guide.docx` | Plain-language user guide |
| `VCE_Calculator_Fun_Facts.docx` | 11 highlights for new users |
| `Soil_Test_Challenges_and_Solutions.docx` | Lawn soil test interpretation challenges and solutions |
| `Garden_Soil_Test_Challenges_and_Solutions.docx` | Garden soil test challenges and solutions |

---

## Attributions

- **Chantel Wilson** — Assistant Professor and 4-H STEAM Extension Specialist, Virginia State University  
- **Michael Goatley Jr.** — Professor and Extension Specialist, Virginia Tech

Virginia Cooperative Extension is a partnership of Virginia Tech, Virginia State University, the U.S. Department of Agriculture, and local governments.

*This calculator is not an official VCE product. It is a homeowner tool built from VCE publications for personal use.*  
