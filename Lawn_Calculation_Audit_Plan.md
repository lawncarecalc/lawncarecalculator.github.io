# Lawn Tab Calculation Audit — Application Rates & Timing

**Scope:** Cool-Season Lawns and Warm-Season Lawns tabs. Covers how much nitrogen per application, which months, the yearly maximum, the bag-label program, and the pounds of product.
**App version audited:** v12.2 (2026-10-12)
**Primary source:** VCE 430-011 / SPES-334, *Lawn Fertilization in Virginia* (Goatley et al.). The user supplied the PDF and screenshots of Tables 1–4 on 2026-10-22.
**Method:** Every number is checked two ways: by hand from the source, and by running the real `index.html` in a headless browser (`auditB.js` in the session scratchpad). A mismatch counts as a bug only after re-reading both the current code and the source table.

Status key: ✅ matches · ⚠️ deliberate difference, needs your confirmation · ❌ wrong, fix proposed · ⬜ not yet checked

---

## Part A — Built-in tables vs. VCE 430-011

### A1. Month-by-month schedule (`VCE_SCHEDULE`) vs. Tables 2–4

Amounts are lbs N per 1,000 sq. ft. per month. "opt" = green (optional) cell in VCE's table.

| Grass | Program | VCE table | App | Status |
| :-- | :-- | :-- | :-- | :-- |
| Tall fescue / bluegrass / ryegrass | 1 | Sep 0.7, Oct 0.7, Nov 0.5 opt, Apr–May 0.5–0.7 opt; season ≤ 3.5 | Sep 0.7, Oct 0.7, **Nov 0.7** opt, Apr or May **0.5** opt | ⚠️ see A4-1, A4-2 |
| Tall fescue | 2 | Sep 0.9, Oct 0.9, Nov 0.5 opt, Apr–May 0.5–0.9 opt; ≤ 3.5 | Sep 0.9, Oct 0.9, **Nov 0.7** opt, Apr or May 0.9 opt | ⚠️ see A4-1 |
| Tall fescue | 3 | Sep 1.0–1.5, Oct 1.0–1.5, Nov 0, Apr–Jun 0–1.0 opt; ≤ 2.8 | Sep 1.5, Oct 1.5, Apr–Jun 1.0 opt; cap 2.8 | ✅ |
| Fine fescue | 1 | Sep 0.7, Apr 0.7 opt; ≤ 2.0 | same | ✅ |
| Fine fescue | 2 | Sep 0.9, Apr 0.9 opt; ≤ 2.0 | same | ✅ |
| Fine fescue | 3 | Sep 1.0, Apr–May 1.0 opt; ≤ 2.0 | same | ✅ |
| Bermuda / St. Augustine | 1 | Apr 0.5 opt, May–Jul 0.7, Aug 0.5 opt; ≤ 4.0 | same | ✅ |
| Bermuda | 2 | Apr 0.5 opt, May–Jul 1.0, Aug 0.5 opt; ≤ 4.0 | same | ✅ |
| Bermuda | 3 | Apr–May 1.0–1.5, Jun–Jul 1.0–1.5, Aug 1.0 opt; ≤ 3.2 | Apr–May 1.5, Jun–Jul 1.5, Aug 1.0 opt; cap 3.2 | ✅ |
| Zoysia / centipede | 1 | May 0.7, Jul 0.7 opt; ≤ 2.0 | **"April–June"** 0.7, Jul 0.7 opt | ⚠️ see A4-3 |
| Zoysia / centipede | 2 | May 1.0, Jul 1.0 opt; ≤ 2.0 | "April–June" 1.0, Jul 1.0 opt | ⚠️ see A4-3 |
| Zoysia / centipede | 3 | May 1.0, Jul 1.0 opt; ≤ 2.0 | "April–June" 1.0, Jul 1.0 opt | ⚠️ see A4-3 |
| Bermuda (overseeded) | all | Yellow Sep–Nov cells, 0.5–0.7 (P1) / 0.5–1.0 (P2, P3) | not modeled | ⚠️ known gap |

### A2. Per-grass numbers (`SPECIES_CONFIG`)

