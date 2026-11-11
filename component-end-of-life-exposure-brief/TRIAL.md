# Trial record: Component end-of-life exposure brief, run once on its invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the invented example in `public/example.md` (Company M, Supplier A, notice SA-LC-2611-07: the settings, the notice, the part list, the where-used export, the inventory export, the demand plan, the alternates list and the availability notes), unchanged from the earlier run. No client data was used.

This is a second run, made on the current `member/template.md` (instruction block and output format) after a review's minor points were applied. It replaces the record of the first run, which had been made on the earlier files. It was not a fresh conversation in a chat product: the template text was read as a file and followed from it. The run was made by the same session that had just edited the template and the example, so it had read the example's published brief before writing its own; it is therefore a weaker test of independence than the first run, and it checks that the edited instructions still lead to a complete, correct brief, not that a stranger would reach it unaided.

## What came out

The full brief, as produced:

```
COMPONENT END-OF-LIFE EXPOSURE BRIEF: SA-LC-2611-07, Supplier A

For: sourcing lead. Prepared Tuesday 10 November 2026 from the notice, the part list, the where-used export, the inventory export (as of 9 November 2026), the demand plan, the alternates list and the availability notes.

Inputs checked: notice received Monday 9 November 2026; 3 parts in the notice, 2 matched to the part list, 1 not matched; where-used 5 rows, 4 assemblies; inventory 7 rows; demand plan 18 rows, 6 monthly periods (2026-11 to 2027-04), 3 assemblies; alternates 2 rows; availability notes 2 rows. Reserved stock is subtracted. Days are calendar days from 10 November 2026.

1. WHAT THE NOTICE SAYS
N1. RG3305-T (CM-1042): end of life. Last-time buy order by Friday 15 January 2027 (66 days). Last shipment Friday 30 April 2027 (171 days). Other: not stated. Replacement named: RG3305-U.
N2. SN-T20-R (CM-2217): constraint. Last-time buy: not stated. Last shipment: not stated. Other: lead time rises from 14 to 40 weeks for orders placed from 1 January 2027 (52 days away); supply is allocated by each customer's 2026 order history. Order placed on 1 January 2027 at 40 weeks would arrive Friday 8 October 2027. Replacement named: none.
N3. CN-88 (no part of ours matched): end of life. Last-time buy order by Wednesday 31 March 2027 (141 days). Last shipment Wednesday 30 June 2027 (232 days). Other: not stated. Replacement named: none. See G1.
Conditions stated: last-time buy orders cannot be cancelled.

2. WHERE EACH PART IS USED
P1. CM-1042, 3.3 V regulator (RG3305-T). Our lifecycle record: active. Used in 3 assemblies: AQ-100 Air monitor main board, 1 each; AQ-150 Legacy monitor board, 1 each; AQ-200 Room hub board, 2 each.
P2. CM-2217, Temperature sensor (SN-T20-R). Our lifecycle record: not recorded. Used in 2 assemblies: AQ-100 Air monitor main board, 1 each; AQ-300 Outdoor probe board, 2 each.

3. APPROVED SUPPLY AGAINST DEMAND
P1. CM-1042.
  Supply: on hand 3,500 (Main stores 2,600; Contract manufacturer 900); reserved 300; available 3,200; confirmed on order 1,500 (PO-5521, due Friday 4 December 2026). Approved supply 4,700.
  Requirement by month: 2026-11 700 · 2026-12 700 · 2027-01 900 · 2027-02 900 · 2027-03 1,000 · 2027-04 1,100. Total 5,300 (AQ-100 3,000; AQ-200 2,300; AQ-150 no demand rows, see G4).
  Cumulative requirement: 700 · 1,400 · 2,300 · 3,200 · 4,200 · 5,300.
  Approved supply covers the requirement through 2027-03 (4,200). It is short from 2027-04: 5,300 cumulative against 4,700, and a gap of at least 600 at the end of the demand plan.
  Dates: last-time buy order by 15 January 2027 (66 days); last shipment 30 April 2027 (171 days).
P2. CM-2217.
  Supply: on hand 2,200 (Main stores 1,800; Contract manufacturer 400); reserved 0; available 2,200; confirmed on order none. Approved supply 2,200.
  Requirement by month: 2026-11 600 · 2026-12 600 · 2027-01 740 · 2027-02 740 · 2027-03 900 · 2027-04 900. Total 4,480 (AQ-100 3,000; AQ-300 1,480).
  Cumulative requirement: 600 · 1,200 · 1,940 · 2,680 · 3,580 · 4,480.
  Approved supply covers the requirement through 2027-01 (1,940). It is short from 2027-02: 2,680 cumulative against 2,200, and a gap of 2,280 at the end of the demand plan.
  Dates: constraint begins 1 January 2027 (52 days).

4. NOT IN APPROVED SUPPLY
U1. P1, replacement named by Supplier A: RG3305-U. It is not on the alternates list; no approval, no stock record. Not counted.
U2. P1, alternate CM-1042-B: under evaluation; no approver or reference recorded; no stock record. Not counted.
U3. P2, open order PO-5530: 1,200 on order, no due date. Not counted until a due date is confirmed.
U4. P1, availability note, buyer, 9 November 2026: Distributor C "hold 'a few thousand' RG3305-T" by phone. Quantity not stated. Unverified. Not counted.
U5. P2, availability note, buyer, 6 November 2026: Distributor D, 800 pieces available, price on request, by email. Unverified. Not counted.
U6. P2, approved alternate CM-2217-ALT: 300 on hand, approved by the component engineer under ECN-0861 for AQ-100 only. Shown apart, not subtracted from the gap: the gap includes AQ-300, which the approval does not cover.

5. QUESTIONS ON REPLACEMENTS
Q1. For component engineering, P1, U2: when is the evaluation of CM-1042-B expected to conclude, and for which assemblies?
Q2. For component engineering, P1, U1: is RG3305-U, named by Supplier A, to be evaluated, and by whom?
Q3. For component engineering, P1: no approved alternate is recorded for CM-1042 in AQ-100; what is the plan for that assembly?
Q4. For component engineering, P1, G4: no approved alternate is recorded for CM-1042 in AQ-150; what is the plan for that assembly?
Q5. For component engineering, P1: no approved alternate is recorded for CM-1042 in AQ-200; what is the plan for that assembly?
Q6. For component engineering, P2, U6: does the approval of CM-2217-ALT extend to AQ-300, whose requirement is 1,480 over the plan?
Q7. For sourcing, P2, U3: what due date is confirmed for PO-5530?
Q8. For sourcing, P1 and P2, U4 and U5: who confirms the quantity and price in the two distributor notes? This brief contacts no one.
Q9. For program management, P1, G4: is AQ-150 still being built, and in what quantities?
Q10. For component engineering, N3, G1: which of our part numbers does CN-88 correspond to?

6. GAPS IN THE RECORDS
G1. CN-88 is in the notice (N3) and not in the affected part list. No where-used, stock or demand work has been done for it.
G2. CM-1042 is recorded as active; the notice says end of life (N1). The record is for component engineering to update; this brief changes nothing.
G3. CM-2217 has no lifecycle status recorded.
G4. AQ-150 uses CM-1042, 1 per assembly, and has no demand rows. Its requirement is not computed, so the CM-1042 requirement of 5,300 and the gap of 600 are minimums.
G5. The demand plan ends at 2027-04. Nothing is known about requirement after that month.
G6. The notice gives no last-time buy date and no last shipment date for SN-T20-R (N2), so the last date to buy or receive CM-2217 is not known.

7. FOR SOURCING
Open: 2 of 2 matched parts are short on approved supply (P1 from 2027-04, P2 from 2027-02); notice parts unmatched: 1; 10 questions; 6 gaps.
Decisions for sourcing:
1. P1: whether to propose a last-time buy by 15 January 2027 (66 days), with the gap of at least 600, the alternate still under evaluation and the notice's statement that such orders cannot be cancelled.
2. P2: whether to propose purchases before 1 January 2027 (52 days), with the gap of 2,280 from 2027-02 and the open order PO-5530 without a due date.
3. N3: whether CN-88 joins this review once component engineering has matched it (last-time buy in 141 days).
Options, none recommended: (a) take the questions and gaps to component engineering and program management as they stand; (b) wait for the answers to Q1 to Q7 before deciding; (c) ask the supplier to confirm the facts listed as not stated or undated: the last-time buy and last shipment dates for SN-T20-R (G6) and the due date of PO-5530; (d) prepare purchase proposals for the sourcing lead's own review.

This brief reads the notice against the records supplied. It qualifies no alternative, approves no design change, orders nothing, contacts no one and changes no record. The sourcing lead decides what to propose, and nothing has been sent or changed.
```

