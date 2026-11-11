# Product configuration margin sheet: an invented example

*Illustrative example with invented data.* The company, the product, the parts, the costs, the rules and the roles below are made up. The company is Alder Fen Devices, an invented maker of field gateways; Q-2611 is an invented quote. Today's date is 2026-11-10 and the currency is dollars. The sheet is run by the sales operations coordinator for the commercial owner and the finance lead.

## What the sales operations coordinator supplies

Quote request:

```
quote_id,configuration,quantity,unit_price,volume_basis
Q-2611,Field gateway kit with 4G module and outdoor enclosure,400,412.00,forecast
```

Costed bill of materials:

```
line,part_number,description,qty_per_unit,unit_cost,cost_status,cost_date
1,GW-100,Main board,1,86.40,standard,2026-09-30
2,CM-4G,Cellular module,1,31.75,quoted,2026-10-20
3,EN-OUT,Outdoor enclosure,1,24.60,quoted,2026-10-12
4,PS-12,Power supply,1,9.85,standard,2026-03-02
5,AN-4G,Antenna,2,4.30,estimate,2026-10-28
6,CB-HRN,Wiring harness,1,,unquoted,
7,SC-M3,Screw kit,1,1.20,standard,2026-09-30
8,LB-GW,Product label,1,0.35,standard,2026-09-30
```

Assembly estimate:

```
step,description,minutes_per_unit,rate_per_hour
A1,Board test and flash,12,54.00
A2,Enclosure fit and wiring,25,54.00
A3,Final test and pack,18,48.00
```

Freight inputs:

```
lane,units_per_shipment,shipment_cost,cost_status
Plant to customer by pallet,40,520.00,estimate
```

Other costs:

```
item,cost_type,amount,cost_status
Enclosure insert mould,tooling,18000.00,quoted
Radio certification for the 4G variant,certification,6500.00,estimate
Support allowance,support,,standard
```

Allocation rules:

```
cost_type,method,value
tooling,spread_over_units,1000
support,percent_of_price,3.0
```

Settings:

```
Currency: dollars
Today: 2026-11-10
Margin floor: 35 percent of price
Cost age limit: 180 days
Alternative units for the volume case: 400
Cost types to look for: tooling, support, warranty, certification
Finance lead: finance lead. Commercial owner: commercial owner. Run by: sales operations coordinator.
Sourcing: sourcing lead. Engineering: engineering lead.
```

The alternative of 400 units is the quote quantity on purpose. The volume case reprices the tooling at the volume actually quoted, instead of the 1,000 units the rule assumes, and leaves every other figure alone.

## What comes out

