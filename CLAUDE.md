# Home Energy Use Estimates — Project Instructions

This file is read automatically by Claude Code every time you start a session in this folder. It replaces the "Project instructions" you had in Cowork/claude.ai — keep it updated as the project evolves.

## Overall Objective
Accurately analyze current home energy consumption at 6960 Old Ridge Road, Waxhaw, NC 28173, and calculate future energy use cost estimates for HVAC and water heating upgrade options (air-source heat pump vs. geothermal/ground-source heat pump), including lifetime cost comparisons.

Phase 1 work (reviewing/validating the annual energy consumption estimates) is basically complete. **Focus on Phase 2** unless told otherwise.

## Response Style
Provide moderately terse responses unless explicitly asked for more detail. When producing analysis or numbers, always show step-by-step how each output number was determined — don't just state a result.

## Phase 1 — Review and Improve the Annual Energy Consumption Estimates (mostly done, revisit if asked)
- Check whether formulas are applied with consistent patterns throughout `Home_Energy_Use_Estimates.xlsx`.
- Suggest corrections or improvements to provided values, formulas, and analysis structure.
- Suggest if additional source materials are needed for proper analysis.
- Answer the "Q:" analytical questions embedded in the spreadsheet, in place, on the row after each question. Question types include: does this table/calculation accurately reflect the Assessment report's data and intent; why do results vary from expectations; is this base load reasonable vs. public data on similar homes; can public heating/cooling degree-day data validate the annual heat load; do these kWh loads compare reasonably with historic Duke Energy usage.

## Phase 2 — Estimate Lifetime Costs of Home Energy Systems, Year-by-Year (current focus)

**Preparation** — in `Lifetime Costs.xlsx`, sheet "Cost Parameters":
- Review the cost parameters and suggest improvements.
- Create named cells for the numerical inputs, and use those names in formulas throughout the output sheets (not raw cell references).
- Update the descriptions in column E to pull live values from the numerical cells (so the description text always matches the current parameter value).

**Main objective** — in `Lifetime Costs.xlsx`, generate two output sheets, each a year-by-year cumulative cost comparison:
- Sheet 1: compare options **T1** and **W1**
- Sheet 2: compare options **T2** and **W2**
- These four options (T1, T2, W1, W2) are defined in `Home_Energy_Use_Estimates.xlsx`, sheet "Future Energy Use Estimates" — that sheet calculates total annual "elec kWh consumed" and "elec $cost" for each option; those numbers feed into Lifetime Costs.
Update "Future Energy Use Estimates" sheet to create named cells those totals, and use those names in formulas throughout the output sheets (not raw cell references).

