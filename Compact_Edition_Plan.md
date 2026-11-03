# Soil Test Report Assistant — Compact Edition (CE): Plan

Draft 11 · 2026-11-02 · Phase 1 built (v13.2); Phase 2a built (v13.3–v13.5); Phase 2b built (v13.6 schedule fixes, v13.7 flower form); 10.9 fixes built (v13.8)

## 1. What CE is

CE is a short way through the Soil Test Report Assistant (STRA). It is for people who want to type in their report's numbers and get a shopping list. It skips the explanation of each test value and answers three questions:

1. **What to buy:** which bags at the local garden center fit the report.
2. **How much to buy:** pounds of product for the season, for the user's lawn size.
3. **When to apply:** the months, and how much to spread each time.

**CE is built into the existing app (`index.html`), not a separate file.** Both versions use the same calculations and the same fertilizer data:

- N limits and caps;
- the VCE month-by-month schedule;
- shade and clipping adjustments;
- the local bag list and the bag-picking filter;
- the lime math.

Given the same inputs, CE and the full version give the same numbers. Sources stay one click away in About & Instructions.

**Goal: as little input and as little background knowledge as possible.**

## 2. Phases

| Phase | Scope |
| :-- | :-- |
| **1** | Waypoint lawn reports, cool- and warm-season. Planned in detail below. |
| **2a** | Waypoint vegetable garden reports |
| **2b** | Waypoint flower garden reports |
| Later (not requested) | VCE reports, shrubs & trees |

## 3. How the two versions share one app

### 3.1 Choosing a version

| Address opened | What happens |
| :-- | :-- |
| `…lawncarecalculator.github.io/` (plain) | Start screen asks: "Full version or Compact Edition?" with a one-line description of each. |
| `…lawncarecalculator.github.io/?mode=ce` | Opens straight into the Compact Edition. |
| `…lawncarecalculator.github.io/?mode=full` | Opens straight into the full version, as it works today. |

- The `?mode=ce` address (or a QR code for it) can go on Help Desk handouts and emails. Master Gardeners can bookmark `?mode=full`.
- A header link, "Switch to the full version" / "Switch to the Compact Edition," is always visible.
- Nothing is saved on the user's device. The app still uses no browser storage.
- **Start Over** keeps the current mode instead of returning to the start screen.

### 3.2 What each version shows

- **Full version:** unchanged, except for the header switch and the updated About & Instructions.
- **Compact Edition:**
  - shows CE's form, CE's results, the header switch and a link to About & Instructions;
  - hides the tab bar, the Soil Test Report tab and its interpretation cards, and the calculator tabs.

### 3.3 Reports CE doesn't cover yet

If a CE user says their report is from VCE, or is for a garden, CE says so plainly. It offers a button to open the full version.

### 3.4 Code changes needed before CE is built

These functions read the lawn tab's form fields by element id:

- `effectiveNRate`
- `shadeFactor`
- `clipCredit`
- `lookForTarget`
- `lookForCore`
- `renderLimeForLawn`

Each gets a version that takes plain values, such as grass, size, N, P and K ratings, shade and clippings. The lawn tabs call the new version with their own field values, and CE calls it with CE's. The lawn tabs must give identical output before and after (section 7).

## 4. Phase 1 — Waypoint lawns: inputs

### 4.1 Progressive disclosure

The inputs are on one page, with no Next buttons. Each section appears once the one above it is answered. Answered sections stay visible and can be changed.

1. **Your grass.** One choice among five, grouped cool/warm: tall fescue/bluegrass/ryegrass, fine fescue, bermuda/St. Augustine, zoysia, centipede. This sets the VCE limit and the schedule.
2. **Lawn size** (sq. ft.), with "How to measure" collapsed underneath.
3. **From your Waypoint report:**
   - annual N (lbs per 1,000 sq. ft.);
   - P rating (Very Low … Very High);
   - K rating.

   A collapsed "Where do I find these?" explains where each appears on a Waypoint report.
