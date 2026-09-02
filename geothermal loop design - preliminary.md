# Geothermal Ground Loop Design — Preliminary

**Date:** 2026-08-28
**Basis:** `geothermal-loop-design-prompt.md` (Project Parameters + Fixed Design Constraints), run against figures in `hvac-summary.md` (as of 2026-08-27) and `Wussow Ground Loop Plot Plan.pdf`.
**Status:** Preliminary planning estimate only — not a final design. See "Assumptions and Flags" below for everything that needs field verification, soil testing, or contractor/PE sign-off before construction.

---

## 1. Summary of Key Results

| Item | Result |
|---|---|
| **Governing load** | Cooling (heat rejection), not heating |
| **Total pipe length required (calculated minimum)** | ~1,430 ft (both loops combined) |
| **Recommended design length** | **~1,800 ft total — 900 ft per loop** (450 ft out + 450 ft back), leaving ~100 ft/loop reserve within the plot plan's 1,000 ft/loop max |
| **Pipe** | 1" nominal SDR-11 HDPE |
| **Design flow** | ~9 GPM total system flow, ~4.5 GPM per loop |
| **Estimated loop head loss** | ~12–14 ft per loop circuit + ~15–20 ft heat pump water-side drop ≈ **30–40 ft total system head** (flag: confirm against WaterFurnace 5-Series submittal data) |
| **Fluid** | ~20% propylene glycol (default), or methanol if the contractor is equipped to handle it |

Both Option A (single narrow trench) and Option B (wide separation) fit comfortably in the available loop field either way. **Option B is the leading choice** — better thermal performance, faster pipe placement/pressure testing, and the trenching machine for the extra passes is already available — at the cost of roughly double Option A's excavation, which isn't a binding constraint on this site.

## 2. Calculations and Assumptions

**Step 1 — Convert 3-ton/36,000 Btu/h nameplate capacity into ground heat extraction/rejection loads**, using WaterFurnace 5-Series efficiency figures from `hvac-summary.md` (COP 4.3 heating / EER 28.7 ≈ COP 8.41 cooling — **flagged: these are the 2.5-ton unit's published figures, applied here to a 3-ton target; confirm against the actual 3-ton model's submittal data once selected**):

- Heating (heat *extracted* from ground) = Capacity × (COP−1)/COP = 36,000 × (4.3−1)/4.3 = 36,000 × 0.767 = **27,627 Btu/h**
- Cooling (heat *rejected* to ground) = Capacity × (COP+1)/COP = 36,000 × (8.41+1)/8.41 = 36,000 × 1.119 = **40,281 Btu/h**

**Step 2 — Heat exchange rate per foot of pipe**, using the steady-state buried-cylinder shape-factor method (Kavanaugh-style simplification for a single isolated horizontal pipe):

q' = k × S' × ΔT, where S' = 2π / cosh⁻¹(2z/d)

