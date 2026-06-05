# VCE Lawn & Garden Care Calculator

**Version 1.5 — June 2026**

An interactive web tool for Virginia homeowners to interpret soil test results and calculate fertilizer and lime needs for lawns, vegetable gardens, and flower beds. Built entirely from official Virginia Cooperative Extension publications and peer-reviewed regional research.

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

**New vs. existing lawn:** Select whether your sample was taken for a new lawn (before seeding or sodding) or an existing lawn. The interpretation card adjusts its guidance accordingly — new lawns should incorporate lime and fertilizer before seeding and use a starter fertilizer; existing lawns follow the standard seasonal program.

Once values are entered, click **Apply to Calculators** to pre-fill area size, P/K ratings, lime recommendation, and lime type into the relevant calculator tabs automatically.

### 2\. Cool-Season Lawns

For tall fescue, Kentucky bluegrass, perennial ryegrass, and fine-leaf fescue. Calculates fertilizer quantities for up to 4 custom application slots per season. Each slot accepts its own N-P-K grade and WIN% (Water Insoluble Nitrogen), enabling mixed programs (e.g. a P-correcting starter in fall plus N-only maintenance applications).

Annual N ceilings and per-application limits follow VCE Publication 430-011 and DCR 2014:

| Grass | Annual N ceiling | P1 max/app | P2 max/app | P3 max/app |
| :---- | :---- | :---- | :---- | :---- |
| Tall fescue / bluegrass / ryegrass | 3.5 lbs/1,000 sq. ft. | 0.7 | 0.9 | 1.5 |
| Fine-leaf fescue | 2.0 lbs/1,000 sq. ft. | 0.7 | 0.9 | 1.0 |

Primary fertilization window: September through November (SON framework).

### 3\. Warm-Season Lawns

For bermudagrass, St. Augustinegrass, zoysiagrass, and centipedegrass. Three grass types with separate N ceilings:

| Grass | Annual N ceiling | P1 max/app | P2 max/app | P3 max/app |
| :---- | :---- | :---- | :---- | :---- |
| Bermudagrass / St. Augustinegrass | 4.0 lbs/1,000 sq. ft. | 0.9 | 1.0 | 1.5 |
| Zoysiagrass | 2.0 lbs/1,000 sq. ft. | 0.7 | 1.0 | 1.0 |
| Centipedegrass | 1.0 lbs/1,000 sq. ft. | 0.5 | 0.5 | 0.5 |

Centipedegrass is intentionally more restricted than zoysiagrass — it is among the most fertilizer-sensitive grasses in Virginia and prone to thatch-related decline at higher N rates.

Primary fertilization window: April through August 15\. The August 15 cutoff is a hard limit — late-season nitrogen on warm-season grasses increases winterkill risk.

**Waypoint note:** Waypoint N recommendations can reach the upper end of the Virginia range, which is appropriate for bermudagrass but too high for zoysiagrass and far too high for centipedegrass. Always verify your chosen annual rate against the ceilings above.

### 4\. Lime

Calculates lime product quantities from the lbs/1,000 sq. ft. recommendation on your soil test report. Enter your lawn size, the CCE (Calcium Carbonate Equivalent) of your lime product, and bag size. Lime is applied in increments of no more than 50 lbs/1,000 sq. ft. at a time; the calculator schedules multiple applications automatically when needed.

### 5\. Vegetable Garden

For vegetable beds and mixed beds (vegetables with flowers). Based primarily on VCE Soil Test Note 19 (SPES-687P) and VCE Publication 426-323.

**Crop types and N rates:**

| Feeding level | N rate (preplant) | Crops |
| :---- | :---- | :---- |
| Heavy feeder | 0.20 lbs/100 sq. ft. | Tomatoes, peppers, corn, broccoli, cabbage, beets, spinach, onions, okra, potatoes |
| Medium feeder | 0.20 lbs/100 sq. ft. | Leafy greens, lettuce, cucumbers, squash, melons, sweet potatoes, asparagus |
| Light feeder | 0.10 lbs/100 sq. ft. | Beans/peas, carrots, root crops |
| Mixed bed | 0.20 lbs/100 sq. ft. | No single sidedress schedule — advisory note only |

The N recommendation from your soil test is the **preplant amount only**. Sidedress amounts are additional fixed applications from crop-specific research and are calculated separately in the application plan table.

**Crop-specific sidedress guidance** is available through the "Vegetable crop fertilizer guidance" collapsible for 20 crops, sourced from Rutgers FS626, VCE 426-series, Clemson HGIC, and UMD Extension.

