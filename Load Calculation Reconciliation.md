# Load Calculation Reconciliation

Bryan Wussow · 6960 Old Ridge Road, Waxhaw, NC 28173 · October 12, 2026

The two documents I've sent you, the 2026 Home Energy Assessment and the 1999 Manual J, give different design loads for this house. This note puts them side by side, shows which part of the house the heat pump serves, and lists corrections to the Assessment's building inputs. It is background for your proposal; your own load calculation governs.

## Summary

- The Assessment's main-floor loads are higher than the Manual J's: about 20% higher for heating and about 49% higher for cooling.
- Several building inputs in the Assessment were wrong (insulation, windows, orientation, shade). The corrected values are listed below.
- The existing 2.5-ton heat pump has cooled the whole home adequately for years, including in 100°F+ weather.
- I expect a 2.5-ton replacement. If your calculation points to a different size, I'd like to see it.

## Main-floor loads, side by side

| | Manual J (1999) | Assessment (2026) |
| --- | --- | --- |
| Method | Room by room, HVAC-Calc 3.0 | Program software, from a tablet survey of the main floor |
| Winter design, outdoor / indoor | 22°F / 70°F | 26°F / 70°F |
| Summer design, outdoor / indoor | 95°F / 75°F | 91°F / 75°F |
| Heating load (Btu/h) | 20,597 | 24,661 |
| Cooling load, total (Btu/h) | 17,243 | about 25,761 |
| Cooling, sensible (Btu/h) | 14,582 | 24,132 |
| Cooling, latent (Btu/h) | 2,661 | 1,629 |

The differences:

- **Heating:** 24,661 − 20,597 = 4,064 Btu/h, or 20% above the Manual J (4,064 ÷ 20,597).
- **Cooling:** 25,761 − 17,243 = 8,518 Btu/h, or 49% above the Manual J (8,518 ÷ 17,243).

The Assessment is higher in both cases even though it uses milder design temperatures (a warmer winter day and a cooler summer day).

## What the heat pump serves

The Manual J reports a whole-building total, but the heat pump does not serve the whole building.

| Zone (1999 Manual J) | Heat loss (Btu/h) | Heat gain (Btu/h) | Served by the heat pump? |
| --- | --- | --- | --- |
| Main Floor | 20,597 | 17,243 | Yes, fully |
| Basement West | 9,606 | 3,357 | Heating: no (wood stove only). Cooling: partly |
| Basement East | 5,604 | 4,719 | Heating: no (wood stove only). Cooling: partly |
| Attic Loft | 2,590 | 2,371 | No; unfinished and unconditioned at this time |
| Whole building | 38,397 | 27,690 | |

- The basement gets minor intentional cooling from two supply ducts left cracked open, plus air moving down the stairway. Those ducts will stay as they are.
- If the basement were fully cooled, the cooling load would be at most 17,243 + 3,357 + 4,719 = 25,319 Btu/h. The real figure is much closer to the main-floor number.
- The Assessment's loads cover the main floor only.

## Corrections to the Assessment's building inputs

I found these errors in the Assessment's Tech Specs. The corrected values may be useful as inputs to your own load calculation.

| Item | Assessment | Corrected |
| --- | --- | --- |
| Conditioned area (main floor) | 1,500 ft² | 1,550 ft² |
| Front orientation | Northwest | South |
| Shading | "Normal" | Heavy shade from mature deciduous trees in spring, summer, and fall |
| Exterior walls (2x4, 1,717 ft²) | R-11 cavity, no continuous insulation | R-13 cavity plus R-3 continuous |
| Attic | One zone, R-18.9, no radiant barrier | 400 ft² floored area: R-30 batts, 9.25 in, no radiant barrier. 1,150 ft² unfloored area: R-38, 16 in, with radiant barrier |
| Main-floor windows | Single pane with storms, U-0.51, SHGC 0.56 | Insulated Low-E argon, U-0.32, SHGC 0.33, no storms. 289 ft² total: North 128, South 77, West 55, East 29 |
| Foundation | 500 ft², 9 ft average wall height | Walkout basement, 1,550 ft² footprint, 8 ft 8 in walls plus rim joist |
| Basement walls | R-4 continuous blanket | About 45% wood frame above grade (R-13 cavity plus R-5 continuous); about 40% 12 in masonry below grade, uninsulated; about 15% 12 in masonry above grade, uninsulated |

Most of these corrections point toward lower loads than the Assessment calculated; the window and shading corrections matter most for cooling. I have not re-run a load calculation with the corrected inputs.

Not changed: the Assessment's air leakage estimate of 3,490 CFM50 (14.96 ACH50).

## Limits of these numbers

- The Manual J is 27 years old and reflects the house as built in 1999.
- The Assessment's loads are software estimates, and I have found errors in their inputs.
- The existing system pairs the heat pump with 10 kW of electric aux heat. A 24,000 Btu/h wood stove has carried most of the heating in practice.
- Neither document replaces your own Manual J.
