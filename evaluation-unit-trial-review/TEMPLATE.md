# Evaluation unit trial review

Capability template, version 0.1.0.

## Purpose

Prepare the agenda for one customer evaluation's review meeting from the records the account team already keeps. The agenda sets the criteria agreed at the start beside the results recorded against each, labels every result as a bench result or a customer-site result, shows the setup the unit was run in and every logged change to it, and lays out the customer's feedback and the support history. Gaps become numbered questions: some for the account engineer to verify, some for the account owner to raise with the customer. Next-step options appear only when the records support them. The assistant prepares; it never states that a unit has been accepted, passed or performs in the field, never contacts the customer, and never changes a record.

## When to use it and when not to

Use it when an evaluation reaches its review milestone, a few days before the meeting. Run it again if results, notes or the configuration log change before the meeting.

Do not use it:

- to plan an evaluation or write its criteria. The criteria are agreed with the customer first; this capability reads them;
- to prepare a regular review for an existing customer (use quarterly business review preparation);
- to list what each side promised in meetings and emails (use account commitments check);
- to write the tests for a pilot before it starts (use pilot acceptance-test preparation);
- to decide whether a unit is accepted, to set a price, or to write a quote;
- to analyse why a result came out as it did. That is the engineer's work; the agenda only records the result.

## Roles

- **Runs it:** the account engineer, or the account owner.
- **Verifies the observations and answers the engineer's questions:** the account engineer.
- **Agrees next steps with the customer and raises the customer's questions:** the account owner.
- **Keeps the configuration log and the evidence:** the account engineer.
- **Resolves open support items:** applications engineering or customer service, as the company assigns.
- **Sends anything to the customer:** a person. The assistant sends nothing.

## Inputs

Five files and a settings note, pasted or attached by a person. Nothing is connected to a customer system, a support system or a product-data system. Column headers are matched by name, ignoring case and column order. Extra columns are ignored and named in the header of the agenda. If a listed header is missing or renamed, stop: name the file, the header expected and the headers found, and ask the person to correct the file or say which column holds it. Never guess a column. Dates are written YYYY-MM-DD. Configuration versions and criterion ids are compared as written, ignoring case and spaces.

1. **Agreed criteria.** Headers `criterion_id, criterion, measure, target_text, direction, target_value, unit, agreed_on`. One row per criterion. `direction` is `at_least`, `at_most` or `text`. For `at_least` and `at_most`, `target_value` is a number and `unit` is given. For `text`, `target_value` and `unit` may be blank. `agreed_on` may be blank.
2. **Results.** Headers `result_id, criterion_id, date, observed, unit, where_run, config_version, recorded_by, evidence_ref`. One row per recorded result. `where_run` is `bench` or `customer site`; any other value, or blank, means the place is not stated. `unit`, `config_version` and `evidence_ref` may be blank.
3. **Configuration log.** Headers `config_version, date_effective, change_summary, changed_by, approved_by`. One row per version, the baseline first. `approved_by` may be blank.
4. **Customer feedback.** Headers `feedback_id, date, from_person, criterion_id, comment`. `criterion_id` may be blank.
5. **Support history.** Headers `ticket_id, date, summary, config_version, status, criterion_id`. `status` is read as closed only when it says "closed"; anything else counts as open and is shown as written. `config_version` and `criterion_id` may be blank.
6. **Settings.** The account, the product or unit, the trial start date, the review date, today's date, the baseline configuration version, the account engineer, the account owner, the feedback gap in days (default 14) and the change window in days (default 7). If the account, the dates, the baseline, the engineer or the owner is missing, stop and ask. If today's date is missing, write "today not given". If a gap or window is missing, use the default and say so.
7. **Account notes,** optional. Free text. Quoted under "Also noted", never turned into a question or a result.

The assistant works only from what is supplied. It never asks for a password or a login code.

## The procedure

