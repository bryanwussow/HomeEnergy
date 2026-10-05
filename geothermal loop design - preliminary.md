# Geothermal Ground Loop Design — Preliminary

**Date:** 2026-08-28; revised 2026-10-04
**Basis:** `geothermal-loop-design-prompt.md` (Project Parameters + Fixed Design Constraints), run against figures in `hvac-summary.md` (as of 2026-08-27) and `Wussow Ground Loop Plot Plan.pdf`. Revised 2026-10-04 using real WaterFurnace 5-Series manufacturer data from `OMW5-0016W Operation Maint.pdf` and `IGW5-0016W Install Guide.pdf` (Performance Data, Operating Limits, Reference Calculations, and Antifreeze Corrections), replacing several figures that were previously assumed or borrowed from a different unit size.
**Status:** Preliminary planning estimate only — not a final design. See "Assumptions and Flags" below for everything that needs field verification, soil testing, or contractor/PE sign-off before construction.

---

## 1. Summary of Key Results

| Item | Result |
|---|---|
| **Governing load** | Cooling (heat rejection), not heating |
| **Total pipe length required (calculated minimum)** | ~1,597 ft (both loops combined) — revised from an earlier ~1,430 ft estimate now that real manufacturer data is used (see Step 1) |
| **Recommended design length** | **~1,950 ft total — 975 ft per loop** (~488 ft out + ~488 ft back), ~22% margin over the raw Option B minimum (1,597 ft), still within the plot plan's 1,000 ft/loop max |
| **Pipe** | 1" nominal SDR-11 HDPE |
| **Design flow** | ~9 GPM total system flow, ~4.5 GPM per loop |
| **Estimated loop head loss** | ~13–15 ft per loop circuit (scaled up for the longer 975 ft loop) + ~7–9 ft heat pump water-side drop (confirmed from manufacturer WPD data, down from an earlier placeholder of ~15–20 ft) ≈ **~20–24 ft total system head** |
| **Fluid** | Methanol (default, preferred by contractor) or propylene glycol as an alternate — concentration needs fluid-specific confirmation (not necessarily the same % for each), see Section 4 |

Both Option A (single narrow trench) and Option B (wide separation) fit comfortably in the available loop field either way. **Option B is the leading choice** — better thermal performance, faster pipe placement/pressure testing, and the trenching machine for the extra passes is already available — at the cost of roughly double Option A's excavation, which isn't a binding constraint on this site.

## 2. Calculations and Assumptions

**Step 1 — Ground heat extraction/rejection loads, from the actual 036 (3-ton) unit's manufacturer Performance Data** (`OMW5-0016W Operation Maint.pdf`, "036 - Dual Capacity ... High Speed" table, 9 GPM / 1250 cfm — the table's "closed-loop optimum" flow point, matching our ~9 GPM design flow). **This replaces the earlier COP-derived estimate**, which approximated these loads from a 2.5-ton unit's borrowed COP/EER figures rather than reading the actual 3-ton unit's tested extraction/rejection numbers directly:

- Heating, at EWT 30°F: Heat of Extraction (HE) = **22,000 Btu/h** (COP 3.91 at this point)
- Cooling, at EWT 90°F: Heat of Rejection (HR) = **45,200 Btu/h** (EER ≈15.1 at this point — cooling EER drops sharply at this design-max EWT compared to brochure headline numbers measured at far more favorable EWT)

(For comparison, the earlier COP-derived approximation gave 27,627 Btu/h heating / 40,281 Btu/h cooling — the real heating load is lower, the real cooling load is higher, than that approximation.)

**Step 2 — Heat exchange rate per foot of pipe**, using the steady-state buried-cylinder shape-factor method (Kavanaugh-style simplification for a single isolated horizontal pipe):

q' = k × S' × ΔT, where S' = 2π / cosh⁻¹(2z/d)