| Item | Source says | App | Status |
| :-- | :-- | :-- | :-- |
| Cool quick-release, one month | DCR via 430-011 p. 2: ≤ 0.7 lb available N per growing month | maxApp P1 0.7 | ✅ |
| Slow-release, one month | ≤ 0.9 cool / ≤ 1.0 warm (430-011 p. 2) | maxApp P2 0.9 cool / 1.0 warm | ✅ |
| Program 3 per application | Table 1: 1.5 only for ≥ 50% slow-release; Table 4 tops at 1.5 (tall, bermuda), 1.0 (fine, zoysia) | 1.5 / 1.0 | ✅ |
| Warm quick-release ceiling | Soil Test Note 18: never > 0.9 (not in 430-011) | maxApp P1 0.9 | ✅ (Note 18) |
| Recommended amounts (`recApp`) | upper value of main months in Tables 2–4 | tall 0.7/0.9/1.5, fine 0.7/0.9/1.0, bermuda 0.7/1.0/1.5, zoysia & centipede 0.7/1.0/1.0 | ✅ |
| Annual maximum (`maxN`) | 3.5 cool, 2.0 fine, 4.0 bermuda, 2.0 zoysia/centipede (Tables 2–3 upper limits; DCR) | same | ✅ |

### A3. Most each program can deliver in a year (sum of months, held to the seasonal cap)

| Grass | P1 hand / app | P2 hand / app | P3 hand / app | Status |
| :-- | :-- | :-- | :-- | :-- |
| Tall fescue | 0.7+0.7+0.7+0.5 = 2.6 / 2.6 | 0.9+0.9+0.7+0.9 = 3.4 / 3.4 | 1.5+1.5+1.0 = 4.0 → cap 2.8 / 2.8 | ✅ |
| Fine fescue | 1.4 / 1.4 | 1.8 / 1.8 | 2.0 / 2.0 | ✅ |
| Bermuda | 3.1 / 3.1 | 4.0 / 4.0 | 4.0 → cap 3.2 / 3.2 | ✅ |
| Zoysia, centipede | 1.4 / 1.4 | 2.0 / 2.0 | 2.0 / 2.0 | ✅ |

Taken strictly from the VCE tables (Nov 0.5), tall fescue would be P1 0.7+0.7+0.5+0.7 = **2.6** (same total) and P2 0.9+0.9+0.5+0.9 = **3.2** (the app gives 3.4).

### A4. Findings from Part A

1. ⚠️ **Tall fescue November is 0.7 in the app; Tables 2 and 3 say 0.5.** This was a deliberate choice in v11.2, following VCE 430-520's "SON" guidance (up to 0.7 lb water-soluble N in Sep, Oct and Nov). It makes no difference to Program 1's total. For Program 2 it raises the yearly maximum from 3.2 to 3.4, so the app shows a 3.4 lb target as "reachable" where 430-011 alone would stop at 3.2. **Decision needed:** keep 430-520 (0.7), or follow 430-011 (0.5)?
2. ⚠️ **Tall fescue spring, Program 1, is 0.5 in the app.** The table allows "0.5 to 0.7 across the period"; the app uses the low end, per SPES-670. This is within VCE's range, and no change is proposed.
3. ⚠️ **Zoysia/centipede main application is labeled "April–June".** All three VCE tables put it in the **May** row only. The 430-011 text gives the warm-season window as April 1 – August 15, which may be where "April–June" came from. **Proposed:** relabel it "May" to match the tables. Optional slot stays July.
4. ❌ **Cool-season lawn-situation table, fine fescue row: "0.7–1.0 lbs".** VCE Tables 2–4 give fine fescue's possible seasonal total as **1.0–2.0**. The 0.7–1.0 figure has no source in 430-011. The same figure appears in the "About your VCE report" note on the Cool-Season tab. **Proposed:** change both to 1.0–2.0, or find the source for 0.7–1.0.
5. ❌ **Cool-season lawn-situation table, "Higher quality" row: 3.0–3.5 lbs, 4 applications.** No program reaches 3.5 in the app: P2 tops at 3.4, and at 3.2 if finding 1 goes the VCE-table way. Program 3 can't do 4 applications (max 3; cap 2.8). **Proposed:** change the range to 3.0–3.4 (or 3.0–3.2), and the application count to "3–4 (P1/P2)".
6. ⚠️ **Bermuda overseeding (yellow cells) not modeled.** This is a known gap. VCE discourages overseeding warm-season grasses other than bermuda. No change is proposed unless you want it.

---

## Part B — Hand-checked core math (run 2026-10-22, all in headless Chromium against v12.2)

### B1. Splitting N across months (`buildAutoSlots`)

Rule: use the fewest applications that reach the target. Required months come first, then optional ones in table order. Spread the target evenly; a month that hits its cap gets its cap, and the rest is re-spread. The total is held to the seasonal cap.

