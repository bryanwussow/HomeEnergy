# Design Prompt: Horizontal Trenched Ground Loop Heat Exchanger (Teardrop Configuration)

Use this prompt as-is with an AI design assistant, or trim the instructional framing and hand the "Project Parameters" and "Fixed Design Constraints" sections to a geothermal contractor or PE as a scope-of-work brief.

---

## Role

Act as a geothermal ground-source heat pump (GSHP) loop design engineer. Design a closed-loop horizontal ground heat exchanger for a residential system, following IGSHPA (International Ground Source Heat Pump Association) horizontal loop guidelines and standard closed-loop sizing practice.

## Project Parameters (fill in before use)

- Heat pump capacity: current planning figure for the equipment itself is 2.5-ton / 30,000 Btu/h nominal, WaterFurnace 5 Series ground-source heat pump (options W1/W2 in `hvac-summary.md`) — this matches the Manual J Main Floor load and the existing system's field-validated performance. **However, size the ground loop itself to 3-ton / 36,000 Btu/h capacity**, not the 2.5-ton equipment figure: half-ton units are becoming less available, a future replacement unit may be a 3-ton variable-speed model, and the user wants a built-in safety margin. Confirm exact model once selected.
- Building heating load / cooling load: Manual J (Main Floor only, the zone the heat pump serves) — **20,597 Btu/h heating, 17,243 Btu/h cooling** (14,582 sensible + 2,661 latent). This is well under the loop's 3-ton/36,000 Btu/h sizing target above, which is intentionally oversized for equipment-availability and safety-margin reasons rather than driven by the load calc itself.
- Location / climate zone: 6960 Old Ridge Road, Waxhaw, NC 28173 — IECC climate zone 3A (Mixed-Humid)
- Undisturbed ground temperature: not field-measured. At the 5 ft trench depth, temperature oscillates seasonally by about ±6°F to ±8°F around the mean — roughly **~52°F in late winter (heating design condition) to ~67°F in late summer (cooling design condition)** for typical unshaded NC Piedmont soil. **Site is forested**: undisturbed ground under forest canopy runs 2–4°F cooler in summer than unshaded turf/bare soil, so use a summer design high of **~63–65°F** (67°F minus 2–4°F) for this site rather than the unshaded figure; use the ~52°F winter low as-is (canopy shading mainly affects summer solar gain, not winter minimum). Mean annual ground temp ≈ 59–60°F.
  - Use the winter low (~52°F) for heating-mode loop-length sizing (minimum entering water temp case) and the canopy-adjusted summer high (~63–65°F) for cooling-mode sizing (maximum entering water temp case) per standard IGSHPA/Kavanaugh practice.
