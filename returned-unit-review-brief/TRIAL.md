# Returned unit review brief: a trial on the invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the invented example in `public/example.md` (Company X, Customer A, return request RR-0318). No client data was used. I took the revised template's instruction block and output format from `member/template.md` and applied them to the example's inputs: the brief date and settings, the return request, the shipment records, the configuration records, the earlier ticket history and the support policy.

Limit of this trial. This is a second run. Before writing the brief I had read the example's finished brief and the record of the first run, so nothing here was written blind. It shows that the revised instruction block, applied to the example's inputs, produces the brief the example now gives. It does not show that the template works on a stranger's records.

## What came out

This is the brief as I produced it, before comparing it with the example.

```
RETURNED UNIT REVIEW BRIEF: RR-0318, Customer A

Prepared for: Dana, service coordinator. Brief date: 2026-11-09. Report received: 2026-11-09.
Internal. No fault has been identified, no handling chosen and no credit proposed.
Nothing has been sent to the customer.

SAFETY REFERRAL
The report says: "One of the nodes smelled hot when we unplugged it." Refer to the product safety officer before any other step. The unit is not named in the report. The brief gives no view on this.

THE REPORT
Contact A-1, received 2026-11-09. Units quoted: 3 (SN-40217, SN-40219, SN-40233).
Reported by the customer: the three nodes "stopped reporting to the hub over the weekend"; the status light is "solid red on two and blinking on the third" (units not named).
Asked for: replacement of the nodes; a credit for the downtime (no amount or basis stated).
Attachments named: photo of the label on SN-40217; photo of the hub status screen (contents not read).

UNIT MATCH
SN-40217: matched.
SN-40219: matched.
SN-40233: not matched, no shipment record has this serial.

SHIPMENT AND CONFIGURATION
SN-40217: Node N2, Rev C. Shipped 2026-03-04, order ORD-5521, Site 1, price 129.00. 250 days since shipment; stated period 365 days from ship date; 115 days left of it.
  Configuration on file at shipment: Firmware 2.4.1; Radio module RM-9; Battery pack BP-3 (2026-03-03, Factory).
  Recorded after shipment: none.
SN-40219: Node N2, Rev C. Shipped 2026-03-04, order ORD-5521, Site 1, price 129.00. 250 days since shipment; stated period 365 days from ship date; 115 days left of it.
  Configuration on file at shipment: Firmware 2.4.1; Radio module RM-9; Battery pack BP-3 (2026-03-03, Factory).
  Recorded after shipment: Firmware, 2.4.1 to 2.5.0, 2026-08-12 (161 days after shipment), Remote update.
The stated period is shown as a count of days. Service and quality decide what it means for handling.

CHANGED OR MODIFIED
Reported by the customer: SN-40219, battery pack swapped "last month"; the record shows Battery pack BP-3, as shipped.
Recorded after shipment: SN-40219, firmware 2.4.1 to 2.5.0 on 2026-08-12, Remote update.
Nothing is said about whether either is related to the report.

EARLIER HISTORY
SN-40217: 1 earlier entry. T-1190, 2026-08-20 (81 days ago): node dropped off the hub for a day; customer restarted it; reported working again.
SN-40219: 1 earlier entry. T-1244, 2026-10-02 (38 days ago): customer asked how to change the battery pack; public guide sent.
SN-40233: none, serial not matched.

EVIDENCE
Photo of the serial label: SN-40217 attachment named (photo of the label on SN-40217), contents not read; SN-40219 not supplied; SN-40233 not supplied
Status indicator state: stated, units not named
Date first seen: stated for all, "over the weekend"
What the unit was connected to: stated for all, "the hub"
Firmware version shown on the hub: attachment named (hub status screen), contents not read
Whether anyone has opened or repaired the unit: SN-40219 stated (battery pack swapped); SN-40217 not supplied; SN-40233 not supplied
Photos of visible damage: not supplied for any unit
Not supplied: SN-40217 2 items, SN-40219 2 items, SN-40233 3 items.

UNMATCHED SERIALS
SN-40233: no record. One character different from SN-40223 (shipped 2026-03-04, Rev C, order ORD-5521, Site 2) and from SN-40231 (shipped 2026-06-17, Rev D, order ORD-6012, Site 3). None is treated as a match.

CONFLICTS
None found.

DECISIONS FOR PEOPLE
Product safety officer: the heat mention above, first.
Service lead and quality lead (one line, as the settings give them): handling for each unit. Matched: SN-40217, SN-40219. Not matched: SN-40233. Open evidence and the reported battery pack swap are listed above.
Hardware engineering: technical points as reported, not assessed: the status light states; the battery pack swap on SN-40219; firmware 2.5.0 recorded on SN-40219 after shipment.
Finance controller: a credit for downtime is asked for; no amount or basis is stated. Recorded order ORD-5521, price 129.00 each on the matched units, as given. No figure has been calculated.

QUESTIONS FOR THE SERVICE COORDINATOR BEFORE IT GOES
1. Which unit smelled hot?
2. Which unit does the customer mean by SN-40233? Is it SN-40223, SN-40231 or another?
3. Which two units show a solid red light and which one blinks?
4. What are the date and part number of the battery pack fitted to SN-40219?
5. The credit request has no amount or basis. Who asks the customer for them?
6. Evidence not supplied: photos of visible damage for all three units; the serial label photo for SN-40219 and SN-40233; whether SN-40217 and SN-40233 have been opened or repaired. Who asks for them?

Prepared for the service coordinator.
Nothing has been sent, no record has been changed and no one has been contacted.
```

## What was observed

- Every required section was produced. Nothing in the instructions told me to stop: the headers matched, every date could be read, none was after the brief date, and a specialist was named. The safety mention was printed first.
- Day counts (250 since shipment, 115 left, 161 days after shipment for the firmware entry, 81 and 38 for the history entries) match the example.
- The block alone was enough this time. The first run found that the block pointed to a default evidence list it did not contain, and the block now carries the list. The policy here supplied its own list, so the default was not used and has not been exercised by this run.
- The first run found three marks that could be read two ways. The revised rules settled them: the named label photo is "attachment named, contents not read" and not "found"; "to the hub" counts as stated for what the unit was connected to; and "service lead and quality lead" is one decision line. I applied the rules as written and they gave one answer each. The counts of items not supplied are 2, 2 and 3.
- The evidence question (question 6) is now in the brief, as step 13 asks.
- My brief and the example's agree on content. The wording of the report section differs a little, as the template leaves the phrasing of claims open.
- Facts not in the inputs: none in my brief that I found.
- Still open: whether "units quoted" should include an unmatched serial (I counted all three), and whether an attachment named for an item is enough to leave it unasked. The template says only that it is not counted as not supplied.
- This was one run, by one model, on one invented example, after reading the answer. It does not show the template works on real records, on other assistants, or on cases such as a missing header or a duplicated serial. Those are among the proposed acceptance tests, none of which has been run.

## After this run

After independent review the template was revised again, with no change to the run recorded above: the block now carries the list of question triggers and the empty-section lines, settles that "units quoted" counts every serial quoted and that an item marked "attachment named, contents not read" raises no question of its own, treats an attachment whose name plainly corresponds to an item the same way as one the customer names as showing it, adds "0 days left of it", and adds a serial one character longer or shorter to the possible matches. I read the revised block against the example's inputs and found it gives the same brief as recorded above. That was a read-through, not a new recorded run, and the default evidence list and every stop condition are still unexercised.
