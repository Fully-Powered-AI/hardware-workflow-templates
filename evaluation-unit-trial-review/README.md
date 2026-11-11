# Evaluation unit trial review

When a customer's evaluation reaches its review milestone, the account engineer and account owner get a trial-review agenda that sets the agreed use case beside the recorded results, setup changes and feedback, with every gap turned into a question and next-step options.

*Capability template · Hardware and physical technology · Sales · version 0.1.0 · [Capabilities Directory](https://fullypowered.ai/capabilities/evaluation-unit-trial-review/)*

## The outcome

An evaluation unit sits with a customer for weeks, and by the review meeting the picture has usually drifted. The use case that was agreed lives in one email, the results in an engineer's log, the setup changes in memory and the customer's opinion in a few messages. This capability template pulls them back together. It reads the agreed criteria, the results, the configuration log, the feedback and the support history, and writes the agenda for the review meeting.

Every criterion appears with what was recorded against it, and every result is labelled by where it was run: on the bench or at the customer's site. A bench result stays a bench result. The agenda never says a unit has been accepted or that it performs in the field; it shows the latest recorded value next to the target as written and leaves the reading to the people in the room.

What the records cannot answer becomes a numbered question. A result under a setup version nobody logged, a criterion with no feedback, a customer remark that fits no agreed criterion, a support note that mentions a swapped part: each is listed for the person who can settle it. The agenda closes with next-step options, each shown only when the records support it. The account engineer verifies the observations. The account owner agrees next steps with the customer. Nothing is sent, and no record is changed.

## Who starts the work, and when

The account engineer, or the account owner, starts it when an evaluation reaches its review milestone: a few days before the meeting, so the engineer has time to check what the agenda raises, and again if results or notes change before the meeting.

## What they supply

- **The agreed criteria,** one row for each, with the measure, the target, how the target is to be compared and the date it was agreed.
- **The recorded results,** each with its criterion, date, observed value, where it was run, the setup version and where the evidence is kept.
- **The configuration log,** with the baseline and every logged change.
- **The customer's feedback,** as dated rows.
- **The support history,** as dated rows with their status.
- **Their settings:** the account, the unit, the trial dates, the baseline version, the engineer and the owner, plus any account notes.

## What comes out

One draft agenda in a fixed order: questions for the account engineer to verify before the meeting; the agreed use case; results by criterion; the setup as it was run; the customer's feedback; the support history; questions for the customer, for the owner to raise; and next-step options. Every empty section says so.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Sales](https://fullypowered.ai/functions/sales/), where an evaluation ends in a decision about what happens next.
- [Customer success and account management](https://fullypowered.ai/functions/customer-success-and-account-management/), where the owner keeps the relationship while the engineer keeps the record.
- [Hardware and physical technology](https://fullypowered.ai/industries/hardware-and-physical-technology/), where a unit in a customer's building behaves differently from the same unit on the bench.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/), where evaluation units are tried on a line or in a plant.
- [Energy](https://fullypowered.ai/industries/energy/), where monitoring and control hardware is trialled on live sites.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where trials are run by a few engineers and the record lives in their own files.
- [Growth and scaling](https://fullypowered.ai/situations/growth-and-scaling/), when more evaluations run at once than one engineer can hold in mind.

It stands apart from three neighbours. [Quarterly business review preparation](https://fullypowered.ai/capabilities/quarterly-business-review-preparation/) is for an existing customer's regular review. [Account commitments check](https://fullypowered.ai/capabilities/account-commitments-check/) lists what each side promised. [Pilot acceptance-test preparation](https://fullypowered.ai/capabilities/pilot-acceptance-test-preparation/) writes the tests before a pilot begins. This one starts after the evaluation has run.

## What has to change for your company

Check that your files have the default column headers listed in the template, or rename them before you run it. Decide how each target is to be compared (at least, at most, or by reading) and write that into the criteria. Set the number of days that counts as a gap in feedback and the window used to look for setup changes; the template starts at 14 and 7. Say who verifies observations and who talks to the customer. It is written to run in ChatGPT, Claude, Copilot or Gemini from the files you paste in; it needs no access to any system.

## What has been checked

Fully Powered AI wrote this capability template. It was editorially reviewed on 10 November 2026. It was tried once in Claude on 2026-11-10 on its invented example, in a run that saw the example's output first, so that run is weaker evidence than a blind one. It has not yet been tested in a client environment, and it has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past evaluation your account engineer already knows well, plus cases written in advance: a header that does not match, a result under a setup version that is not in the log, a criterion with only bench results, a target written as text. The account engineer checks every figure against the records before anyone relies on it. [Pilot acceptance-test preparation](https://fullypowered.ai/capabilities/pilot-acceptance-test-preparation/) builds that test set, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/) describes the record we keep.

- Written by Fully Powered AI.
- Sources and rights reviewed.
- Editorially reviewed on 10 November 2026.
- Package format checked by script on every release.
- Tried once on its invented example in Claude on 10 November 2026. The record is in [TRIAL.md](TRIAL.md).
- Not yet tested in a client environment.

## What is in this folder

- [TEMPLATE.md](TEMPLATE.md): the complete capability template. Roles, inputs, the procedure, exceptions and stop conditions, the output format, a reviewer checklist, acceptance tests, the instructions for an AI assistant and what to customize.
- [EXAMPLE.md](EXAMPLE.md): a worked example with invented data.
- [TRIAL.md](TRIAL.md): what came out when the template was tried on its example.
- [SKILL.md](SKILL.md): the technical file, for AI products that load packaged instructions from a folder.
- [SOURCES.md](SOURCES.md): what the capability drew on, with licences.
- [LICENSE](LICENSE): MIT. Use it, change it, make it yours.

## Start using it

1. Read [EXAMPLE.md](EXAMPLE.md) to see what a good result looks like.
2. Open [TEMPLATE.md](TEMPLATE.md) and set every item under "What to customize" to your own rules, roles and limits.
3. Give your AI assistant the instruction block and the output format from the template, with your own limits in place of the ones the instructions leave open in square brackets. Paste them in as custom instructions in ChatGPT, Claude, Copilot or Gemini, or copy this whole folder into a product that loads `SKILL.md` packages. This folder stands alone; you do not need the rest of the repository.
4. Run it on past work first, using the reviewer checklist and acceptance tests in the template, before anyone relies on it.

## Related capabilities

- [Quarterly business review preparation](https://fullypowered.ai/capabilities/quarterly-business-review-preparation/)
- [Account commitments check](https://fullypowered.ai/capabilities/account-commitments-check/)
- [Pilot acceptance-test preparation](https://fullypowered.ai/capabilities/pilot-acceptance-test-preparation/)

## Make it yours

This is the starting version. Fully Powered AI adapts capabilities to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