**Waypoint note:** Waypoint garden reports provide N in lbs/1,000 sq. ft. — the calculator converts to lbs/100 sq. ft. automatically.

### 6\. Flower Garden

For annual flower beds, perennial flower borders, rose gardens, and spring-flowering bulbs. Based on VCE Soil Test Note 19, VCE Publication 426-200, UMD Extension, Rutgers NJAES, and NC State Extension.

**The nitrogen field is optional on this tab.** If you don't have a soil test N recommendation, the calculator uses research-based defaults for your flower type and clearly labels them as defaults. Users with a soil test can enter their result to override.

**Flower types and default N rates:**

| Type | Default N rate | Primary sources | Key timing rule |
| :---- | :---- | :---- | :---- |
| Annual flowers | 0.10 lbs/100 sq. ft. preplant | VCE Note 19; UMD Extension | Optional half-rate mid-season for heavy bloomers; wash off foliage |
| Perennial flowers | 0.10 lbs/100 sq. ft. spring only | VCE Note 19; UMD Extension; Rutgers NJAES | Compost often sufficient for established beds; no late-season N |
| Roses | 0.20 lbs/100 sq. ft. monthly | VCE Note 19 | March through August; **stop by August 15** |
| Spring-flowering bulbs | 0.36 lbs/100 sq. ft. | NC State spring bulb trials; Rutgers NJAES FS1220 | At planting (fall) \+ at emergence (spring); **never after flowering** |

**Critical bulb rule:** Never fertilize spring-flowering bulbs after they have started flowering. Post-bloom fertilization encourages bulb rot and disease, and may shorten flower life. Allow foliage to die back naturally to recharge the bulbs for next year.

**Excess nitrogen and flowers:** Unlike vegetables, flowering plants respond poorly to excess N — it produces lush foliage at the direct expense of blooms. Apply conservatively.

### 7\. About & Instructions

Source documentation, WIN/program guide, rating scale comparison (VCE vs. Waypoint), and step-by-step usage instructions.

---

## Nitrogen Programs (WIN%)

This calculator uses the three-program framework from VCE Publication 430-011:

| Program | WIN% on bag | Per-application ceiling | Notes |
| :---- | :---- | :---- | :---- |
| Program 1 | \< 15% WIN | Lower | Quick-release (urea, ammonium sulfate); requires more applications |
| Program 2 | 15–49% WIN | Medium | Slow-release component listed on bag |
| Program 3 | ≥ 50% WIN | Higher | Majority slow-release; fewer applications needed |

WIN (Water Insoluble Nitrogen) is always listed on the fertilizer bag label. If no WIN is listed, assume Program 1\.

---

## How to Get a Soil Test

**VCE / Virginia Tech Soil Testing Laboratory**

