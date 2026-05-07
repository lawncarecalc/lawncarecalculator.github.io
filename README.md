# VCE Lawn Care Calculator

An interactive, browser-based web tool that helps Virginia homeowners calculate fertilizer and lime applications for their lawns based on Virginia Cooperative Extension (VCE) soil test results.

---

## Overview

This project converts the official VCE spreadsheet-based calculator (SPES-40A) into a single-file HTML web application. It adds soil test interpretation, WIN-based nitrogen program detection, real-time flags, and carry-over between tabs — all running entirely in the browser with no server or dependencies required.

The tool is intended for homeowners in Virginia who receive a VCE Soil Test Report and want guided, accurate recommendations for fertilizer and lime applications.

---

## Features

### Soil Test Report Tab

- Enter all values from a VCE Soil Test Report (pH, Buffer Index, Est-CEC, P, K, Ca, Mg, Organic Matter, Soluble Salts, Base Saturation)  
- Live interpretation of every measurement in plain English, sourced from VCE Soil Test Notes  
- Color-coded action boxes: red (action needed), amber (monitor), green (good)  
- Lime recommendation card with per-application breakdown (≤ 50 lbs/1,000 sq. ft. rule enforced)  
- **Apply to Calculators** button carries lawn size, P/K ratings, lime recommendation, and lime type directly into the fertilizer and lime calculator tabs  
- **Load Sample Report** button pre-fills the McElfish soil test (Lab ID 26-26039) for demonstration  
- **Print Results** button generates a clean print/PDF view of the interpretation

### Cool-Season Lawn Fertilizer Calculator

For tall fescue, Kentucky bluegrass, fine fescue, and perennial ryegrass.

### Warm-Season Lawn Fertilizer Calculator

For bermudagrass, zoysiagrass, centipedegrass, and St. Augustinegrass.

Both fertilizer calculators provide:

- Applications per year based on N rate and nitrogen program  
- WIN (Water Insoluble Nitrogen) entry with live Program 1 / Program 2 detection  
- Per-application N limits enforced (Program 1: 0.7 lb cool / 0.9 lb warm; Program 2: 0.9 lb cool / 1.0 lb warm)  
- Lbs of fertilizer per application and total lbs for the season  
- Total bags needed based on bag size  
- Total N / P / K nutrients applied  
- Leftover fertilizer adjustment (enter pounds remaining from last year)  
- Program-specific timing schedules with month windows from VCE Table 1

### Lime Calculator

- CCE (Calcium Carbonate Equivalent) adjustment for any bag  
- Applications calculated at ≤ 50 lbs/1,000 sq. ft. per application — fills each application to 50 lbs, with remainder on the last (e.g. 60 lbs → 50 lbs \+ 10 lbs)  
- Total bags needed across a 3-year lime cycle  
- Lime type notes (agricultural vs. dolomitic)

### Flags & Warnings

All flags match the original SPES-40A spreadsheet logic:

| Flag | Condition |
| :---- | :---- |
| N too high | Annual N rate exceeds 3.5 lbs (cool) or 4.0 lbs (warm) per 1,000 sq. ft. |
| P too high | Total P applied per 1,000 sq. ft. exceeds the maximum for the soil's P rating |
| K too high | Total K applied per 1,000 sq. ft. exceeds the maximum for the soil's K rating |
| Missing P | Soil rates Low for P but fertilizer contains no phosphorus |
| Missing K | Soil rates Low for K but fertilizer contains no potassium |
| N per-app exceeded | N per application exceeds the Program 1 or Program 2 limit |

### About & Instructions Tab

- Full instructions for using the calculators (from the original SPES-40A workbook)  
- WIN and nitrogen program explainer  
- Soil test rating reference table (L / M / H / VH)  
- Complete source document citations and author credits

---

## Source Documents

All calculations, recommendations, timing schedules, and flag thresholds are derived from the following official VCE publications:

| Publication | Title | Authors |
| :---- | :---- | :---- |
| SPES-40A | A Spreadsheet-Based Calculator for Lawn Fertilizer and Lime Applications in Virginia | Chantel Wilson (Virginia State University); Michael Goatley Jr. (Virginia Tech) |
| 452-717 / SPES-306P | Soil Test Note 17: Lawn Fertilization for Cool-Season Grasses | M. Goatley, E.H. Ervin, S.E. Heckendorn — VCE, 2021 |
| 452-718 / SPES-305P | Soil Test Note 18: Lawn Fertilization for Warm-Season Grasses | M. Goatley, E.H. Ervin, S.E. Heckendorn — VCE, 2021 |
| 452-701 / SPE-605NP | Soil Test Note 1: Explanation of Soil Tests | R. Maguire, S. Heckendorn — VCE, 2024 |

This web version was inspired by and built with sincere thanks to the original SPES-40A authors, **Chantel Wilson** and **Michael Goatley Jr.**

---

## Technical Notes

### Architecture

- Single self-contained HTML file — no build step, no dependencies, no server required  
- All logic in vanilla JavaScript  
- Styling in embedded CSS using CSS custom properties for theming  
- Google Fonts (Playfair Display, Source Sans 3\) loaded from CDN

### Key Calculation Logic

**Nitrogen program detection**

WIN% of total N \= (WIN lbs on bag ÷ Total N%) × 100

\< 15% WIN  →  Program 1 (quickly available)

≥ 15% WIN  →  Program 2 (slowly available)

**P/K flag threshold (NEED\_RATIO lookup, O32:P41 in SPES-40A)**

P or K applied per 1K sqft \= nRate × (nutrient% ÷ N%)

Flag fires when applied \> NEED\_RATIO\[rating\]

Ratings: L-=3, L=2.5, L+=2, M-=2, M=1.5, M+=1, H-=1, H=0.75, H+=0.5, VH=0

**Lime applications (≤ 50 lbs/1,000 sq. ft. rule)**

Adjusted rate \= recommended lbs × (100 ÷ CCE%)

Applications  \= ceil(adjusted rate ÷ 50\)

Schedule      \= full 50-lb applications, remainder on last

### Browser Compatibility

Tested in Chrome and Safari. Requires a modern browser with ES6+ support.

### Print / PDF Export

The Print Results button on the Soil Test tab triggers `window.print()`. A `@media print` stylesheet hides navigation, input panels, and buttons, leaving only the interpretation cards for a clean single-page report.

---

## Usage

Open `SPES-40A-Calculator.html` in any modern web browser. No installation required.

**Recommended workflow:**

1. Open the **Soil Test Report** tab and enter values from your VCE Soil Test Report  
2. Click **Apply to Calculators** to carry your ratings and lawn size to the fertilizer and lime tabs  
3. Open the **Warm-Season** or **Cool-Season** tab, enter your desired N rate and fertilizer grade  
4. Open the **Lime** tab if lime was recommended on your report  
5. Use **Print Results** on the Soil Test tab to save a PDF of your interpretation

---

## License & Disclaimer

This tool is a web adaptation of publicly available Virginia Cooperative Extension educational materials. It is intended for informational purposes only. Recommendations are valid for up to three growing seasons — retest soil after three years.

For local assistance, contact your [Virginia Cooperative Extension office](https://ext.vt.edu) or visit [soiltest.vt.edu](https://soiltest.vt.edu).

Virginia Cooperative Extension is a partnership of Virginia Tech, Virginia State University, the U.S. Department of Agriculture, and local governments. Programs and employment are open to all, regardless of age, color, disability, gender, gender identity, gender expression, national origin, political affiliation, race, religion, sexual orientation, genetic information, veteran status, or any other basis protected by law.  
