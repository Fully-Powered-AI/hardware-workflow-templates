# Engineering change affected records index

When an engineering change request enters review, the document controller gets one index: the assemblies, revisions, stock and open purchase orders the change reaches in the exports supplied, and a question for each owner wherever the records are unclear.

*Workflow template · Hardware and physical technology · Quality management · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/engineering-change-affected-records-index/)*

## The outcome

The people reviewing a change see, before they meet, where it lands. For each changed part the index shows every assembly that uses it, the revision each assembly points to, the drawing index rows, the stock held at each revision and the purchase orders still open. Nothing is guessed to fill a gap.

What the records cannot answer becomes a numbered question with a named owner: a change with no stated serial applicability, assemblies that point to different revisions of the same part, a substitute nobody has approved, stock with no revision recorded. Engineering decides the design change. Sourcing and operations decide what happens to their orders and stock. The index only makes sure each of them is asked.

## Who starts the work, and when

The document controller or the operations lead starts it when an engineering change request enters review, with the exports taken that day. It is run again if the request is revised or the exports are refreshed, so the questions track the records as they stand.

## What they supply

- The change request: one row for each part changed, with its old and new revision, any stated serial applicability and any named substitute.
- A bill of materials export covering the products affected.
- The drawing index.
- The stock list, with revision and location.
- The open purchase order lines.
- The settings: the change number, today's date, and who owns engineering, sourcing and operations questions.

## What comes out

One index in a fixed order: the changed items, the assemblies above them, and the questions for each owner. Every line quotes the export values it rests on. The only arithmetic is adding quantities held at the same revision. The index releases no revision, judges no design, and changes no record.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Hardware and physical technology](https://fullypowered.ai/industries/hardware-and-physical-technology/), where a revised part can sit in stock, on order and in several assemblies at once.
- [Consumer brands](https://fullypowered.ai/industries/consumer-brands/), where a packaging or component change reaches stock and suppliers. The same assembly-and-revision walk applies to a product with a bill of materials and open orders.
- [Energy](https://fullypowered.ai/industries/energy/), where equipment makers and service teams track revisions across assemblies and spares. It suits a team that holds a bill of materials, a drawing index, stock and orders for its equipment.
- [Operations and process improvement](https://fullypowered.ai/functions/operations-and-process-improvement/), which owns the records around a change.
- [Quality management](https://fullypowered.ai/functions/quality-management/), which controls the documents and records an engineering change touches.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where product records have years of revisions in them.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/), when change requests multiply faster than one person can trace them.

It is a different piece of work from [Design assumption change register](https://fullypowered.ai/workflows/design-assumption-change-register/), which records changes to design criteria, from [Scope change impact review](https://fullypowered.ai/workflows/scope-change-impact-review/), which weighs new work against a project plan, and from [Obsolete copy check](https://fullypowered.ai/workflows/obsolete-copy-check/), which looks for withdrawn documents still in use. This one starts from an engineering change request and follows it into the parts, stock and orders.

## What has to change for your company

Fix the column headers of your five exports once, or map your system's names to the defaults. Decide who answers for engineering, sourcing and operations on a change. Decide how your company words a revision and a status, so the exports compare cleanly. Agree where the index goes and who reads it. If your records hold serial numbers, decide whether a person checks stated applicability against them by hand, since this index never does. The index sends questions only to engineering, sourcing and operations; if a quality owner should also be asked, add that owner and the questions they answer.

## What has been checked

Fully Powered AI wrote this workflow template. It was editorially reviewed on 10 November 2026, and an independent reviewer's findings have since been fixed. It was tried on its invented example in Claude on 10 November 2026, and the record is published with it. No run has yet been made by someone who had not seen the answer. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past change you already know, with cases written in advance: a part with no revision in the bill of materials, stock with no revision recorded, a substitute named but not approved. The document controller checks every line against the exports before anyone relies on the index. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/) sets those cases up.

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

- [Design assumption change register](https://fullypowered.ai/workflows/design-assumption-change-register/)
- [Scope change impact review](https://fullypowered.ai/workflows/scope-change-impact-review/)
- [Obsolete copy check](https://fullypowered.ai/workflows/obsolete-copy-check/)

## Make it yours

This is the starting version. Fully Powered AI adapts workflow templates to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
