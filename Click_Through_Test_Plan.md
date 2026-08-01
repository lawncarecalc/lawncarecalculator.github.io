# Soil Report Assistant — Comprehensive Click-Through Test Plan

**Purpose:** systematically find bugs *of the same kind* as the ones already caught this project — not by re-reading code, but by actually operating the live deployed app the way a real user would, the same method that found every bug in the July 27–August 1, 2026 sessions. Static code review repeatedly missed these; live interaction caught all of them.

**How to use this document:** work through Part 1 first — it's a list of bug *patterns*, not tab-by-tab steps. Each pattern was found in one specific place this project and later found again in a different place. Check every pattern against every tab it could plausibly apply to before moving to Part 2's full walkthrough. Part 2 is the exhaustive per-tab sequence for catching anything the pattern list doesn't.

---

## Part 1 — Known Bug Patterns (check these first, everywhere they could apply)

Each pattern below names the actual bug it's generalized from, then gives a concrete checklist for finding the same shape of bug elsewhere.

### Pattern A: Content written to two places, only one of which should show it
**Origin:** Cool-Season Lawns' Auto-plan mode wrote the identical results table into both the inline (left column) area and the results card (right column), showing the same plan twice on screen.

**Check every tab for:**
- [ ] Does any inline/summary area duplicate content that also appears in a dedicated results card?
- [ ] Cool-Season Lawns — Auto mode (just fixed — reverify)
- [ ] Cool-Season Lawns — Custom mode (per-slot inline results vs. season-summary panel — confirmed different content July 31, but re-verify after any future edit to either)
- [ ] Warm-Season Lawns — same two checks
- [ ] Vegetable Garden — crop guidance panel vs. Nutrient Application Plan
- [ ] Flower Garden — Complete mode vs. Individual mode, check neither duplicates into the other when switching
- [ ] Lime tab — single results panel, but check the pelletized-lime note and CCE note don't repeat
- [ ] Shrubs & Trees — canopy calculation display vs. main results

### Pattern B: A button/link only reachable from one mode, but needed in another
**Origin:** Print Plan button lived only inside Custom-plan mode's div, invisible and unreachable in Auto mode (the default).

**Check every tab with a mode toggle for:**
- [ ] Cool/Warm Lawns: Auto ↔ Custom — is every actionable button (Print Plan, any "add"/"help me choose" button) reachable from **both** modes, not just the one it happened to be built in?
- [ ] Flower Garden: Complete ↔ Individual — same check
- [ ] Vegetable Garden: L×W ↔ Enter Area Directly bed-size toggle — same check
- [ ] Any tab: does switching modes call the *full* wrapper function (e.g. `calcCool()`) or does it call a narrower internal function directly, bypassing wrapper-level logic (print-button visibility, lime re-render, etc.)? This exact bug was found in `setPlanMode()` calling `calcAutoplan()`/`calcMulti()` directly instead of `calcCool()`/`calcWarm()`.

### Pattern C: Soil Test tab value doesn't actually carry over to its destination tab
**Origin:** Lime recommendation entered on the Soil Test tab was never written to Cool/Warm Lawns' new lime fields — `carryOverToCalculators()` had no line for it.