4. **Lime.** "Does your report recommend lime?" If yes, two more fields appear: amount (lbs per 1,000 sq. ft.) and type (Agricultural/Dolomitic).
5. **New lawn?** One checkbox. Unchecked means an existing lawn, the full version's default.
6. **More options** (collapsed). These start at the full version's defaults, so leaving them alone gives the same result:

| Option | Default |
| :-- | :-- |
| Shade | Full sun |
| Returning clippings | No |
| Lime bag CCE % | Treated as 100% |
| Lime bag size | No bag count shown |

Until the required fields are filled, the result area shows "Still needed: …" instead of a blank or partial result.

Every amount is labeled **lbs per 1,000 sq. ft.**, as Waypoint prints it.

### 4.2 Sample report buttons

Two buttons use the real Waypoint lawn samples already in the app:

- **Cool-season:** tall fescue, N 4.0, P Very High, K Medium, 40 lbs dolomitic lime.
- **Warm-season:** zoysia, N 5.0, P Optimum, K Low, no lime.

They fill every field and open every section.

### 4.3 Why P and K ratings, not the report's P₂O₅/K₂O pounds (decided)

How the app uses the ratings:

1. Waypoint ratings are converted to VCE's scale (`carryMap`): Very Low and Low become Low; Medium and Optimum become Medium; Very High becomes High.
2. Each rating sets a rule for the bag (`lookForFilter`):
   - **P High:** no phosphorus at all.
   - **P Medium:** light phosphorus (P₂O₅ no more than half the N).
   - **P Low, or a new lawn (unless P is High):** a starter-type bag (P₂O₅ at least 0.4 × N).
   - **K Low:** K₂O at least 0.25 × N.
   - **K Medium:** K₂O no more than 0.35 × N.
   - **K High:** K₂O no more than 0.2 × N.
3. The N goal (VCE-capped) sets how much to buy and apply. P and K only decide which bags qualify.

Why the pounds are not a substitute:

- **They are Waypoint's prescription, not a measurement.** On reports we reviewed, Waypoint recommends maintenance amounts even at Optimum (e.g., 4.0 lb K₂O at Optimum K on a flower report). VCE says none is needed at that level.
- **They don't map onto the categories.** A K₂O figure above zero can come from Low, Medium or Optimum. A P₂O₅ figure of zero can mean Optimum or Very High. Turning pounds into categories would need cut-offs no publication gives.
- **They depend on other things.** Waypoint's amounts change with CEC and the crop code.
- **They are a yearly nutrient total, not a bag ratio,** and the VCE N cap shifts the ratio further.
- **The new-lawn starter rule** needs the rating plus lawn status.
- **VCE reports print ratings, not P/K pounds,** so ratings keep one input method for later phases.

Possible future addition, made to both versions at once: size a separate straight potash application from Waypoint's K₂O pounds when K is Low.

## 5. Phase 1 — calculation and results

### 5.1 Calculation (shared with the full version)

1. Effective N goal = typed N, then the shade factor, then the clipping credit.
2. Cap at the VCE yearly maximum for the grass. If the cap applies, show a one-line note.
3. For each program (1, 2, 3), get the allowed months and amounts (`VCE_SCHEDULE`) and the per-month split (`buildAutoSlots`).
4. Filter the bags in `LOCAL_SURVEY`:
   - apply `lookForFilter(P, K, new lawn)`;
   - sort each bag into a program by its slow-release content;
   - mark VCE Table 1 grades with ‡.
5. For each bag that fits: lbs to buy for the season and lbs to apply in each month, for the lawn size.
6. Lime: `calcLimeForBed` on the lawn basis (max 50 lbs per 1,000 sq. ft. per application).

### 5.2 Results (decided: same as the full version)

The full version's "What to look for at the garden center" card shows all three programs. Each program block shows:

- the N-P-K range to look for;
- the months and amounts allowed;
- the most it can deliver in a year;
- whether it reaches the goal;
- each local grade with "buy ~X lbs for the season; apply ~Y lbs in [months]".

Below the card, the lime plan.

The warnings are the same as in the full version:

- goal capped;
- program can't reach the goal;
- fine fescue in heavy shade;
- no local bag fits ("ask at the counter").

