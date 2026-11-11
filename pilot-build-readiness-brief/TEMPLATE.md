# Pilot build readiness brief

Capability template, version 0.1.0.

## Purpose

Prepare the brief the build lead reads before a prototype or pilot build: which parts are not yet in hand and by how much, where the bill of materials, the drawing index and the received parts disagree about a revision, which open actions could stop the build, and what the files show against each item of the team's own build checklist. Allocated parts are always kept apart from received parts. Every statement traces to a row in a supplied file. The assistant prepares; it never authorizes a build, marks anything ready, signs off a revision, judges a design, approves a substitute part, chases a supplier or changes a record. Engineering, quality and sourcing confirm, and the build lead decides.

## When to use it and when not to

Use it once the build date and quantity are set, again after each new parts report, and a few days before the build meeting.

Do not use it:

- to release orders to a production floor against approved drawings. That is the job readiness packet;
- to rebuild a schedule when orders or capacity change. That is the production schedule rebuild;
- to work out how many sellable sets the stock supports. That is the kit component availability check;
- to decide whether a design is good enough, whether a revision is acceptable or whether a substitute part will do. Those are engineering and quality decisions;
- to count parts nobody has counted. It works only from the figures supplied.

## Roles

- **Runs it:** the build lead, or the program manager who runs the build.
- **Confirms the parts position:** sourcing.
- **Confirms drawings and revisions:** engineering.
- **Confirms that what arrived is what the build calls for:** quality.
- **Decides whether the build goes ahead:** the build lead, after the three confirmations. Always a person.
- **Owns each open action:** the person named on the actions list.

## Inputs

The assistant works from files and notes the person supplies. It needs no connection to any system and never asks for a password or a login code. Every file is a table with a header row. The default headers are below; set your own once under "What to customize". If a header differs, stop and ask.

1. **Build settings,** typed by the build lead: product, build name, units to build, build date, today's date, the export date of each file, the stale limit in days (default 3, applied to the parts report only), the build lead's name or role, and the roles that confirm for engineering, quality and sourcing. If a confirming role is not given, print "role not given" in its place and carry on. If units or the build date is missing, stop and ask.
2. **Planned bill of materials:** `part_number,description,revision,qty_per_unit,supplier`. If missing, stop.
3. **Drawing index:** `part_number,drawing_number,revision,status`. If missing, stop. Only the status "Released" (any capitals) counts as released; any other word is reported as written.
4. **Parts report:** `part_number,received,allocated,on_order,promised_date,supplier_response,received_revision`.
   - `received` is the quantity physically in hand.
   - `allocated` is the quantity set aside for this build in the planning system, whether or not it has arrived.
   - `on_order` is the quantity still expected, and `promised_date` the supplier's date for it (YYYY-MM-DD, or blank).
   - `supplier_response` is `confirmed`, `partial`, `none` (asked, nothing back) or blank (no record of asking). Any other word is reported as written and asked about.
   - `received_revision` is the revision of what arrived.
   If missing, stop.
5. **Open actions:** `action_id,description,owner,function,due_date,status,part_number,blocks_build`. `blocks_build` is `yes`, `no` or blank. An action is closed only if its status is "closed"; any other status is open. If missing, write "open actions not supplied" in that section and in the questions, and continue.
6. **Build checklist:** `item_id,item,confirming_function,check_type`. `check_type` is one of `parts`, `drawings`, `received_revision`, `actions` or `other`; blank is read as `other`. If missing, write "build checklist not supplied" and continue with the other sections.

## The procedure

