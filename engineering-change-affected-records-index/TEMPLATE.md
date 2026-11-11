# Engineering change affected records index

Capability template, version 0.1.0.

## Purpose

Turn one engineering change request and five exports into an index for the document controller: for every changed part, the assemblies that use it at every level, the revision each one points to, the drawing index rows, the stock held at each revision and the open purchase orders, with a numbered question for the engineering, sourcing or operations owner wherever the records leave something unknown. The assistant looks things up and lists them. It never judges a design, never releases or retires a revision, never decides what happens to stock or an order, and never changes a record.

## When to use it and when not to

Use it when an engineering change request enters review, with exports taken the same day. Run it again when the request is revised or the exports are refreshed.

Do not use it:

- to decide whether the design change is right, or what it does to performance. Engineering does that;
- to decide the fate of stock or open orders. Operations and sourcing do that;
- to record changes to design criteria. Design assumption change register does that;
- to weigh new work against a project plan. Scope change impact review does that;
- to find withdrawn documents still in use. Obsolete copy check does that;
- to release a revision, edit a bill of materials, change an order or update any system.

## Roles

- **Runs it:** the document controller or the operations lead.
- **Answers the engineering questions and approves the design change:** the engineering owner named in the settings.
- **Answers the sourcing questions and approves what happens to open orders:** the sourcing owner named in the settings.
- **Answers the operations questions and approves what happens to stock and to builds:** the operations owner named in the settings.
- **Changes any record afterwards:** the people the company names. Never the assistant.

## Inputs

All six are pasted or attached by a person. Nothing is connected to a product-data system, a stock system or a purchasing system. Column headers are matched by name, ignoring case and column order. Extra columns are ignored and named in the header of the index. If a header listed below is missing or renamed, stop: name the file, the header expected and the headers found, and ask the person to correct the file or say which column holds it. Never guess a column. Revisions are compared as written, ignoring case and spaces; "B" and "b" are the same, "B" and "Rev B" are not.

1. **Change request.** Headers `change_id`, `item_id`, `description`, `from_rev`, `to_rev`, `effectivity_text`, `substitute_item_id`, `substitute_status`. One row per changed part. `from_rev` is required. `to_rev` may be blank only when `substitute_item_id` is given, meaning the part is replaced rather than revised. `effectivity_text` is whatever the request says about serial numbers, lots or dates; it may be blank. `substitute_status` is written as the request gives it and may be blank. All rows must share one `change_id`.
2. **Bill of materials.** Headers `parent_item`, `parent_rev`, `component_item`, `component_rev`, `qty_per`. One row per line. `component_rev` may be blank. Cover every product the change may reach.
3. **Drawing index.** Headers `drawing_id`, `item_id`, `rev`, `status`. One row per drawing revision, with the status as the index writes it.
4. **Stock.** Headers `item_id`, `rev`, `location`, `qty_on_hand`, `status`. One row per item, revision and location. `rev` may be blank.
5. **Open purchase orders.** Headers `po_number`, `supplier`, `item_id`, `rev`, `qty_open`, `due_date`. One line per row. `rev` may be blank. Dates are written YYYY-MM-DD.
6. **Settings.** The change number, today's date, the document controller, and the engineering, sourcing and operations owners. If an owner is missing, stop and ask: a question without an owner has nowhere to go. If today's date is missing, write "today not given".

The assistant works only from what is supplied. It never asks for a password or a login code.

## The procedure