| Case | Hand result | App result | Status |
| :-- | :-- | :-- | :-- |
| Tall P1, 2.5 | Sep/Oct/Nov 0.667, spring 0.5 | same | ✅ |
| Tall P2, 2.5 | Sep 0.9, Oct 0.9, Nov 0.7 (3 apps) | same | ✅ |
| Tall P3, 2.5 | Sep 1.25, Oct 1.25 | same | ✅ |
| Tall P1, 1.0 | Sep 0.5, Oct 0.5 | same | ✅ |
| Tall P1 / P2 / P3, 3.5 | delivers 2.6 / 3.4 / 2.8, short | same | ✅ |
| Tall P3, 3.5 | 2.8 over 3 apps, 0.933 each | same | ✅ |
| Fine P1, 2.0 | 0.7 + 0.7 = 1.4, short | same | ✅ |
| Fine P2, 1.0 | 0.5 + 0.5 | same | ✅ |
| Bermuda P1, 3.0 | Apr 0.5, May–Jul 0.667, Aug 0.5 = 3.0 | same | ✅ |
| Bermuda P3, 3.2 and 4.0 | 1.1, 1.1, Aug 1.0 = 3.2 (cap) | same | ✅ |
| Zoysia P1, 2.0 | 0.7 + 0.7 = 1.4, short | same | ✅ |
| Zoysia P2, 1.5 | 0.75 + 0.75 | same | ✅ |
| Centipede P3, 1.0 | one application, 1.0 | same | ✅ |

**Golden-number correction:** CLAUDE.md's "Bermuda Program 1 at 3.0 lb delivers 2.8, with a warning" dates from v11.1, before the VCE schedule existed. Under the current schedule it delivers **3.0 with no warning** (5 applications). Update the documented golden number.

**Observation, not a bug:** with "fewest applications," a 2.5 lb tall fescue target on Program 2 uses November but not spring. That matches VCE's emphasis on fall feeding.

### B2. Shade and clippings (`effectiveNRate`, `lookForTarget`) — tall fescue, goal 4.0

| Case | Hand | App | Status |
| :-- | :-- | :-- | :-- |
| Full sun | 4.0 → capped at 3.5 | eff 4, used 3.5, capped | ✅ |
| Some shade (×0.67) | 2.68 | 2.68 | ✅ |
| Heavy shade (×0.5) | 2.0 | 2.0 | ✅ |
| Clippings only | 4 − min(4/3, 1.0) = 3.0 | 3.0 | ✅ |
| Heavy shade + clippings | 2.0 − 2.0/3 = 1.333 | 1.333 | ✅ |
| Some shade + clippings | 2.68 − 0.893 = 1.787 | 1.787 | ✅ |

The order is shade first, then the clipping credit, then the cap, as designed. Both reductions come from 430-011 p. 5.

### B3. Program from the bag label (`detectProgram`, survey bags)

| Case | Hand | App | Status |
| :-- | :-- | :-- | :-- |
| 2.98 of 20 N (14.9%) | P1 | P1 | ✅ |
| 3.0 of 20 (15.0%) | P2 | P2 | ✅ |
| 9.98 of 20 (49.9%) | P2 | P2 | ✅ |
| 10 of 20 (50.0%) | P3 | P3 | ✅ |
| 430-011's own example: 5.6 WIN of 16 N = 35% | P2 | P2 | ✅ |
| 32-0-10 methylene urea, 0.5 + 6.8 = 7.3 / 32 = 23% | P2 | P2 | ✅ |
| Survey totals (19 bags) | 5 / 11 / 3 | 5 / 11 / 3 | ✅ |

430-011 confirms the counting rules: methylene urea counts WIN; coated urea counts even though it isn't listed as WIN; "contains 50% organic" doesn't count. The app's added "slowly available from methylene urea" footnote line comes from Goatley's DCR slide deck (v10.8), not from 430-011.

### B4. Pounds of product: lbs = N ÷ %N × 100 × (lawn sq. ft. ÷ 1,000) — 430-011 p. 6 formula

**Against VCE Table 1 (45 cells):** 40 match exactly. Five differ by 0.1 lb:

