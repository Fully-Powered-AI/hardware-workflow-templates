# Pilot build readiness brief: an invented example

*Illustrative example with invented data.* The company, the product, the part numbers, the suppliers, the quantities and every date below are invented. The company is an invented maker of a small field data logger, called the Company here, preparing a pilot build of six units. Suppliers are named by letter and people by role.

The inputs come first, in full, so the template can be run on them. The brief follows. Labels and sections are set as plain text in the template; they are set in list form here for reading.

## The inputs

### 1. Build settings (typed by the build lead)

```
Product: Field logger
Build: Pilot build 1
Units: 6
Build date: Monday 23 November 2026
Today: Tuesday 10 November 2026
Export dates: BOM 2026-11-09; drawing index 2026-11-06;
  parts report 2026-11-09; open actions 2026-11-10
Stale limit: not given
Confirming roles: engineering lead, quality lead, sourcing lead
Build lead: the build lead
```

### 2. Planned bill of materials

```
part_number,description,revision,qty_per_unit,supplier
FL-100,Enclosure body,C,1,Supplier A
FL-101,Enclosure lid,B,1,Supplier A
FL-210,Main board assembly,D,1,Supplier B
FL-220,Sensor module,A,2,Supplier C
FL-230,Battery pack,A,1,Supplier D
FL-240,Antenna cable,B,1,Supplier B
FL-300,Gasket,A,1,Supplier A
FL-310,M3 screw kit,A,2,Supplier E
FL-400,Label set,B,1,Supplier E
FL-500,Packaging tray,A,1,Supplier A
```

### 3. Drawing index

```
part_number,drawing_number,revision,status
FL-100,DWG-1100,C,Released
FL-101,DWG-1101,C,Released
FL-210,DWG-1210,D,Released
FL-220,DWG-1220,A,Released
FL-230,DWG-1230,A,Draft
FL-240,DWG-1240,B,Released
FL-300,DWG-1300,A,Released
FL-310,DWG-1310,A,Released
FL-400,DWG-1400,B,Released
FL-600,DWG-1600,A,Released
```

### 4. Parts report

```
part_number,received,allocated,on_order,promised_date,supplier_response,received_revision
FL-100,6,6,0,,confirmed,C
FL-101,6,6,0,,confirmed,B
FL-210,4,6,2,2026-11-20,confirmed,D
FL-220,5,12,10,2026-11-25,partial,A
FL-230,6,6,0,,confirmed,A
FL-240,0,3,6,,,
FL-300,6,6,0,,confirmed,A
FL-310,12,12,0,,confirmed,A
FL-400,6,6,0,,confirmed,A
```

### 5. Open actions

```
action_id,description,owner,function,due_date,status,part_number,blocks_build
A-01,Confirm gasket compound change,Engineer 1,engineering,2026-11-06,open,FL-300,no
A-02,Release battery pack drawing,Engineer 2,engineering,2026-11-18,open,FL-230,yes
A-03,Chase partial sensor delivery,Buyer 1,sourcing,2026-11-12,open,FL-220,yes
A-04,Inspect first lot of main boards,Quality engineer,quality,2026-11-24,open,FL-210,yes
A-05,Agree label artwork,,engineering,2026-11-16,open,FL-400,
A-06,Update test fixture firmware,Engineer 3,engineering,2026-11-09,closed,,no
A-07,Confirm antenna cable date with Supplier B,Buyer 1,sourcing,,open,FL-240,yes
```

### 6. Build checklist

```
item_id,item,confirming_function,check_type
C1,Every BOM part is in hand in the quantity the build needs,sourcing,parts
C2,Every part has a released drawing at the BOM revision,engineering,drawings
C3,Parts received are at the BOM revision,quality,received_revision
C4,No open action blocks the build,build lead,actions
C5,Test fixture is calibrated and available,quality,other
C6,Assembly partner has confirmed the build slot,build lead,other
```

## The brief

**Pilot build readiness brief: Field logger, Pilot build 1, 6 units, build date Monday 23 November 2026**

- **For:** the build lead. Prepared Tuesday 10 November 2026 from: planned BOM (10 lines, exported 2026-11-09), drawing index (10 rows, exported 2026-11-06), parts report (9 rows, exported 2026-11-09), open actions (7 rows, exported 2026-11-10), build checklist (6 items), settings.
- **Column check:** all headers matched.
- **Basis:** need is quantity per unit × 6. Received means in hand; allocated means set aside in the planning system and is never counted as received. A part with no parts report row is Not reported, never zero. Only drawing status "Released" counts as released. Parts report age: 1 day (limit 3, the default, as none was given): current.
- **Summary:** 10 BOM lines. Received 6. Allocated, not all received 2. Short 1. Not reported 1. Drawing findings 3 lines. Received-revision findings 1 line. Open actions 6 (4 flagged). Checklist items 6.

**Parts not yet in hand**