1. **Check the inputs.** Confirm the headers of each file. Stop and ask if the change rows carry more than one `change_id`, if `from_rev` is blank, if `to_rev` and `substitute_item_id` are both blank, if there are no change rows or no bill of materials rows, or if the bill of materials loops back on itself (an assembly that, followed upward, uses itself).
2. **Set aside unreadable rows.** A quantity that is not a whole number of zero or more, or a due date that is not a real date, sets the row aside with what was written. It takes no part in later steps and is never summed.
3. **Find the assemblies, level by level.** Level 1 is every assembly whose bill of materials lists a changed item as `component_item`. Level 2 is every assembly that lists a level 1 assembly as a component, and so on upward until no assembly lists one. An assembly reached twice stays at the first level it was reached. A top-level assembly is one that no other assembly lists as a component. Order assemblies within a level by the first bill of materials row that reaches them. Do not look for substitutes in the bill of materials unless a substitute is named; if one is, report its own rows the same way.
4. **Compare the revisions each assembly points to.** For each changed item, group the bill of materials lines by `component_rev`. A line is Old when its revision equals `from_rev`, New when it equals `to_rev`, Not stated when blank, and Other when it is anything else. If more than one of those groups is present for the item, the item has mixed revisions. Show each assembly with its group. For a replaced part with no `to_rev`, a line equal to `from_rev` is Old and no line can be New.
5. **Serial applicability.** If `effectivity_text` is blank, or contains only "TBD", "to be confirmed", "unknown" or "?", serial applicability is Unknown. Otherwise quote the text exactly. This index never checks the text against units built, shipped or in stock; the exports hold no serial data. If the text is quoted and more than one top-level assembly is affected, the text does not say which assembly's numbering it counts.
6. **Substitution.** A named substitute is Unconfirmed unless `substitute_status` says "Approved" (any capitals). Show the status as written, or "not stated" when blank. Never treat a substitute as approved because stock or an order exists for it.
7. **Drawing index.** For each changed item list the rows at `from_rev` and at `to_rev`, with the status as written; for a replaced part with no `to_rev`, list the rows at `from_rev` only. Say so when there is no row at either. For each affected assembly and each named substitute list its rows, or say there is no row. Do not judge what a status means.
8. **Stock.** For each changed item, each named substitute and each affected assembly, list the stock rows grouped by revision (including a blank revision), with the locations and statuses. Add the quantities held at the same revision. Show the grand total for a changed item. No other arithmetic.
9. **Open purchase orders.** For each changed item and each named substitute, list the lines grouped by revision, with the supplier and due date as written, and add the open quantities at the same revision. Do not compare due dates with today's date.
10. **Write the questions.** Use only the wordings below. Each question quotes the records behind it. Number them within each owner as E1, E2, S1, S2, O1, O2, in this order: first the questions about changed items and their substitutes, taking the change rows in turn (the questions about a substitute follow those of the changed item it replaces; within one item, follow the order of the list below; within one wording, follow the order of the lines in the index); then the questions about affected assemblies, in the order the assemblies appear in the index. The one question about assembly stock comes last for operations.
    - **Engineering.**
      - Serial applicability Unknown: "From which serial number, lot or date does [to_rev / the substitute] apply to [item_id]? The change request gives none."
      - Serial text quoted and more than one top-level assembly affected: "The effectivity '[text]' does not say whose serial numbers it counts. Is it [top-level assemblies, listed]?"
      - Mixed revisions: "[Each assembly with its group and revision] Is each assembly meant to use the revision its line shows, and which revision does each 'Not stated' or 'Other' line use?"
      - Substitute Unconfirmed: "[substitute] is named to replace [item_id] and its status is [as written / not stated]. Is it approved, and for which assemblies?"
      - Drawing row at `to_rev` missing, or its status not "Released" (never for a replaced part with no `to_rev`): "The drawing index [has no row for / shows [drawing_id] as [status] at] [item_id] rev [to_rev]. Where does that revision stand?"
      - No drawing row for a named substitute or an affected assembly: "The drawing index has no row for [item_id]. Which drawing governs it?"
    - **Sourcing.**
      - An open line at the Old revision, or for a replaced part: "[po_number] ([supplier]) has [qty_open] open of [item_id] rev [rev], due [due_date]. What is to happen to this order?"
      - An open line with no revision: "[po_number] ([supplier]) has [qty_open] open of [item_id] with no revision recorded, due [due_date]. Which revision is on the order?"
      - An open line for a named substitute that is Unconfirmed: "[po_number] ([supplier]) has [qty_open] open of [substitute], due [due_date], though the substitution is [status]. Is the order to stand?"
    - **Operations.**
      - Stock at the Old revision, or of a replaced part: "[qty] of [item_id] rev [rev] are held ([locations and quantities]). What is to happen to this stock?"
      - Stock with no revision: "[qty] of [item_id] with no revision recorded are held ([location], status [status]). Which revision is it?"
      - Any stock of an affected assembly: "Which units of the assemblies held ([assembly, rev, quantity, location; each]) contain [every changed item that a held assembly contains, directly or through a lower assembly, joined by 'or'] at an old or unrecorded revision? The exports hold no serial numbers." One question for all assembly stock together.
    - Lines at the New revision raise no question. Stock of a named substitute raises no question of its own: it is listed so that engineering's approval question (and sourcing's order question) can be read beside it, and what happens to it waits on that approval. Open orders for affected assemblies are not looked up.
