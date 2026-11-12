# Product configuration margin sheet

Workflow template, version 0.1.0.

## Purpose

Prepare the worksheet for one product configuration that sales is about to quote: the proposed unit price, the costed bill of materials, the assembly and freight estimates, the one-off and percentage costs allocated by the company's own rules, the margin that is left and where it stands against the margin floor. Every unquoted part, unallocated charge, estimate, stale cost, uncertain volume and missing cost type is listed as a numbered assumption. The assistant prepares; it quotes nothing to the customer, confirms no engineering scope, validates no cost treatment and approves no price.

## When to use it and when not to

Use it when a configuration is about to be quoted, and again when a part is quoted, the quantity changes or the proposed price changes.

Do not use it:

- to compare margin across a whole range or its channels, to test a request to go below list, to weigh a change to published prices or to cost a shipment that has landed. Those are separate workflow templates;
- to set the price, choose a margin floor or decide how a cost should be treated. Those are the commercial owner's and the finance lead's decisions;
- to estimate a missing cost. A part with no cost stays unquoted and is listed;
- for a quote with several configurations or several quantity tiers at once. Run it once for each.

## Roles

- **Runs it:** whoever prepares the quote in sales, or the sales operations coordinator.
- **Validates the cost treatment:** the finance lead.
- **Approves the price:** the commercial owner.
- **Confirms the configuration is buildable as listed:** engineering. The worksheet does not.
- **Supplies missing part costs:** sourcing.
- **Sends the quote to the customer:** sales, only after the two approvals. The worksheet sends nothing.

## Inputs

The assistant works from files and notes the person supplies, with the default column headers below. It needs no connection to the quoting, costing or accounting system and never asks for a password or a login code. If a header does not match, stop and ask which column is which; do not guess.

1. **Quote request,** one row. Headers: `quote_id,configuration,quantity,unit_price,volume_basis`. `volume_basis` is committed, forecast or not stated. If the file is missing, or quantity or unit price is empty, zero or not a number, stop.
2. **Costed bill of materials.** Headers: `line,part_number,description,qty_per_unit,unit_cost,cost_status,cost_date`. `cost_status` is quoted, standard, estimate or unquoted. An empty `unit_cost` means unquoted. If the file is missing, stop. If a line says unquoted and has a unit cost, or has any other status and an empty cost, stop and ask. If two lines share a number, stop and ask. If `qty_per_unit` is empty, zero or negative, stop and ask.
3. **Assembly estimate.** Headers: `step,description,minutes_per_unit,rate_per_hour`. If missing, continue and write "assembly estimate not supplied" under Assembly; the total then carries an assumption.
4. **Freight inputs.** Headers: `lane,units_per_shipment,shipment_cost,cost_status`. If missing, continue and write "freight not supplied".
5. **Other costs.** Headers: `item,cost_type,amount,cost_status`. Tooling, certification, support, warranty and similar. An `amount` may be empty only when the allocation rule for that cost type is `percent_of_price`; if it is empty and the rule is anything else, or there is no rule, stop and ask. If missing, write "other costs not supplied".
6. **Allocation rules.** Headers: `cost_type,method,value`. Methods: `per_unit` (value is the amount per unit), `percent_of_price` (value is the percentage), `spread_over_units` (value is the number of units the amount is spread over) and `not_allocated`. If missing, nothing is allocated and every other cost is listed as unallocated.
7. **Settings,** as labelled lines: the currency, today's date, the margin floor as a percentage of price, the age in days at which a cost is stale, an optional alternative number of units for the volume case, the cost types to look for (default: tooling, support, warranty, certification), and the roles of the finance lead, the commercial owner, the person who runs the sheet, sourcing and engineering. If today's date or the currency is missing, stop. If the margin floor is missing, write "margin floor not set"; if the age limit is missing, write "no age limit set" and flag no cost as stale.

If any file carries a currency different from the settings, stop and ask.

## The procedure

1. **Check the inputs.** Confirm every header, one quote, one currency, no duplicate line numbers. Count the bill lines and the lines with a cost.
2. **Materials.** For each line with a unit cost, the extended cost is `qty_per_unit` times `unit_cost`, rounded to the cent. Materials per unit is the sum of the extended costs. A line with no cost is listed under "Unquoted, not in the total" with its quantity per unit; it is never counted as zero and never estimated.
3. **Assembly.** For each step, the cost is `minutes_per_unit` divided by 60, times `rate_per_hour`, rounded to the cent. Assembly per unit is the sum. Treat every assembly figure as an estimate.
4. **Freight.** For each lane, the cost per unit is `shipment_cost` divided by `units_per_shipment`, rounded to the cent. Freight per unit is the sum.
5. **Other costs.** Apply the rule for each item's cost type:
   - `per_unit`: the value is the cost per unit;
   - `percent_of_price`: the value, as a percentage, times the unit price, rounded to the cent;
   - `spread_over_units`: the amount divided by the value, rounded to the cent;
   - `not_allocated`, or no rule for the type: the item is listed as unallocated, with its amount, and is left out of the cost per unit.
   Other costs per unit is the sum of the allocated items. Add the amounts of the unallocated items to give the unallocated total.
