# Engineering change affected records index: an invented example

*Illustrative example with invented data.* The company, the parts, the suppliers and every figure below are invented. The company is an invented maker of sensor equipment, called the Company here, and the change request is the invented CR-114. Roles stand in for people and suppliers are lettered. The document controller asks for the index on 10 November 2026. First come the inputs the document controller supplied, in full, then the index the capability returned.

## The inputs

### 1. Settings (typed by the document controller)

```
Change: CR-114
Today: 2026-11-10
Document controller (runs this): Document controller
Engineering owner: Design engineering lead
Sourcing owner: Sourcing lead
Operations owner: Operations lead
```

### 2. Change request

```
change_id,item_id,description,from_rev,to_rev,effectivity_text,substitute_item_id,substitute_status
CR-114,P-2010,Sensor mount bracket,B,C,,,
CR-114,P-3300,Panel connector 6-pin,A,,Serials from 1200 onward,P-3305,Proposed
```

### 3. Bill of materials

```
parent_item,parent_rev,component_item,component_rev,qty_per
A-100,D,P-2010,B,2
A-100,D,P-3300,A,1
A-200,C,P-2010,C,2
A-200,C,P-3300,A,1
A-300,B,P-2010,,1
F-10,F,A-100,D,1
F-10,F,A-300,B,1
F-20,A,A-200,C,1
A-400,A,P-9000,A,4
```

### 4. Drawing index

```
drawing_id,item_id,rev,status
D-2010,P-2010,B,Released
D-2010,P-2010,C,Draft
D-3300,P-3300,A,Released
D-100,A-100,D,Released
D-200,A-200,C,Released
D-300,A-300,B,Released
D-F10,F-10,F,Released
D-9000,P-9000,A,Released
```

### 5. Stock

```
item_id,rev,location,qty_on_hand,status
P-2010,B,Main store,140,Available
P-2010,C,Main store,60,Available
P-2010,B,Line 2,35,Available
P-2010,,Returns shelf,12,Quarantine
P-3300,A,Main store,500,Available
P-3305,A,Main store,80,Available
A-100,D,Finished goods,6,Available
A-300,B,Finished goods,4,Available
F-10,F,Shipping,3,Available
P-9000,A,Main store,900,Available
```

### 6. Open purchase orders

```
po_number,supplier,item_id,rev,qty_open,due_date
PO-7001,Supplier A,P-2010,B,300,2026-11-20
PO-7002,Supplier A,P-2010,C,200,2026-12-04
PO-7003,Supplier B,P-3300,A,1000,2026-11-27
PO-7004,Supplier C,P-2010,,100,2026-12-15
PO-7005,Supplier D,P-3305,A,400,2026-12-10
PO-7010,Supplier B,P-9000,A,50,2026-11-30
```

## The index

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