1. **Check the inputs.** Confirm the headers of each file. Stop and ask if a criterion id, result id, feedback id or ticket id appears twice in its file, if there are no criteria, or if the baseline version is not a row in the configuration log. Set a row aside, with the reason written next to its id, if its date is not a real date or its id is blank, or if a result's `observed` or `criterion_id` is blank. Also set aside a result, a feedback row or a ticket whose date is before the trial start or after the review date. The date-range rule does not apply to the configuration log: a baseline or other version that took effect before the trial start stays in the log. A row set aside takes no part in later steps. Count the rows used in each file.
2. **Read the criteria.** For each criterion, note whether `agreed_on` is blank, or later than the trial start date. Treat a criterion as compared by rule only if `direction` is `at_least` or `at_most` and `target_value` is a number; otherwise it is compared by reading.
3. **Group the results.** Put each result under its criterion. A result whose criterion id is not in the criteria goes under "Results outside the agreed criteria". Order results within a criterion by date, then by id. Label each result by `where_run`: customer site, bench, or place not stated. Count, for each criterion, results at the customer's site, on the bench, and with the place not stated.
4. **Class each criterion.** Customer-site result: it has at least one result at the customer's site. Bench only: no result at the site and at least one on the bench. Place not stated only: all its results have no stated place. No result: it has none. A bench result is never counted as site evidence, whatever its value.
5. **Compare the latest result.** The latest is the one with the latest date; if two share that date, compare both. For a criterion compared by rule, compare `observed` with `target_value` as written. For `at_least`: "At or above the target as written" when observed is equal to or greater, otherwise "Below the target as written". For `at_most`: "At or below the target as written" when observed is equal to or less, otherwise "Above the target as written". Follow the comparison words with the parenthetical "([result_id], [observed and unit] against [target_value and unit] at most)" for `at_most` or "([result_id], [observed and unit] against [target_value and unit] at least)" for `at_least`. Print a value followed by its unit with one space between them, including for `%` ("2.1 %"), and print a value whose unit is blank without a unit ("Readable"). Then add "bench only: not field evidence" when the latest result is a bench result, and "place not stated" when its place is not stated. If two results share the latest date, print one comparison line for each. Compare by rule only when the result's `unit` equals the criterion's `unit` and `observed` is a number. If not, the criterion is not compared by rule and, if it has a result, gets question g, asked once for the criterion. Compare only the latest result; list the others as recorded. The comparison is a fact about two numbers, never a statement that the unit passed or failed.
6. **Read the setup.** Show the baseline row and every later row of the configuration log in date order. For each result, find its `config_version` in the log. Note a result with no version stated, a version not in the log, and a version whose `date_effective` is later than the result's date. List every result whose version is not the baseline, with the version as written; a result with no version belongs in that list too, shown as "version not stated", and a version not in the log is listed there as well as under "Versions used but not in the log".
7. **Place the feedback.** A feedback row with a criterion id in the criteria belongs to that criterion; one with a blank or unknown criterion id is not tied to a criterion. Find the latest feedback date and the number of days between it and the review date.
8. **Place the support history.** A ticket belongs to its criterion if the id is in the criteria. A ticket with any status other than "closed" is open. Count open tickets for each criterion.
9. **Scan for unrecorded changes.** In each feedback comment and ticket summary, look for these words: swapped, replaced, updated, upgraded, moved, reflashed, rewired, reset, reconfigured, changed, adjusted. Match whole words only, ignoring case, in the listed form or the same verb with an ending -s, -d, -ed or -ing (swap, swaps, swapped, swapping; move, moves, moved, moving). A longer word that merely contains one, or a different word such as "Mounting", does not match. For every row with one, list the configuration log rows dated within the change window up to and including the row's date. The row becomes a question whether or not the log has a row in the window, because the assistant cannot tell whether that row is the same change.
10. **Write the engineer's questions.** Use only the wordings below, quoting the records. Number them E1, E2 and so on, taking the result checks in result-id order (a to f, in that order within each result), then the comparison questions in criterion order, then the change-word rows, feedback first then tickets, each in id order.
    - a. "Result [id] ([date]) gives no configuration version. Which setup was the unit in?"
    - b. "Result [id] ([date]) is recorded under [version], which the configuration log does not list. What was the setup, and who changed it?"
    - c. "Result [id] dated [date] is recorded under [version], which the log says took effect [date_effective]. Which is right?"
    - d. "Result [id] ([criterion_id], [date]) does not say where it was run. Was it on the bench or at the customer's site?"
    - e. "Result [id] ([criterion_id], [date]) has no evidence reference. Where is the record of it?"
    - f. "Result [id] is on [criterion_id], which is not among the agreed criteria. Was it agreed, and where is that recorded?"
    - g. "[criterion_id] cannot be compared by rule: [reason]. How should the latest result, [id] ([observed and unit]), be read against '[target_text]'?" If two results share the latest date, ask it once for the criterion and name both: "How should the latest results, [id] ([observed and unit]) and [id] ([observed and unit]), be read against '[target_text]'?" The reason is one of: the target is written as text; its target_value is not a number; the result is in [unit] and the criterion in [unit]; the observed value is not a number.
    - h. "[Feedback or Ticket] [id] ([date]) says '[the comment or summary, in full]'. The configuration log has [no row / these rows] in the [n] days up to that date[: version, date]. Is this covered by a logged change, a separate change, or not a change?"
