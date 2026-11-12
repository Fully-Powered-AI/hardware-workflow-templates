# Returned unit review brief: an invented example

*Illustrative example with invented data.* The company, its customer, its products and every serial, date and figure below are invented. Company X is an invented 40-person business that makes wireless environmental sensor nodes and a hub. Dana is its service coordinator. On Monday 9 November 2026 a return request arrives from Customer A, and the service coordinator runs the workflow template on it.

The inputs come first, in full, so the template can be run on them. The brief follows.

## The inputs

### The date of the brief and the settings

```
Brief date: 2026-11-09
Service coordinator: Dana
Safety referral: product safety officer
Handling decided by: service lead and quality lead
Technical concerns: hardware engineering
Credit approved by: finance controller
```

### The return request

```
Reference: RR-0318
Received: 2026-11-09
Customer: Customer A
Contact: A-1
Serials quoted: SN-40217, SN-40219, SN-40233
Attachments: photo of the label on SN-40217; photo of the hub status screen
Request: "Three of our sensor nodes stopped reporting to the hub over the weekend. The status light is solid red on two and blinking on the third. We want them replaced and a credit for the downtime. We swapped the battery pack on SN-40219 last month. One of the nodes smelled hot when we unplugged it."
```

### The shipment records

```
Serial,Product,Revision,Ship date,Order,Customer,Ship-to,Price
SN-40217,Node N2,Rev C,2026-03-04,ORD-5521,Customer A,Site 1,129.00
SN-40219,Node N2,Rev C,2026-03-04,ORD-5521,Customer A,Site 1,129.00
SN-40223,Node N2,Rev C,2026-03-04,ORD-5521,Customer A,Site 2,129.00
SN-40231,Node N2,Rev D,2026-06-17,ORD-6012,Customer A,Site 3,129.00
```

### The configuration records

```
Serial,Field,Value,Recorded on,Source
SN-40217,Firmware,2.4.1,2026-03-03,Factory
SN-40217,Radio module,RM-9,2026-03-03,Factory
SN-40217,Battery pack,BP-3,2026-03-03,Factory
SN-40219,Firmware,2.4.1,2026-03-03,Factory
SN-40219,Radio module,RM-9,2026-03-03,Factory
SN-40219,Battery pack,BP-3,2026-03-03,Factory
SN-40219,Firmware,2.5.0,2026-08-12,Remote update
SN-40223,Firmware,2.4.1,2026-03-03,Factory
SN-40231,Firmware,2.5.0,2026-06-16,Factory
```

### The earlier ticket history

```
Reference,Date,Serial,Entry
T-1190,2026-08-20,SN-40217,"Customer reported the node dropped off the hub for a day; customer restarted it; reported working again."
T-1244,2026-10-02,SN-40219,"Customer asked how to change the battery pack; public guide sent."
```

### The support policy

```
Stated period: 365 days from ship date.
Evidence before a unit is reviewed:
1. Photo of the serial label
2. Status indicator state
3. Date first seen
4. What the unit was connected to
5. Firmware version shown on the hub
6. Whether anyone has opened or repaired the unit
7. Photos of visible damage
```

## The brief