There is a **Print shopping list** button.

### 5.3 Left out of CE

- The soil test interpretation cards: pH, CEC, buffer, base saturation, organic matter, salts, micronutrients.
- "Build a plan for me" / "Custom plan" (checking a bag the user already has). Users who need it can switch to the full version.

## 6. Project rules that apply

- No brand names. No PII in code or comments.
- **WCAG 2.1 AA:**
  - labels on every field;
  - sections revealed in page order, so keyboard and screen-reader order match the screen;
  - unopened sections use `hidden`, so they are out of the tab order;
  - results in an `aria-live` region;
  - focus moves sensibly from the start screen;
  - contrast checked;
  - mobile layout checked at about 380 px.
- No backtick template literals; HTML entities in JS strings.
- **Printing:** a new `printing-ce` print setting, added to the `body:not(.printing-…)` exclusion list (project rule 30), printed through `printPlan`.
- Version badge bumped on every `index.html` change, using the rolling minor digit.

## 7. Tests

1. **Refactor check (before CE is added):** the lawn tabs give identical output before and after the section 3.4 change. This uses the golden numbers in `Lawn_Calculation_Audit_Plan.md`:
   - tall fescue Program 2 at 3.5 lb → 1.0 / 0.9 / 0.7 / 0.9;
   - 5,000 sq. ft. of 32-0-10 → buy 54.7 lbs;
   - zoysia and bermuda cases;
   - lime.
2. **CE vs. lawn tab:** the same inputs give the same capped goal, program maximums, month amounts, grades, buy/apply lbs and lime numbers. Cases:
   - both sample reports;
   - bermuda with heavy shade + clippings;
   - new lawn with P Low (starter grades only);
   - blank N ("enter your N goal" prompt).
3. **Mode handling:**
   - the plain address shows the start screen;
   - `?mode=ce` and `?mode=full` skip it;
   - the header switch works both ways;
   - Start Over keeps the mode;
   - VCE or garden report in CE → message + full-version button.
4. **Print:** the CE print shows only the shopping list and lime. The full version's prints are unchanged.
5. **General checks:**
   - no page errors;
   - no duplicate ids;
   - `node --check` on the script;
   - axe shows 0 violations;
   - keyboard walk-through.

## 8. Build steps — Phase 1

1. Refactor the section 3.4 functions to accept plain values. Run test 1. Release as its own version.
2. Add the mode handling: start screen, `?mode=` reading, header switch, Start Over change.
3. Build CE's form with progressive disclosure, "Still needed," sample buttons and "More options."
4. Connect CE's results to the shared functions (the card and lime), plus print.
5. Rework About & Instructions:
   - a "Two ways to use this tool" section;
   - a short CE how-to;
   - a note that the `?mode=ce` address can be shared.
6. Run tests 2–5. Bump the version. Update the README section and the CLAUDE.md entry.

## 9. Decisions log

| # | Decision | Outcome |
| :-- | :-- | :-- |
| D1 | How CE and the full version share calculations | **Built into the same app**, one copy of everything (replaces the earlier choice of option B) |
| D2 | File name | **No separate file**, CE lives in `index.html` (replaces `STRA-CE.html`) |
| D3 | Moving between versions | **Start screen + header switch** (replaces the separate link) |
| D4 | "Check a bag I already have" | **Left out** of CE |
| D5 | Sample report buttons | **Yes**, the two Waypoint lawn samples |
| D6 | Title | **"Soil Test Report Assistant — Compact Edition"** |
| D7 | Optional fields | **Collapsed under "More options"**, at the full version's defaults |
| D8 | Progressive disclosure for inputs | **Yes**, section 4.1 |
| D9 | Results | **Same as the full version** (all three programs) |
| D10 | Start screen behavior | **Option b:** ask on the plain address; `?mode=ce` / `?mode=full` skip the question |
| D11 | P and K input | **Ratings**, not the report's pounds (section 4.3) |

## 10. Phase 2a — Waypoint vegetable gardens

### 10.1 What changes from Phase 1

