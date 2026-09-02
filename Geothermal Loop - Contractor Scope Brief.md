# Geothermal Ground Loop — Scope Brief for Contractor Review

**Date:** 2026-08-28
**Property:** 6960 Old Ridge Road, Waxhaw, NC 28173
**Purpose of this document:** background and site parameters for evaluating the homeowner-installed ground loop plan below. See the companion documents for the full design results and site drawing:
- `geothermal loop design - preliminary.md` — full calculations, recommended pipe length/size/flow, and installation notes
- `Wussow Ground Loop Plot Plan.pdf` — site drawing (lot boundaries, loop routing, septic/well/easement locations)

---

## Proposed Scope Split

**Homeowner proposes to install:** the ground loop itself — both trenches (per the wide-separation layout below), the HDPE pipe runs, near-house pipe routing and depth transition, and backfill. Trenching would use a rented trenching tractor capable of a consistent 5 ft depth and 6–12 in. width, for the majority of the ground loop.

**Proposed for contractor to provide:** finalizing the ground loop's connection to the manifold and heat pump, final system pressure testing/purge/fill, fluid charging, and installation of the heat pump unit itself. **Open item for contractor input:** whether the manifold should be built inside the basement or in an exterior below-grade vault (see "Manifold Location" below) — this affects how much of the connection work is field-fusion welding versus mechanical fittings made indoors.

---

## Site & Design Parameters

- **Heat pump capacity:** planning figure is a 2.5-ton / 30,000 Btu/h WaterFurnace 5 Series ground-source heat pump, matching the home's Manual J Main Floor load (20,597 Btu/h heating / 17,243 Btu/h cooling) and the existing system's field-validated performance. **The ground loop itself is sized to 3-ton / 36,000 Btu/h** — larger than the equipment figure — for equipment-availability (half-ton units becoming less common) and safety-margin reasons, and to accommodate a possible future 3-ton variable-speed replacement. Exact model to be confirmed.
- **Climate zone:** IECC 3A (Mixed-Humid).
- **Undisturbed ground temperature:** not field-measured. At 5 ft depth, seasonal swing is roughly 52°F (late winter) to 67°F (late summer) for typical unshaded NC Piedmont soil. The site is forested, which runs ground temperature 2–4°F cooler in summer than unshaded soil — design uses a summer high of ~63–65°F and the unadjusted 52°F winter low.
- **Soil:** not tested on-site. Assumed moist clay, conductivity ≈ 0.9 Btu/(hr·ft·°F), typical for Union County/Waxhaw Piedmont soils. **A soil boring/conductivity test should be performed before finalizing** — actual conductivity could shift the required loop length.
- **Groundwater table depth:** unknown — assumed no perched water above 6 ft pending a site visit.
- **Available lot area:** see plot plan. Loop field runs north/north-northwest from the house across Lot 57A, roughly a 450 ft × 450 ft × 250 ft triangle (55,000+ ft²). Two loops are planned side by side, each able to run up to ~500 ft out and ~500 ft back (≤1,000 ft of pipe per loop, no joints).
- **Setbacks:** not yet finalized — pending the county permit. Per the plot plan, both loop trenches route north/northeast, clear of the septic tank/drain field, well, and the Lot 57B septic easement, all of which sit west/south of the house. Final routing should be confirmed against permitted setbacks once issued.
- **Frost depth:** shallow in this region (~12–18 in.); the 5 ft trench depth is well below it regardless.

## Design Details

1. **Trench depth:** 5 ft to the bottom of the trench, uniform along the entire run (not a two-pipe stacked trench).
2. **Pipe convergence near the house:** outgoing line(s) at 24 in. depth, through their own wall penetration; return line(s) in a separate sleeve, offset 12 in. below (~36 in. depth), through their own separate, nearby wall penetration — keeping the vertical offset through the wall itself (not merging into a single shared opening) to avoid thermal short-circuiting, optionally aided by 2 in. rigid foam between them. The two penetrations are close enough together vertically for a single work area inside to access and manifold both lines.
3. **Two loops planned:** Ground Loop 1 (east, near the Lot 57B line) and Ground Loop 2 (west, near the Lot 58 line), each up to ~500 ft out and ~500 ft back (≤1,000 ft of pipe per loop, no joints).

### Trench Layout — Option B preferred (wide separation)

Each loop's supply and return legs run as separate trenches, held apart at any convenient distance for ~75% of the run, narrowing to ≥6 ft separation for the final stretch approaching the house — roughly 1,800 ft of total trenching across both loops. This is the homeowner's preferred approach over a single narrow shared trench: better thermal performance (avoids short-circuiting between the two legs), faster to place and pressure-test since the trenches don't have to be worked one at a time in a shared cut, and the trenching machine needed for the extra passes is already available. Open to the contractor's feedback if there's a reason to reconsider.

### Manifold Location — open, requesting contractor input

Two options are on the table:
- **Option 1 — inside the walkout basement:** continuous, joint-free pipe runs from the trench field through the basement wall as-is; all joints, valves, and the manifold are made up inside. Simpler to execute and pressure-test from inside, but requires more wall penetrations (up to 4, for the 2 loops).
- **Option 2 — outside, in a below-grade vault:** each loop's lines terminate at fusion-welded joints in an exterior vault near the house, with a single reduced-count pair penetrating the basement wall to the manifold/heat pump inside. Fewer wall penetrations, but requires field fusion welding and a separate vault pressure test, plus the vault itself.

The homeowner has no strong preference yet — this is a good item for the contractor's judgment based on basement wall accessibility and vault excavation feasibility.

## Recommended Design (from `geothermal loop design - preliminary.md`)

| Item | Value |
|---|---|
| Total pipe length | ~1,800 ft (900 ft per loop) |
| Pipe | 1" nominal SDR-11 HDPE |
| Design flow | ~9 GPM total, ~4.5 GPM per loop |
| Estimated system head | ~30–40 ft (flag: confirm against actual WaterFurnace 5-Series submittal data) |
| Fluid | ~20% propylene glycol (default), or methanol if the contractor is equipped to handle it |

**This is a preliminary, homeowner-generated estimate** — see that document's "Assumptions and Flags" section for everything still pending confirmation (soil test, design entering-water-temperature limits, flow rate, groundwater, and final permitted setbacks) before the homeowner proceeds with trenching.
