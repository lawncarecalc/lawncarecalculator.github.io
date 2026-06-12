# Liming Materials CCE Survey — for validating the Lime tab CCE adjustment

The Lime tab's CCE (Calcium Carbonate Equivalent) adjustment can't be validated from a soil test report — the CCE comes from the **lime product label**, not the soil test. This survey gathers the authoritative CCE values for the liming materials a Virginia homeowner would actually find at a garden center, so the calculator's CCE math can be checked against real product values.

## Authoritative source

**VCE 452-510 / SPES-158P, "Sources of Lime for Acid Soils in Virginia"** (Mullins, Alley, Phillips; expert-reviewed Sept 2024). This is the Virginia land-grant source and belongs in the calculator's source hierarchy. It supersedes the generic figures the Lime tab may currently use.

## Table 1 — CCE by material type (VCE 452-510)

| Material | Composition | CCE (%) | Found at garden centers? |
| :-- | :-- | :-- | :-- |
| Pure calcium carbonate | CaCO₃ (pure) | 100 (standard) | Reference only |
| **Calcitic limestone** | CaCO₃ | **80–100** | ✅ common (pelletized & pulverized) |
| **Dolomitic limestone** | CaCO₃·MgCO₃ | **95–108** | ✅ very common (the default "garden lime") |
| Burned / Quick lime | CaO | 150–175 | rare for homeowners (caustic) |
| Hydrated / Slaked lime | Ca(OH)₂ | 120–135 | ⚠️ sold, but fast/caustic — not typical lawn use |
| Marl | CaCO₃ | 70–90 | regional |
| Ground oyster shells | CaCO₃ | 90–100 | ✅ sold as organic amendment |
| Cement kiln dust | Ca oxides | 40–100 | not retail |
| Power plant / wood ashes | Ca, Mg, K oxides | 25–50 | homeowner wood ash only |
| Gypsum | CaSO₄ | **None** | ✅ sold — but does NOT raise pH |

**Critical teaching point for the Help Desk:** gypsum (CaSO₄) is widely sold near lime in garden centers and looks similar, but its **CCE is zero — it does not neutralize acidity or raise pH.** A homeowner who buys gypsum to "lime" their lawn will see no pH change. The calculator should flag this if gypsum is somehow entered, or at least the Lime tab guidance should warn against it.

## Real-world product CCE values (what's actually on the shelf)

- **Pelletized lime** (the most common homeowner product — Pennington, Encap, Soil Doctor, store brands): high quality is labeled **near 100% CCE**; most fall **90–100%**. Per VCE and WVU Extension, quality pelletized lime is "labeled close to 100% CCE."
- **Pulverized/powdered calcitic lime:** typically **85–95%** (Virginia law requires ≥85% CCE to be sold as "Aglime").
- **Dolomitic lime** (calcium + magnesium): **95–108%** — note it can exceed 100%, so the CCE adjustment must accept values >100.
- **"Fast-acting" / prilled enhanced products** (e.g. Cal-Star, Mag-I-Cal): commonly **90–97%** CCE; the "fast" claim is about particle fineness, not CCE.

## Virginia legal floor

By the Virginia Agricultural Liming Materials Act (1994), anything sold as "Aglime" in Virginia must be **≥85% CCE**. So for retail lime products, the practical CCE input range is roughly **85–108%**, with pelletized products clustering near 100%. (Burnt/hydrated limes reach 120–175% but aren't typical lawn purchases.)

## Implications for validating the Lime tab CCE adjustment

The CCE adjustment should scale the recommended lime amount **inversely** to CCE: lower CCE → more material needed. VCE Table 2 gives the exact factors to validate against:

| CCE % | lbs to equal 1 ton pure CaCO₃ | Adjustment factor (vs 100%) |
| :-- | :-- | :-- |
| 50 | 4000 | ×2.00 |
| 60 | 3333 | ×1.67 |
| 70 | 2857 | ×1.42 |
| 80 | 2500 | ×1.25 |
| 90 | 2222 | ×1.11 |
| **100** | **2000** | **×1.00** |
| 110 | 1818 | ×0.91 |
| 120 | 1667 | ×0.83 |
| 135 | 1481 | ×0.74 |
| 150 | 1333 | ×0.67 |
| 175 | 1143 | ×0.57 |

The factor is simply **100 / CCE**. The Lime tab's CCE math should reproduce this column: e.g. a soil-test lime rec of 50 lbs/1,000 sq ft with an 80%-CCE product becomes 50 × (100/80) = **62.5 lbs**; with a 90%-CCE product, 50 × (100/90) = **55.6 lbs**.

## Validation test cases (no soil report needed — these are product-driven)

| Soil-test lime rec | Product | CCE | Expected adjusted amount |
| :-- | :-- | :-- | :-- |
| 50 lbs/1,000 | pelletized (label 100%) | 100 | 50.0 lbs (×1.00) |
| 50 lbs/1,000 | calcitic pulverized | 90 | 55.6 lbs (×1.11) |
| 50 lbs/1,000 | min-spec Aglime | 85 | 58.8 lbs (×1.18) |
| 50 lbs/1,000 | dolomitic (high) | 108 | 46.3 lbs (×0.93) |
| 50 lbs/1,000 | hydrated lime | 135 | 37.0 lbs (×0.74) |

Run each through the Lime tab's CCE input and confirm the output matches the "expected" column (factor = 100 / CCE). Pay special attention to **CCE > 100** (dolomitic, hydrated) — the adjustment must *reduce* the amount, not error or floor at 1.0.

## Recommended Lime-tab improvements surfaced by this survey

1. **Default CCE guidance:** tell the user pelletized products are usually ~100% and to read their label; provide the 85–108% typical range.
2. **Gypsum warning:** gypsum has zero CCE and won't raise pH — warn if a very low/zero CCE is entered, or add a note.
3. **Accept CCE > 100** (dolomitic and hydrated exceed it).
4. **Cite VCE 452-510 / SPES-158P** as the source for the CCE table — it's the Virginia authority and should be added to the About list if not already present.
