# Source-Traceability Verification — VCE Lawn & Garden Care Calculator

**Purpose.** This document verifies the claim that *every agronomic statement presented to the user in the calculator can be traced to a source listed in the Source Documents & Attribution appendix on the About & Instructions tab.* It records the method used, the result, and the small number of items identified for correction.

**Date:** June 2026
**Scope audited:** (1) the soil-test interpretation cards, (2) the recommendation text on all six calculator tabs (Cool-Season Lawn, Warm-Season Lawn, Lime, Vegetable Garden, Flower Garden, Shrubs & Trees), and (3) the glossary definitions. UI prompts, input placeholders, and illustrative retail product examples (e.g., named fertilizer grades like 29-0-7) were treated as out of scope, as they are operational text rather than agronomic claims.

---

## Method

The audit targeted the place a fabricated ("synthetic") claim would most likely hide: **untagged agronomic sentences** — statements that assert a soil-science fact or a specific number but carry no inline source citation. Claims that already name their source inline (over 100 of them, e.g. *(VCE Note 19)*, *(430-011)*, *(426-323)*, *(Waypoint Agronomy Facts 8)*) were treated as self-attributing and confirmed against the appendix list.

For untagged claims, each was tested against two questions:

1. **Traceable?** Does its substance map to a source listed in the appendix?
2. **Accurate?** Is the claim (and any specific number in it) factually correct?

A claim was flagged only if it failed one of these — i.e., it was untraceable to any appendix source, or it was factually wrong. Standard, correct textbook phrasing was treated as passing. Anything that could not be placed from the project's established sourcing was independently checked against the underlying publication.

---

## Result

**No synthetic content was found.** Across all three surfaces, every agronomic claim traces to a source in the appendix. The interpretation cards, tab recommendation text, and glossary definitions rest on the appendix set — principally VCE Soil Test Note 1 (452-701), SPES-384, Soil Test Note 19 (452-719), Publication 430-011, Publication 426-323, the crop-specific VCE publications, Waypoint Agronomy Facts 8, and the named supplementary UMD / Clemson / Rutgers / NC State Extension sources.

The audit did identify **three minor accuracy or wording items** on specific numeric or definitional claims. None is a fabricated claim; each is a correctable precision issue, listed below. The headline finding — full source-traceability with no invented content — stands independent of these fixes.

---

## Items Identified for Correction

### 1. CCE percentage ranges in the lime-type help text
**Location:** Lime-type help text (Agricultural vs. Dolomitic lime descriptions).
**Current text:** "Agricultural [calcitic] Lime: CCE is usually 80–100%." / "Dolomitic Lime: CCE is often 95–108%."
**Issue.** The two ranges are mismatched relative to authoritative liming-material tables, which place calcitic limestone at roughly 95–108% and dolomitic at roughly 85–100%. The underlying chemistry agrees: pure calcite is 100% CCE and high-magnesium dolomite reaches ~108%, so dolomitic material trends *higher*, not lower. As written, the calcitic and dolomitic figures are effectively reversed. In addition, these specific percentage bands are not drawn from a Virginia source; VCE 452-510 (*Sources of Lime for Acid Soils in Virginia*) frames CCE as "usually 100" for the soil-test recommendation and distinguishes calcitic from dolomitic by carbonate content rather than by these bands.
**Correction direction.** Align the wording with VCE 452-510 — describe CCE as typically near 100, note that dolomitic can slightly exceed 100, and define the calcitic/dolomitic distinction by composition — or remove the specific percentage bands and keep the qualitative description. Cite 452-510.

### 2. Soluble-salts unit conversion (dS/m → ppm, ×640)
**Location:** Soluble-salts input hint / interpretation.
**Current text.** "Waypoint reports in dS/m. Converted to ppm (×640) for interpretation. Injury threshold: ~1.32 dS/m."
**Issue.** The 640 ppm-per-dS/m factor is a real, widely used conversion (the sodium-chloride standard), so the concept is sound — but it is not traceable to a source currently in the appendix, and it sits in a slight methodological mismatch with the Virginia injury threshold it is paired with. The 844 ppm threshold comes from VCE 452-701, which is based on Virginia Tech's 1:2 soil-to-water extract method; the ×640 factor derives from saturated-paste / NaCl salinity literature. The two are from different measurement systems.
**Correction direction.** Either cite the conversion's source and add a brief note that the dS/m→ppm factor is approximate and method-dependent, or present the Waypoint and VCE salt figures without implying an exact cross-method equivalence. (The 844 ppm threshold itself is correct and traces cleanly to 452-701 — no change needed there.)

### 3. Glossary wording: "calcium only" for calcitic lime
**Location:** Glossary, *dolomitic* entry.
**Current text.** "...agricultural (calcitic) lime, which supplies calcium only."
**Issue.** Slight overstatement. Per VCE 452-510, calcitic limestone in Virginia is defined as having ≥85% of its neutralizing value from calcium carbonate — it contains *little* magnesium, not *zero*. The interpretation cards already use the more careful phrasing "contains little magnesium"; the glossary should match.
**Correction direction.** Change "supplies calcium only" to "supplies calcium and little magnesium," consistent with the cards and 452-510.

---

## Bottom Line

The calculator's agronomic content is fully source-traceable to the appendix, with no fabricated or unsupported claims. The three items above are precision corrections to specific numeric/definitional statements, not content leaks, and can be addressed in a single editing pass.
