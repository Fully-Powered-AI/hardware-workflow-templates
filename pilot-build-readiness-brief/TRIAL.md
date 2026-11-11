# Pilot build readiness brief: trial on the invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the invented example in `public/example.md` (the six input files: build settings, planned bill of materials, drawing index, parts report, open actions and build checklist). No client data was used. The run was made by a model that did not write the template. It read the template and the example's inputs first, produced the brief, and only then compared it with the example's published output.

## What came out

Everything below was produced from the inputs before the published output was read.

**Pilot build readiness brief: Field logger, Pilot build 1, 6 units, build date Monday 23 November 2026**

- For: the build lead. Prepared Tuesday 10 November 2026 from: planned BOM (10 lines, exported 2026-11-09), drawing index (10 rows, exported 2026-11-06), parts report (9 rows, exported 2026-11-09), open actions (7 rows, exported 2026-11-10), build checklist (6 items), settings.
- Column check: all headers matched.
- Basis: need is quantity per unit x 6. Received means in hand; allocated means set aside in the planning system and is never counted as received. A part with no parts report row is Not reported, never zero. Only drawing status "Released" counts as released. Parts report age: 1 day (limit 3, the default, as none was given): current.
- Summary: 10 BOM lines. Received 6. Allocated, not all received 2. Short 1. Not reported 1. Drawing findings 3 lines. Received-revision findings 1 line. Open actions 6 (4 flagged). Checklist items 6.

Parts not yet in hand

- FL-500 Packaging tray, Supplier A: Not reported. Needs 6; no parts report row. Shortfall cannot be stated.
- FL-240 Antenna cable, Supplier B: Short. Needs 6; received 0; allocated 3; short by 6. On order 6, no date given; covers the shortfall. Supplier response: no response recorded.
- FL-210 Main board assembly, Supplier B: Allocated, not all received. Needs 6; received 4; allocated 6; short by 2. On order 2, promised 2026-11-20 (3 days before the build date); covers the shortfall. Supplier response: confirmed.
- FL-220 Sensor module, Supplier C: Allocated, not all received. Needs 12; received 5; allocated 12; short by 7. On order 10, promised 2026-11-25 (2 days after the build date); covers the shortfall. Supplier response: partial.

Revision conflicts

- FL-101 Enclosure lid: BOM revision B; drawing index revision C (DWG-1101, Released).
- FL-230 Battery pack: drawing DWG-1230 has status Draft; revision A in both the BOM and the drawing index.
- FL-400 Label set: received 6 at revision A; BOM revision B.
- FL-500 Packaging tray: no drawing row.
- Drawing index rows for parts not on the BOM: 1.

Open actions

- A-01 Confirm gasket compound change. Owner Engineer 1; engineering; due 2026-11-06; part FL-300; blocks the build: no. Overdue.
- A-03 Chase partial sensor delivery. Owner Buyer 1; sourcing; due 2026-11-12; part FL-220; blocks the build: yes.
- A-05 Agree label artwork. Owner not assigned; engineering; due 2026-11-16; part FL-400; blocks the build: not stated. No owner. Blocks the build not stated.
- A-02 Release battery pack drawing. Owner Engineer 2; engineering; due 2026-11-18; part FL-230; blocks the build: yes.
- A-04 Inspect first lot of main boards. Owner Quality engineer; quality; due 2026-11-24; part FL-210; blocks the build: yes. Due after the build date.
- A-07 Confirm antenna cable date with Supplier B. Owner Buyer 1; sourcing; no due date; part FL-240; blocks the build: yes. No due date.
- Closed actions: 1.

Against the build checklist

- C1 Every BOM part is in hand in the quantity the build needs (sourcing): Gaps shown: 4 (FL-210, FL-220, FL-240, FL-500).
- C2 Every part has a released drawing at the BOM revision (engineering): Gaps shown: 3 (FL-101, FL-230, FL-500).
- C3 Parts received are at the BOM revision (quality): Gaps shown: 1 (FL-400).
- C4 No open action blocks the build (build lead): Gaps shown: 5 (A-02, A-03, A-04, A-05, A-07).
- C5 Test fixture is calibrated and available (quality): Not evidenced in the files supplied.
- C6 Assembly partner has confirmed the build slot (build lead): Not evidenced in the files supplied.

Questions for the build lead

1. To sourcing: FL-500 Packaging tray needs 6 and has no row in the parts report. Is any in hand or on order?
2. To engineering: FL-500 has no drawing row, and a drawing row (FL-600) exists for a part not on the BOM. What drawing and revision apply to FL-500?
3. To sourcing: FL-240 Antenna cable needs 6; received 0, allocated 3, on order 6 with no promised date and no supplier response recorded. A-07 has no due date. What date has Supplier B given?
4. To sourcing: FL-220 Sensor module is short by 7; the 10 on order are promised for 2026-11-25, 2 days after the build date, and the response is partial. Can 7 be in hand by 2026-11-23?
5. To quality: A-04, the first-lot inspection for FL-210, is due 2026-11-24, one day after the build date. Is that date right for this build?
6. To engineering: FL-101 is revision B on the BOM and revision C on the drawing index; the received parts are revision B. Which revision does the build call for?
7. To engineering: FL-230's drawing is Draft, and A-02 to release it is due 2026-11-18. Will it be released before the build?
8. To quality: FL-400 Label set arrived at revision A; the BOM says B. Are the 6 received to be used?
9. To the build lead: A-05 has no owner and no blocking status, A-01 is overdue, A-07 has no due date. Who owns each, and does A-05 block the build?

