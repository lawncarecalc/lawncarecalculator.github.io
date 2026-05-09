# 🌿 VCE Lawn Care Calculator

A browser-based tool that helps Virginia homeowners interpret soil test results and calculate fertilizer and lime applications for their lawns. Supports reports from both **Virginia Cooperative Extension (VCE) / Virginia Tech** and **Waypoint Analytical**.

---

## 🎯 What It Does

Converts your soil test report into plain-English interpretations and practical application recommendations — how many bags of fertilizer to buy, how many times to apply it, and when.

**Perfect for Virginia homeowners** who receive a soil test report from VCE/Virginia Tech or Waypoint Analytical and want guided, accurate recommendations without reading through multiple extension publications.

---

## ✨ Key Features

### Soil Test Report Interpretation
- Enter all values from your report (pH, Buffer Index, P, K, Ca, Mg, Organic Matter, Soluble Salts, CEC, Base Saturation, micronutrients)
- Every measurement interpreted in plain English with color-coded action boxes
- Supports both **VCE/Virginia Tech** (L–/M/H/VH) and **Waypoint Analytical** (Very Low through Very High) rating scales — switching labs updates all labels, units, and interpretation notes automatically
- Soluble salts unit toggle: ppm (VCE) or dS/m (Waypoint) with automatic conversion
- **Apply to Calculators** button carries your ratings and lawn size into the fertilizer and lime tabs

### Fertilizer Calculator (Cool-Season & Warm-Season)
- Separate tabs for cool-season grasses (fescue, bluegrass, ryegrass) and warm-season grasses (bermuda, zoysia, centipede, St. Augustine)
- Enter your fertilizer's N-P-K grade and WIN value — the calculator determines Program 1 or Program 2 automatically
- Per-application N limits enforced per VCE Soil Test Notes 17 and 18
- Total bags needed, lbs per application, nutrients applied, and timing schedule
- Leftover fertilizer adjustment — enter pounds on hand to reduce new bags needed

### Lime Calculator
- Enter your recommended lime rate and the CCE from the bag label
- Automatically splits large applications into <= 50 lbs/1,000 sq. ft. increments
- Total bags needed across the 3-year lime cycle

### Flags & Warnings
All flags match the original SPES-40A spreadsheet logic:

| Flag | Condition |
| :---- | :---- |
| N too high | Annual N rate exceeds 3.5 lbs (cool) or 4.0 lbs (warm) per 1,000 sq. ft. |
| P too high | P applied per 1,000 sq. ft. exceeds the maximum for your soil's P rating |
| K too high | K applied per 1,000 sq. ft. exceeds the maximum for your soil's K rating |
| Missing P | Soil rates Low for P but selected fertilizer contains no phosphorus |
| Missing K | Soil rates Low for K but selected fertilizer contains no potassium |
| N per-app exceeded | N per application exceeds the Program 1 or Program 2 limit |

---

## 🚀 How to Use

