# Engineering change affected records index: trial on the invented example

- **Product:** Claude, run in Claude Code
- **Model:** Sonnet 5.5 (claude-sonnet-5-5)
- **Date:** 2026-11-10

This record covers three runs on the same invented example. No client data was used in any of them. All three were made with Sonnet 5.5; the record kept from the first two does not separate them by model, and it names no other model. The first two runs were made before the independent review of round 1. The third run, made after it, is the one printed in full.

## The first run

The first run was made by an assistant that had not written the template, which read the inputs first and the published output afterwards. The record does not say whether it was given the whole member template or only the pasted block and output format. Read it as having had the whole template, procedure included, because the review found that the block alone could not have produced the example's question wordings. Its index matched the published example in every fact, sum, count and question number. It differed only in small wording: the mixed-revision question (E2) was worded a little differently, and it kept the status on assembly stock lines where the example left it out. It also found six places where the instructions left room to guess: what counts as "rows used"; the drawing index rows for a replaced part with no to_rev; statuses on assembly stock; the numbering order of substitute and assembly drawing questions; which items the single assembly stock question names; and the Not found section, which read literally listed every assembly for having no open order. The earlier text of that run's index is not reproduced here.

## The second run

After the writer's own check, the template was revised to settle those points and the example's output was brought into line. The second run was made by the assistant that made those revisions, so it was not independent: it had read the first run's record and the earlier example output. It followed the revised template, again with the whole member template in view. The index it printed is word for word the example's index (checked by comparison for this record).

## What the independent review found

A reviewer found that the instruction block, pasted as the template tells the user to, could not produce the example's questions. The fixed wordings and three of the triggers (serial applicability Unknown, quoted effectivity with several top-level assemblies, mixed revisions) were in the procedure but not in the block. The first two runs therefore do not show that the block and output format alone are enough. The block was rewritten to carry the triggers and every fixed wording, a purchase order step for affected assemblies that the output format had no place for was dropped, and the example was run again.

## The third run

The third run was made by Claude, Sonnet 5.5, on 2026-11-10, after those changes. It was given only the fenced instruction block and the output format from the member template, and the six inputs from `public/example.md` ("The inputs"). It was not independent: the same session had made the changes and had the example's published index in view, so it is a check that the block can be followed, not a blind test. Facts, sums and counts were also recomputed with a short script (levels, rows used, stock totals, order lines), which agreed. The index below is what that run produced.

