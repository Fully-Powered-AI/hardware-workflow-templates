# Returned unit review brief

When a failed-unit report or return request arrives, the service coordinator gets one brief tying the customer's report to each unit's shipment record, serial and recorded configuration, with unmatched serials and missing evidence listed. It names no cause.

*Capability template · Hardware and physical technology · Customer support and service · version 0.1.0 · [Capabilities Directory](https://fullypowered.ai/capabilities/returned-unit-review-brief/)*

## The outcome

A customer writes that three units have stopped working and wants them replaced. Before anyone can decide what happens, someone has to find out which units those are, what was shipped, how each was configured and what the customer has not yet told you. This capability template does that reading. It takes the report, your shipment records, your recorded configuration and your support policy, and puts them in one brief.

Each serial the customer quotes is matched to the shipment record only when it is identical. A serial that is one character away from a record is listed as a possible match and never chosen for you. For every matched unit the brief shows the product, revision, ship date, order and the configuration on file, the days since it shipped against the period your policy states, and anything recorded after shipment. Changes the customer mentions, such as a part swapped, are listed as reported. The evidence your policy asks for is checked off unit by unit, and what is missing is listed.

Any mention of heat, a burning smell, smoke, swelling or injury goes to the top of the brief with the specialist your policy names, before anything else. The brief identifies no fault, says nothing about whether a unit meets its specification and recommends no handling. For a case already with engineering, use [field issue handoff to engineering](https://fullypowered.ai/capabilities/field-issue-handoff-to-engineering/); for a complaint or refund request on its own, [complaint and refund request handling](https://fullypowered.ai/capabilities/complaint-and-refund-request-handling/); to record a nonconformity, [nonconformity record draft](https://fullypowered.ai/capabilities/nonconformity-record-draft/).

## Who starts the work, and when

A service coordinator starts it when a failed-unit report or a return request reaches service, and runs it again when the customer sends more evidence. Service and quality decide the handling, engineering reviews any technical concern and finance approves any credit.

## What they supply

- **The customer's report or return request,** pasted as received, with its reference and date.
- **The shipment records,** one row per serial.
- **The configuration records,** with the date each entry was recorded.
- **The earlier ticket history** for the serials concerned, if you have it.
- **Your support policy:** the stated period, the evidence it asks for, and who decides what.
- **Their settings:** the date of the brief and the names of the roles.

## What comes out

One brief in a fixed order: a safety referral if the report mentions one, what the customer reports and asks for, the match of each serial, each matched unit's shipment and configuration record, changes after shipment and reported modifications, earlier history, the evidence found and missing, unmatched serials, conflicts, the decisions each role is asked to make, and questions for the coordinator. Every empty section says so.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Customer support and service](https://fullypowered.ai/functions/customer-support-and-service/), where a return request starts as a few lines from a customer.
- [Quality management](https://fullypowered.ai/functions/quality-management/), where the quality owner decides handling and needs the unit's record beside the report.
- [Hardware and physical technology](https://fullypowered.ai/industries/hardware-and-physical-technology/), where each unit ships with a serial number and a recorded build.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/), where the plant's records say what left the dock.
- [Consumer brands](https://fullypowered.ai/industries/consumer-brands/), where connected products come back from people who never wrote down their setup.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where return handling lives in a few people's habits.
- [Growth and scaling](https://fullypowered.ai/situations/growth-and-scaling/), when return requests outgrow what one coordinator can look up by hand.

## What has to change for your company

Check that your exports have the default column headers listed in the template, or rename them before you run it. Put your own evidence list, period and decision roles into the policy you supply, and name the specialist who receives any possible safety concern. Decide which configuration fields matter for your products. The template assumes entries recorded on or before the ship date describe the unit as shipped. It runs in ChatGPT, Claude, Copilot or Gemini from the files you paste in; it needs no connection to any system.

## What has been checked

Fully Powered AI wrote this capability template. It was editorially reviewed on 10 November 2026. It was tried once on its invented example in Claude on 10 November 2026, and the record of that run is published with it. The run was not blind: the person running it had already read the example's brief and the record of an earlier run, so it shows the revised instructions reach the example's brief, not that they would on a stranger's records. It has not yet been tested in a client environment, and it has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past return your service team already knows well, plus cases written in advance: a serial one digit off, a serial that appears twice, a report that mentions heat, a header that does not match. The coordinator checks every record against the exports before anyone relies on the brief. [Pilot acceptance-test preparation](https://fullypowered.ai/capabilities/pilot-acceptance-test-preparation/) builds that test set.

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

- [Field issue handoff to engineering](https://fullypowered.ai/capabilities/field-issue-handoff-to-engineering/)
- [Complaint and refund request handling](https://fullypowered.ai/capabilities/complaint-and-refund-request-handling/)
- [Nonconformity record draft](https://fullypowered.ai/capabilities/nonconformity-record-draft/)

## Make it yours

This is the starting version. Fully Powered AI adapts capabilities to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
