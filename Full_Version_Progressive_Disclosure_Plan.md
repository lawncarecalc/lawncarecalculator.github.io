# Soil Test Report Assistant — Progressive disclosure in the full version: Plan

Draft 1 · 2026-11-02 · for review. Nothing built yet.

## 1. Goal

Bring the Compact Edition's "answer one question, the next appears" pattern into the full version wherever it reduces what a first-time user faces, without taking anything away from experienced users and Help Desk volunteers.

## 2. What the full version shows today

| Tab | Steps shown at once | Notes |
| :-- | :-- | :-- |
| Soil Test Report | Report type, then about 30 fields for that lab, plus size, grass type, lawn status, lime | The report type already hides the other lab's block |
| Cool / Warm Lawns | 7 numbered steps, plus the step 3 guidance box, the shopping card and the plan builder | The longest tabs |
| Vegetable Garden | 3 numbered steps (lime, nitrogen, nutrient rates) with long sub-sections | Crop guidance already appears only after a crop is chosen |
| Flower Garden | 6 steps; the Complete/Individual choice already shows one body at a time | |
| Shrubs & Trees | 7 steps | |
| Lime (shrubs only) | 5 steps | Short; likely leave as is |

Calculator tabs are already reached only after the Soil Test tab is filled in (tab gating), and most values arrive by carry-over. So the biggest gain is on the **Soil Test tab** and the **lawn tabs**.

## 3. Principles (same as the Compact Edition)

1. A step appears once the step before it is answered, and **stays visible** once shown, even if an answer is later cleared.
2. **Carry-over and sample reports reveal everything they fill**, so a user arriving from the Soil Test tab sees a completed form, not a blank first step.
3. Hidden steps use `hidden` (removed from tab order and screen readers). Focus is never moved automatically; a short "Next: …" line under the answered step says what appeared.
4. A **"Show all steps"** link at the top of each tab turns the reveal off for that tab, for volunteers who know the form. It's remembered for the session only.
5. Optional and advanced items (shade, clippings, bulk density, CCE, bag size, the custom plan builder) go into "More options" collapsibles, as in the Compact Edition.
6. Results and print output don't change. The snapshot tests must pass byte-identical for a filled-in form.

## 4. Proposal by tab

### 4.1 Soil Test Report tab (highest value)

- Step A: "What is this report for?" Nothing else shows until it's answered (today the field grid appears empty first).
- Step B: lawn/bed size, plus grass type and lawn status for lawns.
- Step C: the lab block, split into "Main values" (pH, P, K, lime and lime type, plus N on Waypoint lawns) and "Everything else on your report" (Ca, Mg, micronutrients, CEC, OM, salts, buffer, base saturation), the second as a collapsible that starts **open** so nothing looks missing.
- The interpretation cards and the Continue banner appear as values arrive, as today.

### 4.2 Cool / Warm Lawns

- Steps 1–2 (size, species) first; then step 3 (N goal) with its guidance box collapsed under "Help me choose my N goal"; then 4–5 (P, K ratings); then 6 (the shopping card); then 7 (lime).
- Shade and clippings move into a "More options" box under step 3.
- The plan builder (Build a plan for me / Custom plan) moves under the shopping card as "Plan my applications (optional)".
- After carry-over, all steps that carry-over filled are shown.

### 4.3 Vegetable Garden

- Order already short. Reveal: bed size → nitrogen (crop and/or N) → nitrogen source → nutrient panel and lime. The bulk-density boxes stay where they are (they appear only when needed).

### 4.4 Flower Garden

- Reveal: flower type → bed size → N → fertilizer mode (Complete/Individual) → bed status and lime.

### 4.5 Shrubs & Trees

- Reveal: plant type → canopy → turf → N → fertilizer → P/K ratings. The health-check box at the top stays visible always (VCE Note 20: fertilize only on symptoms).

### 4.6 Lime tab (shrubs only)

- Leave as is (5 short steps).

## 5. Code approach

- One shared helper, `revealSteps(tabPrefix, stepIds, isAnswered)`, keeps a per-tab "furthest step reached" counter, like `ceReached`. Each calc function (`calcCool`, `calcWarm`, `calcGarden`, `calcFlower`, `calcShrub`, `interpretSoilTest`) calls it first.
- Each numbered step's `field-group` gets an id (`cool-step1` …). No field ids change, so carry-over, samples and print code stay the same; `carryOverToCalculators()` and `prefillSampleReport()` set the counter to "all".
- "Show all steps": a per-tab flag that makes `revealSteps` show everything.
- Build tab by tab, each its own version: Soil Test tab, then lawns, then the gardens and shrubs.

## 6. Risks

- **Carry-over filling a hidden step.** Covered by principle 2; tested by loading every sample and checking that no filled field is hidden.
- **Instructions and screenshots.** About & Instructions and README describe every step as visible; each tab's text needs a line about the reveal and "Show all steps."
- **Volunteers' muscle memory.** "Show all steps" covers it; worth asking Help Desk volunteers before the lawn tabs change.
- **Keyboard and Safari.** Revealed steps must join the tab order at the right place; repeat the Safari check with the "Press Tab to highlight each item" setting.

## 7. Tests

1. Snapshots: lawn (9 scenarios) and garden (11) byte-identical for filled forms.
2. Each sample report and each carry-over leaves no filled field hidden.
3. Step-by-step reveal per tab, clearing an answer keeps the step visible, "Show all steps" works.
4. Print matrix unchanged; axe 0; no duplicate ids; keyboard walk-through; 380 px.

## 8. Decisions needed

| # | Question | Suggested default |
| :-- | :-- | :-- |
| P1 | Which tabs get it? | Soil Test tab and lawn tabs first; gardens and shrubs after; Lime tab not at all |
| P2 | Offer "Show all steps"? | Yes, per tab, session only |
| P3 | Move shade/clippings and the plan builder into "More options"? | Yes |
| P4 | Soil Test tab: split values into "Main values" and "Everything else"? | Yes, with "Everything else" open by default |
| P5 | Ask Help Desk volunteers before changing the lawn tabs? | Yes |