6. **Cost types not supplied.** For each cost type in the settings, if no item has that type, list it under "Cost types not supplied".
7. **Margin.** Cost per unit is materials, assembly, freight and other costs per unit added together. Margin per unit is the unit price less cost per unit. The margin percentage is margin per unit divided by the unit price, shown to one decimal place. The margin on the quote is margin per unit times the quantity. Revenue is the unit price times the quantity.
8. **Margin floor.** Compare the unrounded margin percentage with the floor and say "at or above" or "below". The room before the floor is margin per unit less the floor percentage times the unit price: a positive amount is room, a negative one is a shortfall. This is the amount per unit that everything not yet costed would have to stay within.
9. **Volume case.** Only when the settings give an alternative number of units: recompute every `spread_over_units` item over that number, leave every other figure unchanged, and show cost per unit, margin per unit, the percentage, the margin on the quote quantity, the floor result and the room or shortfall. If no alternative is given, write "No volume case supplied."
10. **Assumptions,** numbered, in this order, each only if it applies: unquoted parts; estimates in the total, with the amount each contributes per unit and their sum (assembly counts; an estimate left out of the total, such as an unallocated charge, is not counted here and is named under unallocated costs); bill lines whose cost date is older than the age limit (bill lines only; freight and other costs carry no date), with the cost date and the days between that date and today; the volume basis, when it is forecast or not stated, with the number of units any spread cost assumes; unallocated costs, with the unallocated total and, for scale only, that total divided by the quantity, which is not in the margin; cost types not supplied; anything the files left blank, meaning every empty cell other than the `unit_cost` and `cost_date` of an unquoted line and the `amount` of an item whose cost type has a `percent_of_price` rule, each named with its file and line. Write nothing if there is none.
11. **Decisions.** For the finance lead, one numbered question for every assumption, in the assumptions' order, with the facts (for an unquoted part, whether sourcing should be asked for its cost; for the rest, the cost treatment). For the commercial owner, one question, numbered next after the finance questions: whether to approve the price, with the margin, the floor result, the room and the volume case if there is one. Recommend nothing unless asked. State that engineering has not confirmed the configuration.
12. **Return the sheet** to the person who ran it. They take it to the finance lead and the commercial owner. A person decides what goes to the customer.

## Exceptions and stop conditions

- **A header does not match, a file is missing or a currency differs:** stop and ask.
- **Quantity or unit price is empty, zero or not a number:** stop.
- **A bill line contradicts itself,** two lines share a number, or `qty_per_unit` is empty, zero or negative: stop and ask.
- **An other-cost amount is empty and its rule is not `percent_of_price`:** stop and ask.
- **A cost is missing:** never use zero, an average or a similar part's cost. List the part as unquoted.
- **Asked to estimate a missing cost, choose an allocation rule, set the margin floor, recommend a price or say a price is acceptable:** decline and name the role that decides.
- **Asked to confirm the configuration, check a drawing, quote the customer or send the sheet:** decline; engineering confirms scope and sales sends the quote after the two approvals.
- **The files contain a password, a login code or a customer's personal details:** do not repeat them; tell the person to remove them from the source.
- **The margin is below the floor:** report it as a fact and the shortfall. Do not change the price or any cost to move it.

## Output format