| Grade @ lb N | VCE Table 1 | Exact | App | Why |
| :-- | :-- | :-- | :-- | :-- |
| 6-2-0 @ 1.0 | 16.6 | 16.667 | 16.7 | VCE truncated |
| 16-4-8 @ 1.0 | 6.2 | 6.250 | 6.3 | VCE rounded half down |
| 16-4-8 @ 1.5 | 9.3 | 9.375 | 9.4 | VCE rounded down |
| 32-0-10 @ 1.0 | 3.2 | 3.125 | 3.1 | VCE likely scaled from its 0.5 column (1.6 × 2) |
| 32-0-10 @ 1.5 | 4.8 | 4.688 | 4.7 | VCE likely scaled from its 0.5 column (1.6 × 3) |

✅ The app follows VCE's own published formula exactly. The five differences are rounding inside VCE's table, not app errors. No change proposed.

**Card amounts, 5,000 sq. ft. tall fescue, goal 3.4, Program 2, 32-0-10:**
- Hand: 3.4 ÷ 0.32 × 5 = **53.1** to buy; 0.9 ÷ 0.32 × 5 = **14.1** per Sep/Oct/spring application; 0.7 ÷ 0.32 × 5 = **10.9** in November.
- App: 53.1 / 14.1 / 10.9. ✅
- Months with the same amount are grouped in calendar order. ✅

---

## Part C — Every place that shows a number agrees ⬜ (next)
For the same inputs, compare the "What to look for" card, the auto plan table, the pre-filled Custom plan, the Custom-plan warnings and the print copy. Run for cool and warm, VCE and Waypoint.

## Part D — Edge cases ⬜
- No goal entered (red prompt); no lawn size (per-1,000 fallback).
- Goal above every program's maximum.
- Zoysia/centipede on Program 1; fine fescue in heavy shade.
- Custom application between the recommended amount and the ceiling (amber), and over the ceiling (error).
- 5 Custom applications; a Waypoint N above Virginia's limit.

## Part E — Lime on lawn tabs ⬜
`calcLimeForBed` golden: 40 lbs/1,000 at 90% CCE, 8,000 sq. ft., 40 lb bags → 44.4 / 355.6 total / 1 application / 9 bags. Also a case over the 50 lb per-application limit.

---

## Related item — VCE Table 1 grades vs. the local bag list (`LOCAL_SURVEY`)

| Table 1 grade | In local survey? |
| :-- | :-- |
| 6-2-0 | No |
| 10-10-10 | No |
| 16-4-8 | No |
| 24-25-4 | Yes (2 bags: methylene urea P2, coated urea P2) |
| 28-0-4 | No |
| 32-0-10 | Yes (methylene urea P2, coated urea P3) |
| 20-0-0 | No |
| 38-0-0 | No |
| 45-0-0 | No (survey has 46-0-0) |

Table 1 gives grades only, with no slow-release figure. The program can't be known from the grade alone: Table 1's own footnotes say 0.9/1.0 lb is only for 15–49% slow-release, and 1.5 only for ≥ 50%. These grades also weren't seen locally.

**Done in v12.3 (2026-10-22):** the 7 missing grades were added to `LOCAL_SURVEY` with a `vce:true` flag. They count as quick-release (Program 1), per 430-011: "if water-insoluble nitrogen is not listed... assume it is all water-soluble." On the card they are marked ‡ with a footnote, and the count line reads "19 bags, plus 7 example grades from VCE's Table 1." Checked: the card's 28-0-4 amounts (2.4 lbs at 0.667 lb N, 1.8 lbs at 0.5 lb N) match Table 1. The ‡ marks also appear in the print copy.

---

## Summary of proposed changes (none made yet)
1. Decide November 0.7 (430-520) vs. 0.5 (430-011) for tall fescue Programs 1–2 (A4-1).
2. Relabel the zoysia/centipede main application "May" (A4-3).
3. Fix fine fescue "0.7–1.0 lbs" → 1.0–2.0, in the table and in the VCE note (A4-4).
4. Fix the "Higher quality" row: 3.0–3.4 lbs, 3–4 applications (A4-5).
5. Update CLAUDE.md's bermuda Program 1 golden number (B1).
6. ~~Add VCE Table 1 grades~~ — done in v12.3.

---

## Decisions and fixes — v12.4 (2026-10-22)

| Finding | Decision | Change made |
| :-- | :-- | :-- |
| A4-1 November 0.7 vs. 0.5 | Use 430-011 (2021, more recent than 430-520) | Tall fescue November is now 0.5 lb in Programs 1 and 2. Yearly maximums are now **P1 2.4**, **P2 3.2**, P3 2.8 |
| A4-2 Spring P1 0.5 | Keep | none |
| A4-3 Zoysia/centipede "April–June" | Fix | Relabeled "May" (schedule, card, warm-season intro text, README) |
| A4-4 Fine fescue "0.7–1.0 lbs" | Fix | Now 1.0–2.0 lbs in the cool-season table and the VCE note |
| A4-5 "Higher quality" row | Fix | Now 3.0–3.2 lbs, "4 (Program 2 only)"; the VCE note range was changed to match |