- Soil type and estimated thermal conductivity: not tested on-site. Union County / Waxhaw, NC Piedmont soils are predominantly clay/clay loam (red clay) — assume moist clay ≈ 0.9 Btu/(hr·ft·°F) as a conservative default for this preliminary design. **A site soil boring/conductivity test must be performed before this plan is finalized** — actual conductivity could shift the required loop length meaningfully.
- Groundwater table depth: unknown — assume no perched water above 6 ft unless a contractor's site visit finds otherwise. **[flag: ask user/contractor]**
- Available lot area for the loop field: see `Wussow Ground Loop Plot Plan.pdf` (Lot 57A). Loop field runs North / North-Northwest from the house, bounded by the Lot 58 property line (west, ~657 ft) and the Lot 57B property line (east, ~460 ft), up to the ~280 ft-wide north end of the lot. Overall usable area is roughly a triangle **450 ft × 450 ft × 250 ft, 55,000+ ft²**. Two loop trenches are planned side by side (Ground Loop 1 nearer the Lot 57B/east side, Ground Loop 2 nearer the Lot 58/west side), each able to run nearly 500 ft out and 500 ft back to the house (**up to 1,000 ft of pipe per loop, no joints**). Trench separation: the two legs of each loop (and the two loops from each other) can keep any desired separation for ~75% of the run, narrowing to a minimum ~6 ft separation where parallel runs approach the house.
- Setback constraints: formal setback requirements will be established when the county permit is obtained — **[flag: treat any specific distances below as site layout for reference only, not confirmed permit setbacks]**. Per the plot plan, existing/planned features to keep clear of: septic tank and drain field (with ~50 ft repair-area reserve) sit west of the house, between the house and the well (further west along the Lot 58 line); an easement for Lot 57B's septic system crosses the south/east side of the lot between the house and Old Ridge Road (~150–200 ft run); a future outbuilding is planned ~30 ft north of the septic/drainfield area. Both loop trenches route north/northeast of these features, away from the septic/well/easement area. No wells, utilities, or septic infrastructure are shown in the actual loop-field path (the north 2/3 of the lot), but final routing should be confirmed against the county-permitted setbacks once issued.
- Frost depth for the region: NC Piedmont typical frost depth is shallow, roughly 12–18 in.; the fixed 5 ft trench depth below (constraint #2) is well below this regardless

## Fixed Design Constraints (do not vary these)

Shared constraints — apply regardless of which manifold location or trench-layout option (below) is used:

1. **Trench depth:** 5 ft to the bottom of the trench, uniform depth along the entire run (below frost line, single depth — not a two-pipe stacked trench unless the trencher can achieve it in one pass).
2. **Pipe convergence at house:** Near the house entrance, where the loop(s) converge, the outgoing line(s) can run at 24 in. below the surface; the return line(s) run in a separate sleeve, offset 12 in. below the outgoing line(s) (i.e., ~36 in. depth), rather than side by side. A 2 in. rigid foam (e.g., XPS) layer can be placed between the outgoing and return lines in this section if it helps reduce thermal short-circuiting between them. Supply and return should still terminate close enough together at the house to be routed through a single sleeve/penetration to the manifold or heat pump.
3. **Two loops planned:** per `Wussow Ground Loop Plot Plan.pdf`, Ground Loop 1 and Ground Loop 2 run side by side (Loop 1 nearer the Lot 57B/east line, Loop 2 nearer the Lot 58/west line), each up to ~500 ft out and ~500 ft back (≤1,000 ft of pipe per loop, no joints). Evaluate both loops together as the full loop field.

Two alternative manifold locations are under consideration — design for both and compare (see Required Deliverables):

**Manifold Option 1 — Inside the walkout basement**
- Each loop's supply and return lines run underground as continuous, joint-free pipe from the trench field through the basement wall penetration; all manifold joints, valves, and connections are made inside the basement, where they're accessible and not exposed to ground moisture/soil loads. No pipe joints below grade.
- Simpler for the homeowner to execute: continuous pipe is run under-grade and through the wall with no field joints outside, the manifold is connected inside, and the whole system is pressure-tested from inside the basement in one step.
- Trade-off: more individual wall penetrations into the basement (one supply/return pair per loop — up to 4 penetrations for the 2 planned loops), but no fusion welding or pressure testing needed outside/below grade.

**Manifold Option 2 — Outside, in a below-grade vault**
- Each loop's supply and return lines terminate at fusion-welded joints inside an exterior below-grade vault near the house; a single (or reduced-count) supply/return pair then penetrates the basement wall to reach the manifold/heat pump inside.
- Requires fusion welding of joints in the vault (additional field-fabricated joints, below grade) and a separate pressure test of the vault connections, on top of the loop's own pressure test.
- Trade-off: reduces the number of wall penetrations into the basement (down to one supply/return pair regardless of how many loops feed the vault), at the cost of added below-grade fusion joints, vault construction, and vault access/maintenance considerations.

Two alternative trench-layout options are under consideration for **each loop's supply/return legs** — design for both and compare (see Required Deliverables):

**Option A — Single narrow trench, pipes close together throughout**
- Excavation: single-pass chain trencher only (no backhoe/excavator trenches); narrow trench (~6–8 in. wide) limited to the trencher's cutting width.
- Circuit shape: a single continuous "teardrop" loop per trench — supply and return travel out from the house side by side (or stacked/offset within the narrow trench), diverge slightly to a rounded turn-around point at the far end, and converge again so both ends terminate close together at the house end of the trench. One entry point and one exit point at the house, minimizing trench penetrations into the foundation/mechanical room.
- Pipe spacing within the trench: minimum separation between the two pipe legs along the parallel run per IGSHPA/manufacturer minimums, typically ≥ 12 in. horizontal or an in-trench spacer arrangement, to avoid short-circuiting between supply and return.
- Trade-off: one trenching pass per loop (less excavation), but supply/return run close together the whole way, which raises thermal short-circuiting risk between the two legs.

**Option B — Wide separation for most of the run, separate trenches**
- Excavation: outgoing and return legs of each loop may run as separate trenches (two trenching passes per loop instead of one).
- Circuit shape: outgoing and return legs can maintain any desired separation for ~75% of the loop's length, narrowing to a minimum ~6 ft separation where the legs run parallel approaching the house, then converging to the tight cluster at the house per constraint #2 above.
- Pipe spacing: ≥ 6 ft between legs in the parallel near-house section; wide/site-driven separation is fine for the rest of the run since the legs are in independent trenches.
- Trade-off: more excavation (two passes per loop), but wider separation between supply and return legs for most of the run should reduce thermal short-circuiting and may improve loop efficiency versus Option A.

## Required Deliverables

Ask the design tool (or contractor) to produce:

1. **Pipe sizing** — nominal HDPE pipe diameter (SDR-11) and material spec for the loop.
2. **Required loop length** — total lineal feet of pipe (both legs combined, across both Ground Loop 1 and Ground Loop 2) needed for the stated capacity, soil conductivity, and ground temperature, using standard bore/trench length formulas (e.g., IGSHPA or Kavanaugh method), shown with the calculation and assumptions stated explicitly.
3. **Trench length and layout — Option A vs Option B** — resulting trench length(s) to achieve the required pipe length under each layout option, plus a simple plan-view sketch or description for each (trench path from house, teardrop turn radius or wide-separation routing, pipe convergence point), fitted to the two-loop plot plan.
4. **Option A vs Option B comparison** — compare excavation effort (trenching passes, linear ft of trenching), estimated thermal short-circuiting impact on loop performance, and any cost or installation-time difference; state a recommendation for this site given the forested lot and available separation room.
5. **Header/manifold design — Manifold Option 1 vs Option 2** — how the converged pipe ends from both loops connect to the supply/return manifold under each option: for Option 1 (inside the basement), the wall-penetration detail (sleeve, sealing/waterproofing at the foundation wall, pipe protection through the penetration) for up to 4 penetrations; for Option 2 (below-grade vault), the vault construction, fusion joint layout, and the single reduced-count wall penetration from vault to basement. Cover fusion vs. mechanical fittings, purge/fill valves, and flow-balancing considerations across the two loops under each option, and include whether the 24 in./36 in. vertical offset and optional 2 in. foam layer near the house (constraint #2) is worth using, and how the outgoing/return lines transition from that offset arrangement into each option's manifold point. Compare wall-penetration count, joint count/location, and pressure-testing steps between the two options, and state a recommendation for this site.
6. **Flow and circulation check** — verify flow rate, pressure drop, and pumping power for the calculated loop length(s) are within acceptable range for the heat pump's rated flow.
7. **Fluid selection** — antifreeze type and concentration appropriate for the minimum entering water temperature expected at 5 ft depth in this climate.
8. **Installation notes** — bedding/backfill requirements, pipe protection at the house penetration, pressure testing procedure before backfill, and any code/permit references (local plumbing/mechanical code, IGSHPA installation standard).
9. **Assumptions and flags** — a clear list of every assumption made (soil conductivity, ground temp, load) and anything that should be field-verified or reviewed by a licensed geothermal contractor/PE before construction.

## Output Format

Present the response as: (1) a short summary of key results (loop length, trench length, pipe size), (2) the calculations/assumptions behind them, (3) the layout description, and (4) the installation/deliverable notes — in that order.