**For every field that exists on both the Soil Test tab and a destination tab, confirm it actually transfers:**
- [ ] Lawn → Cool/Warm: lawn size, P rating, K rating, lime rec, lime type, annual N (Waypoint only), grass species default
- [ ] Vegetable Garden: area, P/K ratings (auto-read, not carried — confirm this is *intentional*, not a gap), lime rec, lime CCE/bag size (these are NOT on the Soil Test tab — confirm the app doesn't imply they should carry over)
- [ ] Flower Garden: same set as Vegetable Garden
- [ ] Shrubs & Trees: P/K ratings (still manually entered on Shrub tab itself — confirm this is documented as not-yet-restructured, not a silent gap)
- [ ] Lime tab (Shrub-only now): does anything still try to carry lime values to the old lime-tab fields that no longer matter for lawn/garden purposes? (This exact stale carry-over was found and removed July 31 — check nothing re-added it.)
- [ ] **Test method:** on the Soil Test tab, fill in a real value, click "Continue to [X] Calculator," then check the destination *field itself* (not just that a card mentions the number) actually has it.

### Pattern D: A report-purpose routing check only handles some of the 4 purposes
**Origin:** Several interpretation cards (Lime Recommendation, Base Saturation, Buffer Index, then later the pH card) used a simple `isGarden ? 'garden' : ...` check that lumped vegetable/flower/shrub together, instead of routing each to its own correct tab. Found and fixed in three cards, then found again in a fourth the next session.

**Grep-based check (do this one via code, it's the fastest way):** search the whole file for `isGarden ?` and manually verify every match correctly distinguishes vegetable vs. flower vs. shrub vs. lawn, not just garden-vs-not-garden.

**Click-through check — for every one of the 8 report types, confirm every "Open/Continue to X" button and every routing decision goes to the *actually correct* tab:**
- [ ] VCE Lawn
- [ ] Waypoint Lawn
- [ ] VCE Vegetable Garden
- [ ] Waypoint Vegetable Garden
- [ ] VCE Flower Garden
- [ ] Waypoint Flower Garden
- [ ] VCE Shrubs & Trees
- [ ] Waypoint Shrubs & Trees

### Pattern E: Legacy code from before a restructure is still active, giving contradictory advice
**Origin:** Vegetable Garden's `calcGarden()` retained an entire pre-restructure P/K flag system (`pkHtml`/`P_REC`/`K_REC`) that only stopped firing by coincidence — most Nitrogen Source choices happen to be 0% P/K, but Fish Meal and Bat Guano aren't, and selecting either un-suppressed a "use a zero-phosphorus fertilizer" message directly contradicting the new Nutrient Application Plan shown right below it.

**This is the hardest pattern to catch by clicking through normally, since it depends on a specific input combination that isn't the "default" path. Deliberately test the non-default options:**
- [ ] Vegetable Garden: cycle through *every* Nitrogen Source option (not just the first/default one), checking for any leftover message that contradicts the Nutrient Application Plan section
- [ ] Flower Garden: same, in both Complete and Individual modes
- [ ] Any tab: try every dropdown option, not just the first one shown — legacy branches often only activate on non-default selections
- [ ] Any tab: enter values that produce *unusual* combinations (e.g., a nutrient rated Very High alongside a source that supplies that nutrient) specifically to check whether two systems both try to address it

### Pattern F: A shared color/CSS token reused in a context it wasn't designed for
**Origin:** `--slate-light` was darkened specifically for contrast against light backgrounds; two new card-header subtitles reused it against a dark green header, actual contrast 2.2:1 (needed 4.5:1). Separately, a CSS class (`fieldset.st-fieldset-block > legend`) designed for short uppercase section labels got reused for a long conversational paragraph, rendering it in shouting all-caps.

**Check for:**
- [ ] Any new text added to a dark-background element (card headers, the sample-button toolbar, any `.no-print` toast) — does it use a color actually verified against *that* background, not just any color that "looks like it should work"?
- [ ] Any long-form text using a CSS class whose comment/original purpose describes something shorter or differently-styled
- [ ] Spot-check: view every tab at 100% zoom and look for any text that's hard to read against its background, or any text in unexpected ALL CAPS

### Pattern G: Vegetable-crop-specific wording surfaces on Flower Garden (or vice versa)
**Origin:** Flower Garden's Individual-fertilizer mode reuses `GARDEN_PRODUCTS` (built for Vegetable Garden). Three nitrogen-source notes referenced tomatoes, cole crops, and vegetable-specific planting windows — technically accurate, but confusing to someone growing roses.

**Check:**
- [ ] Flower Garden, Individual mode: read every Nitrogen Source option's note text — any vegetable-specific crop names or seasonal vegetable-planting references?
- [ ] Flower Garden, Individual mode: read every P/K/Ca/Mg/S/micronutrient amendment note (shared `NUTRIENT_AMENDMENTS`) — same check
- [ ] Vegetable Garden: less likely direction, but check whether any flower-specific language (bloom, ornamental) leaked in from shared data

### Pattern H: A print-media CSS rule's exclusion list wasn't updated when a new tab/prefix was added
**Origin:** The "default print view" rule that shows the Soil Test tab was written with `:not(.printing-cool):not(.printing-warm):not(.printing-lime):not(.printing-garden)` — missing `.printing-flower` and `.printing-shrub` when those were added later, causing the Soil Test tab to print *simultaneously* with whichever of those two was actually requested.

**Check:**
- [ ] For each of the 6 tabs with a Print Plan button, click it and confirm the printed output shows **only** that tab's content — not the Soil Test tab's interpretation cards also appearing
- [ ] Confirm the printed output **includes** the Timing/Application-Timing card for that tab (a second, separate bug from the same investigation)
- [ ] Confirm the Print Plan button's on-page **position** doesn't imply it excludes content above/below it that it actually includes (the "is this button's placement misleading" UX issue, separate from whether print itself works)

### Pattern I: A generic/shared interpretation card gives a subtly different threshold than a tab-specific one for the same fact
**Origin:** The Soil Test tab's generic Manganese card said availability "drops sharply above pH 6.5"; Vegetable Garden's Manganese Sulfate note (independently verified against Cornell/UMD/Michigan State) says it "becomes limiting above ~6.5" but the sharp drop is actually above 7.5 — two different claims sharing the same number, found only because a user compared the two pages directly.

**Check:**
- [ ] For every nutrient/factor discussed on **both** the Soil Test tab's generic interpretation card **and** a specific amendment note elsewhere (Vegetable Garden, Flower Garden, Lime), read both side by side and confirm the specific numbers/thresholds actually agree
- [ ] Particular attention: pH thresholds for P, K, Ca, Mg, S, Zn, Mn, Cu, Fe, B — each of these appears on the Soil Test tab generically and is referenced again in at least one calculator tab's amendment logic

---

## Part 2 — Full Per-Tab Walkthrough

For each tab below, actually enter data and read every result — don't just confirm a field exists.

### 2.1 — Soil Test Report tab
- [ ] Load each of the 4 sample buttons (Lawn, Flower Garden, Vegetable Garden Waypoint, VCE Vegetable Garden); confirm every field populates correctly and every interpretation card shows sensible values
- [ ] Manually select each of the 8 report-type dropdown values with no other data entered; confirm the field layout (VCE vs. Waypoint block, lawn vs. garden fields) switches correctly every time
- [ ] Enter a value low enough / high enough to trigger every rating tier (Low, Medium/Optimum, High, Very High) for P, K, Ca, Mg — confirm each interpretation card's message actually changes appropriately
- [ ] Confirm the "Continue to [X] Calculator" button is genuinely unreachable-but-visible before P/K are entered (the button-appears-before-tab-unlocks behavior confirmed July 29) — is this still the intended design, or should it be revisited now that so much has changed?
- [ ] Test the "Need to see the instructions?" prompt — Yes/No paths
- [ ] Tab through the entire page with keyboard only; confirm nothing is skipped (regression-check the July 27 tabindex fix)

### 2.2 — About & Instructions tab
- [ ] Expand every collapsible section; confirm none reference removed features (Lime tab for lawns, old blended-fertilizer-only Flower Garden, etc.)
- [ ] Confirm the numbered steps in each per-tab mini-guide match the actual current field numbering on that tab (a renumber on the real tab without updating the instructions is an easy drift to introduce)

### 2.3 — Cool-Season Lawns
- [ ] Enter values in Auto mode fully; confirm results panel populates, inline area shows brief summary only (not a duplicate table), Print Plan button appears after the Timing card and works
- [ ] Switch to Custom mode; add 4 application slots; confirm season summary totals compute correctly and match manual arithmetic
- [ ] Switch back to Auto mode; confirm no stale Custom-mode data leaks into the Auto display
- [ ] Enter a lime recommendation, CCE, and bag size; confirm the lime display box appears with correct math (spot-check against `calcLimeForBed()`'s formula by hand)
- [ ] Clear the lime recommendation field; confirm the lime box disappears rather than showing stale data
- [ ] Toggle every shade option (Full sun, Some shade, Heavy shade) and every clipping option; confirm the effective N rate note updates and the math is right
- [ ] Click "Back to Soil Test Report" at the bottom; confirm it actually navigates there

### 2.4 — Warm-Season Lawns
- [ ] Repeat every Cool-Season check above
- [ ] Confirm species-specific per-application caps differ correctly from Cool-Season's (bermuda/St. Augustine tolerate higher rates)
- [ ] Confirm no August 15 cutoff logic error (warm-season N timing rule)

### 2.5 — Lime tab
- [ ] Confirm it's now unreachable for Lawn, Vegetable Garden, and Flower Garden report types — only Shrubs & Trees should unlock it
- [ ] With a Shrub report entered, confirm lime values carry over correctly
- [ ] Enter a CCE below 50%; confirm the gypsum warning appears
- [ ] Confirm "Back to Soil Test Report" link works

### 2.6 — Vegetable Garden
- [ ] Enter every crop type in turn; confirm the merged guidance panel (feeding level, pH, N default, sidedress timing) shows correct, crop-specific values for at least 4–5 different crops spanning heavy/medium/light feeders
- [ ] Cycle through every Nitrogen Source option (see Pattern E above) — this is the highest-value single check given what it already found
- [ ] Enter a Waypoint numeric target for at least 3 different micronutrients inline; confirm each computes a precise amount and that switching away and back doesn't lose the entered value
- [ ] Enter lime rec + CCE + bag size; confirm math and bag count
- [ ] Confirm the organic/synthetic toggle works for every amendment that offers both
- [ ] Confirm the bulk-density widget appears only for unsourced products and accepts a manual entry correctly

### 2.7 — Flower Garden
- [ ] Repeat the crop-type and lime checks from Vegetable Garden (adapted for annual/perennial/rose/bulb)
- [ ] Toggle Complete ↔ Individual mode multiple times; confirm P/K rows correctly suppress in Complete mode and correctly show real amendments in Individual mode every time (not just the first switch)
- [ ] In Individual mode, cycle through every Nitrogen Source option, reading every note for vegetable-specific language (Pattern G)
- [ ] Confirm switching flower type doesn't reset the fertilizer mode toggle unexpectedly

### 2.8 — Shrubs & Trees
- [ ] Confirm the deficiency-symptom framing still shows first, before any product recommendation
- [ ] Enter every plant type; confirm canopy-doubling math is correct for at least 3 different canopy sizes
- [ ] Confirm P/K ratings (still manually entered here, not yet auto-filled from Soil Test tab) work correctly — and flag this as the one tab still on the pre-restructure P/K entry pattern, for future prioritization
- [ ] Confirm acid-loving species get the "may not need/want lime" framing rather than a generic lime push

---

## Part 3 — Cross-Cutting Checks (do these last, across everything above)

- [ ] **Print output for all 6 calculator tabs**, in sequence, without reloading between them — confirm no state leaks from one tab's print into another's (this is exactly how the Soil-Test-tab-printing-alongside-Flower-Garden bug was found)
- [ ] **Full keyboard-only pass** across every tab — Tab key reaches every interactive element in a sensible order, no skips
- [ ] **Contrast spot-check** on any newly-added text since the last full sweep (compute actual ratios for anything new, don't eyeball it)
- [ ] **Mobile/narrow-width check** — resize to ~380px and confirm no horizontal overflow or unreadable wrapped text, especially on the newer Cool/Warm lime fields and Flower Garden's mode toggle
- [ ] **Re-run the whole plan on the actual deployed URL, not just a local copy** — several bugs this project were deployment-lag issues where a fix was correct locally but the live site hadn't caught up yet; confirm what's live matches what's expected before concluding a check "passed"
