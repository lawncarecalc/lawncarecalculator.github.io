# VCE Lawn & Garden Care Calculator

An interactive, single-file web calculator that helps Virginia homeowners interpret soil test results and plan fertilizer and lime applications. Built from official Virginia Cooperative Extension publications.

**Current version:** v1.4  
**File:** `lawn_garden_calc_v1_4.html`  
**No installation required** — open the file in any modern browser.

---

## What it does

- Interprets soil test reports from **VCE / Virginia Tech** and **Waypoint Analytical**
- Provides plain-English interpretation cards for every measurement on your report
- **Build a plan for me** — enter your fertilizer grade and the calculator divides your annual N target across the right number of applications automatically
- **Custom plan** — build your own multi-application season with up to 4 slots, each with a different fertilizer grade
- Calculates **lime** quantities with CCE adjustment and application schedule
- Calculates fertilizer and lime for **vegetable and flower gardens** (VCE Soil Test Note 19)
- Carries soil test values directly into the calculator tabs with one click
- Print-ready output for both auto and custom plans

---

## How to use

### Step 1 — Soil Test Report tab

Select your report type:
- VCE / Virginia Tech — Lawn
- Waypoint Analytical — Lawn
- VCE / Virginia Tech — Vegetable & Flower Garden
- Waypoint Analytical — Garden

Enter your values exactly as they appear on your report. Units, rating scales, and interpretation language adjust automatically. The tool interprets every measurement with a color-coded action recommendation.

**Enter your lawn or bed size first** — this is required for fertilizer quantities to calculate. Once P and K ratings and grass type are entered, a green "Apply to Calculators" bar appears. Click it to pre-fill all the calculator tabs at once.

### Step 2 — Cool-Season or Warm-Season Lawns tab

**Step 1:** Enter your lawn size.

**Step 2:** Select your grass species:
- Cool-season: Tall fescue / Kentucky bluegrass / Perennial ryegrass, or Fine-leaf fescue
- Warm-season: Bermudagrass / St. Augustinegrass, or Zoysiagrass / Centipedegrass

**Step 3:** Choose your annual N rate using the guidance table. The table shows a suggested annual application total, the maximum per application by program, and the minimum number of applications needed. Your soil test report may include an N recommendation — use it as a starting point but check it against the Virginia ceilings in the table. Waypoint reports sometimes recommend rates that exceed Virginia's limits for certain grass types.

- **Returning clippings?** Reduce your total by up to one-third.
- **Heavy shade?** Use one-half to two-thirds of the full-sun rate.

**Step 4:** Use the **"Help me choose a fertilizer"** section (tap to expand) to find an appropriate grade based on your P and K ratings. The section explains what the three numbers on a fertilizer bag mean, how to find WIN on the label, and lists common grades.

**Step 5 — Build a plan for me (default):** Enter your fertilizer's N-P-K grade and WIN%. The calculator determines your program (P1/P2/P3), calculates the minimum number of applications needed to stay within per-application limits, divides your annual N target equally, and shows a plan table with suggested timing and total lbs to purchase. Click **Print Plan** for a clean printed copy.

**Step 5 — Custom plan:** Switch to custom mode to build your own plan with up to 4 application slots. Each slot can have a different fertilizer grade — useful when your first application needs P correction and later ones are N-only maintenance. The custom plan is pre-populated from your auto plan inputs as a starting point.

### Step 3 — Lime tab

Enter your lawn size, lime recommendation, lime type, CCE (from the bag), and bag size. The calculator shows the number of applications needed, lbs per application, and total bags.

### Step 4 — Garden & Flowers tab

Enter bed dimensions (or area directly for irregular beds), N recommendation, P and K ratings, fertilizer grade or product, and lime recommendation. Shows fertilizer weight, approximate volume, lime for your bed, and timing guidance by garden type.

---

## Fertilizer programs

Per VCE Publication 430-011 and DCR 2014:

| Program | WIN % on bag | Cool-season max/application | Warm-season max/application |
| :---- | :---- | :---- | :---- |
| Program 1 — Quick-release | < 15% (or not listed) | 0.7 lb N / 1,000 sq. ft. | 0.9 lb N / 1,000 sq. ft. |
| Program 2 — Slow-release | 15–49% | 0.9 lb N / 1,000 sq. ft. | 1.0 lb N / 1,000 sq. ft. |
| Program 3 — Majority slow | ≥ 50% | 1.0–1.5 lb N / 1,000 sq. ft. | 1.0–1.5 lb N / 1,000 sq. ft. |

WIN (Water Insoluble Nitrogen) is listed under Guaranteed Analysis on the fertilizer bag. If not listed, assume Program 1. Sulfur-coated and polymer-coated urea are slow-release but may not list WIN explicitly — look for those terms in the ingredient list.