**Formatting:**
- ~2–3 rows per year, ~2–3 columns per option (that year's annual numbers + a cumulative-cost column).
- Row and column headings provided and frozen (locked from scrolling).

**Costs to include, per option:**
- Initial/up-front costs (shown before the year-by-year rows start)
- Ongoing costs for 25 years:
  - Electricity consumed that year, and that year's $ cost
  - Service and repair costs that year
  - Heat pump replacement cost if/when the unit reaches end of service life

Numerical cost parameters for proposed new equipment and electricity cost come from the "Cost Parameters" sheet in `Lifetime Costs.xlsx`.

**At the start of each option's columns, show:**
- The option name (matching the heading text from `Home_Energy_Use_Estimates.xlsx` → "Future Energy Use Estimates") (Create and use named cells for these names.)
- The annual electric energy consumption from "Future Energy Use Estimates" for that option, and below it a "what if" value — initially equal to the above, but user-editable so the homeowner can manually adjust it and see updated results flow through the years
- For geothermal option columns only: a live-calculated number of years required for the geothermal up-front cost premium to be recovered via cumulative cost savings vs. the air-source option
- Finally, the up-front costs — the starting point for the cumulative cost calculation

**For each year, show:**
- The $/kWh cost of electricity projected for that year (increases each subsequent year by the escalation % in Cost Parameters — this is a present-value/nominal projection, not inflation-adjusted back to today's dollars)
- The electric energy consumption for that year for that option:
  - Year 1: prorate for the number of months given in Cost Parameters (partial first year, e.g. mid-year install)
  - All subsequent years: 100% of the annual consumption for that option
- That year's electricity cost for that option
- Service, repair, and replacement costs for that year
- Cumulative cost-to-date for that option, in its own column

**Formula convention:** wherever a cost parameter is used in the output sheets, reference it by its named cell, not a raw cell address.

## Source Materials In This Folder
- `Home_Energy_Use_Estimates.xlsx` — central workbook gathering data from all source materials (see "Spreadsheet Breakdown" below)
- `Lifetime Costs.xlsx` — Cost Parameters sheet (inputs) + two output sheets to be generated (T1/W1 comparison, T2/W2 comparison)
- `source-materials/Home Energy Assessment Report - Bryan Wussow.md` — Energy Saver NC Home Energy Assessment report (text extract of the original PDF), audit dated Mar 26, 2026. Baseline energy analysis and recommended upgrades to reach stated Goal levels.
- `source-materials/README - HVAC Heat Load Calculations PDF missing.md` — flags that the Manual J heat load calc PDF needs to be manually added to this folder (see that file for why)
- `source-materials/Heating Cooling Degree Days Waxhaw area.xlsx` — heating/cooling degree-day data for airport weather stations near the home
- `source-materials/Trane Heat Pump Brochure (72-1209-R-41).md` — Trane air-source heat pump lineup and SEER2/HSPF2 ratings (text extract)
- `source-materials/WaterFurnace CCW5-0016W Product Comparison (7-5-3 Series).md` — WaterFurnace ground-source heat pump series comparison (text extract)
- `source-materials/Water Furnace 5 Series EER COP.md` — WaterFurnace 5 Series detailed EER/COP table by size and loop type (text extract — cross-check against original PDF before relying on exact row alignment)
- `source-materials/Geothermal Energy Comparison - Monarch.md` — Monarch Air, Heat & Geothermal's budget-level geothermal proposal and savings estimate vs. the audit baseline (text extract)
- `Prompt Planning.md` — the original prompt-planning notes this CLAUDE.md was derived from; kept for reference

**Important:** several of the files above are plain-text/Markdown re-creations of PDFs, not the original PDF files (the export process only had access to extracted text for PDF-type project files, not the original bytes). Numbers were preserved carefully, but exact table/chart layout was not. If precision on a specific figure matters, it's worth asking the user to confirm against the original PDF, or having them add the original PDF file to this folder so it can be read directly.

## Spreadsheet Breakdown — Home_Energy_Use_Estimates.xlsx
- **A1:** Captures Energy Consumption values from the Assessment Report.
- **A2:** Captures Energy Goals from the Assessment Report if all upgrades are installed.
- **A3:** Attempts to separate energy use details.
- **A4:** Adjusts energy use details using more accurate assumptions — becomes the basis for comparing energy consumption across upgrade options.
- **B2:** Validates the formulas used so far to make energy use estimates.
- **B4:** Calculates more realistic Goals than the Assessment's Goal values in A2.
- **T1, T2, W1, W2:** Annual energy usage and savings (or additional cost) for the available heat pump replacement options, with and without the wood stove assisting. (T = Trane/air-source, W = WaterFurnace/geothermal, presumably; confirm exact option definitions in the spreadsheet itself.)
- Historic Data: Duke Energy bill history appears in multiple contexts, as relevant.
- Equipment Performance Values: performance figures for the existing air-source heat pump, a new Trane air-source heat pump, and a new WaterFurnace ground-source heat pump appear in multiple contexts, as relevant.

## Status
**Phase 1 is complete.** The A1 table and the rest of Phase 1's review/validation work are done — do not revisit unless the user brings it up.

**Phase 2 is the current focus.** A ready-to-run Phase 2 prompt is in `Phase 2 Prompt.md` in this folder — it covers building the year-by-year lifetime cost comparison sheets (T1 vs W1, T2 vs W2) in `Lifetime Costs.xlsx`, with exact source cell references from `Home_Energy_Use_Estimates.xlsx`. Start there. Note: `Lifetime Costs.xlsx` currently has a broken external-workbook link (it points to a file named `Home_Energy_Use_Estimates 11.xlsx` instead of the actual `Home_Energy_Use_Estimates.xlsx` in this folder) — `Phase 2 Prompt.md` calls this out as the first thing to fix.

## Working Norms
- This folder is not yet a git repo. Consider running `git init` early so Claude Code can track changes to the spreadsheets/instructions over time (note: Excel .xlsx files are binary, so git will track them as opaque blobs — diffs won't be human-readable, but version history and rollback still work).
- When editing the .xlsx files, prefer preserving existing formulas/named ranges over hardcoding values, per the Phase 2 instructions above (named cells).
