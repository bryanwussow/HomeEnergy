# Calculations Explained

Plain-language walkthroughs of the less-obvious calculations used elsewhere in this project. Each entry links back to the document where the calculation is actually used — this file exists to explain the *why*, not to be the source of truth for the numbers themselves.

---

## Heat pump capacity vs. ground heat extraction/rejection

**Used in:** `geothermal loop design - preliminary.md`, Section 2, Step 1.

The heat pump doesn't create the 36,000 Btu/h it delivers to the house — it *moves* most of it, and generates a smaller amount from compressor work. The ground loop only has to handle the moved portion, not the full nameplate capacity. That's why you can't just divide nameplate capacity by a heat-exchange rate to size the loop — you first have to back out the compressor's contribution.

**Heating mode:** The heat pump extracts heat from the ground and delivers it to the house, using compressor work (electricity) to do the "lifting" (raise the temperature to something useful indoors). By definition:

> COP = (heat delivered to house) / (compressor electrical work)

So:
- compressor work = Capacity / COP = 36,000 / 4.3 = 8,372 Btu/h
- heat extracted from ground = Capacity − compressor work = 36,000 − 8,372 = **27,628 Btu/h**

That's the same as the shortcut formula used in the design doc: Capacity × (COP−1)/COP, since (COP−1)/COP = 1 − 1/COP.

**Cooling mode:** It's the mirror image. The heat pump pulls heat *out* of the house (that's the cooling capacity) and has to dump it somewhere — into the ground loop. But the compressor work also ends up as heat that gets rejected into the loop too (compressor work turns into heat, same as running a motor). So the ground loop has to reject **more** than the nameplate cooling capacity, not less:

- compressor work = Capacity / COP = 36,000 / 8.41 = 4,281 Btu/h
- heat rejected to ground = Capacity + compressor work = 36,000 + 4,281 = **40,281 Btu/h**

Same shortcut: Capacity × (COP+1)/COP.

**Why this matters for loop sizing:** it's the reason cooling governs the loop length (40,281 Btu/h to reject) rather than heating (only 27,627 Btu/h to extract), even though the nameplate capacity is identical in both modes — cooling mode has to shed *more* heat into the ground than heating mode has to pull *out* of it, for the same box.

---

## Heat exchange rate per foot of buried pipe (shape-factor method)

**Used in:** `geothermal loop design - preliminary.md`, Section 2, Step 2.

Step 1 gives the total load the ground has to absorb or reject (Btu/h). To turn that into a required pipe length, you need to know: *for a given temperature difference between the ground and the fluid in the pipe, how many Btu/h can one foot of buried pipe actually move?* That rate, `q'` (Btu/(h·ft)), is what Step 2 calculates.

**Why it's not simple radial conduction:** for a pipe buried deep in an infinite mass of soil, there's no clean finite answer — heat just keeps spreading outward forever, so the resistance to infinity is technically infinite. What makes this solvable is that the pipe isn't in an infinite medium — it sits a finite distance below the ground surface, which acts as the effective reference temperature (the "undisturbed ground temperature" in Project Parameters is measured at that depth). That finite path gives a well-defined thermal resistance. Engineers handle this with a **conduction shape factor** — a purely geometric number (depends only on burial depth `z` and pipe diameter `d`, not on soil type) that captures how that finite path length affects heat flow. This exact shape factor — a cylinder buried below an isothermal plane — is a standard result from heat-transfer textbooks.

**The formula**, `q' = k × S'`, where `S' = 2π / cosh⁻¹(2z/d)`, works like Ohm's law for heat: heat flow = a "conductance" (`k × S'`) times the driving temperature difference (`ΔT`). `k` carries the soil's material property (conductivity); `S'` carries pure geometry, and is itself dimensionless — both `2π` and `cosh⁻¹` of a ratio are unitless.

**Plugging in the numbers:**
- `k = 0.9` Btu/(hr·ft·°F) — the moist-clay soil assumption
- `d = 1.315 in = 0.1096 ft` — the pipe's *outer* diameter (1" nominal SDR-11 HDPE) — this is the surface heat actually crosses
- `z = 5 ft` — burial depth, straight from the trench-depth constraint
- `2z/d = 10 / 0.1096 = 91.3` — the pipe is tiny compared to how deep it's buried
- `cosh⁻¹(91.3) ≈ 5.21` — this grows only *logarithmically*, so even though the depth-to-diameter ratio is ~91×, the resulting factor is a modest ~5.2, not something astronomically large
- `S' = 2π / 5.21 = 1.21` (dimensionless — pure geometry, no units)
- `q' = 0.9 × 1.21 = 1.09 × ΔT` Btu/(h·ft)

**What that final number means:** for every 1°F of temperature difference between the ground and the fluid inside the pipe, one foot of pipe can move about 1.09 Btu/h. Step 3 plugs in the actual design ΔTs (22°F heating, 26°F cooling) to get the real Btu/(h·ft) rates, which Step 1's loads get divided by to arrive at the required pipe length.