Re-checked after the change (headless browser):
- Tall P1 2.5 → 0.7, 0.7, 0.5, 0.5 = 2.4, which is short of the target.
- Tall P2 2.5 → 0.667 × 3 + Nov 0.5.
- Tall at 3.5 → the card shows 2.4 / 3.2 / 2.8, and Program 2 comes closest.
- 5,000 sq. ft. of 32-0-10 on Program 2 at 3.4 → capped at 3.2: buy 50.0, 14.1 per Sep/Oct/spring application, 7.8 in November.
- Zoysia → "May 0.7 · July 0.7 (optional)".
- The custom plan pre-fills Sep/Oct/Nov/May.
- No page errors; syntax clean.

**Golden numbers updated:** the 5,000 sq. ft. 32-0-10 example is now 50.0 / 14.1 / 7.8 (was 53.1 / 14.1 / 10.9), and the tall fescue season maximums are 2.4 / 3.2 / 2.8.


## Revised — v12.5 (2026-10-22)

The user confirmed 430-520 (Fall Lawn Care) is the 2025 edition. Standing rule: **where VCE publications disagree, the most recent one is the standard.** So A4-1 is reversed: tall fescue November is up to 0.7 lb on Programs 1 and 2 (430-520), and the yearly maximums are back to 2.6 / 3.4 / 2.8. The "Higher quality" row now reads 3.0–3.4 lbs, 4 applications (Program 2 only). The zoysia "May" label and fine fescue 1.0–2.0 stay. Golden numbers are back to 53.1 / 14.1 / 10.9.

**New open item from the rule:** 430-520 allows controlled-release N up to 1 lb in early September. The app's Program 2 September amount is 0.9 (430-011 Table 3). This needs a decision.


## Revised — v12.6 (2026-10-22)

Open item resolved (user: "follow 430-520's guidance"). Cool-season **Program 2 early September is now up to 1.0 lb** (430-520: early-September controlled-release up to 1 lb N; 430-011 Table 3 shows 0.9). Applies to tall fescue and fine fescue. Cool-season Program 2 never-exceed ceiling raised to 1.0. In custom mode, a slot in a month whose schedule amount is higher than the usual recommendation (September) uses that month's amount, so a 1.0 lb September slot shows "Within" instead of the amber note.

- Yearly maximums: tall fescue **2.6 / 3.5 / 2.8** (Program 2 now reaches the 3.5 limit); fine fescue **1.4 / 1.9 / 2.0**.
- "Higher quality" row: 3.0–3.5 lbs. Max-per-application column: "0.9–1.0 (P2)".
- Golden numbers: tall fescue P2 at 3.5 → early Sep 1.0, Oct 0.9, Nov 0.7, spring 0.9. 5,000 sq. ft. of 32-0-10 → buy 54.7 lbs; 15.6 in early September, 14.1 in October and spring, 10.9 in November. Tall P2 at 2.5 → 0.9 / 0.9 / 0.7.
- Custom slot checks (21-0-3 coated, Program 2): September 1.0 → within; 1.1 → exceeds 1.0.

**Still open:** 430-520's "up to 1 lb" controlled-release figure vs. Program 3's September and October 1.5 lb (430-011 Table 4). Not changed; needs a decision.

## Revised — v12.7 (2026-10-22)

Cool-season **Program 3 is now 1.0 lb per application** (user decision). 430-520 (2025) defines controlled-release as ≥15% water-insoluble N and allows up to 1 lb per application. That covers Program 3 products, so it replaces 430-011 Table 4's 1.5 lb for tall fescue in September and October. The seasonal cap stays 2.8 (430-011; 430-520 gives none).

- Tall fescue Program 3: Sep 1.0, Oct 1.0, Apr–Jun 1.0 (optional) → 2.8 max (three applications; was two of 1.5).
- Fine fescue Program 3 was already 1.0 → no change. Warm-season unchanged (430-520 covers cool-season grasses).
- Golden: tall P3 at 2.5 → 0.83 × 3; at 2.0 → 1.0 × 2; goal 3.5 capped → 0.93 × 3.
- Custom slot (40-0-5, 32% coated = Program 3): 1.0 within; 1.1 exceeds 1.0.