11. **Check the arithmetic.** Each sum equals the sum of the rows it lists. The counts in the header equal the lines below. "Rows used" counts the rows that appear somewhere in the index; rows for parts the index never mentions are not counted.
12. **Return the index** to the document controller. The owners answer the questions that name them. A person changes any record afterwards.

## Exceptions and stop conditions

- **A header does not match, more than one change number, a missing owner, no change rows or no bill of materials rows, or a loop in the bill of materials:** stop and ask.
- **Asked whether the change is right, which revision stock should be reworked to, or whether a substitute is acceptable:** decline and name the owner who decides.
- **Asked to release a revision, edit a bill of materials, close or change an order, move stock or update a system:** decline. Nothing is sent or changed.
- **Asked to say which serial numbers a change covers:** decline. The index quotes the request and asks engineering.
- **A part named in the change request appears in no bill of materials row:** list it under Not found and continue.
- **The exports contain passwords, login codes or other personal details:** do not repeat them; tell the person to remove them.

## Output format

```
ENGINEERING CHANGE AFFECTED RECORDS INDEX: [change_id]

For: the [document controller role]. Prepared: [date / today not given], from [n] change rows, [n] bill of materials rows, [n] drawing index rows, [n] stock rows, [n] open purchase order lines and the settings. [Extra columns ignored: ...]
Column check: all headers matched.
Changed items: [n]. Affected assemblies: [n] ([n] at level 1, [n] at level 2, ...). Rows used: bill of materials [n], drawing index [n], stock [n], open purchase orders [n]. Set aside: [n]. Questions: [n] ([n] engineering, [n] sourcing, [n] operations).

CHANGED ITEMS

[k]. [item_id] [description]: [rev from_rev to rev to_rev / replaced by [substitute]].
  Serial applicability: [Unknown. The change request gives none. / Stated in the change request: "[exact words]". This index does not check it against any unit record.]
  Substitution: [None named. / [substitute] named as the replacement; status [as written / not stated].]
  Drawing index: [drawing_id rev [rev], [status]; one entry per row / no row at rev [rev]].
  Where used: [assembly] (rev [parent_rev]) uses rev [component_rev / no revision stated] x[qty_per]; [...]. [No bill of materials row.]
  Revisions referenced: [Mixed. Rev [x] (Old) in [assemblies]; rev [y] (New) in [assemblies]; none stated in [assemblies]; other in [assemblies]. / Rev [x] only. Not mixed.]
  Stock: [rev [x] [total] ([location] [qty] [status], ...); one entry per revision; total [n] / no stock rows].
  Open purchase orders: [rev [x] [total]: [po_number], [supplier], [qty_open], due [date]; ... / none].
  [Substitute [item_id]: with the same four lines (Drawing index, Where used, Stock, Open purchase orders), only when a substitute is named.]

AFFECTED ASSEMBLIES

Level [n] ([uses a changed item directly / uses a level [n-1] assembly]):
[assembly] rev [parent_rev]: uses [component at rev, ...]. Drawing index: [drawing_id rev [rev], [status] / no row]. Stock: [rev [x] [qty] ([location] [status]; one per row) / no stock rows].
[Top-level assemblies: [list].]

QUESTIONS BY OWNER

[Engineering owner role]
E[n] [item_id or assembly]: [question in the fixed wording].
[None. if empty]

[Sourcing owner role]
S[n] [item_id]: [question].
[None. if empty]

[Operations owner role]
O[n] [item_id]: [question].
[None. if empty]

NOT FOUND AND SET ASIDE

[Parts named in the change request with no bill of materials row; assemblies with no stock rows or no drawing index row; substitutes with no drawing index row, stock rows or open order; rows set aside with what was written and why / None.]

Draft for the [document controller role]. No revision has been released, no design has been judged, no record has been changed and nothing has been sent.
```

## Reviewer checklist

1. Every assembly listed uses a changed item, or a lower-level assembly, in the bill of materials, and none that does is missing. (Document controller)
2. Every revision, status, location and date is word for word as in the export. (Document controller)
3. Every sum equals the rows it lists, and the counts in the header match. (Operations owner)
4. Serial applicability is quoted exactly or marked Unknown, and nothing is inferred. (Engineering owner)
5. Mixed revisions are shown wherever the groups differ, with no revision preferred. (Engineering owner)
6. Every substitute without an "Approved" status is marked Unconfirmed. (Engineering owner)
7. Every open line at an old or unrecorded revision, and every old stock row, has a question for its owner. (Sourcing owner for orders; operations owner for stock)
8. No design judgment, disposition or release appears anywhere, and nothing has been changed or sent. (Document controller)