**Two caveats worth keeping in mind:**
1. This treats the pipe as *isolated* — no interference from its neighboring leg. That's the same limitation behind the doc's Option A (close-spaced trench) needing a 15–25% length penalty versus Option B (wide separation).
2. It's a steady-state snapshot at one design ΔT, not a full seasonal/transient model — a real IGSHPA/Kavanaugh design would also account for how the ground recovers heat over the year. Consistent with this being a preliminary estimate, not a final design.

---

## Design ΔT, and why a single-snapshot design is normal for horizontal loops

**Used in:** `geothermal loop design - preliminary.md`, Section 2, Step 3.

Step 3 just supplies the actual driving temperature differences and finishes the arithmetic Steps 1–2 set up: it pairs each mode's ground temperature (from Project Parameters) with a design entering-water-temperature (EWT) target, gets a ΔT (22°F heating, 26°F cooling), runs each through Step 2's `q'` formula, and divides Step 1's load by the result to get a required length. Cooling needs more pipe (1,424 ft vs. 1,156 ft), so it governs the design.

**EWT vs. LWT — two different points in the same loop.** "EWT" (entering water temperature) is the temperature of fluid *returning from the ground loop to the heat pump* — i.e., after it has already picked up heat from the ground (heating mode) or shed heat to the ground (cooling mode). "LWT" (leaving water temperature) is the fluid *leaving the heat pump and entering the ground loop* — the opposite end of the same circuit. Step 3 only uses EWT, because that's the number the heat pump manufacturer actually specifies operating limits around (and it's also, conveniently, the more conservative point to design to — see below). LWT can still be estimated for context: the design flow rate (~3 GPM/ton) is specifically chosen to keep the heat pump's own water-side temperature change in a serviceable ~8–10°F range, so LWT runs about that much colder than EWT in heating mode (~30°F EWT → ~20–22°F LWT) and that much warmer in cooling mode (~90°F EWT → ~98–100°F LWT). LWT isn't needed to size the loop length, but it matters for antifreeze selection — it's the coldest point in the whole system, not EWT.

**Is it customary to design off one steady-state ΔT rather than a full annual/transient model?** Yes, for horizontal loops specifically. The more rigorous Kavanaugh method — monthly loads, g-functions, multi-year ground temperature drift — is standard for **vertical bore fields**, where drilling is expensive enough that getting the length precisely right matters, and bores sit deep enough that the ground's annual cycling behaves differently. For horizontal loops, standard industry practice (what residential geothermal contractors actually use) is to design to the *seasonal extremes* — worst-case winter low and worst-case summer high ground temperature — rather than simulate the whole year. That's not skipping the seasonal effect; it's how the seasonal effect gets handled in this class of design: size for the worst point of the cycle instead of modeling the whole cycle. A full annual model earns its cost on large or vertical systems; here, with abundant land and a design that already carries meaningful margin over the calculated minimum, it isn't necessary.

**Does the loop "run out of capacity" partway along its length?** Yes — this is a real effect the calculation doesn't explicitly model, and it's the same phenomenon as the approach temperature in ordinary heat-exchanger design. As fluid travels through the trench, its temperature keeps closing in on the ground temperature, so the local driving ΔT keeps shrinking along the flow path — the far end of the loop genuinely does less work per foot than the near end. Step 3 applies one ΔT uniformly across the whole length instead of modeling that decay.

The saving grace: the ΔT used (based on design EWT) happens to be the *smallest* ΔT anywhere on the loop, not the largest. EWT is measured where fluid re-enters the heat pump — after it has already picked up the most heat it's going to get from the ground (heating) or shed the most heat it's going to lose (cooling). Everywhere else along the trench the fluid is farther from ground temperature, so the true local ΔT is larger there. Applying the smallest (EWT-based) ΔT everywhere means assuming the whole loop performs as poorly as its worst point — that overstates the required length rather than understating it.

Roughly quantifying how much: for a single-stream heat exchanger against a reservoir held at a fixed temperature (a good model here, since the ground's thermal mass vastly exceeds the fluid's), the fluid temperature decays exponentially toward the reservoir temperature along the flow path, with a characteristic "decay length" of `(mass flow × fluid specific heat) ÷ (per-foot conductance from Step 2)`. At ~4.5 GPM per loop with a ~20% glycol solution (cp ≈ 0.93 Btu/lb·°F), that works out to roughly 2,000 ft — compared to the ~900 ft loop itself. So the fluid only closes about 35–40% of the gap to ground temperature over the full loop length: a real but moderate effect, not an extreme one. It's a legitimate reason the recommended design (1,800 ft) sits above the raw calculated minimum (1,430 ft), alongside the pipe-interference margin from the previous section.
