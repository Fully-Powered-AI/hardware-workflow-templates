# Product configuration margin sheet: tried on its invented example

- **Product:** Claude, run in Claude Code

Model: Claude Sonnet 5.5 (model ID claude-sonnet-5-5), run as a coding agent in a terminal session. Date: 2026-11-10.

This is the second run, of the revised version. The first run found defects that were then fixed (see the end of this record); the first run's output is not reproduced here because the revision replaces it.

The inputs are the invented example in [example.md](example.md): the made-up company Alder Fen Devices and its made-up quote Q-2611. No client data was used. The instructions followed were the fenced block and the output format in the revised member template. The inputs used were the quote request, the eight-line bill of materials, the assembly estimate, the freight input, the three other costs, the two allocation rules and the settings, all as written in the example.

One thing to know before reading the result: this was not a blind run. I had read the example, including its published output, before the run, and I wrote the template revision and the example's wording myself. I worked each figure from the inputs and the revised instruction block, and I checked the result against the example afterwards. Treat the match as a check that the revised block is followable and the arithmetic consistent, not as proof that someone seeing the inputs cold would get the same answer.

## What came out

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

## What was observed

- **Every required part was produced,** in the order the format gives, and the trace line closes it. Nothing in the inputs triggered a stop condition: headers matched, one quote, one currency, no duplicate lines, no contradicting line, no empty quantity.
- **Difference from the published example.** None: the sheet is the same as the example's output, line for line. The figures, assumptions and decisions follow from the inputs and the block alone, which the first run could not show, because the first block lacked the rule that assembly is an estimate and the final assumption.
- **The settings stops and defaults** (today's date and currency present; margin floor and age limit present; cost types supplied) were not exercised, because the example supplies every setting.
- **Blanks.** The empty `unit_cost` and `cost_date` on the unquoted line and the empty support `amount` under a percent_of_price rule are excluded by the block's definition, so there is no final assumption about blanks. That was the intended reading.
- **Estimates in the total** counted the antenna, freight and assembly (69.30) and not the certification estimate, which is outside the total and appears under unallocated costs, as the block says.
- **Stale costs** were checked on bill lines only; one was found (PS-12, 253 days).
- **Facts not in the inputs.** None beyond the arithmetic, the 253-day count (2026-03-02 to 2026-11-10) and the 16.25 scale figure, all derived from the inputs.
- **Nothing was recommended.** Whether to approve the price was left to the commercial owner.

What this run did not cover: the stop rules (a header that does not match, a bill line that contradicts itself, two lines with the same number, an empty or negative quantity per unit, an empty amount with no percentage rule, a differing currency, a missing file, a missing date or currency) were not run, nor were the missing-floor and missing-age-limit defaults, a password in the files, or the requests the template declines. The acceptance tests in the template were not run.

## What the first run found, and what changed

The first run listed defects in the template, all now addressed: the instruction block was shorter than the procedure (missing the settings stops and defaults, the default cost types, the duplicate-line and quantity stops, the assembly-is-an-estimate rule, the rule not to repeat passwords or personal details, and the blanks assumption); the version note said the template had not been tried; the shortfall was worded two ways; the commercial owner's question number was not explained; stale costs, estimates not in the total, finance questions, rounding of percentage results and thousands separators were undefined; and the sheet's "Prepared by" line lacked an article. The revision defines each.

The trial covers one run on one invented example. It does not show how the template performs on a real company's files.