- Step 0 ("Which report do you have?") gets a working **Waypoint vegetable garden** choice. Waypoint flower and shrub reports, and all VCE reports, still show the "not covered yet" message.
- Choosing it shows the garden form (below) instead of the lawn form. The lawn form is unchanged.

### 10.2 Inputs (progressive disclosure, as in Phase 1)

1. **Bed size** (sq. ft.), with "How to measure" collapsed underneath (length × width).
2. **Nitrogen.** Either or both, at least one required (G1, same as the full version):
   - **What will you grow?** The full version's crop list, including "Mixed bed." Sets the sidedress schedule, and the research N rate if no report N is entered.
   - **Your report's N** (lbs per 1,000 sq. ft.). If entered, it is the preplant rate.
   With neither, "Still needed: a crop or your report's nitrogen."
3. **Nitrogen products: organic or synthetic?** One question: Organic / Synthetic / Show both (G3). **Applies to nitrogen only**; the other nutrients get their own product choice in step 4.
4. **Other nutrients from your report's Soil Fertility Guidelines** (G2, G9). Built one nutrient at a time:
   1. **"Tick each nutrient your report lists with a number above 0."** One checkbox per nutrient, in the report's order: P₂O₅, K₂O, Mg, S, B, Cu, Mn, Zn, Fe. A collapsed "Where do I find these?" points to the Soil Fertility Guidelines table (and says to use the row for the crop code that matches the bed).
   2. **Ticking a nutrient opens its value box:** "Amount from your report (lbs per 1,000 sq. ft.)."
   3. **Once a value is entered, the product choice appears:** a dropdown of the products the app can size from that number, each labeled Organic or Synthetic. If a nutrient has only one product, it's shown directly with no dropdown.

      | Nutrient | Products offered |
      | :-- | :-- |
      | P₂O₅ | Triple superphosphate (synthetic) |
      | K₂O | Sulfate of potash, muriate of potash (synthetic) |
      | Mg | Epsom salts, K-Mag (organic); magnesium oxide (synthetic) |
      | S | Gypsum (organic); elemental sulfur (synthetic) |
      | B | Borax (synthetic) |
      | Cu | Copper sulfate (synthetic) |
      | Mn | Manganese sulfate (synthetic) |
      | Zn | Zinc sulfate monohydrate, zinc sulfate heptahydrate (synthetic) |
      | Fe | none: shows "VCE names iron sulfate or chelated iron but gives no rate; follow the product label" |

   4. **Once a product is chosen, its amount and method appear in the row** (10.3 A).

   Unticked = none needed. No rating dropdowns. Why targets and not ratings (checked against three real Waypoint garden reports, July 2026): the target is Waypoint's actual instruction and the rating doesn't predict it. Mg rated Medium got a target of 0; S and B rated Optimum got targets (0.13, 0.04); B was 0.04 on every Garden-Home row whatever the rating. The target also changes with the crop code (same sample: K₂O 2.0 Garden-Home vs. 4.0 Perennials). Very High always meant 0 and Low always meant a positive amount, so the target carries everything the rating would.

   Organic P and K products (bone meal, rock phosphate, granite dust, greensand, wood ash) aren't offered: their VCE rates are flat rates tied to a rating, not sized from a target. A one-line note under the P and K rows says so.