```
RETURNED UNIT REVIEW BRIEF: RR-0318, Customer A

Prepared for: Dana, service coordinator. Brief date: 2026-11-09. Report received: 2026-11-09.
Internal. No fault has been identified, no handling chosen and no credit proposed.
Nothing has been sent to the customer.

SAFETY REFERRAL
The report says: "One of the nodes smelled hot when we unplugged it." Refer to the product safety officer before any other step. The unit is not named in the report. The brief gives no view on this.

THE REPORT
Contact A-1, received 2026-11-09. Units quoted: 3 (SN-40217, SN-40219, SN-40233).
Reported by the customer: the three nodes stopped reporting to the hub "over the weekend"; the status light is solid red on two and blinking on the third (units not named).
Asked for: replacement of the three units; a credit for the downtime (no amount or basis stated).
Attachments named: photo of the label on SN-40217; photo of the hub status screen (contents not read).

UNIT MATCH
SN-40217: matched.
SN-40219: matched.
SN-40233: not matched, no shipment record with this serial.

SHIPMENT AND CONFIGURATION
SN-40217: Node N2, Rev C. Shipped 2026-03-04, order ORD-5521, Site 1, price 129.00. 250 days since shipment; stated period 365 days from ship date; 115 days left of it.
  Configuration on file at shipment: Firmware 2.4.1; Radio module RM-9; Battery pack BP-3 (all recorded 2026-03-03, Factory).
  Recorded after shipment: none.
SN-40219: Node N2, Rev C. Shipped 2026-03-04, order ORD-5521, Site 1, price 129.00. 250 days since shipment; stated period 365 days from ship date; 115 days left of it.
  Configuration on file at shipment: Firmware 2.4.1; Radio module RM-9; Battery pack BP-3 (all recorded 2026-03-03, Factory).
  Recorded after shipment: Firmware 2.5.0, recorded 2026-08-12 (161 days after shipment), Remote update.
The stated period is shown as a count of days. Service and quality decide what it means for handling.

CHANGED OR MODIFIED
Reported by the customer: SN-40219, battery pack swapped by the customer "last month" (no date or part number given). The record still shows Battery pack BP-3 as shipped.
Recorded after shipment: SN-40219, firmware 2.4.1 to 2.5.0 on 2026-08-12, Remote update.
Nothing is said about whether either is related to the report.

EARLIER HISTORY
SN-40217: 1 earlier entry. T-1190, 2026-08-20 (81 days ago): dropped off the hub for a day, restarted by the customer, reported working again.
SN-40219: 1 earlier entry. T-1244, 2026-10-02 (38 days ago): customer asked how to change the battery pack; public guide sent.
SN-40233: none, serial not matched.

EVIDENCE
Photo of the serial label: SN-40217 attachment named (photo of the label on SN-40217), contents not read; SN-40219 not supplied; SN-40233 not supplied
Status indicator state: stated, units not named (solid red on two, blinking on the third)
Date first seen: stated for all, "over the weekend"
What the unit was connected to: stated for all, "the hub"
Firmware version shown on the hub: attachment named (hub status screen), contents not read
Whether anyone has opened or repaired the unit: SN-40219 stated, the customer swapped the battery pack; SN-40217 not supplied; SN-40233 not supplied
Photos of visible damage: not supplied for any unit
Not supplied: SN-40217 2 items, SN-40219 2 items, SN-40233 3 items.

UNMATCHED SERIALS
SN-40233: no record. One character different from SN-40231 (shipped 2026-06-17, Rev D, order ORD-6012, Site 3) and from SN-40223 (shipped 2026-03-04, Rev C, order ORD-5521, Site 2). None is treated as a match.

CONFLICTS
None found.

DECISIONS FOR PEOPLE
Product safety officer: the heat mention above, first.
Service lead and quality lead: how each unit is handled. Matched: SN-40217, SN-40219. Not matched: SN-40233. Open evidence and the modification above are listed.
Hardware engineering: technical points as reported, not assessed: status light states; battery pack swap on SN-40219; firmware 2.5.0 on SN-40219 after shipment.
Finance controller: the credit asked for. No amount or basis is stated. Recorded order ORD-5521, price 129.00 each on the matched units; no figure has been calculated.

QUESTIONS FOR THE SERVICE COORDINATOR BEFORE IT GOES
1. Which unit smelled hot?
2. Which unit does the customer mean by SN-40233: SN-40231, SN-40223 or another?
3. Which two units show solid red and which blinks?
4. What are the date and part number of the battery pack fitted to SN-40219?
5. The request for a credit has no amount or basis. Who asks the customer for them?
6. Evidence not supplied: photos of visible damage for all three units; the serial label photo for SN-40219 and SN-40233; whether SN-40217 and SN-40233 have been opened or repaired. Who asks for them?

Prepared for the service coordinator.
Nothing has been sent, no record has been changed and no one has been contacted.
```