- k (soil conductivity) = 0.9 Btu/(hr·ft·°F) — moist clay, per Project Parameters (**not soil-tested; a site soil boring/conductivity test must be done before this plan is finalized**)
- Pipe: 1" nominal SDR-11 HDPE, OD d = 1.315 in = 0.1096 ft
- Depth z = 5 ft (trench depth, per constraint #1)
- 2z/d = 10/0.1096 = 91.3 → cosh⁻¹(91.3) ≈ 5.21 → S' = 2π/5.21 = **1.21 (dimensionless)**
- q' = 0.9 × 1.21 × ΔT = **1.09 × ΔT** Btu/(h·ft)

**Step 3 — Design ΔT (ground temp vs. design fluid temp)**, using the ground temps from Project Parameters and assumed design entering-water-temperatures (EWT — the temperature of fluid *returning from the ground loop to the heat pump*, after it has already picked up or shed heat in the trench) typical for a mild-climate horizontal loop with antifreeze (**flagged: confirm min/max EWT against the actual WaterFurnace 5-Series spec sheet**):

- Heating: ground low 52°F, design min EWT ≈ 30°F → ΔT = 22°F → q' = 1.09 × 22 = 23.9 Btu/(h·ft) → **L = 27,627 / 23.9 ≈ 1,156 ft**
- Cooling: ground high (canopy-adjusted) 64°F, design max EWT ≈ 90°F → ΔT = 26°F → q' = 1.09 × 26 = 28.3 Btu/(h·ft) → **L = 40,281 / 28.3 ≈ 1,424 ft** ← **governs**

For reference (not used in the length calculation above): the fluid *leaving* the heat pump and entering the ground loop — the LWT — would run roughly 8–10°F colder than EWT in heating mode and 8–10°F warmer than EWT in cooling mode, since the design flow rate (~3 GPM/ton) is specifically chosen to keep the heat pump's water-side temperature change in that range. That puts estimated LWT at **~20–22°F heating** and **~98–100°F cooling** — i.e., the coldest/hottest point the fluid actually reaches, right as it enters the trench, before warming/cooling back toward EWT over the length of the loop. This is a separate, rougher assumption than the EWT figures above (which should still be confirmed against manufacturer data) — it isn't needed to size the loop length, but it's useful context for antifreeze selection and for sanity-checking the loop-saturation discussion below.

**Cross-check against industry rule-of-thumb table** (ft of pipe per ton, horizontal 2-pipe, moist clay, mixed-humid climate): typical range 400–670 ft/ton × 3 tons = **1,200–2,000 ft**. The shape-factor result (1,424 ft) sits within this range, closer to the lower/mid end — consistent, gives confidence in the estimate.

**Important limitation:** this calculation treats each pipe leg as an *isolated* pipe with no thermal interaction from its neighboring leg. That's a reasonable approximation for **Option B** (wide separation), but **Option A** (both legs close together in one narrow trench) will underperform this estimate due to mutual heat interference between supply and return — industry practice is to add roughly 15–25% extra length to compensate. That pushes Option A's effective target to **~1,650–1,800 ft**, while Option B could likely get by with something closer to the raw **~1,430–1,500 ft**.

**Second limitation — ΔT is treated as uniform along the pipe, when it actually shrinks along the flow path.** Step 3's ΔT (22°F heating, 26°F cooling) is based on design EWT — the point where fluid re-enters the heat pump, after it has already picked up the most heat it will get from the ground (heating) or shed the most heat it will lose (cooling). Everywhere else along the trench, the fluid is farther from ground temperature and the true local ΔT is larger. Applying the EWT-based ΔT uniformly assumes the whole loop performs at its worst (most "saturated") point — this is a conservative simplification (it overstates required length, not understates it), not an error, but it's still a simplification rather than a full log-mean-temperature-difference or exponential-decay analysis. Roughly quantifying: at ~4.5 GPM per loop with ~20% glycol (cp ≈ 0.93 Btu/lb·°F), the loop's thermal "decay length" (mass flow × cp ÷ Step 2's per-foot conductance) is roughly 2,000 ft versus the ~900 ft loop itself — so the fluid only closes ~35–40% of the gap to ground temperature over the full loop length. This is a real but moderate source of built-in conservatism, and part of why the recommended design sits above the raw calculated minimum, alongside the interference margin above.

**Recommended design point: 1,800 ft total (900 ft/loop)** — covers Option A's interference-derated requirement with margin, and gives Option B extra headroom, while staying within each loop's 1,000 ft plot-plan limit (leaving ~100 ft/loop, i.e. ~10%, in reserve for field contingency — soil conductivity or groundwater conditions worse than assumed).

## 3. Layout Description

