# Energy Use: Corrected Estimates and Future Scenarios

Bryan Wussow · 6960 Old Ridge Road, Waxhaw, NC 28173 · October 12, 2026

These are my own working estimates, built from the 2026 Home Energy Assessment's figures. They explain how I heat the house today and why I'm weighing both an air-source and a geothermal heat pump. They are background only: I'm not asking you to change anything in the Energy Saver NC program's model.

## What I corrected in the Assessment's current-use picture

The Assessment assumed the heat pump does half the heating. In practice I switch the heat pump off when it drops below about 50°F and heat with the wood stove, and the electric resistance heat is disabled.

| Share of heat delivered | Assessment | Corrected |
| --- | --- | --- |
| Heat pump | 50% | 26% |
| Wood stove | 40% | 74% |
| Electric resistance | 10% | 0% |

The corrected split comes from my wood fuel log and a comparison of Duke Energy bills against local heating degree days.

I kept the Assessment's total electricity use and its heating and cooling loads. Only the breakdown changes:

| Electricity (kWh/yr) | Assessment | Corrected |
| --- | --- | --- |
| Heating | 3,542 | 1,320 |
| Cooling | 2,142 | 2,142 |
| Base load, including water heating | 4,417 | 6,636 |
| Total | 10,101 | 10,098 |

- The total is fixed by the electric meter, so electricity the heat pump isn't using for heating must be base load instead. (The 3 kWh gap between the totals is rounding.)
- At $0.16/kWh, the corrected total costs 10,098 × $0.16 = $1,616 per year.
- The correction also means I burn about twice as much wood as the Assessment assumed: 41.6 vs. 21.9 MMBtu of fuel per year.

## Future scenarios

Four scenarios, each a 2.5-ton heat pump, with and without the wood stove.

| | Air-source | Geothermal |
| --- | --- | --- |
| Reference equipment | 2026 Trane 17 series, multi-speed | WaterFurnace 5 Series, horizontal closed loop, with desuperheater |
| Cooling efficiency | 16 SEER2 (seasonal COP about 4.7) | 28.7 EER (COP about 8.4) |
| Heating efficiency | 8.1 HSPF2 (seasonal COP about 2.4) | 4.3 COP |

Assumptions common to all four:

- Air sealing as the Assessment recommends, lowering heating and cooling loads by about 5.8%.
- The existing electric water heater stays.
- Other base load is unchanged at 5,079 kWh/yr.
- Electricity costs $0.16/kWh.

| Scenario | Wood stove share of heating | Heating (kWh) | Cooling (kWh) | Water heating (kWh) | Total (kWh/yr) | Cost ($/yr) | vs. today ($1,616) |
| --- | --- | --- | --- | --- | --- | --- | --- |
| T1: air-source, with wood stove | 50% | 1,975 | 1,329 | 1,557 | 9,939 | $1,590 | saves $25 |
| T2: air-source, no wood stove | 0% | 4,003 | 1,329 | 1,557 | 11,968 | $1,915 | costs $299 more |
| W1: geothermal, with wood stove | 50% | 1,090 | 741 | 842 | 7,753 | $1,240 | saves $375 |
| W2: geothermal, no wood stove | 0% | 2,180 | 741 | 842 | 8,843 | $1,415 | saves $201 |

Each total is heating + cooling + water heating + 5,079 kWh of other base load. For T1: 1,975 + 1,329 + 1,557 + 5,079 = 9,939 kWh (the parts are rounded, so a sum can be off by 1), and 9,939 × $0.16 = $1,590.

What the table shows:

- **Geothermal vs. air-source:** about $350 per year less with the wood stove ($1,590 − $1,240) and about $500 less without it ($1,915 − $1,415).
- **Keeping the wood stove at 50%:** about $325 per year less for air-source ($1,915 − $1,590) and about $174 less for geothermal ($1,415 − $1,240).
- **Desuperheater:** it cuts water heating electricity by about 714 kWh per year (1,557 − 842).
- **Today's wood use is higher than 50%.** The 50% share is my plan to burn less wood, which is why T1 saves so little against today.

## Limits of these numbers

- They are annual estimates built on the Assessment's modeled loads, not on measurements of this house.
- The efficiency ratings are reference values: 16 SEER2 / 8.1 HSPF2 is the low end of the Trane 17 series, and the geothermal figures are the part-load AHRI ground-loop rating. Your proposed equipment will change the results.
- Equipment and installation costs are left out on purpose.