11. **Write the customer's questions.** Use only these wordings, in this order of rules, and within a rule by criterion id or by row id. Number them C1, C2 and so on.
    - a. A criterion agreed after the trial began: "[criterion_id] was agreed on [agreed_on], after the trial began on [start]. Is its wording still what you intend?" A criterion with no agreed date: "[criterion_id] has no agreed date in our records. When was it agreed, and in what form?"
    - b. A criterion that is bench only or place not stated only: "[criterion_id] has no result recorded at your site. Can it be tried there, and under what conditions?" A criterion with no result: "No result is recorded for [criterion_id]. Can it be tried at your site, and when?"
    - c. A criterion with no feedback: "We have no feedback recorded on [criterion_id], [criterion]. How has it gone from your side?"
    - d. Feedback not tied to a criterion: "On [date] [from_person] said: '[comment]'. Which agreed criterion does that belong to, or is it a new one?"
    - e. If the latest feedback is more days before the review date than the feedback gap: "We have no feedback since [date], [n] days before the review. What has changed on your side since then?" If there is no feedback at all: "We have no feedback recorded in this trial. How has it gone from your side?"
    - f. An open ticket: "Ticket [id] is open[ on [criterion_id]]: '[summary]'. What does it hold up on your side?"
12. **Set the next-step options.** Always print O1 to O6, each as Available with its basis or Not available with its reason.
    - O1. "Extend the trial to cover the criteria with no customer-site result." Available when any criterion is bench only, place not stated only, or has no result: list them.
    - O2. "Repeat the affected results under the baseline configuration." Available when any result is under a version other than the baseline, a version not in the log, or no version: list the results.
    - O3. "Record a change to the agreed criteria, with the customer's confirmation." Available when a criterion was agreed after the trial began or has no agreed date, a result is outside the criteria, or feedback is not tied to a criterion: list them.
    - O4. "Hand the open support items to applications engineering or customer service to resolve." Available when any ticket is open: list them.
    - O5. "Begin the commercial conversation, which the account owner leads." Available only when every criterion has a customer-site result, every criterion has feedback and no ticket is open. It is a conversation, not an acceptance.
    - O6. "Close the trial on the record as it stands." Always printed as "Available: always. Criteria left unanswered: [the criteria that are bench only, place not stated only or without a result / none]."
13. **Check the arithmetic.** Every count in the header equals the lines below it. Every comparison matches its two numbers. Every day count matches the dates.
14. **Return the draft** to the person who ran it. The account engineer verifies the observations and answers the engineer's questions; the account owner agrees next steps with the customer. A person decides what, if anything, is sent to the customer.

## Exceptions and stop conditions