- Forms and sample boxes: your local Virginia Cooperative Extension office  
- Mailing address: 145 Smyth Hall (MC 0465), 185 Ag Quad Ln, Blacksburg VA 24061  
- Fee (in-state): $10 routine test; $4 organic matter add-on  
- More information: [soiltest.vt.edu](https://soiltest.vt.edu)

**Waypoint Analytical**

- Submit form: [waypointanalytical.com](https://www.waypointanalytical.com)  
- Richmond lab: 7621 Whitepine Road, Richmond VA 23237 · 804-743-9401  
- Test codes for home use: S1M (lawn) or S3M (garden, includes micronutrients)

Sample in fall or early spring for most accurate results. Do not sample when soil is extremely wet. Take 10–12 sub-samples per area and mix before submitting.

---

## Primary Sources

All rate calculations, application limits, and timing guidance derive from the sources below. The calculator never invents or extrapolates — every threshold and recommendation is traceable to a specific publication.

### VCE Core Publications

| Publication | Title |
| :---- | :---- |
| 430-011 / SPES-334P | Lawn Fertilization in Virginia |
| 430-520 / SPES-223P | Fall Lawn Care |
| 430-522 / SPES-669P | Maintenance Calendar for Warm-Season Turfgrasses |
| 430-523 / SPES-670P | Maintenance Calendar for Cool-Season Turfgrasses |
| 452-717 / SPES-306P | Soil Test Note 17 — Cool-Season Grasses |
| 452-718 / SPES-305P | Soil Test Note 18 — Warm-Season Grasses |
| 452-719 / SPES-687P | Soil Test Note 19 — Vegetable and Flower Gardens |
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
| DCR 2014 | Virginia Nutrient Management Standards and Criteria |

### Supplementary Regional Sources (Vegetable Garden)

Used to supplement VCE Note 19 for home garden topics where VCE is silent. All are from land-grant university Cooperative Extension programs in the Mid-Atlantic region and consistent with VCE on all material points.

- **UMD Extension** — N rates by feeding level; organic matter N credit (garden context only); fish emulsion in cool soils  
- **Clemson HGIC** — Sidedress product guidance; calcium nitrate as preferred sidedress N source; sandy soil splitting  
- **Rutgers NJAES FS626** — Organic fertilizer N% and release rates; crop-specific sidedress amounts (Table 2\)  
- **NC State Cooperative Extension** — Calcium nitrate rationale; blossom end rot framing  
- **Mid-Atlantic Commercial Veg Guide 2026/2027** — Per-crop pH targets (principles only — commercial guide)

### Supplementary Regional Sources (Flower Garden)

Used where VCE Note 19 is silent, particularly for perennial N rates and spring-flowering bulbs.

- **UMD Extension — Care of Annuals and Perennials** — 0.10 lbs N/100 sq. ft. for annuals and perennials; spring-only timing for perennials; compost as alternative  
- **Rutgers NJAES FS1220 — Spring Flowering Bulbs** — No post-bloom fertilization; treat spring bulbs as perennials; divide when flowers decline  
- **NC State Extension — Spring-Flowering Bulbs Trials** — N is the primary nutrient need for bulbs (not phosphorus); 4 lbs 9-9-6 per 100 sq. ft. trial rate; two-application protocol (planting \+ emergence)

### Lab Reference

- **Waypoint Analytical — Agronomy Facts 8** — Waypoint rating labels, dS/m salt units, Buffer pH terminology

---

## Source Policy

VCE is always primary. UMD Extension and Clemson HGIC are co-primary for home garden topics where VCE is silent. Rutgers FS626 and NC State are supporting sources for vegetable gardens. NC State and Rutgers NJAES are primary for spring-flowering bulbs (VCE does not publish a home-garden bulb N rate). The Mid-Atlantic Commercial Veg Guide is cited for principles only — not rates.

Sources outside this hierarchy (OSU, UNH, non-regional extensions) are not used.

---

## Limitations

- **Requires a soil test** for the lawn and vegetable calculators. The flower tab provides research-based defaults for users without a soil test; all other tabs require a soil test N or lime recommendation to generate quantities.  
- **Virginia soils and climate** — Primary audience is Chesterfield County and the Piedmont clay belt (Zone 7b). Recommendations are appropriate statewide but are calibrated for Virginia conditions.  
- **Lawn N cannot be estimated from a soil test** — VCE 430-011 is explicit: turfgrass nitrogen requirements cannot be reliably evaluated by a soil test. The N recommendation on a lawn soil test report is a research-based guideline, not a measured deficiency.  
- **Recommendations are valid for 3 years** — Lime and fertilizer recommendations from a single soil test cover up to three growing seasons. Retest every 3–4 years for lawns, every 2–3 years for active vegetable beds.  
- **Soil texture is not inferred** — The calculator never infers sandy, clay, or loam classification from CEC or Buffer Index values. Soil texture affects leaching risk and application frequency but requires direct measurement.

---

## Supporting Documents

| Document | Description |
| :---- | :---- |
| `CLAUDE.md` | Development context for AI-assisted sessions — technical implementation details, source boundaries, critical rules |
| `VCE_Calculator_Development_History.docx` | Full development history February–May 2026 |
| `VCE_Calculator_User_Guide.docx` | Plain-language user guide for both lawn and garden tabs |
| `VCE_Calculator_Fun_Facts.docx` | 11 highlights for new users |
| `Soil_Test_Challenges_and_Solutions.docx` | Lawn soil test interpretation challenges and solutions (7 challenges) |
| `Garden_Soil_Test_Challenges_and_Solutions.docx` | Garden soil test challenges and solutions (10 challenges) |

---

## Attributions

- **Chantel Wilson** — Assistant Professor and 4-H STEAM Extension Specialist, Virginia State University  
- **Michael Goatley Jr.** — Professor and Extension Specialist, Virginia Tech

Virginia Cooperative Extension is a partnership of Virginia Tech, Virginia State University, the U.S. Department of Agriculture, and local governments.

*This calculator is not an official VCE product. It is a homeowner tool built from VCE publications for personal use.*  