- **Two loops** per `Wussow Ground Loop Plot Plan.pdf`: Ground Loop 1 (east, near Lot 57B line) and Ground Loop 2 (west, near Lot 58 line), each a teardrop running ~450 ft north/north-northwest from the house and back (900 ft round trip), well within the ~500 ft one-way / 1,000 ft round-trip room the plot plan allows.
- **Option A layout:** each loop is a single ~450 ft trench; supply and return pipes travel together the whole way, diverge slightly at a rounded turnaround ~450 ft out, converge again at the house. Trenching required: ~450 ft per loop, **~900 ft total trenching** for both loops.
- **Option B layout:** each loop's supply and return legs run as separate trenches, held apart (any distance) for ~75% of the run, narrowing to ≥6 ft separation for the final stretch approaching the house. Trenching required: ~450 ft per leg × 2 legs × 2 loops = **~1,800 ft total trenching** (double Option A's excavation for the same pipe footage).
- **Option B is the leading choice for the homeowner:** better thermal performance (avoids Option A's close-spaced short-circuiting derate — see Section 2's "Important limitation"), pipe can be placed and pressure-tested faster since separate trenches can be worked without waiting on a shared narrow cut, and the trenching machine needed for the extra passes is already available. The added excavation (double Option A's linear footage) is the trade-off, but land isn't the constraint here.
- **Near the house:** both loops converge; outgoing lines run at 24 in. depth and cross the foundation wall through their own penetration, return lines in a separate sleeve 12 in. below (≈36 in. depth) through their own separate, nearby penetration — keeping the vertical offset through the wall itself (not merging into one opening) to avoid thermal short-circuiting, optionally aided by 2 in. rigid foam between them. The two penetrations are close enough together vertically for a single work area inside to access both, before reaching whichever manifold location is chosen below.
- **Manifold — two options under consideration:**
  - **Option 1 (inside the basement):** continuous, joint-free pipe runs from the trench field through the basement wall as-is, with all fusion joints, valves, and the manifold made up inside the basement. Simpler to execute (one pressure test, from inside, after the wall penetrations); costs more wall penetrations — up to 4 for the 2 planned loops.
  - **Option 2 (outside, below-grade vault):** each loop's supply/return lines terminate at fusion-welded joints in an exterior below-grade vault near the house, with a single reduced-count pair then penetrating the basement wall to the manifold/heat pump inside. Fewer wall penetrations, at the cost of field fusion welding and a separate vault pressure test, plus the vault itself.
  - No recommendation yet between the two — see Section 4.

## 4. Installation / Deliverable Notes

- **Flow & circulation:** ~9 GPM total (3 GPM/ton design standard), split ~4.5 GPM per loop across the two parallel loops. At 4.5 GPM in 1" SDR-11 pipe (ID ≈1.077 in), velocity ≈1.6 ft/s — acceptable for HDPE, though on the low side for peak convective heat transfer; trades off against much lower head loss than 3/4" pipe (~12–14 ft/900 ft loop vs. ~43 ft/900 ft loop for 3/4" pipe) over these long runs. **Flag: confirm required flow rate and heat-pump water-side pressure drop against the actual WaterFurnace 5-Series submittal data** once a specific model is chosen — this drives total pump head and circulator sizing (likely 1/2–3/4 HP class, TBD).
- **Fluid:** ~20% propylene glycol (simpler default, avoids methanol's flammability/handling concerns), or methanol if the heat pump contractor is equipped to handle it (lower viscosity, better heat-transfer performance at these temperatures). Either should give freeze protection below the coldest point in the system, the estimated ~20–22°F LWT entering the ground loop (colder than the 30°F design EWT — see Step 3). Confirm concentration and choice against manufacturer-approved fluid list.
- **Bedding/backfill:** clean fine backfill immediately around the pipe (trenchers don't place bedding automatically); native soil backfill above, compacted in lifts; keep sharp rock away from pipe wall.
- **Pressure testing:** standard IGSHPA practice — pressurize to ~100 psi, hold and monitor (e.g., 30 min–24 hr) with no pressure loss, before backfilling any section. Under Manifold Option 2 (vault), the vault's fusion joints need their own pressure test in addition to this.
- **Wall penetration:** sealed sleeve through the basement foundation wall (hydraulic cement or a purpose-made geothermal wall boot) to prevent water intrusion. Under Manifold Option 1 this means up to 4 penetrations (one supply/return pair per loop); under Option 2, a single reduced-count pair from the vault.
- **Manifold location — still open:** Option 1 (inside basement) is simpler for the homeowner to execute — continuous under-grade pipe through the wall, manifold connected and the whole system pressure-tested from inside in one step — but costs more wall penetrations. Option 2 (below-grade vault) reduces wall penetrations to one pair but requires fusion welding joints in the vault plus a separate vault pressure test. No recommendation made yet; flag for the contractor/PE to weigh in on, given site-specific factors like basement wall accessibility and vault excavation feasibility.
- **Permits/code:** confirm with Union County whether the loop excavation itself needs a permit (separate from the mechanical/HVAC permit for the heat pump); given proximity to the septic system and well shown on the plot plan, county health department review of trench routing may also apply. Setbacks remain pending county permit issuance.
- **Assumptions/flags requiring field verification or PE/contractor sign-off before construction:** soil conductivity (0.9 Btu/hr·ft·°F — **not soil-tested; a site soil boring/conductivity test must be done before this plan is finalized**), ground temperatures (regional estimate + canopy correction, not measured), design min/max EWT (30°F/90°F, assumed), COP/EER figures (borrowed from the 2.5-ton unit spec for this 3-ton target), flow rate (3 GPM/ton assumed), groundwater table depth (assumed dry above 6 ft), and final setbacks (pending county permit).