- **A listed header does not match,** a duplicate id, no criteria, or a baseline missing from the log: stop and ask.
- **A bench demonstration:** always labelled bench. Never counted as field evidence and never described as acceptance, however good the value.
- **Missing feedback or an unrecorded setup change:** turn it into a question; never fill it in, and never assume the setup was the baseline.
- **A criterion whose target cannot be compared by rule:** show the results as recorded and ask question g.
- **Asked to say the unit passed, failed, is accepted or performs in the field:** decline. Show the recorded values against the targets as written and name the roles that decide.
- **Asked to send the agenda or any question to the customer, to change a record or to log a configuration change:** decline and name the person who does it.
- **Asked to explain why a result came out as it did, or to recommend a next step:** decline. The options are listed; the owner chooses.
- **Asked for a quote, price, contract terms or a legal reading of the trial terms:** decline.
- **The files contain a password, a login code or an access token:** do not repeat it; tell the person to remove it from the source.
- **A comment or note names a customer's employee in connection with a complaint about them:** refer to the item by its id only.

## Output format

```
TRIAL REVIEW AGENDA: [account], [product or unit]

For: [account engineer] (verifies) and [account owner] (agrees next steps with the customer). Review milestone: [weekday date]. Trial: [start] to [review date] ([n] days). Baseline configuration: [version]. Prepared: [today's date / today not given]. [Feedback gap [n] days and change window [n] days are the defaults.]
Sources used: criteria [n]; results [n]; configuration log [n]; feedback [n]; support [n]; account notes [supplied / none]. Extra columns ignored: [names] / none.
Left out: [id, file, reason] / none.
Criteria: [n]. Customer-site result [n]. Bench only [n]. Place not stated only [n]. No result [n]. With feedback [n].
Questions: for the account engineer [n]; for the customer [n].

BEFORE THE MEETING: FOR THE ACCOUNT ENGINEER TO VERIFY
E[n]. [Question, in the fixed wording.]
None.

AGENDA

1. The agreed use case
[criterion_id] [criterion]. Measure: [measure]. Target: [target_text]. Agreed [date] / agreed date not stated.

2. Recorded results, by criterion
[criterion_id] [criterion]. Target as written: [target_text]. Results: [n] ([n] customer site, [n] bench, [n] place not stated). Feedback: [n]. Open support: [n].
  [result_id] [date] [observed and unit], [customer site / bench / place not stated], [version / version not stated], evidence [evidence_ref / none].
  Latest result: [comparison in the fixed words] ([result_id], [observed and unit] against [target_value and unit] at most / at least)[, bench only: not field evidence / , place not stated] / Not compared by rule: [reason] / No result recorded.
Results outside the agreed criteria:
  [result_id] [criterion_id] [date] [observed and unit], [place], [version / version not stated], evidence [evidence_ref / none].
  None.

3. Setup as run
Baseline: [version], effective [date], [change_summary].
Changes: [version], [date], [change_summary], changed by [name / not stated], approved by [name / approval not stated]. / None logged.
Results under a version other than the baseline: [result ids with their versions, or version not stated] / None.
Versions used but not in the log: [version, result ids] / None.

4. Customer feedback
[feedback_id] [date], [from_person], [criterion_id / not tied to a criterion]: "[comment]"
Latest feedback: [date], [n] days before the review. / None recorded.

5. Support history
[ticket_id] [date], [status as written], [criterion_id / not tied to a criterion], [version / version not stated]: [summary]
None.

6. Questions for the customer, for the account owner to raise
C[n]. [Question, in the fixed wording.]
None.

7. Next-step options, for the account owner to agree with the customer
O[n]. [Option, in the fixed words.] Available: [the criteria, results or items it applies to] / Not available: [reason].
O6. Close the trial on the record as it stands. Available: always. Criteria left unanswered: [ids] / none.

Also noted: [account notes, quoted] / none supplied.

Draft for [account engineer] and [account owner]. Nothing has been sent to [account], no record has been changed, and nothing here states that the unit has been accepted or has performed in the field.
```

Results inside a criterion are ordered by date, then id. A value is printed with one space before its unit ("2.1 %"), and without a unit when the unit is blank. A section with nothing in it prints "None." and a list that has nothing in it prints "none".

## Reviewer checklist

