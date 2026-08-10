# Phase 2 Prompt — Lifetime Cost Comparison

Paste the block below into Claude Code (in this folder) to kick off Phase 2. It's a tightened version of the Phase 2 section from `Prompt Planning.md`, with the actual sheet/cell references filled in so Claude doesn't have to guess or re-derive them.

---

## First, a housekeeping fix

`Lifetime Costs.xlsx` has named ranges (`A4KwhConsum`, `A4DollarConsum`, `kwhcost`, `kwhmmbtu`, `PctRedAirSeal`, etc.) that point to an **external link** to a file called `Home_Energy_Use_Estimates 11.xlsx` — not the `Home_Energy_Use_Estimates.xlsx` that's actually in this folder. That link is currently broken, so any formula using those names in Lifetime Costs.xlsx is probably returning `#REF!` or a stale cached value.

Please fix this first: repoint the external link at `Home_Energy_Use_Estimates.xlsx` in this same folder.

## Preparation — Cost Parameters sheet in `Lifetime Costs.xlsx`

Look at the parameters currently in the "Cost Parameters" sheet and tell me if anything looks off or is missing:

- **Trane air-source heat pump** (rows 7–14): initial cost $0 (A8, "covered"), service life 12 years (A10), replacement cost $14,000 present value (A11), tuneup $200 (A12) every 1 year (A13), repairs of $800 in service years 6 and 9 (A14/C14/D14).
- **WaterFurnace ground-source heat pump** (rows 16–24): initial unit cost $1,700 (A17) + ground loop $3,000 after Duke Energy rebate (A18), service life 27 years (A20), replacement cost $17,700 (A21), tuneup $200 (A22) every 6 years (A23), repairs of $800 in service years 12 and 20 (A24/C24/D24).
- **Other parameters** (rows 26–33): electricity $0.1511/kWh (A28), 3%/year escalation above inflation (A30), analysis starts 2026 (A32), first year is prorated to 4 months (A33).

Then:
1. Create named cells for every numeric input above (e.g. `TraneInitialCost`, `TraneServiceLife`, `TraneReplacementCost`, `TraneTuneupCost`, `TraneTuneupInterval`, `TraneRepairCost`, `TraneRepairYear1`, `TraneRepairYear2`, and the WaterFurnace/electricity equivalents — pick clear names, these are just suggestions).
2. Use those names (not raw cell refs) in every formula on the output sheets below.
3. Rewrite column E's descriptions so they pull the live value in with a formula (e.g. `="replacement cost - $"&TEXT(TraneReplacementCost,"#,##0")&" (present value)"`) instead of static text, so the description can never drift out of sync with the number.

## Main objective — two new output sheets

Build two new sheets in `Lifetime Costs.xlsx`:

- **Sheet "T1 vs W1"** — Trane air-source *with* wood stove vs. WaterFurnace geothermal *with* wood stove
- **Sheet "T2 vs W2"** — Trane air-source *without* wood stove vs. WaterFurnace geothermal *without* wood stove

Each option's starting annual **electric kWh consumed** and **electric $ cost** comes from `Home_Energy_Use_Estimates.xlsx`, sheet "Future Energy Use Estimates":

| Option | Label cell | Total annual kWh | Total annual $ cost |
|---|---|---|---|
| T1 (Trane + wood stove) | A84 | G93 | H93 |
| T2 (Trane, no wood stove) | A104 | G113 | H113 |
| W1 (WaterFurnace + wood stove) | A123 | G132 | H132 |
| W2 (WaterFurnace, no wood stove) | A143 | G152 | H152 |

Pull these in as live cross-workbook references (or, if you fixed the link problem above by hardcoding, hardcode these four pairs the same way, clearly labeled with source and date).

### Layout, each sheet
- ~2–3 rows per year, ~2–3 columns per option (that year's annual numbers + a running cumulative-cost column).
- Row and column headers frozen (Freeze Panes) so they stay visible while scrolling 25 years down.

### At the top of each option's columns, show:
1. The option name/label (from the table above).
2. The annual electric kWh consumption pulled from Future Energy Use Estimates, and directly below it a **"what if" cell** — initially equal to that value, but meant for me to overwrite by hand later to test different consumption assumptions. Every year's calculation below should reference the "what if" cell, not the pulled-in value directly, so my manual overrides actually flow through.
3. For the WaterFurnace (W1/W2) columns only: a live-calculated **"years to payback"** — the number of years until WaterFurnace's higher up-front cost is offset by its cumulative savings vs. the corresponding Trane option (W1 vs T1, W2 vs T2).
4. The up-front cost total (initial unit/install cost + ground loop cost if applicable) — this is where the cumulative-cost running total starts, before Year 1's operating costs are added.

### For each of the 25 years, show:
- That year's $/kWh electricity rate — Year 1 uses the base rate (`A28`/named cell); every subsequent year multiplies the prior year's rate by `(1 + escalation%)`.
- That year's electric consumption for that option — Year 1 uses only the prorated fraction (months-in-Cost-Parameters ÷ 12) of the "what if" annual value; Year 2 onward use 100% of it.
- That year's electricity cost = that year's rate × that year's consumption.
- That year's service cost (only in years matching the tuneup interval), repair cost (only in the specific named repair years), and replacement cost (only in the year the unit hits its service-life age — repeating every service-life interval if the 25-year window is long enough to hit it twice).
- A running cumulative-cost column: prior cumulative + this year's (electricity + service + repair + replacement).

## When you're done
Give me a short summary of: which named cells you created, where the T1/T2/W1/W2 source numbers came from (cell references), and how you handled the broken external link. I'll want to spot-check a couple of years' math by hand before I trust the 25-year totals.