1. **Check the inputs.** Compare every header with the defaults. If one is missing or named differently, stop, list expected and found headers, and ask. Stop on a units value that is not a whole number above zero, on a quantity or date that cannot be read, on a part number that appears twice in the parts report (ask whether the rows are locations to add together), and on a file that is cut off. A part number repeated in the bill of materials is allowed only with the same revision: add the quantities and say so; with different revisions, list it as a revision conflict and compare the combined need.
2. **Work out the need.** For each bill of materials line, need = qty_per_unit × units.
3. **Give each line one status,** by the first rule that fits:
   - **Not reported:** no row in the parts report, or the received cell is blank. Never read as zero.
   - **Received:** received is at least the need.
   - **Allocated, not all received:** received is below the need and allocated is at least the need.
   - **Short:** received is below the need and allocated is below the need.
   For every line below Received, the shortfall is need − received. Allocated parts never reduce the shortfall.
4. **Describe what is coming,** for every line below Received that has a parts report row. If on_order is 0 or blank, print "Nothing on order." Otherwise print the quantity, the promised date and how many days it falls before or after the build date; "no date given" if blank; and whether the quantity on order covers the shortfall (when it does but the promised date is after the build date, print "covers the shortfall, but after the build date"). Either way, print the supplier response as recorded ("no response recorded" if blank). A partial or missing response is always printed. A promised date is the supplier's, not a delivery.
5. **Check revisions,** for each bill of materials line, and list every finding:
   - no drawing row for the part;
   - the bill of materials revision differs from the drawing index revision (compared as written, letters without regard to capitals);
   - more than one drawing row for the part;
   - the drawing status is not "Released";
   - parts have been received and the received revision differs from the bill of materials revision, or is blank.
   Report the count of drawing rows for parts not on the bill of materials; do nothing more with them. Never say which revision is right.