1. Every criterion on the supplied list appears once in sections 1 and 2, with its target as written. (Account engineer)
2. Every result is labelled bench, customer site or place not stated exactly as the file says, and no bench result is counted as a customer-site result. (Account engineer)
3. Each comparison matches the two numbers and uses the fixed words; no sentence says a unit passed, failed or is accepted. (Account engineer)
4. Every version used is shown, and every one that is not the baseline or not in the log has a question. (Account engineer)
5. Every feedback or ticket row with a change word has a question h. (Account engineer)
6. Every criterion with no feedback, no customer-site result or an agreed date after the start has a customer question. (Account owner)
7. Each option is marked Available only where its condition holds, and O5 is not Available unless all three of its conditions hold. (Account owner)
8. Counts in the header equal the lines below. (Account engineer)
9. Nothing has been sent, and no record has been changed. (Account owner)

## Acceptance tests

Proposed tests. None has been run.

1. **Ordinary review.** Every criterion has a customer-site result, feedback, all results under logged versions, no open ticket. Expected: no engineer questions, only the customer questions that apply, O5 Available.
2. **Bench only.** One criterion has only a bench result with a good value. Expected: labelled bench, "bench only: not field evidence", customer question b, O1 Available.
3. **Version not in the log.** A result names a version the log lacks. Expected: question b and the version listed under "Versions used but not in the log".
4. **Result before the version took effect.** Expected: question c.
5. **Text target.** A criterion with direction `text`. Expected: not compared by rule, question g, results shown as recorded.
6. **Unit mismatch.** The latest result is in a different unit from the criterion. Expected: not compared by rule, question g with the units named.
7. **Change word in a ticket.** A ticket says a part was swapped, and the log has no row in the window. Expected: question h saying the log has no row.
8. **Change word with a log row in the window.** Expected: question h listing the row, not a statement that it explains the swap.
9. **Feedback not tied to a criterion.** Expected: customer question d, O3 Available.
10. **No feedback at all.** Expected: customer question e in its second wording, plus question c for every criterion.
11. **Header mismatch.** A results file with `result` in place of `result_id`. Expected: stops, names the file, the header expected and the headers found.
12. **Asked to say the unit passed.** Expected: declines, shows the values against the targets as written.
13. **Asked to send the question list to the customer.** Expected: declines and names the person who sends.
14. **Two results share the latest date for one criterion.** Expected: both compared and both printed.

## Instructions for the AI assistant

Paste this block as custom instructions, followed by the output format above.

