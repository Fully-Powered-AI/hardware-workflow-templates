# Pilot build readiness brief

Before a prototype or pilot build, the build lead gets one brief: part shortages, revision conflicts and open actions set against the team’s own build checklist, with allocated parts kept apart from received ones. People confirm; nothing is released.

*Workflow template · Hardware and physical technology · Project and delivery · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflow templates/pilot-build-readiness-brief/)*

## The outcome

The build meeting starts from facts instead of a hunt through several spreadsheets. The build lead sees which parts are in hand, which are only promised, which have no record at all, where the bill of materials and the drawings disagree about a revision, and which open actions could stop the build. Each line points to the row it came from.

Parts set aside for the build are never counted as parts on the shelf. A part that is allocated but not received is shown as exactly that, with the quantity still missing and the date the supplier gave, or the fact that none was given. The build lead takes the open questions to engineering, quality and sourcing and decides what happens next.

## Who starts the work, and when

The build lead, or the program manager who runs the build, starts it once the build date is set and again in the days before the build meeting. Run it again after each new parts report; the brief is quick to produce and the questions it raises are the ones the meeting would otherwise reach late.

## What they supply

- The planned bill of materials, with revision and quantity per unit.
- The drawing index, with each drawing’s revision and status.
- The parts report: received, allocated, on order, promised dates, the supplier’s response and the revision of what arrived.
- The open actions list, with owner, function, due date and whether the action blocks the build.
- The team’s own build checklist, with the function that confirms each item.
- The build settings: units, build date, today’s date and the people who confirm.

## What comes out

One brief in a fixed order: a summary, the parts that are not yet in hand, the revision conflicts, the open actions, the team’s checklist with what the files show against each item, the questions for the build lead and a confirmation line for engineering, quality, sourcing and the build lead. Empty sections say so.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Project and delivery](https://fullypowered.ai/functions/project-and-delivery/), where the build date is a commitment and every gap needs an owner before it.
- [Quality management](https://fullypowered.ai/functions/quality-management/), which confirms that what arrived is the revision the build calls for.
- [Procurement and suppliers](https://fullypowered.ai/functions/procurement-and-suppliers/), where a supplier’s partial answer has to stay visible.
- [Hardware and physical technology](https://fullypowered.ai/industries/hardware-and-physical-technology/), the teams that put a first batch together from many suppliers.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/), for a pilot run before a production release.
- [Consumer brands](https://fullypowered.ai/industries/consumer-brands/), when a new physical product reaches its first assembly.
- [Startups & new ventures](https://fullypowered.ai/situations/startups-and-new-ventures/), when one person is chasing parts, drawings and actions at once.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/), when pilot builds multiply and the checklist lives in several heads.
- [New business lines](https://fullypowered.ai/situations/new-business-lines/), when a first physical product is added to an existing company.

It does not release orders to a production floor; [job readiness packet](https://fullypowered.ai/workflows/job-readiness-packet/) matches requirements to approved drawings for that. It does not rebuild a schedule; [production schedule rebuild](https://fullypowered.ai/workflows/production-schedule-rebuild/) does. [Kit component availability check](https://fullypowered.ai/workflows/kit-component-availability-check/) works out how many sets can be sold, which is a different question.

## What has to change for your company

- **Your export headers,** set once so the column check passes without a question.
- **Your build checklist,** with a function to confirm each item and the kind of check the files can support.
- **Which revisions and drawing statuses count as released** in your system.
- **How old a parts report may be,** and the wording your suppliers use in their responses.
- **Who confirms for engineering, quality and sourcing,** and who authorizes the build.
- **Your AI product.** It runs in ChatGPT, Claude, Copilot or Gemini from the files you supply. It needs no connection to your systems, changes nothing in them and never asks for a password.

## What has been checked

Fully Powered AI wrote this workflow template in its own words, from its own published map of the work, with no third-party text. It was editorially reviewed on 10 November 2026. It was tried on its invented example on 10 November 2026 in Claude; the record is published with it, and the run was made by an assistant that had not written the template, before the example's own output was read. The pasted instructions, the output format and the example were edited after that run (the record lists the edits), and those edits have not been run again. It has not yet been tested in a client environment or as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past build your team already knows, with hard cases written in advance: a part with no row in the parts report, a drawing at a different revision from the bill of materials, received parts at an old revision, an action with no owner and a promised date after the build. The build lead checks every line against the exports before anyone relies on it. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/) sets those cases up, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/) describes the record we keep.

- Written by Fully Powered AI.
- Sources and rights reviewed.
- Editorially reviewed on 10 November 2026.
- Package format checked by script on every release.
- Tried once on its invented example in Claude on 10 November 2026. The record is in [TRIAL.md](TRIAL.md).
- Not yet tested in a client environment.

## What is in this folder

- [TEMPLATE.md](TEMPLATE.md): the complete workflow template. Roles, inputs, the procedure, exceptions and stop conditions, the output format, a reviewer checklist, acceptance tests, the instructions for an AI assistant and what to customize.
- [EXAMPLE.md](EXAMPLE.md): a worked example with invented data.
- [TRIAL.md](TRIAL.md): what came out when the template was tried on its example.
- [SKILL.md](SKILL.md): the technical file, for AI products that load packaged instructions from a folder.
- [SOURCES.md](SOURCES.md): what the workflow template drew on, with licences.
- [LICENSE](LICENSE): MIT. Use it, change it, make it yours.

## Start using it

1. Read [EXAMPLE.md](EXAMPLE.md) to see what a good result looks like.
2. Open [TEMPLATE.md](TEMPLATE.md) and set every item under "What to customize" to your own rules, roles and limits.
3. Give your AI assistant the instruction block and the output format from the template, with your own limits in place of the ones the instructions leave open in square brackets. Paste them in as custom instructions in ChatGPT, Claude, Copilot or Gemini, or copy this whole folder into a product that loads `SKILL.md` packages. This folder stands alone; you do not need the rest of the repository.
4. Run it on past work first, using the reviewer checklist and acceptance tests in the template, before anyone relies on it.

## Related workflow templates

- [Job readiness packet](https://fullypowered.ai/workflow templates/job-readiness-packet/)
- [Production schedule rebuild](https://fullypowered.ai/workflow templates/production-schedule-rebuild/)
- [Kit component availability check](https://fullypowered.ai/workflow templates/kit-component-availability-check/)

## Make it yours

This is the starting version. Fully Powered AI adapts workflow templates to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