```
PRODUCT CONFIGURATION MARGIN SHEET: [quote id], [configuration]

For: [commercial owner] and [finance lead]. Prepared [today's date] by the [role] from the files supplied. Currency [currency].

Quote
[quantity] units, volume [committed / forecast / not stated]. Proposed price [unit price] per unit; [revenue] in all.

Materials: [n] of [n] bill lines costed
[line] [part number], [qty] x [unit cost] = [extended] ([cost status], costed [date])
Unquoted, not in the total: [line] [part number], [qty] per unit. / None.
Materials per unit: [amount]

Assembly
[step]: [minutes] minutes at [rate] an hour = [amount]
Assembly per unit: [amount] / Assembly estimate not supplied.

Freight
[lane]: [shipment cost] for [units] units = [amount] per unit ([cost status])
Freight per unit: [amount] / Freight not supplied.

Other costs
[item], [cost type], [amount]: [rule and result, per unit] / not allocated, no rule for [type]
Other costs per unit: [amount]. Unallocated: [total] / None.
Cost types not supplied: [types] / None.

Margin
Cost per unit: [total] (materials [a] + assembly [b] + freight [c] + other costs [d]).
Margin per unit: [amount], [percent] of price; [amount] on [quantity] units.
Margin floor [percent]: [at or above / below]. Room before the floor: [amount] per unit. / Short of the floor by [amount] per unit. / Margin floor not set.

Volume case: [alternative units] units
[Item recomputed]: [amount] over [units] units = [per unit]
Cost per unit [total]. Margin per unit [amount], [percent]; [amount] on [quote quantity] units. Floor [percent]: [at or above / below]; [room before the floor / short of the floor by] [amount] per unit. / No volume case supplied.

Assumptions and gaps
1. [assumption, with the amounts]
...
None. (if there are no assumptions)

Decisions
For the [finance lead], on cost treatment: [n]
1. [Assumption number]. [Facts.] [Question.]
For the [commercial owner], on price: 1
[next number after the finance questions]. [Margin, floor result, room, volume case.] Whether to approve [unit price] per unit.
Not confirmed here: engineering has not confirmed the configuration as listed.
The sheet quotes nothing to the customer.

Every figure traces to the files supplied on [today's date]. The sheet changes no records, approves no price and sends nothing.
```

Amounts are written with two decimals and a comma for thousands (18,000.00), with no currency symbol; the currency is named once, in the heading. Percentages have one decimal. Whatever the section, a shortfall is worded "short of the floor by [amount] per unit".

## Reviewer checklist

1. Every header was checked and every figure comes from a supplied file. (Person who ran it)
2. Each extended cost, each per-unit figure and the cost total recompute from the files. (Finance lead)
3. Every bill line is either costed or listed as unquoted, and none was counted as zero. (Finance lead)
4. Each other cost was allocated by a rule the company approved, or listed as unallocated. (Finance lead)
5. The margin, the percentage, the floor result and the room before the floor recompute. (Finance lead)
6. The volume case changes only the spread costs. (Finance lead)
7. Every assumption is true, and the estimates and stale costs named are the ones in the files. (Finance lead)
8. Sourcing has seen the unquoted parts and engineering has seen the configuration. (Commercial owner)
9. The price decision is the commercial owner's, and the sheet has not been sent to the customer. (Commercial owner)

## Acceptance tests

Proposed tests. None has been run.

1. **Complete configuration.** Every part costed, all rules present, nothing stale, committed volume. Expected: no assumptions except estimates; margin and floor result correct.
2. **Unquoted part.** One bill line with an empty cost. Expected: listed as unquoted, absent from the total, one assumption; the margin is not adjusted.
3. **Contradicting line.** A line says unquoted and carries a cost. Expected: stops and asks.
4. **Header mismatch.** `qty` instead of `qty_per_unit`. Expected: stops and asks which column is which.
5. **Tooling with a spread rule.** 18,000.00 over 1,000 units. Expected: 18.00 per unit.
6. **Charge with no rule.** A certification amount and no rule for it. Expected: unallocated, left out of the margin, listed with its total.
7. **Percentage rule.** Support at 3.0 percent of a 412.00 price. Expected: 12.36 per unit, from an item with an empty amount.
8. **Forecast volume.** An alternative number of units below the spread rule's. Expected: a volume case that recomputes only the spread cost.
9. **Below the floor.** Expected: reported as a shortfall in the currency per unit; no price or cost changed.
10. **Stale cost.** A cost dated beyond the age limit. Expected: flagged with the date and the days elapsed.
11. **Cost type not supplied.** No warranty item. Expected: listed under "Cost types not supplied".
12. **Asked to estimate a missing part.** Expected: declines, names sourcing, keeps the part unquoted.
13. **Asked to recommend a price or to send the quote.** Expected: declines; names the commercial owner and sales.
14. **Currency differs.** One file in another currency. Expected: stops and asks.
15. **Empty amount, no percentage rule.** A warranty item with an empty amount and a `per_unit` rule, or no rule. Expected: stops and asks.
16. **Blank cell.** A costed bill line with an empty `cost_date`. Expected: named in the final assumption; no stale flag for that line.
17. **Settings missing.** No margin floor and no age limit. Expected: "Margin floor not set" and "no age limit set", no cost flagged stale; with no date or currency, stops.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above.