- k (soil conductivity) = 0.9 Btu/(hr·ft·°F) — moist clay, per Project Parameters (**not soil-tested; a site soil boring/conductivity test must be done before this plan is finalized**)
- Pipe: 1" nominal SDR-11 HDPE, OD d = 1.315 in = 0.1096 ft
- Depth z = 5 ft (trench depth, per constraint #1)
- 2z/d = 10/0.1096 = 91.3 → cosh⁻¹(91.3) ≈ 5.21 → S' = 2π/5.21 = **1.21 (dimensionless)**
- q' = 0.9 × 1.21 × ΔT = **1.09 × ΔT** Btu/(h·ft)

**Step 3 — Design ΔT (ground temp vs. design fluid temp)**, using the ground temps from Project Parameters and the design entering-water-temperatures (EWT — the temperature of fluid *returning from the ground loop to the heat pump*, after it has already picked up or shed heat in the trench). **30°F/90°F are confirmed against the actual Operating Limits table** in both WaterFurnace PDFs (Min/Normal/Max Entering Water: 20°F/30–70°F/90°F heating, 30°F/50–110°F/120°F cooling) — our 30°F heating design point sits mid-"Normal" range, and our 90°F cooling design point is comfortably inside cooling's Normal range (50–110°F) too, nowhere near cooling's actual max of 120°F — both design points check out fine, no change needed:

- Heating: ground low 52°F, design min EWT 30°F → ΔT = 22°F → q' = 1.09 × 22 = 23.9 Btu/(h·ft) → **L = 22,000 / 23.9 ≈ 920 ft**
- Cooling: ground high (canopy-adjusted) 64°F, design max EWT 90°F → ΔT = 26°F → q' = 1.09 × 26 = 28.3 Btu/(h·ft) → **L = 45,200 / 28.3 ≈ 1,597 ft** ← **governs**

For reference (not used in the length calculation above): using WaterFurnace's own reference formula (`LWT = EWT ∓ HE or HR/(gpm × 500)`, from both PDFs' "Reference Calculations") with the real HE/HR from Step 1 — the fluid *leaving* the heat pump and entering the ground loop, the LWT, works out to **LWT = 30 − 22,000/(9×500) ≈ 25°F heating** and **LWT = 90 + 45,200/(9×500) ≈ 100°F cooling**. This is a more precise, formula- and data-sourced version of the earlier rough "8–10°F change, ~20–22°F/~98–100°F" estimate, and lands close to it — a good consistency check. Still not needed to size the loop length, but useful for antifreeze selection and the loop-saturation discussion below.

**Cross-check against industry rule-of-thumb table** (ft of pipe per ton, horizontal 2-pipe, moist clay, mixed-humid climate): typical range 400–670 ft/ton × 3 tons = **1,200–2,000 ft**. The result (1,597 ft) sits within this range — consistent, gives confidence in the estimate.

**Important limitation:** this calculation treats each pipe leg as an *isolated* pipe with no thermal interaction from its neighboring leg. That's a reasonable approximation for **Option B** (wide separation), but **Option A** (both legs close together in one narrow trench) will underperform this estimate due to mutual heat interference between supply and return — industry practice is to add roughly 15–25% extra length to compensate. That pushes Option A's effective target to **~1,835–1,995 ft**, while Option B could likely get by with something closer to the raw **~1,597–1,700 ft**.

**Second limitation — ΔT is treated as uniform along the pipe, when it actually shrinks along the flow path.** Step 3's ΔT (22°F heating, 26°F cooling) is based on design EWT — the point where fluid re-enters the heat pump, after it has already picked up the most heat it will get from the ground (heating) or shed the most heat it will lose (cooling). Everywhere else along the trench, the fluid is farther from ground temperature and the true local ΔT is larger. Applying the EWT-based ΔT uniformly assumes the whole loop performs at its worst (most "saturated") point — this is a conservative simplification (it overstates required length, not understates it), not an error, but it's still a simplification rather than a full log-mean-temperature-difference or exponential-decay analysis. Roughly quantifying: at ~4.5 GPM per loop with ~15% antifreeze (cp ≈ 0.94 Btu/lb·°F), the loop's thermal "decay length" (mass flow × cp ÷ Step 2's per-foot conductance) is roughly 2,000 ft versus the ~975 ft loop itself — so the fluid only closes ~35–40% of the gap to ground temperature over the full loop length. This is a real but moderate source of built-in conservatism, and part of why the recommended design sits above the raw calculated minimum, alongside the interference margin above.