Confirmations

- Sourcing, sourcing lead: items C1; gaps shown 4; not evidenced in the files none. Confirmed by: ______ Date: ______
- Engineering, engineering lead: items C2; gaps shown 3; not evidenced in the files none. Confirmed by: ______ Date: ______
- Quality, quality lead: items C3, C5; gaps shown 1; not evidenced in the files C5. Confirmed by: ______ Date: ______
- Build lead: items C4, C6; gaps shown 5; not evidenced in the files C6. Decision on the build: ______ Date: ______

Draft for the build lead. This brief authorizes no build, signs off no revision and judges no design. Nothing has been changed in any record and no supplier has been contacted. Figures are worked out from the files supplied, as of Tuesday 10 November 2026.

## What was observed

- **Every required part was produced:** header and basis lines, summary, the four working sections, checklist results, questions, confirmations and the closing line. Nothing in the inputs triggered a stop: all headers matched, no part number was repeated in the parts report, and no one asked for a ready verdict.
- **Figures matched the published example** on every count: line statuses, shortfalls, days against the build date, revision findings, the six open actions and four flags, and all six checklist results.
- **Differences from the published example** were in wording only. The example writes weekday dates ("Friday 20 November"); this run used the ISO dates from the files. The example adds "Received parts are revision B" to the FL-101 finding and "4 days overdue" to a question; this run left both out. The example's question wording differs, and it asks "Are the 6 received to be used or replaced?", where this run asked only whether they are to be used. This run added the FL-600 drawing row to question 2.
- **No fact appeared in either output that is not in the inputs.** The example's "4 days overdue" and "a day after the build date" are worked out from dates in the inputs.
- **Where the template left room to guess:**
  - The date style is not set. The format says "weekday date" in the header but gives no style for dates inside lines. This run mixed one weekday date in the header with ISO dates elsewhere.
  - The number of questions is not fixed. "One question for each finding a person has to settle" does not say whether two findings on one part (FL-500 has no parts row and no drawing row) are one question or two, or whether the same function's findings are grouped. The example and this run both split FL-500 by function but differ elsewhere.
  - The order of questions is not set beyond "stale report first".
  - Where a line is below Received, covers the shortfall, but arrives after the build date (FL-220), the template has no wording for it. This run and the example both print "covers the shortfall" and rely on the date line to show the lateness.
  - The "Revision conflicts" heading also holds the received-revision finding (FL-400) and the missing drawing row. The format shows only a general line for each finding, so this run chose its own wording.
  - The roles on the confirmations lines ("sourcing lead") come from the settings, but nothing says what to print if a settings role is missing.
- **A gap between the instruction block and the rest of the template.** The fenced instruction block says "use the output format exactly" but does not contain the format, and it leaves out several rules that sit only in the procedure: the stops for a repeated part number in the parts report or the bill of materials, for a units value that is not a whole number, and for a cut-off file; the "open actions not supplied" and "build checklist not supplied" fallbacks; counting actions linked to parts not on the bill of materials; the ordering of the parts and actions lists; and the confirmations step. A run given only the block would not know these. This run had the whole template.
- **Stale statements in the template.** The acceptance tests are headed "None has been run" and the version notes say "Not yet run on its example". The tests were not run in this trial. Only the one example was.
- **Nothing in the example exercised** the stale-report path, the repeated-part-number stops, a missing actions or checklist file, a changed header, or the decline of a request to say "ready". Those paths were not tried.
- **Limits.** This was one run of one model on one invented example. It shows the template can be followed to the example's figures. It does not show how it behaves on real exports, other products, or other AI products, and it is not a test for any client.

## Edits made after this run

The record above is unchanged. After the run, the pasted instructions, the output format and `public/example.md` were edited, so the example no longer matches this run's output in these places:

- The FL-220 line in the example now prints "covers the shortfall, but after the build date"; the run printed "covers the shortfall" (see the observation above about the missing wording).
- The date style, the order of the questions and the missing-role rules were set, and two example questions swapped places.
- A later round added a line for actions linked to a part not on the BOM ("none" in the example), a "Nothing on order." wording, line patterns for each kind of revision finding, the definitions of received, allocated and the supplier response words in the pasted block, and the rule for where a question about a part's open action goes. The context note "Received parts are revision B." was removed from the example's FL-101 finding, which brings it back in line with this run.

None of these edits has been run again. A second run on the edited template and example would be needed to show that it still produces the example.