```
PRODUCT CONFIGURATION MARGIN SHEET: Q-2611, Field gateway kit with 4G module and outdoor enclosure

For: commercial owner and finance lead. Prepared 2026-11-10 by the sales operations coordinator from the files supplied. Currency dollars.

Quote
400 units, volume forecast. Proposed price 412.00 per unit; 164,800.00 in all.

Materials: 7 of 8 bill lines costed
1 GW-100, 1 x 86.40 = 86.40 (standard, costed 2026-09-30)
2 CM-4G, 1 x 31.75 = 31.75 (quoted, costed 2026-10-20)
3 EN-OUT, 1 x 24.60 = 24.60 (quoted, costed 2026-10-12)
4 PS-12, 1 x 9.85 = 9.85 (standard, costed 2026-03-02)
5 AN-4G, 2 x 4.30 = 8.60 (estimate, costed 2026-10-28)
7 SC-M3, 1 x 1.20 = 1.20 (standard, costed 2026-09-30)
8 LB-GW, 1 x 0.35 = 0.35 (standard, costed 2026-09-30)
Unquoted, not in the total: 6 CB-HRN, 1 per unit.
Materials per unit: 162.75

Assembly
A1: 12 minutes at 54.00 an hour = 10.80
A2: 25 minutes at 54.00 an hour = 22.50
A3: 18 minutes at 48.00 an hour = 14.40
Assembly per unit: 47.70

Freight
Plant to customer by pallet: 520.00 for 40 units = 13.00 per unit (estimate)
Freight per unit: 13.00

Other costs
Enclosure insert mould, tooling, 18,000.00: spread over 1,000 units = 18.00 per unit
Radio certification for the 4G variant, certification, 6,500.00: not allocated, no rule for certification
Support allowance, support: 3.0 percent of price = 12.36 per unit
Other costs per unit: 30.36. Unallocated: 6,500.00
Cost types not supplied: warranty

Margin
Cost per unit: 253.81 (materials 162.75 + assembly 47.70 + freight 13.00 + other costs 30.36).
Margin per unit: 158.19, 38.4 percent of price; 63,276.00 on 400 units.
Margin floor 35 percent: at or above. Room before the floor: 13.99 per unit.

Volume case: 400 units
Enclosure insert mould: 18,000.00 over 400 units = 45.00 per unit
Cost per unit 280.81. Margin per unit 131.19, 31.8 percent; 52,476.00 on 400 units. Floor 35 percent: below; short of the floor by 13.01 per unit.

Assumptions and gaps
1. Unquoted part: line 6 CB-HRN, wiring harness, 1 per unit, has no cost. The margin above leaves it out.
2. Estimates in the total: line 5 AN-4G 8.60 per unit, freight 13.00 per unit and the assembly estimate 47.70 per unit; 69.30 per unit in all.
3. Stale cost: line 4 PS-12, costed 2026-03-02, 253 days before today; the limit is 180 days.
4. Volume: forecast. The tooling rule spreads 18,000.00 over 1,000 units; the quote is for 400.
5. Unallocated: radio certification, 6,500.00, estimate, with no rule. It is not in the margin; for scale only, 16.25 per unit at 400 units.
6. Cost type not supplied: warranty.

Decisions
For the finance lead, on cost treatment: 6
1. Assumption 1. The wiring harness has no cost, and the room before the floor is 13.99 per unit. Whether sourcing should be asked for its cost before the price is decided.
2. Assumption 2. Estimates make up 69.30 of the 253.81 cost per unit. Whether estimates belong in the total for this quote.
3. Assumption 3. The PS-12 standard cost is 253 days old against a 180-day limit. Whether the standard cost still holds.
4. Assumption 4. The tooling rule spreads over 1,000 units and the forecast is 400. At 400 the spread is 45.00 per unit and the margin is 31.8 percent. Whether the rule applies at this volume.
5. Assumption 5. Certification, 6,500.00, has no rule and is outside the margin. At 400 units it would be 16.25 per unit, more than the 13.99 of room. Which rule applies to certification.
6. Assumption 6. No warranty cost was supplied. Whether warranty is nil for this configuration or missing.
For the commercial owner, on price: 1
7. Margin 38.4 percent against a 35 percent floor, with 13.99 per unit of room; 31.8 percent and 13.01 per unit short in the volume case. Whether to approve 412.00 per unit.
Not confirmed here: engineering has not confirmed the configuration as listed.
The sheet quotes nothing to the customer.

Every figure traces to the files supplied on 2026-11-10. The sheet changes no records, approves no price and sends nothing.
```

## How the figures were reached

Seven bill lines have a cost; line 6 has none and is left out, not counted as zero. The extended costs are 86.40, 31.75, 24.60, 9.85, 8.60 (2 x 4.30), 1.20 and 0.35, which add to 162.75. Assembly is 12/60 x 54.00 = 10.80, 25/60 x 54.00 = 22.50 and 18/60 x 48.00 = 14.40, which add to 47.70. Freight is 520.00 / 40 = 13.00. Tooling is 18,000.00 / 1,000 = 18.00; support is 3.0 percent of 412.00 = 12.36; they add to 30.36. Certification has no rule, so 6,500.00 stays out. Cost per unit is 162.75 + 47.70 + 13.00 + 30.36 = 253.81, and the margin is 412.00 - 253.81 = 158.19, which is 38.4 percent of 412.00. On 400 units that is 63,276.00, and revenue is 164,800.00. The floor is 35 percent of 412.00 = 144.20, so the room is 158.19 - 144.20 = 13.99. In the volume case tooling is 18,000.00 / 400 = 45.00, so the cost is 253.81 + 27.00 = 280.81, the margin is 131.19, which is 31.8 percent and 52,476.00 on 400 units, and the shortfall is 144.20 - 131.19 = 13.01. Estimates are 8.60 + 13.00 + 47.70 = 69.30. PS-12's cost date to today is 253 days. Certification at 400 units is 6,500.00 / 400 = 16.25.
