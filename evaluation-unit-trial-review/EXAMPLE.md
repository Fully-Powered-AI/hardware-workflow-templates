# Evaluation unit trial review: an invented example

*Illustrative example with invented data.* The company, the customer, the people, the product, the readings and the dates below are all invented. Tarnwick Devices is an invented maker of a flow monitor. Customer B is an invented regional water utility that has had one evaluation unit for six weeks. Ines is the account engineer and Marcus is the account owner. First come the inputs they supplied, in full, then the agenda the workflow template returned.

## The inputs

### 1. Settings

```
Account: Customer B (an invented regional water utility)
Product: FX-1 flow monitor, one evaluation unit
Trial start: 2026-09-07
Review date: 2026-10-19
Today: 2026-10-14
Baseline configuration: CFG-A
Account engineer: Ines
Account owner: Marcus
Feedback gap: default
Change window: default
```

### 2. Agreed criteria

```
criterion_id,criterion,measure,target_text,direction,target_value,unit,agreed_on
K1,Reading accuracy against the reference meter,24-hour average error,Error of 2% or less,at_most,2,%,2026-08-24
K2,Battery life between charges,Days of logging at a 15-minute interval,30 days or more,at_least,30,days,2026-08-24
K3,Uploads reach the customer's dashboard,Share of scheduled uploads received,98% or more,at_least,98,%,2026-08-24
K4,Installed by the customer's own technician,Minutes from unboxing to first reading,45 minutes or less,at_most,45,minutes,2026-09-14
K5,Display readable outdoors,Reading the display at midday,Readable at midday without shading,text,,,2026-08-24
```

### 3. Results

```
result_id,criterion_id,date,observed,unit,where_run,config_version,recorded_by,evidence_ref
R1,K1,2026-09-10,1.4,%,bench,CFG-A,Ines,LOG-0910
R2,K1,2026-09-24,2.6,%,customer site,CFG-B,Ines,LOG-0924
R3,K1,2026-10-08,1.9,%,customer site,CFG-B,Ines,LOG-1008
R4,K2,2026-10-12,29,days,customer site,CFG-B,Ines,BAT-1012
R5,K3,2026-09-30,99.1,%,bench,CFG-A,Ines,UPL-0930
R6,K5,2026-09-15,Readable,,customer site,CFG-A,Ines,PHOTO-0915
R7,K1,2026-10-13,2.1,%,customer site,CFG-C,Ines,LOG-1013
R8,K6,2026-10-01,Works,,customer site,CFG-B,Ines,
```

### 4. Configuration log

```
config_version,date_effective,change_summary,changed_by,approved_by
CFG-A,2026-09-07,Baseline as shipped: firmware 2.1 and 15-minute logging,Tarnwick Devices,Marcus
CFG-B,2026-10-01,Firmware 2.2 loaded and antenna moved to a roof mount,Ines,Marcus
```

### 5. Customer feedback

```
feedback_id,date,from_person,criterion_id,comment
F1,2026-09-18,Plant manager,K5,Display is hard to read at midday when the sun hits the housing
F2,2026-09-29,Technician,K4,Mounting took most of a morning because the bracket holes did not line up with our pipe clamp
F3,2026-10-02,Plant manager,,We would want an alarm output before we could roll this out
```

### 6. Support history

```
ticket_id,date,summary,config_version,status,criterion_id
S1,2026-09-22,Unit stopped uploading for two days; cleared by a power cycle,CFG-A,closed,K3
S2,2026-10-05,Customer swapped the power adapter for one from their own stores after the battery warning,CFG-B,open,K2
S3,2026-10-09,Display blank after a cold morning; recovered by noon,CFG-B,open,K5
```

### 7. Account notes

```
The plant manager asked that the review fit in 45 minutes.
```

## The output