5. **Lime.** "Does your report recommend lime?" If yes: amount (lbs per 1,000 sq. ft.) and type.
6. **New bed?** One checkbox (= the full version's "New / preplant"). Sets the lime limit per application (10 vs. 5 lbs per 100 sq. ft.).
7. **More options** (collapsed): organic matter % (shows the full version's organic-matter nitrogen note when 5% or more), lime CCE %, lime bag size.

Required: bed size, a crop or report N, the N-product preference, and the lime answer (plus amount if yes). For each ticked nutrient: a value and, where there's a choice, a product. Ticking no nutrients is fine ("no other nutrients needed"). "Still needed" names any ticked nutrient missing its value or product.

Sample button: the existing **Vegetable Garden – Waypoint** sample (report N 1.5; K₂O 2.0, S 0.13, B 0.04, Mn 0.05 ticked with the first product preselected; no lime), with an example bed size.

### 10.3 Results (G10: in each row as you go, and gathered at the bottom)

**A. In each nutrient row,** as soon as its product is chosen: amount for the bed and how to apply it (rules in B2).

**B. One card at the bottom, "Your shopping list,"** once everything required is filled. This is what prints.

1. **Nitrogen** (G4: short list by preference). For each product, the full version's plan: preplant amount for the bed, plus each sidedress step with timing and amount.
   - Synthetic: calcium nitrate (15.5-0-0), ammonium sulfate (21-0-0), urea (46-0-0).
   - Organic: blood meal (13% N), feather meal (10% N), soybean meal (7% N).
   - "Show both": all six.
   Sidedress product follows the full version's rule (the same product if it is N-only, otherwise calcium nitrate). Organic-matter note and sandy-soil note as in the full version.
2. **Other nutrients:** one line per ticked nutrient with its chosen product, amount and method, the same text as in its row. Sized with the full version's target math (value ÷ 10 × bed/100 ÷ product %).
   - **Phosphorus:** "Apply beside the row or planting hole, not broadcast" (Waypoint comment; already in the app's P notes).
   - **Potassium, magnesium, sulfur:** broadcast and mix into the top few inches.
   - **Boron and manganese: the instruction is the dissolve method, not a footnote.** At these targets the amounts are a few grams (B 0.04 → about 16 g of borax per 100 sq. ft.; Mn 0.05 → about 8 g of manganese sulfate), which can't be spread evenly dry. The line reads: "Weigh ~X oz (Y g) of [product], dissolve it in 1–2 gallons of water, and pour it evenly over the bed. Don't band boron near plants." No teaspoon figure unless a sourced bulk density exists (project rule). Copper and zinc amounts are similarly small; whether they get the same instruction needs a source check before coding.
   - **Sulfur: say when another product already covers it.** If K₂O is ticked with sulfate of potash, the sulfur line reads "Covered by your sulfate of potash (it supplies ~X lb S per 1,000 sq. ft., more than your report's Y)." When ammonium sulfate is among the nitrogen products shown: "If you use ammonium sulfate for nitrogen, you don't need a separate sulfur product." Otherwise, the chosen sulfur product's amount. Waypoint's own comment names the same three products. *(Sulfur percentages need a named source before coding: sulfate of potash ~17% S is already cited to Rutgers FS626 in the app; ammonium sulfate ~24% S needs one.)*
   - Epsom salts', magnesium oxide's and K-Mag's "your dolomitic lime already covers this" rule applies as in the full version.
   - Products with no sourced density show weight only ("weigh for accuracy"); CE leaves out the bulk-density entry box.
3. **Lime**, as the full version's "Lime for Your Bed" (CCE, applications, bags).
4. **Weights in pounds and ounces** everywhere (most kitchen scales show lb and oz): under 1 lb → ounces to 0.1 (e.g., "5.2 oz"); 1 lb and over → "1 lb 4.5 oz"; under 1 oz → ounces plus grams (e.g., "0.6 oz (16 g)"), since that's below most kitchen scales' useful resolution. Same formatter as the full version gets (10.9 item 4).
5. **Print shopping list** and the survey prompt, as in Phase 1. The print copy is the bottom card only.

### 10.4 Left out of CE

Soil test interpretation cards; nutrient ratings; the 11 other N products and Note 19 flat-rate options (including organic P and K); the bulk-density entry box; the Waypoint ENR comparison.

### 10.5 Code changes before the CE garden form

`calcGarden()` and `renderNutrientStatusPanel()` read the Vegetable Garden tab and Soil Test tab fields directly. Each gets a value-based core, as in Phase 1:

As built (v13.3):
- `gardenNSource(key)` — resolves a nitrogen product key (or Note 19 flat-rate key) to its N %, density and flags.
- `gardenNPlanHTML(v)` — the nitrogen plan (preplant rows, OM note, sidedress table). Optional `v.wl` (weight formatter) and `v.ui` (step wording) let CE show pounds-and-ounces and its own step numbers; the full version passes neither.
- `gardenLimeHTML(v)` — the "Lime for Your Bed" box (also takes `v.wl`).
- `targetProductLbs(target100, hundredths, pct)` — the target math, shared with `renderNutrientStatusPanel()`.
CE builds its own nutrient rows (no ratings), so `renderNutrientStatusPanel()` itself wasn't split.
- The Vegetable Garden and Flower Garden tabs must give byte-identical output before and after (snapshot test, as in Phase 1).

### 10.6 Tests

1. Snapshot: Vegetable and Flower Garden tabs identical before/after the 10.5 change (VCE + Waypoint samples, several crops, N sources, targets, lime, OM).
2. CE vs. Vegetable Garden tab: same bed, crop/N, product, targets (no ratings) and lime give the same numbers. Hand-check one case per calc path.
3. Modes and step 0: Waypoint vegetable opens the garden form; flower/shrub/VCE still get the message; switching report type keeps entries.
4. Print: CE garden prints only the shopping list; full-version prints unchanged.
5. General: no page errors, no duplicate ids, syntax, axe 0, keyboard walk-through, 380 px layout.

### 10.7 Build steps — Phase 2a

1. Value-based garden cores (10.5); snapshot test; release as its own version.
2. Step 0 change + CE garden form (including the tick → value → product rows), "Still needed," sample button, More options.
3. Results card, lime, print, survey.
4. About & Instructions: CE now covers Waypoint vegetable gardens; CE how-to steps.
5. Tests 2–5; README; CLAUDE.md.

### 10.8 Phase 2a decisions

| # | Decision | Outcome |
| :-- | :-- | :-- |
| G1 | Crop and N | **Either, like the full version** (crop list and/or report N, one required) |
| G2 | Nutrient inputs | **Targets only, no ratings** |
| G3 | Organic vs. synthetic | **One preference question for nitrogen products only** (organic / synthetic / show both); other nutrients choose per row (G9) |
| G4 | Nitrogen products | **Short list by preference** (3 synthetic, 3 organic) |
| G5 | Organic P/K, which can't be sized from a target | **Not offered**; a one-line note under the P and K rows explains why (replaces the earlier 'show the synthetic with a note' default, since the per-row choice made it moot) |
| G6 | Tiny micronutrient amounts | **Dissolve-and-pour is the instruction**, weight in oz + grams |
| G7 | Sulfur already supplied by the N or K product | **Say so** instead of listing a separate sulfur purchase |
| G8 | Decimal pounds | **Pounds and ounces** (grams under 1 oz) |
| G9 | Entering the other nutrients | **Tick the nutrient → value box → product choice → amount and method** |
| G10 | Where results appear | **Both**: in each nutrient row as you go, and gathered in a printable shopping list at the bottom |

### 10.9 Full-version findings (garden tabs), from the three July 2026 reports — proposed, not yet approved

1. **"Medium counts as low."** `nutrientRatingStatus()` treats VCE M and Waypoint ME as low, so flat-rate amendments fire at Medium.
   - **Sourced for P, K, Mg:** the app's notes cite VCE Soil Test Note 19 ("when P/K/Mg rates Medium or Low"), and VCE 452-701 says at Medium "a moderate amount of fertilizer is typically recommended." (Note 19 itself couldn't be re-fetched this session; the citation is from earlier sessions.)
   - **Not sourced for Mn and B:** the manganese flat rate comes from NC State, whose trigger is a deficiency index (Mn-AI below 25) and which calls 3–30 ppm generally adequate. The vegetable report's Mn is 19 ppm, rated Medium, so the app adds manganese to soil NC State calls adequate. The liquid borax rate (UMD) states no rating condition.
   - **The VCE rule is applied to Waypoint's scale.** Waypoint defines Medium as a 50% chance of response (Very Low ~100%, Low ~75%, Optimum 0–25%), on a different extractant (Mehlich-3). Waypoint's own target at Medium was sometimes positive (P, S, B, Mn) and sometimes 0 (Mg).
2. **Manganese rate.** The flat rate (0.05 lb of product per 100 sq. ft.) is correctly scaled from NC State's broadcast rate of 20–25 lb of manganese sulfate *product* per acre, so it isn't a math error. But it is about 3 times Waypoint's target (0.05 lb of *Mn* per 1,000 sq. ft. ≈ 7.6 g of product per 100 sq. ft.), and NC State's own soil-test-based rate is 10 lb per acre (the article doesn't say whether that's Mn or product).
3. **When a Waypoint report gives both a Low rating and a target, the flat rate is the default.** Example: P Low with a P₂O₅ target of 4.5 defaults to bone meal at 10 lb per 100 sq. ft.; triple superphosphate sized to 4.5 is the second choice.
4. **Decimal pounds** on the garden, flower and shrub tabs (e.g., "0.33 lbs") → pounds and ounces, grams under 1 oz (same formatter as CE). Lawn amounts (bags, spreader rates per 1,000 sq. ft.) stay in decimal pounds unless decided otherwise.
5. **The Flower Garden – Waypoint sample's Mg rating.** The sample (built from the perennial-bed report) rates Mg Optimum from its 12.7% saturation; the report's bar is in Medium.

Fixes (approved Nov 2, built v13.8; A chosen as "blank counts as 0"):
- **A. On Waypoint reports, the target decides.** Above 0 → only the target-sized products are offered. Blank or 0 → "nothing to add," whatever the rating. (Found while building: the sample reports wrote unprefixed target keys, so their targets had never shown; fixed with `sampleTargets()`.)
- **B. Mn and B flat rates fire only at Very Low / Low** (and VCE "DEF"), not Medium. P, K, Mg keep Medium per Note 19.
- **C. Pounds-and-ounces formatter** for garden/flower/shrub amounts.
- **D. Re-rate the flower sample's Mg as Medium** (bar reading), or note why %saturation was used.

## 11. Phase 2b — Waypoint flower gardens (built v13.6–v13.7)

### 11.1 What changes from Phase 2a

- Step 0 gets a working **"Waypoint Analytical, for a flower garden"** choice. Shrubs and trees (Waypoint) and all VCE reports still show the "not covered yet" message, now worded "for shrubs or trees."
- The flower form reuses the vegetable garden form and code. Only step 2 and the nitrogen schedule are different. Steps 3–7 are the same: N product preference, nutrient rows (tick → amount → product), lime, new bed, More options.
- **Individual nutrients only** (user decision, Nov 2). The full version's "Complete N-P-K fertilizer" mode isn't offered in CE.

### 11.2 Inputs

1. **Bed size**, as in Phase 2a.
2. **Nitrogen.** At least one is required:
   - **What kind of flower bed?** Annual, perennial, roses, or spring-flowering bulbs (the full version's four types). This sets the schedule. If no report N is entered, it also sets the research N rate.
   - **Your report's N** (lbs per 1,000 sq. ft.). If entered, it's the amount for each application.
3. **Nitrogen products**: Synthetic / Organic / Show both, with the same short list as vegetables.
4. **Other nutrients**: same rows and products as Phase 2a. The "Where do I find these?" note adds one thing: **a Waypoint flower report can print more than one row** (for example, "Garden-Home" and "Perennials"). Use the row that matches the bed, because the amounts differ. On the sample report, K₂O is 2.0 on the Garden-Home row and 4.0 on the Perennials row.
5. **Lime**, 6. **New bed?**, and 7. **More options**: as in Phase 2a. The organic-matter note uses the full version's flower wording ("excess nitrogen suppresses flowering, so lean low or skip").

Sample button: **Flower garden**, the real perennial-bed report the full version's flower sample uses. It fills in the Perennials row targets, no lime, OM 6.5%, an example bed size, and flower type Perennial.

### 11.3 Results

Same layout as vegetables: a result in each row as you go, plus a printable "Your shopping list." Each nitrogen product gets a collapsible card, and weights are in pounds and ounces. The nitrogen card shows the flower schedule (11.4) instead of the crop side-dress table, and the bulb and rose "stop" rows read "No fertilizer."

### 11.4 Flower nitrogen schedules — needs a decision (checked against VCE Soil Test Note 19, Nov 2)

Note 19's Flowers section gives **no rates and no annual, perennial or bulb schedules.** It says three things:
- Broadcast the recommended amount before planting.
- Avoid excess fertilizer, which gives leafy growth and few flowers.
- For roses: "Repeat the basic fertilizer application each month from March through August."

The full version's flower tab doesn't match this in two places. It also doesn't match its own text:

| Flower type | Full version now | Source says | Proposed (CE and full version) |
| :-- | :-- | :-- | :-- |
| Annual | Preplant, then a mid-season row showing the **full** preplant amount, while the row's own text says "half the preplant rate" | UMD: optional light mid-season application at half rate | Preplant amount; mid-season (optional) at **half** |
| Perennial | One early-spring application | UMD, Rutgers: spring only | No change |
| Roses | March, then one "after each bloom flush" row (full amount), then "Stop by August 15." Two amounts in total | **Note 19: the basic amount every month, March–August (6 applications)** | Six monthly rows (March–August) of the basic amount, then "Stop by August 15" |
| Bulbs | At planting (fall), at emergence (spring), stop after flowering | NC State, Rutgers FS1220 | No change |

The 0.10 lb N per 100 sq. ft. default for annuals and perennials is cited to "VCE Note 19; UMD Extension." Note 19 gives no flower rate, so the citation should be UMD only. The rose 0.20 rate is also cited only to Note 19, which gives no rate, so it has no source at all right now (F3). Fixing the annual/perennial citations is part of F1.

**Decision F1:** fix the annual and rose schedules (and the citations) in both CE and the full version? If yes, the full-version change goes in Phase 2b build step 1. It will be the only difference in the snapshot test, limited to the annual mid-season row and the rose rows.

### 11.5 Code changes

- **`flowerNPlanHTML(v)`**: a value-based core taken out of `calcFlower()`, for the default-rate note, quantity rows and application-plan table. It takes `wl` and `ui` the way `gardenNPlanHTML` does. `calcFlower()` calls it, and so does CE.
- The flower schedule data moves into `FLOWER_APP_PLAN` as per-step multipliers (1, 0.5 or 0), so the table can't show the wrong amount again.
- CE: a `kind` flag (`veg` or `flower`) on the garden form decides step 2's options, the N plan core, the OM wording, the sample and the "Still needed" text. The nutrient rows, lime, print and survey code are shared unchanged.

### 11.6 Tests

1. Snapshot: the Vegetable Garden tab stays identical. On the Flower Garden tab, only the rows approved in F1 change (Complete and Individual modes).
2. CE flower vs. the Flower Garden tab in Individual mode: same numbers for the same inputs, one hand-check per flower type.
3. Step 0: flower opens the flower form, vegetable still opens the vegetable form, and shrub and VCE still show the message. Switching between vegetable and flower keeps bed size, nutrients and lime.
4. Print, plus the general checks: page errors, duplicate ids, axe, keyboard, 380 px.

### 11.7 Build steps

1. `flowerNPlanHTML` and the schedule data, with the F1 fixes if approved. Snapshot test. Released as its own version.
2. Step 0, the flower form (`kind` flag), the sample button and "Still needed."
3. Results, print, About & Instructions (CE covers flower gardens), README and CLAUDE.md.

### 11.8 Open decisions

| # | Question | Default if not changed |
| :-- | :-- | :-- |
| F1 | Fix the annual mid-season (half) and rose (monthly March–August) schedules and the citations, in both versions | **Yes** (built v13.6; the Vegetable Garden tab's legacy rose entry was aligned too) |
| F2 | Report N for roses: is it the amount for each monthly application? | **Yes** |
| F3 | Rose default rate | **0.15 lb N per 100 sq. ft.** — NC State, *Roses for North Carolina* (1994): 1–2 lbs of 10-10-10 per 100 sq. ft. every 4 weeks = 0.10–0.20; middle used; six applications (0.9 lb) stay inside NC State's season total. Clemson's *Growing Roses* gives no rate (label rates only). |
