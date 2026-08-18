# HVAC Load, Equipment & Cost Summary

> Source of truth for home HVAC load calculations, equipment options, and cost estimates.
> Other conversations/projects (e.g., geothermal ground loop design) should read this file
> rather than relying on values repeated in chat history. Update this file whenever numbers
> change — don't just report the change in conversation.

**Last updated:** 2026-08-18
**Updated by / in conversation:** "read over the project information" session (populated from `Home_Energy_Use_Estimates.xlsx`, `Lifetime Costs.xlsx`, and the Assessment report; then reconciled against the Manual J PDF and real-world operating history)

---

## 1. Project Basics

- Address / location: 6960 Old Ridge Road, Waxhaw, NC 28173
- Climate zone: Not stated in the Assessment report. Waxhaw, NC (Union County) falls in IECC climate zone 3A (Mixed-Humid) per published IECC maps — inferred, not sourced from a project document. Flag/confirm if this matters for a future calc.
- Conditioned floor area: 1,500 ft² — this is **Main Floor only**. The central heat pump system heats/cools the Main Floor only; the basement is partly finished and gets only incidental conditioned air (not a fully served zone); the attic loft is unfinished and unconditioned (no conditioned air reaches it at all). The Assessment report's "Conditioned Area: 1500 ft²" figure and its load numbers below reflect this same Main-Floor-only scope. (2 floors above grade + full basement, average wall height 9 ft; basement floor area 500 ft²)
- House age / construction type: Built 1999. Exterior walls: 2x4 frame, wood/fiber-cement siding, 1,717.02 ft² modeled area.
- Insulation levels:
  - Walls: R-11 cavity, R-0 continuous
  - Attic: R-18.9 (fiberglass/rockwool batts or blown, 7–9" depth, no radiant barrier)
  - Basement walls: R-4 continuous (fiberglass blanket)
  - Windows: single-pane + storm, wood/metal clad frame, U-value 0.51, SHGC 0.56 (NE 29.43 ft², SE 147.17 ft², SW 55.19 ft², NW 122.64 ft²)
  - Air leakage: 3,490 CFM50 now (14.96 ACH50) → goal 2,617.5 CFM50 (11.22 ACH50); home not professionally air sealed
- Design temperatures used: Winter 26°F outdoor / 70°F indoor; Summer 91°F outdoor / 75°F indoor (per Assessment report)

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

**Assessment report** (Energy Saver NC / Franklin Energy, audited by Aristide Brown, Mar 26, 2026, Job/Report ID #390562) — also Main-Floor-only scope (its "Conditioned Area: 1500 ft²" matches the Main Floor):
- Heating load: 24,661 Btu/h (Base) / 25,334 Btu/h (Improved), at winter design condition (26°F outdoor / 70°F indoor)
- Cooling load: Base — Sensible 24,132 + Latent 1,629 = ~25,761 Btu/h total; Improved — Sensible 23,597 + Latent 1,593 = ~25,190 Btu/h total, at summer design condition (91°F outdoor / 75°F indoor)
- Cross-referenced (for annual heating/cooling *energy*, not design-day Btu/h) against `Home_Energy_Use_Estimates.xlsx` → "Degree-Day Base Load Check" sheet, which validates via degree-day regression.

**Reconciliation (Main Floor vs Main Floor, both sources):** scoping both to Main Floor only narrows the heating gap (Manual J 20,597 vs Assessment ~24,661–25,334, Assessment ~20–23% higher — plausibly just methodology/vintage differences) but does **not** numerically resolve cooling: Manual J's Main Floor cooling (17,243 Btu/h) is ~46–49% *lower* than the Assessment's Main-Floor cooling estimate (~25,190–25,761 Btu/h). That gap is still unexplained on paper — but it's moot in practice: per the user, the existing 2.5-ton unit has, in years of actual operation, cooled the entire home sufficiently even in 100°F+ heat. Treat cooling capacity as field-validated rather than pushing for a fresh load calc on that basis alone. See memory note `heat-pump-sizing-field-validation` for the full operating-history context (also covers heating: the wood stove has historically carried most of the heating load, with heat strips as backup when it's not in use).
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
- [ ] Confirm/decide climate zone if it becomes relevant to a future calc (currently just inferred as IECC 3A from location)
- [ ] Decide on a leading option among T1/T2/W1/W2 (or continue treating this as open pending more source data, e.g. contractor quotes)

## 6. Change Log

| Date | Change | Changed in conversation |
|---|---|---|
| 2026-08-18 | Filled in template from `Home_Energy_Use_Estimates.xlsx` (Current Energy Consumption sheet's Assessment-report figures; Future Energy Use Estimates T1/T2/W1/W2 annual kWh & $cost), `Lifetime Costs.xlsx` (Cost Parameters, 25-yr payback calc for both output sheets), and `source-materials/Home Energy Assessment Report - Bryan Wussow.md` (envelope, design temps, load figures) | "read over the project information" session |
| 2026-08-18 | Added Manual J load figures (`source-materials/HVAC Heat Load Calculations.pdf`), noted its whole-building vs Main-Floor-only zone breakdown (heat pump serves Main Floor only; basement incidental; attic loft unconditioned), and recorded that years of real-world operation validate the existing 2.5-ton cooling capacity and show the wood stove/heat strips historically carry heating | same session, continued |
| 2026-08-18 | Clarified the Trane's $0 "initial cost" in Cost Parameters: outside funding covers the full install cost (not an unpriced/unknown item) | same session, continued |
