# Design Prompt: Horizontal Trenched Ground Loop Heat Exchanger (Teardrop Configuration)

Use this prompt as-is with an AI design assistant, or trim the instructional framing and hand the "Project Parameters" and "Fixed Design Constraints" sections to a geothermal contractor or PE as a scope-of-work brief.

---

## Role

Act as a geothermal ground-source heat pump (GSHP) loop design engineer. Design a closed-loop horizontal ground heat exchanger for a residential system, following IGSHPA (International Ground Source Heat Pump Association) horizontal loop guidelines and standard closed-loop sizing practice.

## Project Parameters (fill in before use)

- Heat pump capacity: current planning figure for the equipment itself is 2.5-ton / 30,000 Btu/h nominal, WaterFurnace 5 Series ground-source heat pump (options W1/W2 in `hvac-summary.md`) — this matches the Manual J Main Floor load and the existing system's field-validated performance. **However, size the ground loop itself to 3-ton / 36,000 Btu/h capacity**, not the 2.5-ton equipment figure: half-ton units are becoming less available, a future replacement unit may be a 3-ton variable-speed model, and the user wants a built-in safety margin. Confirm exact model once selected.
- Building heating load / cooling load: Manual J (Main Floor only, the zone the heat pump serves) — **20,597 Btu/h heating, 17,243 Btu/h cooling** (14,582 sensible + 2,661 latent). This is well under the loop's 3-ton/36,000 Btu/h sizing target above, which is intentionally oversized for equipment-availability and safety-margin reasons rather than driven by the load calc itself.
- Location / climate zone: 6960 Old Ridge Road, Waxhaw, NC 28173 — IECC climate zone 3A (Mixed-Humid)
- Undisturbed ground temperature: not field-measured; typical for the NC Piedmont is ~58–60°F. **[flag: confirm with a local geothermal contractor or NC ground-temp reference before finalizing]**
- Soil type and estimated thermal conductivity: not tested on-site. Union County / Waxhaw, NC Piedmont soils are predominantly clay/clay loam (red clay) — assume moist clay ≈ 0.9 Btu/(hr·ft·°F) as a conservative default. **[flag: a site soil boring/conductivity test would tighten this]**
- Groundwater table depth: unknown — assume no perched water above 6 ft unless a contractor's site visit finds otherwise. **[flag: ask user/contractor]**
- Available lot area for the loop field: unknown — **[ask user: dimensions or sketch of usable yard area, distance/direction from the house/mechanical room]**
- Setback constraints: unknown — **[ask user: property lines, septic field/drain lines, well, existing utilities, trees/root zones near 6960 Old Ridge Road]**
- Frost depth for the region: NC Piedmont typical frost depth is shallow, roughly 12–18 in.; the fixed 5 ft trench depth below (constraint #2) is well below this regardless

## Fixed Design Constraints (do not vary these)

1. **Excavation method:** Single-pass chain trencher only (no backhoe/excavator trenches). Trench width is limited to the trencher's cutting width — assume a narrow trench (~6–8 in. wide) unless told otherwise.
2. **Trench depth:** 5 ft to the bottom of the trench, uniform depth along the entire run (below frost line, single depth — not a two-pipe stacked trench unless the trencher can achieve it in one pass).
3. **Circuit shape:** A single continuous "teardrop" loop per trench — the two pipe runs (supply and return) travel out from the house side by side (or one stacked/offset within the narrow trench), diverge slightly to a rounded turn-around point at the far end of the loop field, and converge again so both pipe ends terminate close together at the house end of the trench. The goal is one entry point and one exit point at the house, minimizing the number of trench penetrations into the foundation/mechanical room.
4. **Pipe convergence at house:** Supply and return pipe ends must exit the trench within a tight cluster (specify max separation, e.g., ≤ 12 in.) so they can be routed together through a single sleeve/penetration to the manifold or heat pump.
5. **Pipe spacing within the trench:** Specify minimum separation between the two pipe legs along the parallel run (per IGSHPA / manufacturer minimums, typically ≥ 12 in. horizontal or in-trench spacer arrangement) to avoid short-circuiting between supply and return.

## Required Deliverables

Ask the design tool (or contractor) to produce:

1. **Pipe sizing** — nominal HDPE pipe diameter (SDR-11) and material spec for the loop.
2. **Required loop length** — total lineal feet of pipe (both legs combined) needed for the stated capacity, soil conductivity, and ground temperature, using standard bore/trench length formulas (e.g., IGSHPA or Kavanaugh method), shown with the calculation and assumptions stated explicitly.
3. **Trench length and layout** — resulting single-trench length to achieve that pipe length in the teardrop configuration, plus a simple plan-view sketch or description (trench path from house, teardrop turn radius, pipe convergence point).
4. **Header/manifold design** — how the converged pipe ends connect to the supply/return manifold at the house, including fusion vs. mechanical fittings, purge/fill valves, and flow-balancing considerations for a single-circuit loop.
5. **Flow and circulation check** — verify flow rate, pressure drop, and pumping power for the calculated loop length are within acceptable range for the heat pump's rated flow.
6. **Fluid selection** — antifreeze type and concentration appropriate for the minimum entering water temperature expected at 5 ft depth in this climate.
7. **Installation notes** — bedding/backfill requirements, pipe protection at the house penetration, pressure testing procedure before backfill, and any code/permit references (local plumbing/mechanical code, IGSHPA installation standard).
8. **Assumptions and flags** — a clear list of every assumption made (soil conductivity, ground temp, load) and anything that should be field-verified or reviewed by a licensed geothermal contractor/PE before construction.

## Output Format

Present the response as: (1) a short summary of key results (loop length, trench length, pipe size), (2) the calculations/assumptions behind them, (3) the layout description, and (4) the installation/deliverable notes — in that order.
