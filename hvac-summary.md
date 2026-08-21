# HVAC Load, Equipment & Cost Summary

> Source of truth for home HVAC load calculations, equipment options, and cost estimates.
> Other conversations/projects (e.g., geothermal ground loop design) should read this file
> rather than relying on values repeated in chat history. Update this file whenever numbers
> change — don't just report the change in conversation.

**Last updated:** 2026-08-21
**Updated by / in conversation:** "read over the project information" session (populated from `Home_Energy_Use_Estimates.xlsx`, `Lifetime Costs.xlsx`, and the Assessment report; then reconciled against the Manual J PDF, real-world operating history, and user-supplied corrections to the Assessment report's tablet-generated Tech Specs); most recently the "Tech Specs corrections" session (2026-08-21), which corrected walls, attic, foundation/basement, and windows

---

## 1. Project Basics

- Address / location: 6960 Old Ridge Road, Waxhaw, NC 28173
- Climate zone: IECC climate zone 3A (Mixed-Humid) — confirmed by user. (Not stated in the Assessment report itself; matches published IECC maps for Waxhaw, NC / Union County.)
- Conditioned floor area: **1,550 ft²** — this is **Main Floor only** (corrected by user from the Assessment report's stated 1,500 ft²). The central heat pump system heats/cools the Main Floor only.
- "Floors above grade: 2" (per Assessment report) = the Main Floor (conditioned) + an attic bonus room above it that is **unfinished and unconditioned** — not a second full conditioned story. The basement is below grade (not counted in this "2"), partly finished, and receives only partial heat-pump cooling (via two intentionally-cracked basement ducts plus stairway airflow — see below) and no heat-pump heating (heated separately by wood stove only) — not a fully served zone. **Foundation type: Walkout Basement** (corrected by user), total footprint **1,550 ft²** — same outer perimeter as the Main Floor (corrected by user from the previously-listed 500 ft², which was simply wrong). Wall height: **8'8" + rim joist** (corrected by user from 9 ft average).
- Front of building orientation: **South** (corrected by user — the Assessment report/text-extract had stated NW, which was wrong).
- Shielding: **generous mature deciduous tree shade in spring, summer, and fall** (corrected by user — the Assessment report had stated "Normal" shielding). This is likely a meaningful contributor to real-world cooling load being lower than the Assessment's modeled cooling estimate (see Section 2).
- House age / construction type: Built 1999. Exterior walls: 2x4 frame, wood/fiber-cement siding, 1,717.02 ft² modeled area.
- Insulation levels:
  - Walls: R-13 cavity, R-3 continuous (corrected by user from Assessment report's R-11 cavity/R-0 continuous; "Wall 1," 1,717.02 ft², matches the modeled area already on file)
  - Attic: two zones per Assessment Tech Specs (corrected by user from the single blended R-18.9 / 7–9" depth / no-radiant-barrier figure):
    - Attic 1 (area with attic floor): 400 ft², batts, 9.25 in depth, R-30, no radiant barrier
    - Attic 2 (area with no floor): 1,150 ft², batts or blown, 16 in depth, R-38, radiant barrier: yes
    - Combined attic area 1,550 ft² (matches Main Floor conditioned area — the attic sits above the whole Main Floor)
  - Basement walls: three-part breakdown (corrected by user from the single blended R-4 continuous / fiberglass blanket figure):
    - ~45%: wood frame, above grade, R-13 cavity, R-5 continuous
    - ~40%: 12" masonry, below grade, no insulation
    - ~15%: 12" masonry, above grade, no insulation
  - Basement conditioning: **heating is intentional, via wood stove only** (not the central heat pump). **Cooling is also intentional but partial** — provided by two basement supply ducts deliberately cracked open, plus airflow down the stairway when the stairway door is open; **not** duct leakage (corrected by user — no duct losses involved). Still only a partial/secondary supply compared to the Main Floor's fully-ducted zone, which is why the basement isn't treated as a fully served zone for load-calc purposes.
  - Windows — Main Floor (corrected by user, replacing the Assessment's single-pane + storm / U-0.51 / SHGC-0.56 / NE-SE-SW-NW figures entirely): 3/4" insulated, Low-E, Argon fill, avg U-value 0.32, SHGC 0.33, no storm windows, Energy Star: yes. By compass direction: East 29 ft², North (back) 128 ft², West 55 ft², South (front) 77 ft² — total 289 ft². (Directions now given as true N/E/S/W, consistent with the corrected South-front orientation in the line above — this also resolves the previously-flagged need to re-check the old NE/SE/SW/NW breakdown.)
  - Windows — Basement (above grade): insulated, Low-E, Argon fill, avg U-value 0.45. Area not yet specified.
  - Air leakage: 3,490 CFM50 now (14.96 ACH50) → goal 2,617.5 CFM50 (11.22 ACH50); home not professionally air sealed
- Design temperatures used: Winter 26°F outdoor / 70°F indoor; Summer 91°F outdoor / 75°F indoor (per Assessment report)
- **Reliability note:** many of the Assessment report's Tech Specs (walls, attic, windows, etc. above) were generated by tablet-based software using its camera to survey each Main Floor room. The user has already found errors in this data (front orientation, shielding — corrected above) and expects to correct more as they're identified — treat unconfirmed Tech Specs figures as provisional.

## 2. Load Calculation

**Important scope note:** the central heat pump system serves the **Main Floor only**. The basement is partly finished and receives only incidental/partial conditioned air (not a fully served zone). The attic loft is unfinished and unconditioned — no conditioned air reaches it. Both load estimates below need to be read with this in mind (see reconciliation note at the bottom).

**Manual J** — room-by-room, `HVAC-Calc 3.0` software, dated 8/10/99 (near original construction). See `source-materials/HVAC Heat Load Calculations.pdf`. Design conditions modeled on Charlotte: Winter outdoor 22°F / indoor 70°F; Summer outdoor 95°F / indoor 75°F, grains 32, daily range Medium. Design airflow: 1,200 CFM total (room-by-room Heating/Cooling CFM also in the PDF). The PDF gives a **whole-building** total plus a per-zone breakdown; the whole-building total is not what the heat pump actually has to serve (see below), so the per-zone breakdown matters here:

| Zone | Heat Loss (Btu/h) | Heat Gain (Btu/h) | Sensible | Latent |
|---|---|---|---|---|
| Main Floor | 20,597 | 17,243 | 14,582 | 2,661 |
| Basement West | 9,606 | 3,357 | 3,001 | 356 |
| Basement East | 5,604 | 4,719 | 4,004 | 715 |
| Attic Loft | 2,590 | 2,371 | 2,294 | 77 |
| **Whole building (all zones)** | **38,397** | **27,690** | 23,881 | 3,809 |

- **Main Floor only** (what the heat pump actually serves, best-available reference): **20,597 Btu/h heating**, **17,243 Btu/h cooling** (14,582 sensible + 2,661 latent)
- **Main Floor + full Basement** (upper bound, if the basement's incidental conditioning were treated as fully served): 35,807 Btu/h heating, 25,319 Btu/h cooling — true system load is somewhere between the Main-Floor-only and this upper-bound figure, closer to the Main-Floor-only end since basement conditioning is described as incidental, not primary.
- Attic Loft's 2,590/2,371 Btu/h is not relevant to heat pump sizing at all (unconditioned).

**Assessment report** (Energy Saver NC / Franklin Energy, audited by Aristide Brown, Mar 26, 2026, Job/Report ID #390562) — also Main-Floor-only scope (its stated "Conditioned Area: 1500 ft²" was itself off by 50 ft²; corrected to 1,550 ft² per Section 1):
- Heating load: 24,661 Btu/h (Base) / 25,334 Btu/h (Improved), at winter design condition (26°F outdoor / 70°F indoor)
- Cooling load: Base — Sensible 24,132 + Latent 1,629 = ~25,761 Btu/h total; Improved — Sensible 23,597 + Latent 1,593 = ~25,190 Btu/h total, at summer design condition (91°F outdoor / 75°F indoor)
- Cross-referenced (for annual heating/cooling *energy*, not design-day Btu/h) against `Home_Energy_Use_Estimates.xlsx` → "Degree-Day Base Load Check" sheet, which validates via degree-day regression.
- **Reliability flag:** this heating load figure (24,661 Btu/h) is a tablet-software estimate the user describes as using "often poor assumptions" and expects to correct some of going forward — it should not be weighted as equal in reliability to the Manual J. It's presented here for reference, not as a validated design load.

**Heating source split (Now / historical actual):** the Assessment report's "Now" heating allocation (Heat Pump 50%, Wood Stove 40%, Electric Resistance 10%) is the auditor's guess, not measured data. The authoritative data-driven estimate is in `Home_Energy_Use_Estimates.xlsx` → A4, built from actual fuel-log data plus a degree-day regression: **73.6% wood / 26.4% heat pump / 0% electric resistance**. Use the A4 split, not the Assessment report's guessed split, whenever "actual/historical" heating source breakdown is needed. (This is distinct from T1/W1's forward-looking 50/50 wood/heat-pump *planning* assumption in the same workbook — that's a stated future intent, not a description of current/historical usage.)

**Reconciliation (Main Floor vs Main Floor, both sources):** scoping both to Main Floor only narrows the heating gap (Manual J 20,597 vs Assessment ~24,661–25,334, Assessment ~20–23% higher) but does **not** numerically resolve cooling: Manual J's Main Floor cooling (17,243 Btu/h) is ~46–49% *lower* than the Assessment's Main-Floor cooling estimate (~25,190–25,761 Btu/h). Given the Assessment's heating load is now flagged as a low-confidence tablet-software estimate (see above), its cooling load should be viewed with the same skepticism — it's plausible the mature deciduous tree shade (see Section 1, also not reflected in the Assessment's "Normal" shielding entry until corrected) is part of why real-world cooling performance is better than either paper number would suggest. In practice this is moot either way: per the user, the existing 2.5-ton unit has, in years of actual operation, cooled the entire home sufficiently even in 100°F+ heat. Treat cooling capacity as field-validated rather than pushing for a fresh load calc on that basis alone. See memory note `heat-pump-sizing-field-validation` for the full operating-history context (also covers heating: the wood stove has historically carried most of the heating load, per the A4 73.6%/26.4%/0% split above, with heat strips as backup when it's not in use).
- All heat pump options currently under consideration (existing, T1/T2, W1/W2) are sized at 2.5 tons (30,000 Btu/h) — above the Main-Floor-only Manual J heating load (20,597) but below the whole-building total (38,397); the existing system's electric-resistance aux heat exists to cover shortfalls, and real-world operating history shows this combination (heat pump + wood stove + heat strips) has been adequate. Note that T2/W2 (no wood stove) shift more of the heating burden onto the heat pump/heat strips than historical experience reflects.
- The Manual J is 27 years old (from 2026) and predates any insulation/air-sealing changes since — treat it as a legacy reference, not a fully current calc.

## 3. Equipment Options Under Consideration

| Option | Type | Capacity (tons / Btu-h) | Efficiency (SEER2/HSPF2/COP) | Status |
|---|---|---|---|---|
| Existing | Air-source heat pump (1999, central, shared ducts) + small wood stove (24,000 Btu/h, 60 AFUE) + electric resistance aux | 2.5 ton (30,000 Btu/h) | 11 SEER / 6.8 HSPF | in place, being replaced |
| Trane (T1/T2) | Air-source heat pump — 2026 Trane, 17 series, multi-speed | 2.5 ton | 16 SEER2 / 8.1 HSPF2 | considering (T1 = with wood stove @ 50/50 planning split, T2 = no wood stove) |
| WaterFurnace (W1/W2) | Geothermal / ground-source heat pump — WaterFurnace 5 Series, desuperheater, horizontal closed loop | 2.5 ton | 28.7 Cooling EER (≈8.41 COP) / 4.3 Heating COP | considering (W1 = with wood stove @ 50/50 planning split, W2 = no wood stove) |

**Leading option (if decided):** Not yet decided. Per current `Lifetime Costs.xlsx` figures (below), W1 (geothermal, keep wood stove) shows the best annual savings and pays back its upfront premium over T1 in ~8 years; T2 (Trane, no wood stove) is the only option that costs more per year than current usage.

## 4. Cost Estimates

Equipment/install costs are per **equipment type** (Trane vs. WaterFurnace) from `Lifetime Costs.xlsx` → Cost Parameters. T1/T2 share Trane's cost figures; W1/W2 share WaterFurnace's — the T-vs-2 split only changes assumed wood-stove usage (and therefore annual energy cost), not equipment cost.

| Option | Equipment cost | Installation cost | Incentives / tax credits | Net estimated cost | Source / date |
|---|---|---|---|---|---|
| Trane (T1/T2) | $0 shown as "initial cost" in Cost Parameters — outside funding covers the full cost of installing the Trane equipment | n/a (covered by the same outside funding) | Outside funding source (not further detailed) covers full install cost | $0 net upfront; $14,000 present-value replacement cost budgeted for end-of-life (12-yr service life, not covered by the outside funding) | `Lifetime Costs.xlsx` Cost Parameters, as of 2026-08-18 |
| WaterFurnace (W1/W2) | $1,700 initial unit cost | $3,000 ground loop cost | Included in the $3,000 loop figure — "after Duke Energy rebate" | $4,700 total upfront | `Lifetime Costs.xlsx` Cost Parameters, as of 2026-08-18 |

**Annual operating cost by scenario** (from `Home_Energy_Use_Estimates.xlsx` → Future Energy Use Estimates, Year-1 full-year basis):

| Scenario | Annual kWh | Annual $ cost | vs. current usage ($1,526/yr) |
|---|---|---|---|
| T1 (Trane, wood stove) | 9,927 | $1,500 | +$26/yr savings |
| T2 (Trane, no wood stove) | 11,949 | $1,805 | –$280/yr (costs more) |
| W1 (Geothermal, wood stove) | 7,746 | $1,170 | +$355/yr savings |
| W2 (Geothermal, no wood stove) | 8,832 | $1,335 | +$191/yr savings |

**25-year lifetime cost comparison** (`Lifetime Costs.xlsx`, both sheets built out with escalating electricity rates, service/repair/replacement schedules, and running cumulative cost):
- Geothermal payback vs. Trane (upfront premium of $4,700 recovered via cumulative savings): **W1 vs T1 — 8 years**; **W2 vs T2 — 7 years**.
- Electricity rate assumption: $0.1511/kWh base (2026), escalating 3%/yr, present-value/nominal projection (not inflation-adjusted).

Ongoing service/repair assumptions (present value):
- Trane: $200/yr tuneup; $800 repair in service years 6 and 9; $14,000 replacement at 12-year service life.
- WaterFurnace: $200 tuneup every 6 years; $800 repair in service years 12 and 20; $17,700 replacement at 27-year service life (falls outside the 25-yr analysis window, so no replacement cost shown in either output sheet).

## 5. Open Questions / Next Steps

- [ ] Review the Cost Parameters values themselves for overall reasonableness — flagged as a not-yet-done pass in `CLAUDE.md`
- [ ] Decide on a leading option among T1/T2/W1/W2 (or continue treating this as open pending more source data, e.g. contractor quotes)
- [ ] Get basement above-grade window area (type/U-value known: insulated, Low-E, Argon, U-0.45; ft² not yet given)

## 6. Change Log

| Date | Change | Changed in conversation |
|---|---|---|
| 2026-08-18 | Filled in template from `Home_Energy_Use_Estimates.xlsx` (Current Energy Consumption sheet's Assessment-report figures; Future Energy Use Estimates T1/T2/W1/W2 annual kWh & $cost), `Lifetime Costs.xlsx` (Cost Parameters, 25-yr payback calc for both output sheets), and `source-materials/Home Energy Assessment Report - Bryan Wussow.md` (envelope, design temps, load figures) | "read over the project information" session |
| 2026-08-18 | Added Manual J load figures (`source-materials/HVAC Heat Load Calculations.pdf`), noted its whole-building vs Main-Floor-only zone breakdown (heat pump serves Main Floor only; basement incidental; attic loft unconditioned), and recorded that years of real-world operation validate the existing 2.5-ton cooling capacity and show the wood stove/heat strips historically carry heating | same session, continued |
| 2026-08-18 | Clarified the Trane's $0 "initial cost" in Cost Parameters: outside funding covers the full install cost (not an unpriced/unknown item) | same session, continued |
| 2026-08-20 | Confirmed IECC climate zone 3A. Corrected conditioned area 1,500→1,550 ft², clarified "2 floors above grade" = Main Floor + unconditioned attic bonus room (not a second full story), corrected front orientation NW→South and shielding "Normal"→heavy deciduous tree shade. Flagged the Assessment report's 24,661 Btu/h heating load as a low-confidence tablet-software estimate. Replaced the Assessment's guessed "Now" heating-source split (HP 50%/wood 40%/aux 10%) with A4's data-driven split (73.6% wood / 26.4% heat pump / 0% electric resistance) | "correct various facts in hvac-summary" session |
| 2026-08-20 | Corrected wall insulation: R-11 cavity/R-0 continuous → R-13 cavity/R-3 continuous ("Wall 1," 1,717.02 ft²) | "Tech Specs corrections" session |
| 2026-08-21 | Corrected attic insulation: replaced single blended R-18.9 (7–9" depth, no radiant barrier) figure with two-zone breakdown — Attic 1 (floored, 400 ft², R-30 batts, 9.25", no radiant barrier) and Attic 2 (no floor, 1,150 ft², R-38, 16" batts/blown, radiant barrier yes) | "Tech Specs corrections" session |
| 2026-08-21 | Corrected foundation: Walkout Basement, total footprint 500→1,550 ft² (same outer perimeter as Main Floor; user confirmed 500 ft² was simply wrong), wall height 9 ft avg → 8'8" + rim joist | "Tech Specs corrections" session |
| 2026-08-21 | Corrected basement walls: replaced blended R-4 continuous (fiberglass blanket) figure with 3-part breakdown (45% wood frame above grade R-13 cavity/R-5 continuous, 40% 12" masonry below grade uninsulated, 15% 12" masonry above grade uninsulated). Added basement conditioning detail: heating intentional via wood stove only; cooling corrected from "incidental/leakage" to intentional-but-partial, via two deliberately-cracked basement supply ducts plus stairway airflow, not duct losses | "Tech Specs corrections" session |
| 2026-08-21 | Corrected windows: replaced Assessment's single-pane+storm/U-0.51/SHGC-0.56/NE-SE-SW-NW breakdown with Main Floor figures (3/4" insulated Low-E Argon, U-0.32, SHGC 0.33, no storms, Energy Star; East 29/North 128/West 55/South 77 ft², total 289 ft², true compass directions matching corrected South-front orientation) and added Basement above-grade window type (insulated Low-E Argon, U-0.45; area not yet given) | "Tech Specs corrections" session |
| 2026-08-21 | Dropped the reliability note's mention of the old per-window compass breakdown, now superseded by the corrected window data above. Tech Specs corrections session completed (walls, attic, foundation/basement, windows) | "Tech Specs corrections" session |
