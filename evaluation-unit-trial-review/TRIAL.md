# Evaluation unit trial review: tried once on its invented example

- **Product:** Claude, run in Claude Code
- **Model:** Claude Sonnet 5.5 (model ID claude-sonnet-5-5)
- **Date:** 2026-11-10

The inputs were the invented example in `public/example.md` (Tarnwick Devices, Customer B, the FX-1 flow monitor). No client data was used. The model that ran it did not write the template.

## How it was run

The model followed the fenced instruction block and the output format in `member/template.md` on the seven invented inputs: settings, agreed criteria, results, configuration log, customer feedback, support history and account notes. One thing went wrong with the method. The command that opened the example file printed the whole file, so the example's published output was seen before the model produced its own. The model then worked every step from the template's rules and did not copy. Because it saw the answer first, the match below is weaker evidence than a blind run would be.

## What came out

The model produced all parts of the output format: the header with counts, six engineer questions (E1 to E6), the seven agenda sections, ten customer questions (C1 to C10), the six next-step options, "Also noted" and the closing draft line. Nothing in the template told it to stop for this input: every header matched, no id was repeated, the baseline was in the log, and no row was set aside.

Substantial parts, as produced:

```
TRIAL REVIEW AGENDA: Customer B, FX-1 flow monitor, one evaluation unit

For: Ines (verifies) and Marcus (agrees next steps with the customer). Review milestone: Monday 2026-10-19. Trial: 2026-09-07 to 2026-10-19 (42 days). Baseline configuration: CFG-A. Prepared: 2026-10-14. Feedback gap 14 days and change window 7 days are the defaults.
Sources used: criteria 5; results 8; configuration log 2; feedback 3; support 3; account notes supplied. Extra columns ignored: none.
Left out: none.
Criteria: 5. Customer-site result 3. Bench only 1. Place not stated only 0. No result 1. With feedback 2.
Questions: for the account engineer 6; for the customer 10.

E1. Result R2 dated 2026-09-24 is recorded under CFG-B, which the log says took effect 2026-10-01. Which is right?
E2. Result R7 (2026-10-13) is recorded under CFG-C, which the configuration log does not list. What was the setup, and who changed it?
E3. Result R8 (K6, 2026-10-01) has no evidence reference. Where is the record of it?
E4. Result R8 is on K6, which is not among the agreed criteria. Was it agreed, and where is that recorded?
E5. K5 cannot be compared by rule: the target is written as text. How should the latest result, R6 (Readable), be read against 'Readable at midday without shading'?
E6. Ticket S2 (2026-10-05) says 'Customer swapped the power adapter for one from their own stores after the battery warning'. The configuration log has these rows in the 7 days up to that date: CFG-B, 2026-10-01. Is this covered by a logged change, a separate change, or not a change?

Latest results against the targets as written:
K1: Above the target as written (R7, 2.1 % against 2 % at most).
K2: Below the target as written (R4, 29 days against 30 days at least).
K3: At or above the target as written (R5, 99.1 % against 98 % at least), bench only: not field evidence.
K4: No result recorded.
K5: Not compared by rule: the target is written as text.
Results outside the agreed criteria: R8 (K6, "Works", customer site, CFG-B, evidence none).
Results under a version other than the baseline: R2, R3, R4, R8 (CFG-B), R7 (CFG-C). Versions used but not in the log: CFG-C (R7).
Latest feedback: 2026-10-02, 17 days before the review.

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

O1. Available: K3 (bench only), K4 (no result).
O2. Available: R2, R3, R4, R7, R8.
O3. Available: K4 (agreed after the trial began), R8 (outside the criteria), F3 (not tied to a criterion).
O4. Available: S2, S3.
O5. Not available: K3 and K4 have no customer-site result, K1, K2 and K3 have no feedback, and two tickets are open.
O6. Available: the criteria without a customer-site result stay unanswered.

Also noted: "The plant manager asked that the review fit in 45 minutes."

Draft for Ines and Marcus. Nothing has been sent to Customer B, no record has been changed, and nothing here states that the unit has been accepted or has performed in the field.
```

The model also printed the sections the extract above leaves out (the agreed use case, the full per-criterion results with their counts, the setup, the feedback rows and the support rows) in the template's format.

## What was observed

- **Every required part was produced,** and the counts, comparisons and day counts checked out against the inputs (42 days of trial, 17 days since the last feedback, and 2.1 against 2, 29 against 30 and 99.1 against 98).
- **Difference from the published example:** none of substance. The questions, options, counts and comparisons are the same, because the fixed wordings and the ordering rules left almost no room. The reservation is the one above: the example's output was seen first.
- **Facts in the output that are not in the inputs:** none. The weekday "Monday" for 2026-10-19 is computed from the date, and the day counts are computed.
- **Where the template left room to guess:**
  - The parenthetical after a comparison, such as "(R7, 2.1 % against 2 % at most)", has no wording in the template. It was written in the example's style, so another run could word it differently.
  - How to print an observed value with an empty unit, such as "Readable", and whether to put a space before "%", is not stated.
  - Section 3 says to list "every result whose version is not the baseline". It does not say whether a result with no stated version belongs in that list as well as in question a. This input had none.
  - Question h for a ticket mentioning "swapped" says only that the log has a row in the window. Question g's reason wording is fixed, but the comparison line for a criterion that has several results on its latest date is described only by an acceptance test.
  - Option wording is "fixed", but the output format shows O-lines as "[Option] Available: ..." and the example drops the "Available:" pattern for O6 into a clause that reads awkwardly ("Available: the criteria without a customer-site result stay unanswered").
  - The word list for unrecorded changes is matched on endings. "Mounting" in feedback F2 was judged not to match "moved", but the template does not say how loosely to match.
- **Nothing was a stop.** No refusal paths (a request to say the unit passed, or to send anything) were exercised, so the template's declines were not tried.
- **Limits:** one run, one model, one product, on invented data. The template's acceptance tests were not run, and nothing here shows how it behaves with a client's real files.

## Note added after this run

After this run, on 2026-11-10, the template was revised in response to a review: its instruction block now carries every fixed wording and condition, and the rules for dates, comparison lines, versions, value printing, change words and the sixth option were tightened. The revised template has not been rerun, so nothing above describes the revised wording. The recorded run and observations above are unchanged.