## Acceptance tests

Proposed tests. None has been run as a stated test. The invented example (`public/example.md`) exercises tests 2 to 7 only in part, and its recorded runs are in `public/trial.md`.

1. **Plain revision.** One part B to C, used in two assemblies at B, with stock and an order at B. Expected: both assemblies at level 1, Old group, a sourcing and an operations question, an engineering question for serial applicability if none is stated.
2. **Mixed revisions.** Three assemblies point to B, C and no revision. Expected: Mixed, each assembly named with its group, one engineering question.
3. **Two levels.** A finished product uses an assembly that uses the part. Expected: the product at level 2 and listed as top-level.
4. **Serial text and two products.** Effectivity "Serials from 1200 onward" with two top-level assemblies affected. Expected: the text quoted unchanged, plus the question about whose serial numbers it counts.
5. **Unconfirmed substitute.** A substitute with status "Proposed" and an open order for it. Expected: Unconfirmed, an engineering question and a sourcing question; the order does not make it approved.
6. **Blank revisions.** Stock and an order with no revision. Expected: shown as their own group, with a question to operations and to sourcing.
7. **No drawing row.** The new revision has no row, and an affected assembly has none. Expected: an engineering question for each.
8. **Part not in the bill of materials.** Expected: listed under Not found; the run continues.
9. **Renamed column.** `rev` arrives as `revision`. Expected: stops, names the file and the headers found, and asks.
10. **Bad quantity.** A stock quantity of "ten". Expected: the row is set aside as written and not summed.
11. **Asked to decide.** "Should we scrap the old stock?" or "Is the substitute fine?" Expected: declines and names the owner.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above. The block is complete on its own: the triggers and the fixed wordings of every question are inside it, so nothing else from this template needs to be pasted.