- FL-500 Packaging tray, Supplier A: Not reported. Needs 6; no parts report row. Shortfall cannot be stated.
- FL-240 Antenna cable, Supplier B: Short. Needs 6; received 0; allocated 3; short by 6. On order 6, no date given; covers the shortfall. Supplier response: no response recorded.
- FL-210 Main board assembly, Supplier B: Allocated, not all received. Needs 6; received 4; allocated 6; short by 2. On order 2, promised Friday 20 November (3 days before the build date); covers the shortfall. Supplier response: confirmed.
- FL-220 Sensor module, Supplier C: Allocated, not all received. Needs 12; received 5; allocated 12; short by 7. On order 10, promised Wednesday 25 November (2 days after the build date); covers the shortfall, but after the build date. Supplier response: partial.

**Revision conflicts**

- FL-101 Enclosure lid: BOM revision B; drawing index revision C (DWG-1101, Released).
- FL-230 Battery pack: drawing DWG-1230 has status Draft; revision A in both the BOM and the drawing index.
- FL-400 Label set: received 6 at revision A; BOM revision B.
- FL-500 Packaging tray: no drawing row.
- Drawing index rows for parts not on the BOM: 1.

**Open actions**

- A-01 Confirm gasket compound change. Owner Engineer 1; engineering; due Friday 6 November; part FL-300; blocks the build: no. Overdue.
- A-03 Chase partial sensor delivery. Owner Buyer 1; sourcing; due Thursday 12 November; part FL-220; blocks the build: yes.
- A-05 Agree label artwork. Owner not assigned; engineering; due Monday 16 November; part FL-400; blocks the build: not stated. No owner. Blocks the build not stated.
- A-02 Release battery pack drawing. Owner Engineer 2; engineering; due Wednesday 18 November; part FL-230; blocks the build: yes.
- A-04 Inspect first lot of main boards. Owner Quality engineer; quality; due Tuesday 24 November; part FL-210; blocks the build: yes. Due after the build date.
- A-07 Confirm antenna cable date with Supplier B. Owner Buyer 1; sourcing; no due date; part FL-240; blocks the build: yes. No due date.
- Actions linked to a part not on the BOM: none.
- Closed actions: 1.

**Against the build checklist**

- C1 Every BOM part is in hand in the quantity the build needs (sourcing): Gaps shown: 4 (FL-210, FL-220, FL-240, FL-500).
- C2 Every part has a released drawing at the BOM revision (engineering): Gaps shown: 3 (FL-101, FL-230, FL-500).
- C3 Parts received are at the BOM revision (quality): Gaps shown: 1 (FL-400).
- C4 No open action blocks the build (build lead): Gaps shown: 5 (A-02, A-03, A-04, A-05, A-07).
- C5 Test fixture is calibrated and available (quality): Not evidenced in the files supplied.
- C6 Assembly partner has confirmed the build slot (build lead): Not evidenced in the files supplied.

**Questions for the build lead**

1. To sourcing: FL-500 Packaging tray (Supplier A) needs 6 and has no row in the parts report. Has it been ordered, and is any in hand?
2. To engineering: FL-500 has no row in the drawing index. Is there a drawing for it, and at what revision?
3. To sourcing: FL-240 Antenna cable needs 6; received 0, allocated 3, on order 6, with no promised date and no supplier response recorded. A-07 for this has no due date. What date has Supplier B given?
4. To quality: A-04, the first-lot inspection of FL-210, is due Tuesday 24 November, a day after the build date. The 2 boards still to arrive are promised for Friday 20 November. Is the inspection date right for a build on Monday 23 November?
5. To sourcing: FL-220 Sensor module is short by 7 of 12. The 10 on order are promised for Wednesday 25 November, 2 days after the build date, and the supplier's response is partial. A-03 is due Thursday 12 November. Can the 7 be in hand by Monday 23 November?
6. To engineering: FL-101 is revision B on the BOM and revision C on the drawing index; the 6 received are revision B. Which revision does the build call for?
7. To engineering: FL-230 has a Draft drawing, and A-02 to release it is due Wednesday 18 November. Will it be released before the build?
8. To quality: FL-400 Label set arrived at revision A; the BOM calls for B. A-05 on the artwork has no owner. Are the 6 received to be used or replaced?
9. To the build lead: A-05 has no owner and no blocking status, A-01 is 4 days overdue, and A-07 has no due date. Who owns each, and does A-05 block the build?

**Confirmations**

- Sourcing, the sourcing lead: items C1; gaps shown 4; not evidenced in the files none. Confirmed by: ______________ Date: ________
- Engineering, the engineering lead: items C2; gaps shown 3; not evidenced in the files none. Confirmed by: ______________ Date: ________
- Quality, the quality lead: items C3, C5; gaps shown 1; not evidenced in the files C5. Confirmed by: ______________ Date: ________
- Build lead: items C4, C6; gaps shown 5; not evidenced in the files C6. Decision on the build: ______________ Date: ________

Draft for the build lead. This brief authorizes no build, signs off no revision and judges no design. Nothing has been changed in any record and no supplier has been contacted. Figures are worked out from the files supplied, as of Tuesday 10 November 2026.