## What was observed

- **Every required part was produced.** Sections 1 to 7, the inputs line and the closing line came out. Nothing in the inputs triggered a stop: all labels and headers matched, the last-time buy dates were not later than the last shipment dates, no stock was negative, no where-used rows repeated, the demand months were consecutive, today's date and the stock export date were given, and the alternates list and availability notes were supplied.
- **Figures recomputed by hand from the inputs.** Supply 4,700 (3,500 on hand less 300 reserved plus 1,500 on PO-5521 due 4 December 2026) and 2,200; monthly requirements 700, 700, 900, 900, 1,000, 1,100 and 600, 600, 740, 740, 900, 900; totals 5,300 and 4,480; short from 2027-04 and 2027-02; gaps of at least 600 and 2,280; day counts 66, 171, 141, 232 and 52, and the arrival date of 8 October 2027 (1 January 2027 plus 40 weeks). All agree with the brief.
- **Order references.** The references PO-5521 and PO-5530 were read from the `location` column, as the template now says, since the inventory export has no order-reference column.
- **Constraint date.** The date SN-T20-R's constraint begins, 1 January 2027, was read from the other statement, as the template now says; the notice line has no field for it.
- **Questions.** Q3 to Q5 came from the rule to write one question for each assembly that no approved alternate covers (AQ-100, AQ-150 and AQ-200 for CM-1042); Q6 covers AQ-300 for CM-2217, whose approved alternate is approved for AQ-100 only. The count is ten.
- **Gaps.** The unmatched notice part, the two lifecycle records, the assembly with no demand rows, the end of the demand plan and the undated SN-T20-R fields were listed. No listed part was missing from the notice, so that gap kind did not arise. The order in which the end of the demand plan and the undated notice fields are numbered (G5, G6) differs from the order in which step 9 lists the kinds; the template does not require the order.
- **Options line.** Options (b) and (c) follow the format's fixed text, with the Q range and the facts filled in.
- **Reviewer checklist:** all eight items were checked against this brief and each holds.
- **Facts not in the inputs.** None was added.
- **Cases not exercised.** The conditions added to the instruction block (a missing date setting, "alternates list not supplied", an approved row with no approver or reference, "order reference not recorded", a listed part not in the notice) did not arise in this example, so they were read but not exercised. None of the acceptance tests other than the normal notice was run.
- **Limits of this trial.** One run, one product, one invented example, by the session that had edited the files. It shows the edited instructions can be followed to a complete, correct brief on this example. It does not show how the template performs with a real notice, real exports with messy headers, or in a chat product with pasted text.

## Earlier run

A first run was made on the earlier template and example, before an independent review. It produced a complete brief with the same figures, and showed several wordings that the template then changed (a lead-time rule, a whole-month rule, a single statement of conditions, "Last-time buy: not stated", the Dates line and numbering gaps before questions). It is superseded by this record, which describes the current files.