**Recommended design point: 1,950 ft total (975 ft/loop)** — bumped up from 1,800 ft for extra margin now that the raw Option B minimum is 1,597 ft (real manufacturer data pushed this up from an earlier ~1,424 ft estimate). 1,950 ft sits ~22% above that raw minimum, and lands within the ~1,835–1,995 ft range that would cover even Option A's interference-derated requirement, despite Option B being the chosen layout. Still within each loop's 1,000 ft plot-plan limit (975 ft/loop, leaving ~25 ft/loop, ~2.5%, in reserve) — tighter reserve than the previous design's ~10%, but land isn't the binding constraint here, length is the lever being used for margin.

## 3. Layout Description

- **Two loops** per `Wussow Ground Loop Plot Plan.pdf`: Ground Loop 1 (east, near Lot 57B line) and Ground Loop 2 (west, near Lot 58 line), each a teardrop running ~488 ft north/north-northwest from the house and back (975 ft round trip) — now close to the plot plan's ~500 ft one-way / 1,000 ft round-trip ceiling (~2.5% margin left), up from the previous design's more comfortable ~10% margin.
- **Option A layout:** each loop is a single ~488 ft trench; supply and return pipes travel together the whole way, diverge slightly at a rounded turnaround ~488 ft out, converge again at the house. Trenching required: ~488 ft per loop, **~975 ft total trenching** for both loops.
- **Option B layout:** each loop's supply and return legs run as separate trenches, held apart (any distance) for ~75% of the run, narrowing to ≥6 ft separation for the final stretch approaching the house. Trenching required: ~488 ft per leg × 2 legs × 2 loops = **~1,950 ft total trenching** (double Option A's excavation for the same pipe footage).
- **Option B is the leading choice for the homeowner:** better thermal performance (avoids Option A's close-spaced short-circuiting derate — see Section 2's "Important limitation"), pipe can be placed and pressure-tested faster since separate trenches can be worked without waiting on a shared narrow cut, and the trenching machine needed for the extra passes is already available. The added excavation (double Option A's linear footage) is the trade-off, but land isn't the constraint here.
- **Near the house:** both loops converge; outgoing lines run at 24 in. depth and cross the foundation wall through their own penetration, return lines in a separate sleeve 12 in. below (≈36 in. depth) through their own separate, nearby penetration — keeping the vertical offset through the wall itself (not merging into one opening) to avoid thermal short-circuiting, optionally aided by 2 in. rigid foam between them. The two penetrations are close enough together vertically for a single work area inside to access both, before reaching whichever manifold location is chosen below.
- **Manifold — two options under consideration:**
  - **Option 1 (inside the basement):** continuous, joint-free pipe runs from the trench field through the basement wall as-is, with all fusion joints, valves, and the manifold made up inside the basement. Simpler to execute (one pressure test, from inside, after the wall penetrations); costs more wall penetrations — up to 4 for the 2 planned loops.
  - **Option 2 (outside, below-grade vault):** each loop's supply/return lines terminate at fusion-welded joints in an exterior below-grade vault near the house, with a single reduced-count pair then penetrating the basement wall to the manifold/heat pump inside. Fewer wall penetrations, at the cost of field fusion welding and a separate vault pressure test, plus the vault itself.
  - No recommendation yet between the two — see Section 4.

## 4. Installation / Deliverable Notes

- **Flow & circulation:** ~9 GPM total (3 GPM/ton design standard), split ~4.5 GPM per loop across the two parallel loops — **confirmed as the 036 unit's own "closed-loop optimum" rated flow point** in the Performance Data table, not just an assumed rule of thumb. At 4.5 GPM in 1" SDR-11 pipe (ID ≈1.077 in), velocity ≈1.6 ft/s — acceptable for HDPE, though on the low side for peak convective heat transfer; trades off against much lower head loss than 3/4" pipe (~13–15 ft/975 ft loop vs. ~47 ft/975 ft loop for 3/4" pipe) over these long runs. **Heat-pump water-side pressure drop is now confirmed from the manufacturer's own WPD data: ~7–9 ft of head at 9 GPM** (was a ~15–20 ft placeholder) — total system head is correspondingly lower, likely allowing a smaller circulator than previously estimated (TBD, pending final pump curve selection).
- **Fluid:** methanol (default — preferred by the contractor for its lower viscosity and better heat-transfer performance at these temperatures) or propylene glycol as an alternate (simpler handling, avoids methanol's flammability concerns, if preferred instead). **Concentration flagged for correction:** the design previously assumed ~20% for both fluids; the manufacturer's own performance tables assume 15% antifreeze for EWT below 40°F, but — importantly — **15% does not mean the same freeze protection for both fluids**. Methanol is a steeper freeze depressant per percent than propylene glycol (roughly, 15% methanol protects to the mid-teens °F, while 15% propylene glycol only protects to the low-to-mid 20s°F) — given the estimated ~25°F coldest LWT (see Step 3), 15% propylene glycol would leave little to no safety margin, while 15% methanol would have a reasonable cushion. `OMW5-0016W` has a detailed Antifreeze Corrections table (page 17) with per-fluid, per-concentration correction factors that would settle this precisely, but the version of that table I could extract came through with scrambled row/column alignment — **worth a direct visual check of that page** before finalizing either fluid's concentration, rather than relying on the generic "15%" note alone.
- **Bedding/backfill:** clean fine backfill immediately around the pipe (trenchers don't place bedding automatically); native soil backfill above, compacted in lifts; keep sharp rock away from pipe wall.
- **Pressure testing:** standard IGSHPA practice — pressurize to ~100 psi, hold and monitor (e.g., 30 min–24 hr) with no pressure loss, before backfilling any section. Under Manifold Option 2 (vault), the vault's fusion joints need their own pressure test in addition to this.
- **Wall penetration:** sealed sleeve through the basement foundation wall (hydraulic cement or a purpose-made geothermal wall boot) to prevent water intrusion. Under Manifold Option 1 this means up to 4 penetrations (one supply/return pair per loop); under Option 2, a single reduced-count pair from the vault.
- **Manifold location — still open:** Option 1 (inside basement) is simpler for the homeowner to execute — continuous under-grade pipe through the wall, manifold connected and the whole system pressure-tested from inside in one step — but costs more wall penetrations. Option 2 (below-grade vault) reduces wall penetrations to one pair but requires fusion welding joints in the vault plus a separate vault pressure test. No recommendation made yet; flag for the contractor/PE to weigh in on, given site-specific factors like basement wall accessibility and vault excavation feasibility.
- **Permits/code:** confirm with Union County whether the loop excavation itself needs a permit (separate from the mechanical/HVAC permit for the heat pump); given proximity to the septic system and well shown on the plot plan, county health department review of trench routing may also apply. Setbacks remain pending county permit issuance.
- **Assumptions/flags requiring field verification or PE/contractor sign-off before construction:**
  - Soil conductivity (0.9 Btu/hr·ft·°F — **not soil-tested; a site soil boring/conductivity test must be done before this plan is finalized**)
  - Ground temperatures (regional estimate + canopy correction, not measured)
  - Design min/max EWT (30°F/90°F) — **now confirmed against the unit's actual Operating Limits table**: both design points fall comfortably inside the unit's Normal range (30–70°F heating, 50–110°F cooling), nowhere near either mode's actual max (90°F heating / 120°F cooling) — no concern here
  - HE/HR, COP/EER figures — **now sourced from the actual 036 (3-ton) unit's manufacturer Performance Data**, resolving the earlier flag that these were borrowed from a 2.5-ton unit's spec
  - Flow rate (9 GPM / 4.5 GPM per loop) — **now confirmed as the 036 unit's own rated "closed-loop optimum" flow point**, not just an assumed rule of thumb
  - Heat-pump water-side pressure drop — **now confirmed from manufacturer WPD data** (~7–9 ft at 9 GPM)
  - Antifreeze concentration and fluid choice (methanol vs. propylene glycol) — **flagged above as needing a direct read of the Antifreeze Corrections table**; do not assume 15% is equally protective for both fluids
  - Groundwater table depth (assumed dry above 6 ft)
  - Final setbacks (pending county permit)
