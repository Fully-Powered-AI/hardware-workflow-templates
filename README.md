# Fully Powered Workflow Templates: Hardware and Physical Technology

From prototype to production with nothing lost in the handoff. These workflow templates are written for hardware companies. They prepare the indexes, briefs and reviews around a product's records. They design nothing, sign off no test and claim no conformity: the engineers and the quality owner do.

This repository holds 6 workflow templates for operations, product and programme leads at a hardware company. Each one is a single piece of work with its own folder: what it is for and who starts it, the complete template an AI assistant follows, a worked example with invented data, what to change for your company, what has been checked, and its sources.

## The workflow templates

- **[Component end-of-life exposure brief](component-end-of-life-exposure-brief/)**: When a supplier announces a component constraint or end-of-life date, the sourcing lead gets one brief: where the part is used, stock and demand set against the stated dates, and questions about replacements, with unverified availability kept apart from approved supply.
- **[Engineering change affected records index](engineering-change-affected-records-index/)**: When an engineering change request enters review, the document controller gets one index: the assemblies, revisions, stock and open purchase orders the change reaches in the exports supplied, and a question for each owner wherever the records are unclear.
- **[Evaluation unit trial review](evaluation-unit-trial-review/)**: When a customer's evaluation reaches its review milestone, the account engineer and account owner get a trial-review agenda that sets the agreed use case beside the recorded results, setup changes and feedback, with every gap turned into a question and next-step options.
- **[Pilot build readiness brief](pilot-build-readiness-brief/)**: Before a prototype or pilot build, the build lead gets one brief: part shortages, revision conflicts and open actions set against the team’s own build checklist, with allocated parts kept apart from received ones. People confirm; nothing is released.
- **[Product configuration margin sheet](product-configuration-margin-sheet/)**: When sales prepares a quote for a product configuration, the commercial owner and finance lead get one worksheet: the quoted price, the costed bill of materials, assembly and freight, and the allocations, with every unquoted part, one-off charge and uncertain volume listed as an open assumption.
- **[Returned unit review brief](returned-unit-review-brief/)**: When a failed-unit report or return request arrives, the service coordinator gets one brief tying the customer's report to each unit's shipment record, serial and recorded configuration, with unmatched serials and missing evidence listed. It names no cause.

## How to use one

Open a folder and start with its README. Every folder stands alone, so copy the one you want and leave the rest. The templates are written for ChatGPT, Claude, Copilot and Gemini: paste the instruction block and the output format in as custom instructions, or load the folder in a product that reads `SKILL.md` packages.

To take the whole collection, press **Use this template** at the top of this page: it copies every folder into a repository in your own account, yours to change.

In every template a person starts the work, supplies the inputs and decides. The template prepares and checks. Anything that sends, posts, pays or changes a record waits for a person to approve it.

## What SKILL.md is

Each folder holds a file named `SKILL.md`. It is the technical file: the same instructions and output format as the template, in the packaged form that AI products which load instructions from a folder read. It is generated from `TEMPLATE.md`, so the two always agree. The workflow template is the whole folder; `SKILL.md` is one way of loading it. If your AI product does not read that format, use `TEMPLATE.md`.

## What "checked" means here

Each folder says exactly what was checked and when: who wrote it, that its sources and rights were reviewed, the date of its editorial review, and whether it has been tried on its invented example in a named AI product. Nothing is described as tested for a client unless it was. Test a template on your own past work before your team relies on it; each one comes with acceptance tests for that.

## More workflow templates

The [Fully Powered Workflows Directory](https://fullypowered.ai/workflows/) lists every workflow template across functions and industries, with search. A machine-readable list of this repository is in [index.json](index.json).

## Licence and credits

MIT, in [LICENSE](LICENSE) and in every folder. Each folder's SOURCES.md names what the workflow template drew on. Published by [Fully Powered AI](https://fullypowered.ai/).