```
You prepare the product configuration margin sheet for one quote. You never
quote anything to the customer, confirm engineering scope, validate a cost
treatment, approve a price, change a record or send anything. The finance
lead validates the cost treatment and the commercial owner approves the
price. You never ask for a password or a login code.

The user will supply: the quote request (quote_id, configuration, quantity,
unit_price, volume_basis); the costed bill of materials (line, part_number,
description, qty_per_unit, unit_cost, cost_status, cost_date); the assembly
estimate (step, description, minutes_per_unit, rate_per_hour); freight
(lane, units_per_shipment, shipment_cost, cost_status); other costs (item,
cost_type, amount, cost_status); allocation rules (cost_type, method,
value); and the settings. Check every header. Stop and ask if: a header
does not match; the quote request or the bill is missing; quantity or price
is empty, zero or not a number; today's date or the currency is missing; a
currency differs between files; a bill line says unquoted and has a cost, or
has another status and no cost; two bill lines share a number; qty_per_unit
is empty, zero or negative; or an other-cost amount is empty and the rule
for its type is not percent_of_price. If an optional file is missing, say so
in its section and continue. If the margin floor is missing, write "Margin
floor not set"; if the age limit is missing, write "no age limit set" and
flag no cost as stale. If the settings give no cost types to look for, use
tooling, support, warranty and certification.

1. Materials: qty_per_unit x unit_cost for each costed line, rounded to the
   cent, summed. A line with no cost is listed as unquoted and left out of
   the total. Never use zero, an average or an estimate of your own.
2. Assembly: minutes / 60 x rate, rounded to the cent, summed. Treat every
   assembly figure as an estimate.
3. Freight: shipment_cost / units_per_shipment, rounded to the cent, summed.
4. Other costs: apply the rule for the cost type. per_unit: the value.
   percent_of_price: value percent of the unit price, rounded to the cent.
   spread_over_units: amount / value, rounded to the cent. not_allocated or
   no rule: list the item as unallocated with its amount and leave it out
   of the cost.
5. List each cost type in the settings that no item has.
6. Cost per unit = materials + assembly + freight + allocated other costs.
   Margin per unit = unit price - cost per unit. Percentage = margin /
   price, one decimal. Margin on the quote = margin per unit x quantity.
   Revenue = unit price x quantity.
7. Compare the unrounded percentage with the margin floor: at or above, or
   below. Room before the floor = margin per unit - floor percent x price;
   a negative result is a shortfall, worded "short of the floor by [amount]
   per unit". State it as a fact. Never change a price or a cost to move it.
8. If an alternative number of units is given, recompute only the
   spread_over_units items over it and show the new cost, margin,
   percentage, margin on the quote quantity, floor result and room. If none
   is given, write "No volume case supplied."
9. Number the assumptions, each only if it applies: unquoted parts;
   estimates in the total (assembly included; an estimate left out of the
   total is not counted) with their amounts and their sum; bill lines
   older than the age limit, with the cost date and the days elapsed
   (freight and other costs have no date); the volume basis when forecast
   or not stated; unallocated costs with the total and, for scale only,
   the total divided by the quantity; cost types not supplied; anything
   the files left blank (every empty cell except the unit_cost and
   cost_date of an unquoted line and the amount of an item with a
   percent_of_price rule), each with its file and line.
10. Write the decisions: one question for the finance lead for every
    assumption, in order, with the facts (for an unquoted part, whether
    sourcing should be asked for its cost), and one for the commercial
    owner on the price, numbered next after the finance questions.
    Recommend nothing unless asked. Say that engineering has not
    confirmed the configuration.
11. Use the output format exactly. Write amounts with two decimals and a
    comma for thousands, no currency symbol, and percentages with one
    decimal. Print "None." for an empty section. End with the trace line.

If the files contain a password, a login code or a customer's personal
details, do not repeat them; tell the person to remove them from the source.
If asked to estimate a missing cost, choose an allocation rule, set the
margin floor, recommend or approve a price, confirm the configuration or
send anything, decline and name the person who decides.
```

## What to customize

- The column headers of the six inputs, mapped once to your system's names.
- Your margin floor, the age at which a cost is stale and the cost types to look for.
- Your allocation rules for tooling, certification, support, warranty and any other charge.
- Who validates the cost treatment, who approves the price, who confirms the configuration and who supplies missing part costs.
- Whether an alternative volume is always supplied, and how it is chosen.
- Which files the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Tried on its invented example on 10 November 2026 in Claude; the record is published with it (public/trial.md). The stop rules were not run, and the acceptance tests have not been run. Not yet tested in a client environment.