### Online
Visit: **[https://lawncarecalc.github.io/lawncarecalculator.github.io/](https://lawncarecalc.github.io/lawncarecalculator.github.io/)**

### Offline
1. Download `index.html` above
2. Double-click to open in any modern web browser
3. Works completely offline — no internet required!

### Recommended Workflow
1. Open the **Soil Test Report** tab and select your lab (VCE or Waypoint) from the dropdown
2. Enter the values from your soil test report — rating dropdowns show the correct scale for your lab
3. Click **Apply to Calculators** to carry your ratings and lawn size to the fertilizer and lime tabs
4. Open the **Warm-Season** or **Cool-Season** tab, enter your desired N rate and fertilizer grade
5. Open the **Lime** tab if lime was recommended on your report
6. Use **Print Results** on the Soil Test tab to save a PDF of your interpretation

---

## 📖 Example Usage

**Your Situation:**
- Waypoint Analytical soil test report
- Soil pH 5.9 · Buffer pH 6.81 · P rated Medium · K rated Medium · Mg rated Low
- Lime recommendation: 50 lbs / 1,000 sq. ft. (dolomitic)
- Cool-season lawn (tall fescue), 5,000 sq. ft.

**Steps:**
1. Select **Waypoint Analytical** from the lab dropdown — units and rating scales update automatically
2. Enter pH, Buffer pH, P, K, Ca, Mg values — cards appear with plain-English interpretation
3. Click **Apply to Calculators** — lawn size, P/K ratings, lime type, and lime rate are pre-filled
4. On the **Cool-Season** tab, enter your N rate (e.g. 2.0 lbs) and fertilizer grade (e.g. 16-4-8)
5. **Results:**
   - **3 applications** at Program 1 timing (Sept, Oct, Nov)
   - **19.5 lbs of fertilizer per application** for your 5,000 sq. ft. lawn
   - **2 bags needed** (based on 40 lb bag size)
6. On the **Lime** tab — **1 application** of 250 lbs total (50 lbs/1,000 sq. ft. x 5 = 250 lbs)

---

## 📐 How It Works

### WIN / Nitrogen Program Detection
```
WIN% of total N = (WIN lbs listed on bag / Total N%) x 100

< 15% WIN  ->  Program 1 (quickly available nitrogen)
>= 15% WIN ->  Program 2 (slowly available nitrogen)
```

**Per-application N limits (from VCE Soil Test Notes 17 & 18):**

| Program | Cool-Season Max | Warm-Season Max |
| :---- | :---- | :---- |
| Program 1 | 0.7 lb N / 1,000 sq. ft. | 0.9 lb N / 1,000 sq. ft. |
| Program 2 | 0.9 lb N / 1,000 sq. ft. | 1.0 lb N / 1,000 sq. ft. |

### P/K Flag Threshold
```
P or K applied per 1K sqft = nRate x (nutrient% / N%)
Flag fires when: applied > NEED_RATIO[rating]

NEED_RATIO: L-=3, L=2.5, L+=2, M-=2, M=1.5, M+=1, H-=1, H=0.75, H+=0.5, VH=0
```

### Lime Calculation
```
Adjusted rate = recommended lbs x (100 / CCE%)
Applications  = ceil(adjusted rate / 50)
Schedule      = full 50-lb/1,000 sq. ft. applications, remainder on last
```

---

## 🔬 Multi-Lab Support

This tool supports reports from Virginia Cooperative Extension / Virginia Tech and Waypoint Analytical. Selecting your lab from the dropdown adjusts rating labels, nutrient value units, soluble salts units, and interpretation notes automatically.

**Fertility ratings are directly comparable between labs.** Both labs calibrate their rating thresholds to the same agronomic decision point — the soil concentration at which plant response to fertilization becomes uncertain. A Waypoint "Medium" and a VCE "M" convey the same agronomic meaning and are used interchangeably in all calculations.

**Nutrient units by lab:**

| Measurement | VCE / Virginia Tech | Waypoint Analytical |
| :---- | :---- | :---- |
| P, K, Ca, Mg | lb/A | ppm |
| Soluble Salts | ppm | dS/m (auto-converted x 640) |
| Buffer measurement | Buffer Index | Buffer pH (same concept) |

**Note:** lb/A and ppm values are display-only context. Only the fertility ratings (Low / Medium / High / Very High) drive recommendations and flags — no unit conversion is applied to the values themselves.

---

## ⚠️ Important Notes

### Retest After 3 Years
All fertilizer recommendations are valid for up to three growing seasons. Lime recommendations cover a three-year period. After that, have your soil retested.

### Follow Your Report
This tool interprets your soil test report — it does not replace it. Always follow your lab's specific recommendations and read fertilizer bag labels before applying.

### Maximum Application Rates
Never apply more than 50 lbs of lime per 1,000 sq. ft. in a single application. Never exceed the per-application nitrogen limits for your program — the calculator will flag violations.

---

## 🛠️ Technical Details

- **Technology:** Pure HTML/CSS/JavaScript — no frameworks, no build step, no dependencies
- **File:** Single self-contained HTML file
- **File Size:** ~115 KB
- **Browser Support:** All modern browsers; JavaScript written in ES5 for broad compatibility including older Safari versions
- **Privacy:** All calculations run locally in the browser — no data is sent anywhere
- **Offline Capable:** Works without an internet connection after download (Google Fonts loads from CDN when online)
- **Print / PDF Export:** Print Results button triggers `window.print()` — a print stylesheet hides navigation and inputs, leaving only the interpretation cards

---

## 📚 Source Documents

All calculations, recommendations, timing schedules, and flag thresholds are derived from these official publications:

| Publication | Title | Authors |
| :---- | :---- | :---- |
| SPES-40A | A Spreadsheet-Based Calculator for Lawn Fertilizer and Lime Applications in Virginia | Chantel Wilson (VSU); Michael Goatley Jr. (VT) |
| 452-717 / SPES-306P | Soil Test Note 17: Lawn Fertilization for Cool-Season Grasses | M. Goatley, E.H. Ervin, S.E. Heckendorn — VCE, 2021 |
| 452-718 / SPES-305P | Soil Test Note 18: Lawn Fertilization for Warm-Season Grasses | M. Goatley, E.H. Ervin, S.E. Heckendorn — VCE, 2021 |
| 452-701 / SPE-605NP | Soil Test Note 1: Explanation of Soil Tests | R. Maguire, S. Heckendorn — VCE, 2024 |
| Agronomy Facts 8 | Soil Test Interpretation: Terms and Definitions | Large / Ruiz Jr. — Waypoint Analytical, 2023 |
| DCR 2014 | Virginia Nutrient Management Standards and Criteria | Virginia Department of Conservation and Recreation |

This web version was inspired by and built with sincere thanks to the original SPES-40A authors, **Chantel Wilson** and **Michael Goatley Jr.**

---

## 💡 Pro Tips

- **Use the Load Sample Report button** on the Soil Test tab to see a fully worked example before entering your own values
- **Carry over to calculators** — the Apply to Calculators button saves time and prevents entry errors
- **Check your fertilizer bag** for the WIN value under "Guaranteed Analysis" — it determines your nitrogen program and per-application limits
- **Dolomitic vs. agricultural lime** — if your Mg is low, dolomitic is preferred as it supplies both calcium and magnesium
- **Print your results** — the Print Results button produces a clean PDF of your soil test interpretation for your records

---

## 📄 License & Disclaimer

This tool is a web adaptation of publicly available Virginia Cooperative Extension educational materials. It is intended for informational purposes only. Recommendations are valid for up to three growing seasons — retest soil after three years.

For local assistance, contact your [Virginia Cooperative Extension office](https://ext.vt.edu) or visit [soiltest.vt.edu](https://soiltest.vt.edu).

Virginia Cooperative Extension is a partnership of Virginia Tech, Virginia State University, the U.S. Department of Agriculture, and local governments. Programs and employment are open to all, regardless of age, color, disability, gender, gender identity, gender expression, national origin, political affiliation, race, religion, sexual orientation, genetic information, veteran status, or any other basis protected by law.

---

**Happy lawn care! 🌱**

*This calculator is for educational purposes. Always follow your soil test lab's specific recommendations and fertilizer label instructions.*

**Last updated:** May 2026