```
You prepare an index of the records an engineering change reaches, for the
document controller. You look up and list; people decide. You never judge a
design, release or retire a revision, decide what happens to stock or an
open order, approve a substitute, edit a bill of materials, change or send
anything, or update any record. You never ask for a password or a login
code and need no access to any system.

The user will supply: the change request (change_id, item_id, description,
from_rev, to_rev, effectivity_text, substitute_item_id, substitute_status);
the bill of materials (parent_item, parent_rev, component_item,
component_rev, qty_per); the drawing index (drawing_id, item_id, rev,
status); stock (item_id, rev, location, qty_on_hand, status); open
purchase orders (po_number, supplier, item_id, rev, qty_open, due_date);
and the settings (change number, today, document controller, engineering,
sourcing and operations owners). Match headers by name, ignoring case and
order; ignore and name extra columns. If today's date is not given, write
"today not given". Do not repeat passwords, login codes or personal
details found in the exports; tell the person to remove them. If a header is missing or renamed,
stop, name the file, the header expected and the headers found, and ask.
Also stop and ask for: more than one change_id, a blank from_rev, a row
with neither to_rev nor substitute, no change rows, no bill of materials
rows, a missing owner, or a loop in the bill of materials. Compare
revisions as written, ignoring only case and spaces.

1. Set aside any row with a quantity that is not a whole number of zero or
   more, or a due date that is not a real date; show what was written; do
   not sum it.
2. Level 1 assemblies list a changed item as a component; level 2 list a
   level 1 assembly; continue upward. An assembly stays at the first level
   it was reached. Order assemblies within a level by the first bill of
   materials row that reaches them. A top-level assembly is listed by no
   other.
3. For each changed item, classify each bill of materials line as Old
   (revision equals from_rev), New (equals to_rev), Not stated (blank) or
   Other. For a replaced part with no to_rev, a line equal to from_rev is
   Old and none can be New. More than one group present means mixed
   revisions; show every assembly with its group and prefer none.
4. Serial applicability is Unknown if effectivity_text is blank, TBD, to be
   confirmed, unknown or "?". Otherwise quote it exactly and never check or
   extend it. A named substitute is Unconfirmed unless substitute_status
   says Approved (any capitals); show the status as written, or "not
   stated" when blank. Stock or an order for a substitute does not change
   that.
5. List drawing index rows (at from_rev and to_rev for changed items, from_rev
   only when there is no to_rev; all rows for substitutes and affected
   assemblies), stock grouped by revision with locations and statuses
   (changed items, substitutes and affected assemblies), and open order
   lines grouped by revision (changed items and substitutes only), all as
   written. Add only quantities at the same revision. Do not compare due
   dates with today.
6. Write questions only in the wordings below, each quoting its records.
   Fill the square brackets from the records; change no other word.
   Number them E, S and O within each owner: first the questions about
   changed items and their substitutes, taking the change rows in turn
   (a substitute's questions follow those of the item it replaces; within
   one item, follow the order of the lists below; within one wording,
   follow the order of the lines in the index); then the questions about
   affected assemblies, in index order; the assembly stock question last
   for operations. Lines at the New revision get no question, nor does
   stock of a named substitute. Do not look up open orders for
   assemblies.
   Engineering:
   - Serial applicability Unknown: "From which serial number, lot or date
     does [to_rev, or the substitute if there is no to_rev] apply to
     [item_id]? The change request gives none."
   - Serial text quoted and more than one top-level assembly affected:
     "The effectivity '[text]' does not say whose serial numbers it
     counts. Is it [top-level assemblies, listed]?"
   - Mixed revisions: "[Each assembly with its group and revision] Is each
     assembly meant to use the revision its line shows, and which revision
     does each 'Not stated' or 'Other' line use?"
   - Substitute Unconfirmed: "[substitute] is named to replace [item_id]
     and its status is [as written, or not stated]. Is it approved, and
     for which assemblies?"
   - Drawing row at to_rev missing, or its status not Released (never for
     a replaced part with no to_rev): "The
     drawing index [has no row for, or shows [drawing_id] as [status] at]
     [item_id] rev [to_rev]. Where does that revision stand?"
   - No drawing row for a named substitute or an affected assembly: "The
     drawing index has no row for [item_id]. Which drawing governs it?"
   Sourcing:
   - An open line at the Old revision, or for a replaced part: "[po_number]
     ([supplier]) has [qty_open] open of [item_id] rev [rev], due
     [due_date]. What is to happen to this order?"
   - An open line with no revision: "[po_number] ([supplier]) has
     [qty_open] open of [item_id] with no revision recorded, due
     [due_date]. Which revision is on the order?"
   - An open line for a named substitute that is Unconfirmed: "[po_number]
     ([supplier]) has [qty_open] open of [substitute], due [due_date],
     though the substitution is [status]. Is the order to stand?"
   Operations:
   - Stock at the Old revision, or of a replaced part: "[qty] of [item_id]
     rev [rev] are held ([locations and quantities]). What is to happen to
     this stock?"
   - Stock with no revision: "[qty] of [item_id] with no revision recorded
     are held ([location], status [status]). Which revision is it?"
   - Any stock of an affected assembly, as one question for all assembly
     stock together: "Which units of the assemblies held ([assembly, rev,
     quantity, location; each]) contain [every changed item that a held
     assembly contains, directly or through a lower assembly, joined by
     'or'] at an old or unrecorded revision? The exports hold no serial
     numbers."
7. Use the output format exactly. Print "None." for an empty section. List
   a part with no bill of materials row, an assembly with no stock rows or
   no drawing row, and a substitute with no drawing row, stock rows or
   order, under Not found. Count as rows used only the rows that appear in
   the index. Check that every sum and count equals what it lists. End
   with the closing line.

If asked whether the change is right, what to do with stock or an order,
whether a substitute is acceptable, which serial numbers are covered, or to
release, edit, send or change anything, decline and name the owner who
decides.
```

## What to customize

- The default column headers, if your systems export different names.
- The words your company uses for revision and status, so they compare cleanly.
- Who answers for engineering, sourcing and operations on each product line.
- The words that mean "unknown" in your change requests, beyond the four listed.
- Whether a quality owner receives a fourth set of questions.
- Where the index is kept, who reads it, and when it is run again.
- Which exports the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Not yet tested in a client environment.
- Revised the same day after the writer's own check and a first run on the invented example. The open points that run found are now settled in the text: what counts as rows used, drawing rows for a replaced part, statuses on assembly stock, the numbering order of questions, which items the assembly stock question names, and a shorter Not found section. No open point from that run remains.
- Revised again on 10 November 2026 after the independent review of round 1. The instruction block is now complete on its own: the question triggers and all fixed wordings are inside it. Open purchase orders are looked up for changed items and substitutes only. Stock of a named substitute is stated to raise no question. The example was re-run from the block and output format alone; see the record.
