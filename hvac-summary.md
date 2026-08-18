# HVAC Load, Equipment & Cost Summary

> Source of truth for home HVAC load calculations, equipment options, and cost estimates.
> Other conversations/projects (e.g., geothermal ground loop design) should read this file
> rather than relying on values repeated in chat history. Update this file whenever numbers
> change — don't just report the change in conversation.

**Last updated:** 2026-08-18
**Updated by / in conversation:** "read over the project information" session (populated from `Home_Energy_Use_Estimates.xlsx`, `Lifetime Costs.xlsx`, and the Assessment report)

---

## 1. Project Basics

- Address / location: 6960 Old Ridge Road, Waxhaw, NC 28173
- Climate zone: Not stated in the Assessment report. Waxhaw, NC (Union County) falls in IECC climate zone 3A (Mixed-Humid) per published IECC maps — inferred, not sourced from a project document. Flag/confirm if this matters for a future calc.
- Conditioned floor area: 1,500 ft² (2 floors above grade + full basement, average wall height 9 ft; basement floor area 500 ft²)
- House age / construction type: Built 1999. Exterior walls: 2x4 frame, wood/fiber-cement siding, 1,717.02 ft² modeled area.
- Insulation levels:
  - Walls: R-11 cavity, R-0 continuous
  - Attic: R-18.9 (fiberglass/rockwool batts or blown, 7–9" depth, no radiant barrier)
  - Basement walls: R-4 continuous (fiberglass blanket)
  - Windows: single-pane + storm, wood/metal clad frame, U-value 0.51, SHGC 0.56 (NE 29.43 ft², SE 147.17 ft², SW 55.19 ft², NW 122.64 ft²)
  - Air leakage: 3,490 CFM50 now (14.96 ACH50) → goal 2,617.5 CFM50 (11.22 ACH50); home not professionally air sealed
- Design temperatures used: Winter 26°F outdoor / 70°F indoor; Summer 91°F outdoor / 75°F indoor (per Assessment report)

## 2. Load Calculation

- Method used: Energy Saver NC / Franklin Energy home energy assessment's own modeled load (audit report figures) — **not** an independent Manual J calculation. The actual Manual J heat load calc PDF (`HVAC Heat Load Calculations.pdf`) is still missing from `source-materials/` (see `source-materials/README - HVAC Heat Load Calculations PDF missing.md`) and has not been added to this folder yet.
- Heating load: 24,661 Btu/h (Base) / 25,334 Btu/h (Improved), at winter design condition (26°F outdoor / 70°F indoor)
- Cooling load: Base — Sensible 24,132 + Latent 1,629 = ~25,761 Btu/h total; Improved — Sensible 23,597 + Latent 1,593 = ~25,190 Btu/h total, at summer design condition (91°F outdoor / 75°F indoor)
- Load calc source / date: Home Energy Assessment Report (Energy Saver NC / Franklin Energy), audited by Aristide Brown, Mar 26, 2026, Job/Report ID #390562. Cross-referenced (for annual heating/cooling *energy*, not design-day Btu/h) against `Home_Energy_Use_Estimates.xlsx` → "Degree-Day Base Load Check" sheet, which validates via degree-day regression.
- Notes / caveats: These are the Assessment's own modeled figures, not a contractor Manual J. Get the original Manual J PDF into this folder before relying on these numbers for final equipment sizing — the current 2.5-ton equipment selections in `Home_Energy_Use_Estimates.xlsx` should be checked against it once available.

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
| Trane (T1/T2) | $0 shown as "initial cost" in Cost Parameters, noted "the cost is covered" — meaning unclear, worth confirming with user | n/a (not broken out separately) | none itemized | $0 upfront; $14,000 present-value replacement cost budgeted for end-of-life (12-yr service life) | `Lifetime Costs.xlsx` Cost Parameters, as of 2026-08-18 |
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

- [ ] Get the original Manual J heat load calc PDF (`HVAC Heat Load Calculations.pdf`) into `source-materials/` and cross-check the Assessment's Btu/h loads and the 2.5-ton equipment sizing against it
- [ ] Confirm what "the cost is covered" means for the Trane's $0 initial-cost entry in Cost Parameters (rolled into another cost? not yet priced?)
- [ ] Review the Cost Parameters values themselves for overall reasonableness — flagged as a not-yet-done pass in `CLAUDE.md`
- [ ] Confirm/decide climate zone if it becomes relevant to a future calc (currently just inferred as IECC 3A from location)
- [ ] Decide on a leading option among T1/T2/W1/W2 (or continue treating this as open pending more source data, e.g. contractor quotes)

## 6. Change Log

| Date | Change | Changed in conversation |
|---|---|---|
| 2026-08-18 | Filled in template from `Home_Energy_Use_Estimates.xlsx` (Current Energy Consumption sheet's Assessment-report figures; Future Energy Use Estimates T1/T2/W1/W2 annual kWh & $cost), `Lifetime Costs.xlsx` (Cost Parameters, 25-yr payback calc for both output sheets), and `source-materials/Home Energy Assessment Report - Bryan Wussow.md` (envelope, design temps, load figures) | "read over the project information" session |