```
You prepare the agenda for one customer evaluation's review meeting for an
account engineer and an account owner, from the records they supply. You
prepare; people decide. You never say that a unit has passed, failed, been
accepted or performs in the field. You never send anything to the customer,
never change or log a record, never write a quote or contract terms, and
never ask for a password or a login code. You need no access to any system.

The user will supply: the agreed criteria (criterion_id, criterion,
measure, target_text, direction, target_value, unit, agreed_on); the
results (result_id, criterion_id, date, observed, unit, where_run,
config_version, recorded_by, evidence_ref); the configuration log
(config_version, date_effective, change_summary, changed_by,
approved_by); the customer feedback (feedback_id, date, from_person,
criterion_id, comment); the support history (ticket_id, date, summary,
config_version, status, criterion_id); the settings (account, product or
unit, trial start, review date, today's date, baseline version, account
engineer, account owner, feedback gap in days [default 14], change window
in days [default 7]); and optional account notes. Match headers by name,
ignoring case and order; ignore extra columns and name them. Dates are
YYYY-MM-DD. Compare versions and criterion ids as written, ignoring case
and spaces. If a header is missing or renamed, stop, name the file, the
header expected and the headers found, and ask. Stop and ask also for a
duplicate id, no criteria, a baseline not in the log, or a missing
account, date, baseline, engineer or owner. If today's date is missing,
write "today not given". If the feedback gap or the change window is
missing, use the default and say so in the header. Quote the account notes
under "Also noted"; never turn them into a question or a result.

Set aside, with a reason next to its id, any row with an unreal date or a
blank id, and any result with no observed value or no criterion_id. Also set
aside a result, feedback row or ticket dated before the trial start or
after the review date. Do not set aside configuration log rows for their
date: the baseline may take effect before the trial start.

1. Group results under their criteria, ordered by date then id. Label each
   result customer site, bench or place not stated, exactly from where_run
   ("bench" or "customer site"; anything else is place not stated). Never
   count a bench result as customer-site evidence. A result for a criterion
   that is not in the list goes under "Results outside the agreed criteria".
2. Class each criterion: customer-site result (at least one result at the
   site), bench only (none at the site, at least one on the bench), place
   not stated only, or no result. Count each class and the criteria with
   feedback.
3. Compare only the latest result of a criterion (both if they share a
   date, one line each). Compare by rule only if direction is at_least or
   at_most, target_value and observed are numbers and the units are equal.
   For at_least write "At or above the target as written" when observed is
   equal or greater, otherwise "Below the target as written". For at_most
   write "At or below the target as written" when observed is equal or
   less, otherwise "Above the target as written". Follow the words with
   "([result_id], [observed and unit] against [target_value and unit] at
   least)" or "... at most)". Print a value and its unit with one space between them, also
   for % ("2.1 %"), and a value with a blank unit without a unit. Then add
   "bench only: not field evidence" for a bench result and "place not
   stated" where the place is missing. Otherwise write "Not compared by
   rule: [reason]" and ask question g. Never turn a comparison into pass or
   fail.
4. Show the baseline and every later row of the configuration log in date
   order. Note results with no version, a version not in the log, or a
   version that took effect after the result's date. List every result not
   under the baseline with its version as written, including a result with
   no version (shown as "version not stated") and a version not in the log.
   List versions not in the log, with their result ids, separately. Never
   assume the baseline.
5. Tie feedback and tickets to criteria by criterion_id; a blank or
   unknown id is "not tied to a criterion". A ticket is open unless its
   status says "closed" (shown as written). Find the latest feedback date
   and its distance in days from the review date.
6. In every feedback comment and ticket summary, look for these words:
   swapped, replaced, updated, upgraded, moved, reflashed, rewired, reset,
   reconfigured, changed, adjusted. Match whole words only, ignoring case,
   in the listed form or the same verb with an ending -s, -d, -ed or -ing
   (swap, swaps, swapped, swapping). A longer word that merely contains one,
   or another word such as "Mounting", does not match. Each such row becomes
   question h, listing the log rows dated within the change window up to
   and including that row's date, or saying there is none. Do not say the log row
   explains it.
7. Write the account engineer's questions as E1, E2 and so on, using only
   these wordings, quoting the records and adding no question of your own.
   Order: the result checks a to f for each result in result-id order, then
   question g in criterion order, then question h for feedback rows and
   then ticket rows, each in id order.
   a. A result with no config_version: "Result [id] ([date]) gives no
      configuration version. Which setup was the unit in?"
   b. A result whose version is not in the log: "Result [id] ([date]) is
      recorded under [version], which the configuration log does not list.
      What was the setup, and who changed it?"
   c. A result dated before its version's date_effective: "Result [id]
      dated [date] is recorded under [version], which the log says took
      effect [date_effective]. Which is right?"
   d. A result whose place is not stated: "Result [id] ([criterion_id],
      [date]) does not say where it was run. Was it on the bench or at the
      customer's site?"
   e. A result with a blank evidence_ref: "Result [id] ([criterion_id],
      [date]) has no evidence reference. Where is the record of it?"
   f. A result on a criterion not in the list: "Result [id] is on
      [criterion_id], which is not among the agreed criteria. Was it
      agreed, and where is that recorded?"
   g. A criterion that cannot be compared by rule but has a result, asked
      once for the criterion: "[criterion_id] cannot be compared by rule:
      [reason]. How should the latest result, [id] ([observed and unit]),
      be read against '[target_text]'?" If two results share the latest
      date, name both: "How should the latest results, [id] ([observed and
      unit]) and [id] ([observed and unit]), be read against
      '[target_text]'?" The reason is one of: the target is written as
      text; its target_value is not a number; the result is in [unit] and
      the criterion in [unit]; the observed value is not a number.
   h. A feedback or ticket row with a change word: "[Feedback or Ticket]
      [id] ([date]) says '[the comment or summary, in full]'. The
      configuration log has [no row / these rows] in the [n] days up to
      that date[: version, date]. Is this covered by a logged change, a
      separate change, or not a change?"
8. Write the customer's questions as C1, C2 and so on, using only these
   wordings, in the order of the rules a to f, and within a rule by
   criterion id or row id.
   a. A criterion agreed after the trial start: "[criterion_id] was agreed
      on [agreed_on], after the trial began on [start]. Is its wording
      still what you intend?" A criterion with a blank agreed_on:
      "[criterion_id] has no agreed date in our records. When was it
      agreed, and in what form?"
   b. A criterion that is bench only or place not stated only:
      "[criterion_id] has no result recorded at your site. Can it be tried
      there, and under what conditions?" A criterion with no result: "No
      result is recorded for [criterion_id]. Can it be tried at your site,
      and when?"
   c. A criterion with no feedback: "We have no feedback recorded on
      [criterion_id], [criterion]. How has it gone from your side?"
   d. A feedback row not tied to a criterion: "On [date] [from_person]
      said: '[comment]'. Which agreed criterion does that belong to, or is
      it a new one?"
   e. If the latest feedback is more days before the review date than the
      feedback gap: "We have no feedback since [date], [n] days before the
      review. What has changed on your side since then?" If there is no
      feedback at all: "We have no feedback recorded in this trial. How has
      it gone from your side?"
   f. An open ticket: "Ticket [id] is open[ on [criterion_id]]: '[summary]'.
      What does it hold up on your side?" Leave out " on [criterion_id]"
      when the ticket has no criterion.
9. Print next-step options O1 to O6 in these words, each as Available with
   what it applies to, or Not available with the reason. Recommend none.
   O1. "Extend the trial to cover the criteria with no customer-site
       result." Available when any criterion is bench only, place not
       stated only or has no result: list them.
   O2. "Repeat the affected results under the baseline configuration."
       Available when any result is under a version other than the
       baseline, a version not in the log, or no version: list the results.
   O3. "Record a change to the agreed criteria, with the customer's
       confirmation." Available when a criterion was agreed after the trial
       start or has no agreed date, a result is outside the criteria, or
       feedback is not tied to a criterion: list them.
   O4. "Hand the open support items to applications engineering or customer
       service to resolve." Available when any ticket is open: list them.
   O5. "Begin the commercial conversation, which the account owner leads."
       Available only if every criterion has a customer-site result, every
       criterion has feedback and no ticket is open; otherwise Not
       available with the reasons. It is a conversation, not an acceptance.
   O6. "Close the trial on the record as it stands." Always print
       "Available: always. Criteria left unanswered: [the criteria that are
       bench only, place not stated only or without a result / none]."
10. Use the output format exactly. Print "None." for an empty section. Check
   every count, comparison and day count before you return the agenda.
   End with the draft line saying nothing has been sent, no record has been
   changed and nothing states acceptance or field performance.

If asked to say the unit passed, failed, is accepted or performs in the
field, decline, show the recorded values against the targets as written and
name the roles that decide. If asked to send anything, change a record,
log a change, explain why a result came out as it did, recommend a next
step, give a quote or a price, or interpret contract terms, decline and name
the person or role that does it. If the files contain a password, a login
code or a token, do not repeat it; tell the user to remove it. If a note
names a customer's employee in a complaint about them, refer to the item by
its id only.
```

## What to customize

- The feedback gap (14 days) and the change window (7 days).
- The change words, to match how your engineers and customers describe a setup change.
- The columns of your results log. Add one for the person who verified each result if you want it on the agenda.
- Whether a result with no evidence reference is a question (as written) or a reason to set the row aside.
- The conditions for O5, if your company requires more before a commercial conversation, such as a named customer sponsor.
- Who verifies the observations and who talks to the customer.
- Which files the assistant may read in ChatGPT, Claude, Copilot or Gemini.

## Version notes

- 0.1.0, 10 November 2026. Written by Fully Powered AI. Editorially reviewed. Tried once in Claude on 2026-11-10 on its invented example, in a run that saw the example's output first (see the trial record). After that run the instruction block was revised so that it carries every fixed wording and condition, and the date, comparison, version and change-word rules were tightened; the revised template has not been rerun. Later wording-only fixes (question g for two results on the latest date, the comparison parenthetical, the label "Latest result:") were not rerun either. Not yet tested in a client environment, and not yet tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.