```
TRIAL REVIEW AGENDA: Customer B, FX-1 flow monitor, one evaluation unit

For: Ines (verifies) and Marcus (agrees next steps with the customer). Review milestone: Monday 2026-10-19. Trial: 2026-09-07 to 2026-10-19 (42 days). Baseline configuration: CFG-A. Prepared: 2026-10-14. Feedback gap 14 days and change window 7 days are the defaults.
Sources used: criteria 5; results 8; configuration log 2; feedback 3; support 3; account notes supplied. Extra columns ignored: none.
Left out: none.
Criteria: 5. Customer-site result 3. Bench only 1. Place not stated only 0. No result 1. With feedback 2.
Questions: for the account engineer 6; for the customer 10.

BEFORE THE MEETING: FOR THE ACCOUNT ENGINEER TO VERIFY
E1. Result R2 dated 2026-09-24 is recorded under CFG-B, which the log says took effect 2026-10-01. Which is right?
E2. Result R7 (2026-10-13) is recorded under CFG-C, which the configuration log does not list. What was the setup, and who changed it?
E3. Result R8 (K6, 2026-10-01) has no evidence reference. Where is the record of it?
E4. Result R8 is on K6, which is not among the agreed criteria. Was it agreed, and where is that recorded?
E5. K5 cannot be compared by rule: the target is written as text. How should the latest result, R6 (Readable), be read against 'Readable at midday without shading'?
E6. Ticket S2 (2026-10-05) says 'Customer swapped the power adapter for one from their own stores after the battery warning'. The configuration log has these rows in the 7 days up to that date: CFG-B, 2026-10-01. Is this covered by a logged change, a separate change, or not a change?

AGENDA

1. The agreed use case
K1 Reading accuracy against the reference meter. Measure: 24-hour average error. Target: Error of 2% or less. Agreed 2026-08-24.
K2 Battery life between charges. Measure: Days of logging at a 15-minute interval. Target: 30 days or more. Agreed 2026-08-24.
K3 Uploads reach the customer's dashboard. Measure: Share of scheduled uploads received. Target: 98% or more. Agreed 2026-08-24.
K4 Installed by the customer's own technician. Measure: Minutes from unboxing to first reading. Target: 45 minutes or less. Agreed 2026-09-14.
K5 Display readable outdoors. Measure: Reading the display at midday. Target: Readable at midday without shading. Agreed 2026-08-24.

2. Recorded results, by criterion
K1 Reading accuracy against the reference meter. Target as written: Error of 2% or less. Results: 4 (3 customer site, 1 bench, 0 place not stated). Feedback: 0. Open support: 0.
  R1 2026-09-10 1.4 %, bench, CFG-A, evidence LOG-0910.
  R2 2026-09-24 2.6 %, customer site, CFG-B, evidence LOG-0924.
  R3 2026-10-08 1.9 %, customer site, CFG-B, evidence LOG-1008.
  R7 2026-10-13 2.1 %, customer site, CFG-C, evidence LOG-1013.
  Latest result: Above the target as written (R7, 2.1 % against 2 % at most).
K2 Battery life between charges. Target as written: 30 days or more. Results: 1 (1 customer site, 0 bench, 0 place not stated). Feedback: 0. Open support: 1.
  R4 2026-10-12 29 days, customer site, CFG-B, evidence BAT-1012.
  Latest result: Below the target as written (R4, 29 days against 30 days at least).
K3 Uploads reach the customer's dashboard. Target as written: 98% or more. Results: 1 (0 customer site, 1 bench, 0 place not stated). Feedback: 0. Open support: 0.
  R5 2026-09-30 99.1 %, bench, CFG-A, evidence UPL-0930.
  Latest result: At or above the target as written (R5, 99.1 % against 98 % at least), bench only: not field evidence.
K4 Installed by the customer's own technician. Target as written: 45 minutes or less. Results: 0 (0 customer site, 0 bench, 0 place not stated). Feedback: 1. Open support: 0.
  Latest result: No result recorded.
K5 Display readable outdoors. Target as written: Readable at midday without shading. Results: 1 (1 customer site, 0 bench, 0 place not stated). Feedback: 1. Open support: 1.
  R6 2026-09-15 Readable, customer site, CFG-A, evidence PHOTO-0915.
  Latest result: Not compared by rule: the target is written as text.
Results outside the agreed criteria:
  R8 K6 2026-10-01 Works, customer site, CFG-B, evidence none.

3. Setup as run
Baseline: CFG-A, effective 2026-09-07, Baseline as shipped: firmware 2.1 and 15-minute logging.
Changes: CFG-B, 2026-10-01, Firmware 2.2 loaded and antenna moved to a roof mount, changed by Ines, approved by Marcus.
Results under a version other than the baseline: R2 (CFG-B), R3 (CFG-B), R4 (CFG-B), R7 (CFG-C), R8 (CFG-B).
Versions used but not in the log: CFG-C (R7).

4. Customer feedback
F1 2026-09-18, Plant manager, K5: "Display is hard to read at midday when the sun hits the housing"
F2 2026-09-29, Technician, K4: "Mounting took most of a morning because the bracket holes did not line up with our pipe clamp"
F3 2026-10-02, Plant manager, not tied to a criterion: "We would want an alarm output before we could roll this out"
Latest feedback: 2026-10-02, 17 days before the review.

5. Support history
S1 2026-09-22, closed, K3, CFG-A: Unit stopped uploading for two days; cleared by a power cycle
S2 2026-10-05, open, K2, CFG-B: Customer swapped the power adapter for one from their own stores after the battery warning
S3 2026-10-09, open, K5, CFG-B: Display blank after a cold morning; recovered by noon

6. Questions for the customer, for the account owner to raise
C1. K4 was agreed on 2026-09-14, after the trial began on 2026-09-07. Is its wording still what you intend?
C2. K3 has no result recorded at your site. Can it be tried there, and under what conditions?
C3. No result is recorded for K4. Can it be tried at your site, and when?
C4. We have no feedback recorded on K1, Reading accuracy against the reference meter. How has it gone from your side?
C5. We have no feedback recorded on K2, Battery life between charges. How has it gone from your side?
C6. We have no feedback recorded on K3, Uploads reach the customer's dashboard. How has it gone from your side?
C7. On 2026-10-02 Plant manager said: 'We would want an alarm output before we could roll this out'. Which agreed criterion does that belong to, or is it a new one?
C8. We have no feedback since 2026-10-02, 17 days before the review. What has changed on your side since then?
C9. Ticket S2 is open on K2: 'Customer swapped the power adapter for one from their own stores after the battery warning'. What does it hold up on your side?
C10. Ticket S3 is open on K5: 'Display blank after a cold morning; recovered by noon'. What does it hold up on your side?

7. Next-step options, for the account owner to agree with the customer
O1. Extend the trial to cover the criteria with no customer-site result. Available: K3 (bench only), K4 (no result).
O2. Repeat the affected results under the baseline configuration. Available: R2, R3, R4, R7, R8.
O3. Record a change to the agreed criteria, with the customer's confirmation. Available: K4 (agreed after the trial began), R8 (outside the criteria), F3 (not tied to a criterion).
O4. Hand the open support items to applications engineering or customer service to resolve. Available: S2, S3.
O5. Begin the commercial conversation, which the account owner leads. Not available: K3 and K4 have no customer-site result, K1, K2 and K3 have no feedback, and two tickets are open.
O6. Close the trial on the record as it stands. Available: always. Criteria left unanswered: K3, K4.

Also noted: "The plant manager asked that the review fit in 45 minutes."

Draft for Ines and Marcus. Nothing has been sent to Customer B, no record has been changed, and nothing here states that the unit has been accepted or has performed in the field.
```