```
ENGINEERING CHANGE AFFECTED RECORDS INDEX: CR-114

For: the Document controller. Prepared: 2026-11-10, from 2 change rows, 9 bill of materials rows, 8 drawing index rows, 10 stock rows, 6 open purchase order lines and the settings.
Column check: all headers matched.
Changed items: 2. Affected assemblies: 5 (3 at level 1, 2 at level 2). Rows used: bill of materials 8, drawing index 7, stock 9, open purchase orders 5. Set aside: 0. Questions: 15 (7 engineering, 4 sourcing, 4 operations).

CHANGED ITEMS

1. P-2010 Sensor mount bracket: rev B to rev C.
  Serial applicability: Unknown. The change request gives none.
  Substitution: None named.
  Drawing index: D-2010 rev B, Released; D-2010 rev C, Draft.
  Where used: A-100 (rev D) uses rev B x2; A-200 (rev C) uses rev C x2; A-300 (rev B) uses no revision stated x1.
  Revisions referenced: Mixed. Rev B (Old) in A-100; rev C (New) in A-200; none stated in A-300.
  Stock: rev B 175 (Main store 140 Available, Line 2 35 Available); rev C 60 (Main store 60 Available); no revision 12 (Returns shelf 12 Quarantine); total 247.
  Open purchase orders: rev B 300: PO-7001, Supplier A, 300, due 2026-11-20; rev C 200: PO-7002, Supplier A, 200, due 2026-12-04; no revision 100: PO-7004, Supplier C, 100, due 2026-12-15.

2. P-3300 Panel connector 6-pin: replaced by P-3305.
  Serial applicability: Stated in the change request: "Serials from 1200 onward". This index does not check it against any unit record.
  Substitution: P-3305 named as the replacement; status Proposed.
  Drawing index: D-3300 rev A, Released.
  Where used: A-100 (rev D) uses rev A x1; A-200 (rev C) uses rev A x1.
  Revisions referenced: Rev A only. Not mixed.
  Stock: rev A 500 (Main store 500 Available); total 500.
  Open purchase orders: rev A 1000: PO-7003, Supplier B, 1000, due 2026-11-27.
  Substitute P-3305:
    Drawing index: no row.
    Where used: no bill of materials row.
    Stock: rev A 80 (Main store 80 Available); total 80.
    Open purchase orders: rev A 400: PO-7005, Supplier D, 400, due 2026-12-10.

AFFECTED ASSEMBLIES

Level 1 (uses a changed item directly):
A-100 rev D: uses P-2010 at rev B, P-3300 at rev A. Drawing index: D-100 rev D, Released. Stock: rev D 6 (Finished goods Available).
A-200 rev C: uses P-2010 at rev C, P-3300 at rev A. Drawing index: D-200 rev C, Released. Stock: no stock rows.
A-300 rev B: uses P-2010 with no revision stated. Drawing index: D-300 rev B, Released. Stock: rev B 4 (Finished goods Available).
Level 2 (uses a level 1 assembly):
F-10 rev F: uses A-100 at rev D, A-300 at rev B. Drawing index: D-F10 rev F, Released. Stock: rev F 3 (Shipping Available).
F-20 rev A: uses A-200 at rev C. Drawing index: no row. Stock: no stock rows.
Top-level assemblies: F-10, F-20.

QUESTIONS BY OWNER

Design engineering lead
E1 P-2010: From which serial number, lot or date does rev C apply to P-2010? The change request gives none.
E2 P-2010: A-100 (rev D) uses rev B (Old); A-200 (rev C) uses rev C (New); A-300 (rev B) uses no revision stated (Not stated). Is each assembly meant to use the revision its line shows, and which revision does each 'Not stated' or 'Other' line use?
E3 P-2010: The drawing index shows D-2010 as Draft at P-2010 rev C. Where does that revision stand?
E4 P-3300: The effectivity 'Serials from 1200 onward' does not say whose serial numbers it counts. Is it F-10 or F-20?
E5 P-3305: P-3305 is named to replace P-3300 and its status is Proposed. Is it approved, and for which assemblies?
E6 P-3305: The drawing index has no row for P-3305. Which drawing governs it?
E7 F-20: The drawing index has no row for F-20. Which drawing governs it?

Sourcing lead
S1 P-2010: PO-7001 (Supplier A) has 300 open of P-2010 rev B, due 2026-11-20. What is to happen to this order?
S2 P-2010: PO-7004 (Supplier C) has 100 open of P-2010 with no revision recorded, due 2026-12-15. Which revision is on the order?
S3 P-3300: PO-7003 (Supplier B) has 1000 open of P-3300 rev A, due 2026-11-27. What is to happen to this order?
S4 P-3305: PO-7005 (Supplier D) has 400 open of P-3305, due 2026-12-10, though the substitution is Proposed. Is the order to stand?

Operations lead
O1 P-2010: 175 of P-2010 rev B are held (Main store 140, Line 2 35). What is to happen to this stock?
O2 P-2010: 12 of P-2010 with no revision recorded are held (Returns shelf, status Quarantine). Which revision is it?
O3 P-3300: 500 of P-3300 rev A are held (Main store 500). What is to happen to this stock?
O4 P-2010, P-3300: Which units of the assemblies held (A-100 rev D, 6, Finished goods; A-300 rev B, 4, Finished goods; F-10 rev F, 3, Shipping) contain P-2010 or P-3300 at an old or unrecorded revision? The exports hold no serial numbers.

NOT FOUND AND SET ASIDE

No bill of materials row: P-3305. No stock rows: A-200, F-20. No drawing index row: P-3305, F-20. No rows set aside.

Draft for the Document controller. No revision has been released, no design has been judged, no record has been changed and nothing has been sent.
```

## What was observed

- Every part of the output format was produced, and nothing stopped the run: all headers matched, one change number, owners present, no loop in the bill of materials, no unreadable rows.
- All 15 questions were reachable from the block alone: each trigger and wording it needed is inside the block, and their numbers and order followed the block's rule. The result is identical to the published example, which is expected given the caveat above and so is a weak check of the example itself.
- Stock of the substitute P-3305 (80) is listed and raises no operations question; the block now says so. Open orders for assemblies are not looked up.
- The facts, sums and counts agree with a separate recomputation from the inputs: 3 assemblies at level 1, 2 at level 2; rows used 8, 7, 9 and 5; P-2010 stock 247, P-3300 500, P-3305 80.
- The assistant was not asked to decide anything, so the decline paths were not exercised, and no input had a bad header or an unreadable row.
- This shows the block and output format can be followed to the example. It does not show how the template performs on real exports or in other products, and no independent run has yet been made on the revised block.