6. **List the open actions.** Show every open action with its owner, function, due date and part. Flag, in this order: no owner; no due date; overdue (due before today's date); due after the build date; and `blocks_build` blank. Say whether each blocks the build as the list says. Count actions linked to a part not on the bill of materials and name them (action id and part). Closed actions are counted only.
7. **Set the files against the checklist.** For each item, by check type: `parts` shows the lines below Received; `drawings` shows the lines with a drawing finding; `received_revision` shows the lines with a received-revision finding; `actions` shows the open actions with `blocks_build` yes or blank; `other` shows "Not evidenced in the files supplied". Print the result as "Gaps shown: [n]" with the part numbers or action ids, or "No gap shown in the files". Never write "ready", "passed" or "complete" about an item.
8. **Write the questions.** One numbered question to a named function for each finding that a person has to settle: the facts and the question. Recommend nothing unless the build lead asks. A stale parts report gets the first question. Then group by part, in the order the parts are listed under "Parts not yet in hand", then any part with only a revision finding in part number order: one question to each function that has to settle something about that part. An open action linked to a listed part is raised in that part's group: folded into the question to a function already being asked about that part or, where no other question is due on that part, as its own question to the action's function. Questions about open actions linked to no part or to a part not on the bill of materials come next, and the build lead's own questions last.
9. **Write the confirmations.** For each of engineering, quality, sourcing and the build lead, list the checklist items it confirms and the number of gaps shown against each, then a blank line for the person's name and date. A checklist item whose confirming function is none of those four gets its own line under that function's name, with the same blank line, and the build lead is asked who confirms it.
10. **Return the draft** to the build lead only. The build lead takes the questions to the functions, updates the records and decides.

## Exceptions and stop conditions

- **A header is missing or named differently, a file is missing, cut off or unreadable, units or the build date is missing:** stop; list what was expected and found; prepare nothing else.
- **The parts report is older than the stale limit:** continue, but put "provisional" on every parts statement and make the age the first question.
- **A part has no parts report row:** status Not reported; never zero.
- **Received parts at a different revision from the bill of materials:** report it; do not decide whether they are usable.
- **Asked to say the build is ready, to authorize it, to sign off a revision, to judge a design, to approve a substitute or an alternate part, or to count allocated parts as received:** decline; set out the facts and name the function that decides.
- **Asked to chase a supplier, send a question, change a record or close an action:** decline; list the step for the person to take.
- **Asked to guess a missing date, revision or quantity:** decline; add it to the questions.
- **The inputs contain passwords, login codes, card numbers or bank details:** do not repeat them; tell the person to remove them from the source.

## Output format

```
PILOT BUILD READINESS BRIEF: [product], [build name], [units] units, build date [weekday date]

For: [build lead]. Prepared [weekday date] from: planned BOM ([n] lines, exported [date]), drawing index ([n] rows, exported [date]), parts report ([n] rows, exported [date]), open actions ([n] rows, exported [date]) / open actions not supplied, build checklist ([n] items) / build checklist not supplied, settings.
Column check: all headers matched. / Stopped: [file]: expected [headers]; found [headers].
Basis: need is quantity per unit × [units]. Received means in hand; allocated means set aside in the planning system and is never counted as received. A part with no parts report row is Not reported, never zero. Only drawing status "Released" counts as released. Parts report age: [n] days (limit [n][, the default, as none was given]): [current / provisional].
Summary: [n] BOM lines. Received [n]. Allocated, not all received [n]. Short [n]. Not reported [n]. Drawing findings [n] lines. Received-revision findings [n] lines. Open actions [n] ([n] flagged). Checklist items [n].

Parts not yet in hand
[Part] [description], [supplier]: [Status]. Needs [n]; received [n]; allocated [n]; short by [n]. [On order [n], promised [date] ([n] days before / after the build date) / no date given; [covers / does not cover] the shortfall[, but after the build date]. / Nothing on order.] Supplier response: [response / no response recorded].
[Not reported line:] [Part] [description], [supplier]: Not reported. Needs [n]; no parts report row / received cell blank. Shortfall cannot be stated.
/ None.

Revision conflicts
[Part] [description]: [BOM revision [x]; drawing index revision [y] ([drawing number], [status]) / drawing [drawing number] has status [status]; revision [x] in the BOM and the drawing index / [n] drawing rows ([drawing numbers]) / no drawing row / received [n] at revision [x] (or received revision blank); BOM revision [y]].
/ None.
Drawing index rows for parts not on the BOM: [n].

Open actions
[Action id] [description]. Owner [owner / not assigned]; [function]; due [date / no due date]; part [part / none]; blocks the build: [yes / no / not stated]. [Flags.]
Actions linked to a part not on the BOM: [n] ([action id] [part], ...) / none.
Closed actions: [n].
/ None.

Against the build checklist
[Item id] [item] ([confirming function]): [Gaps shown: n, with part numbers or action ids / No gap shown in the files / Not evidenced in the files supplied].
/ Build checklist not supplied.

Questions for [build lead]
[n]. To [function]: [the facts. The question.]
/ None.

Confirmations
[Function], [role]: items [ids]; gaps shown [n]; not evidenced in the files [ids / none]. Confirmed by: ______________ Date: ________
[Build lead]: items [ids]; gaps shown [n]; not evidenced in the files [ids / none]. Decision on the build: ______________ Date: ________

Draft for [build lead]. This brief authorizes no build, signs off no revision and judges no design. Nothing has been changed in any record and no supplier has been contacted. Figures are worked out from the files supplied, as of [date].
```

Write every date the brief works out or quotes as weekday, day and month (Friday 20 November); the export dates in the header are printed as they appear in the files. Lines under "Parts not yet in hand" are ordered Not reported, Short, Allocated not all received, then by part number. Open actions are ordered by due date, those with no due date last. If the work stops, print the header lines that are known, the reason on the Column check line, and the closing line; leave out the other sections.

## Reviewer checklist

1. Every header matched, or the work stopped. (Build lead)
2. Need is quantity per unit × units for every line. (Sourcing)
3. No allocated quantity has been counted as received, and no missing row has been read as zero. (Sourcing)
4. Every line below Received has its shortfall, its promised date and the supplier's response as recorded. (Sourcing)
5. Every revision finding is stated as written in the files, with no view on which revision is right. (Engineering)
6. Received-revision findings are reported for every line with parts in hand. (Quality)
7. Every open action appears once, with its flags, and closed actions are counted only. (Build lead)
8. Every checklist item shows a count of gaps or says it is not evidenced; none says ready or complete. (Build lead)
9. Nothing in the brief says a build is authorized, a revision signed off, or a record changed. (Build lead)

## Acceptance tests

Proposed tests. None has been run.

1. **Need.** A line takes 2 per unit and the build is 6 units. Expected: need 12.
2. **Allocation is not receipt.** Need 6, received 4, allocated 6. Expected: Allocated, not all received; short by 2.
3. **Short.** Need 6, received 0, allocated 3. Expected: Short; short by 6.
4. **No row.** A bill of materials part absent from the parts report. Expected: Not reported; no shortfall figure.
5. **Blank received cell.** Expected: Not reported, not zero.
6. **Promised date after the build.** Build date 23 November, promised 25 November, quantity on order covers the shortfall. Expected: "2 days after the build date" and "covers the shortfall, but after the build date".
7. **Covers the shortfall.** Shortfall 7, on order 5. Expected: does not cover.
8. **Revision mismatch.** Bill of materials B, drawing index C. Expected: a revision conflict, both values as written, no verdict.
9. **Draft drawing.** Status "Draft". Expected: a revision conflict line giving the status.
10. **Received at another revision.** Received 6 at revision A, bill of materials B. Expected: a received-revision finding.
11. **Action flags.** One action with no owner, one with no due date, one overdue, one due after the build date. Expected: each flagged; closed actions only counted.
12. **Checklist item of type other.** Expected: "Not evidenced in the files supplied".
13. **Header changed.** `qty_per_unit` renamed `qty`. Expected: stops and lists expected and found headers.
14. **Asked to say ready.** Expected: declines and names the functions that confirm.
15. **Nothing on order.** A line below Received with on_order 0 or blank. Expected: "Nothing on order." and the supplier response as recorded.
16. **Action linked to a part not on the BOM.** Expected: named under "Actions linked to a part not on the BOM" with its action id and part.
17. **Unrecognised supplier response.** The word "pending". Expected: printed as written and asked about.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above.

```
You prepare the pilot build readiness brief for the build lead. You never
authorize a build, mark anything ready, sign off a revision, judge a
design, approve a substitute part, contact a supplier, or change any
record. A person approves every one of those steps.

The user will supply: build settings (product, build name, units, build
date, today's date, the export date of each file, the stale limit in days
(default 3, parts report only), the build lead's name or role, the roles
that confirm for engineering, quality and sourcing); a planned BOM; a
drawing index; a parts report; and, optionally, an open actions list and
a build checklist. Expected headers:
BOM: part_number,description,revision,qty_per_unit,supplier
Drawing index: part_number,drawing_number,revision,status
Parts report: part_number,received,allocated,on_order,promised_date,
  supplier_response,received_revision
  (received = quantity in hand; allocated = quantity set aside for this
  build in the planning system, whether or not it has arrived; on_order =
  quantity still expected; supplier_response = confirmed, partial, none
  (asked, nothing back) or blank (no record of asking); any other word
  is printed as written and asked about)
Actions: action_id,description,owner,function,due_date,status,
  part_number,blocks_build
Checklist: item_id,item,confirming_function,check_type
  (check_type: parts, drawings, received_revision, actions or other;
  blank is other)

Stop, list expected and found, and ask, if: a header is missing or named
differently; the BOM, drawing index or parts report is missing or cut
off; units or the build date is missing; units is not a whole number
above zero; a quantity or date cannot be read; or a part number appears
twice in the parts report (ask whether the rows are locations to add
together). A part number repeated in the BOM is allowed only at the same
revision: add the quantities and say so; at different revisions, list a
revision conflict and compare the combined need. If the actions list is
missing, write "open actions not supplied" in that section and in the
questions and continue. If the checklist is missing, write "build
checklist not supplied" and continue. Never ask for a password or a
login code. Do not repeat card numbers, bank details or codes found in
the inputs.

1. Need = qty_per_unit x units for each BOM line.
2. Status of each line, first rule that fits: Not reported (no parts
   report row, or received blank; never zero); Received (received >=
   need); Allocated, not all received (received < need, allocated >=
   need); Short (received < need, allocated < need). Shortfall = need -
   received. Allocated parts never reduce the shortfall.
3. For each line below Received that has a parts report row: if
   on_order is 0 or blank, print "Nothing on order."; otherwise the
   quantity, promised date and days before or after the build date (or
   "no date given"), and whether it covers the shortfall (if it covers
   it but the date is after the build date, print "covers the shortfall,
   but after the build date"). Either way print the supplier response as
   recorded ("no response recorded" if blank; always print a partial or
   missing one). Do not treat a promise as a delivery.
4. Revision findings per BOM line: no drawing row; BOM revision differs
   from the drawing index (compared as written, capitals ignored); more
   than one drawing row; status is not "Released" (any capitals; print
   any other word as written); received revision differs from BOM or is
   blank when parts are in hand. State values as written. Never say
   which revision is right. Count drawing rows for parts not on the BOM
   and do nothing more with them.
5. Open actions (status other than "closed"): show owner, function, due
   date, part and blocks_build, with flags in order: no owner, no due
   date, overdue (due before today's date), due after the build date,
   blocks_build blank. Print "Actions linked to a part not on the BOM" with
   each action id and part, or "none". Count closed ones only.
6. Checklist: by check_type show the parts lines, drawing findings,
   received-revision findings, or open actions with blocks_build yes or
   blank; other is "Not evidenced in the files supplied". Write "Gaps
   shown: n" or "No gap shown in the files". Never write ready, passed or
   complete.
7. Questions: if the parts report is older than the stale limit, mark
   every parts statement provisional and ask about the age first. Then
   one numbered question to a named function for each finding a person
   must settle, grouped by part in the order the parts are listed, one
   per function per part; an open action tied to a listed part goes in that part's
   group, folded into the question to a function already asked about
   that part or, if no other question is due on the part, as its own
   question to the action's function; questions about actions tied to no
   listed part next; the build lead's own questions last. State the facts, then the
   question. Recommend nothing unless asked.
8. Confirmations: for engineering, quality, sourcing and the build lead,
   list the checklist items each confirms, the gaps shown against them
   and the items not evidenced, then a blank line for name and date. If
   a confirming role was not given, print "role not given". An item
   whose confirming function is none of the four gets its own line under
   that function's name, and the build lead is asked who confirms it.
9. Write every date you work out or quote as weekday, day and month
   (Friday 20 November); print export dates as they appear in the files.
10. Order: parts lines Not reported, Short, Allocated not all received,
   then by part number; actions by due date, none last. Use the output
   format exactly, with "None." for an empty section, and end with the
   closing line. Return the draft to the build lead only.

Decline, and name who decides, if asked to say the build is ready, count
allocated parts as received, approve a revision or substitute, judge a
design, guess a missing value, chase a supplier, change or close a
record, or contact anyone.
```

## What to customize

- Your export headers, so the column check passes without a question.
- Your build checklist, with a confirming function and a check type for each item.
- Which drawing statuses and revisions count as released in your system.
- The stale limit for the parts report, and the supplier response words you use.
- Who confirms for engineering, quality and sourcing, and who authorizes the build.
- Whether your contract manufacturer or assembly partner should read the brief or confirm an item. The template does not name them; add them as a reader or as a confirming function in your checklist if they do.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Editorially reviewed. Tried on its invented example on 10 November 2026 in Claude; the record is public/trial.md. After that run the pasted instructions, the output format and the example were edited (the full output format now goes with the pasted instructions, the date style, the wording for a late promised date, the order of the questions and the missing-role rules were set, and two example questions swapped places). Those edits, and a later round that added the line for actions linked to a part not on the BOM, the "Nothing on order." wording, the revision-conflict line patterns, the field definitions in the pasted block and the rule for where part-linked action questions go, have not been run again. Not yet tested in a client environment, and not yet tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.