**Reading the bag:** The three numbers (e.g. 16-4-8) are the percentages by weight of nitrogen (N), phosphorus (P), and potassium (K). A 40 lb bag of 16-4-8 contains 6.4 lbs of actual nitrogen.

---

## Annual nitrogen ceilings (per 430-011 and DCR 2014)

| Grass type | Annual maximum |
| :---- | :---- |
| Tall fescue / Kentucky bluegrass / Perennial ryegrass | 3.5 lbs N / 1,000 sq. ft. |
| Fine-leaf fescue | 2.0 lbs N / 1,000 sq. ft. |
| Bermudagrass / St. Augustinegrass | 4.0 lbs N / 1,000 sq. ft. |
| Zoysiagrass / Centipedegrass | 2.0 lbs N / 1,000 sq. ft. |

**Clipping recycling:** Returning clippings to the lawn offsets up to one-third of seasonal nitrogen needs. If you mulch-mow consistently, reduce your annual target accordingly.

**Shade:** Grasses in heavily shaded areas need only one-half to two-thirds as much nitrogen as the same grass in full sun.

---

## Timing

**Cool-season grasses — think "SON":** September, October, and November is the primary fertilization window. Fall applications build density, root growth, and carbohydrate reserves far more effectively than spring fertilization. *(VCE 430-520)*

**Warm-season grasses:** April 1 through August 15 is the primary window. A modest September application for bermudagrass can benefit winter hardiness — but do not fertilize after August 15 with anything other than the specific fall bermudagrass program, as late nitrogen increases winterkill risk. *(VCE 430-520)*

---

## Supported soil test reports

| Lab | Rating scale | Nutrient units | Salts | Buffer measurement |
| :---- | :---- | :---- | :---- | :---- |
| VCE / Virginia Tech | L-/L/L+/M-/M/M+/H-/H/H+/VH | lb/A | ppm | Buffer Index |
| Waypoint Analytical | Very Low / Low / Medium / Optimum / Very High | ppm | dS/m (auto-converted) | Buffer pH |

Units, labels, and rating scales switch automatically when you select your report type. Waypoint ratings are mapped to VCE equivalents for all calculations.

---

## Choosing your annual N rate — note on Waypoint reports

Waypoint soil test reports include a nitrogen recommendation that may reach the upper end of the Virginia range. This is appropriate for bermudagrass but can exceed the VCE annual ceiling for cool-season grasses or zoysiagrass/centipedegrass. Always verify the Waypoint N recommendation against the guidance table on the Cool-Season or Warm-Season tab before entering it as your annual target.

---

## Choosing a fertilizer at the garden center

The calculator does not recommend specific brands. The "Help me choose a fertilizer" section (collapsible, on both the Cool-Season and Warm-Season tabs) provides:
- A plain-language explanation of what the three numbers on a bag mean
- A grade recommendation based on your soil test P and K ratings
- Instructions for finding WIN on the label
- A common grades reference table

---

## Source documents

| Publication | Title |
| :---- | :---- |
| SPES-40A | Spreadsheet-Based Calculator for Lawn Fertilizer and Lime Applications in Virginia |
| 430-011 / SPES-334P | Lawn Fertilization in Virginia — VCE 2021 |
| 430-520 / SPES-223P | Fall Lawn Care — VCE 2025 |
| 452-717 / SPES-306P | Soil Test Note 17: Lawn Fertilization for Cool-Season Grasses — VCE 2021 |
| 452-718 / SPES-305P | Soil Test Note 18: Lawn Fertilization for Warm-Season Grasses — VCE 2021 |
| 452-719 / SPES-687NP | Soil Test Note 19: Vegetable and Flower Gardens — VCE |
| 452-701 / SPE-605NP | Soil Test Note 1: Explanation of Soil Tests — VCE 2024 |
| Agronomy Facts 8 | Soil Test Interpretation: Terms and Definitions — Waypoint Analytical 2023 |
| DCR 2014 | Virginia Nutrient Management Standards and Criteria |

---

## Attributions

**Chantel Wilson** — Assistant Professor and 4-H STEAM Extension Specialist, College of Agriculture, Virginia State University

**Michael Goatley Jr.** — Professor and Extension Specialist, School of Plant and Environmental Sciences, Virginia Tech

Virginia Cooperative Extension is a partnership of Virginia Tech, Virginia State University, the U.S. Department of Agriculture, and local governments. VCE programs and employment are open to all, regardless of age, color, disability, gender, gender identity, gender expression, national origin, political affiliation, race, religion, sexual orientation, genetic information, veteran status, or any other basis protected by law.

For more information visit **ext.vt.edu** or **soiltest.vt.edu**.

---

## Files

| File | Description |
| :---- | :---- |
| `lawn_garden_calc_v1_4.html` | Main application |
| `CLAUDE.md` | Developer/AI session context |
| `README.md` | This file |
