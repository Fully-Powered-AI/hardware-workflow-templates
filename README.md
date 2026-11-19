# AI workflow templates for hardware companies

FullyPowered Workflow Templates for hardware and physical technology companies turn the AI your company already pays for into a team that knows how the work is done: a sourcing lead with the component end-of-life exposure brief prepared, a build lead with the pilot build readiness brief checked, a service coordinator with the returned unit review brief prepared. 6 workflow templates, made to be customized and deployed. All plain Markdown, all free, MIT license.

We are FullyPowered AI. We build AI workflows for companies, and these are the templates we start from. We publish them because a good starting point should be open to everyone. Copy one. Change it. Make it yours.

> [!TIP]
> **Missing a template that is not listed here, or want these customized for your organization? Reach out to us.** These are templates, made to be customized and deployed. FullyPowered AI customizes and builds AI workflows, connects them to your business systems, installs them in your agents and puts them in the hands of the people who own the work. [See more examples for hardware and physical technology companies](https://fullypowered.ai/industries/hardware-and-physical-technology/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-readme&from=gh-hardware-readme) · [Have one built for your team](https://fullypowered.ai/pricing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-readme&from=gh-hardware-readme) Not sure where to start? Email hello@fullypowered.ai and a person will answer.

**Who this is for**

- Hardware founders and operations heads who have paid for AI and want it doing real work.
- Programme and product leads who want a workflow their team can run this week.
- The engineer or coordinator who gets a precise brief and still makes every call.

**What these are for**

- **Your best way of doing it, for the whole team.** One piece of work, written down precisely enough that an assistant prepares it the same way every time.
- **Work you can check.** Every template says what it needs, what it produces, what it checked and what it could not.
- **A person decides.** Anything that sends, posts, pays or changes a record waits for someone to approve it.
- **Tied into your business systems.** A workflow can be designed to pull from the systems your company already runs, and even push data back into them, with guardrails and a person approving. [Browse the Connectors Directory](https://fullypowered.ai/connectors/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-readme&from=gh-hardware-readme).
- **Free, open and portable.** MIT-licensed plain instructions that run in the assistant or agent your team already uses: ChatGPT, Claude, Claude Code, Claude Cowork, Codex, Copilot, Gemini, Grok, Perplexity.

**Quick start**

1. **Try the returned unit review today.** Open ChatGPT, Claude, Copilot or Gemini. Copy the text below into a new chat, then replace each square bracket with something you already have: a customer's return message, your shipment list and your support rules. You need no sign-in here and nothing is installed.

   ```text
   You prepare a returned unit review brief for a service coordinator. Use only what I paste below. Match each serial the customer quotes to my shipment list exactly; never guess a near match, only list it as a possible one. If the message mentions heat, smoke, a burning smell or injury, put that first, quote it, and give no view. For each matched unit show the product, revision, ship date, days since shipment and any recorded or reported change. List which evidence from my support rules is missing. Name no cause, choose no handling and propose no credit. End with questions for me. A person decides everything and nothing is sent. Customer message: [paste]. Shipment list: [paste]. Support rules: [paste]. Today's date: [date].
   ```

2. Read what comes back. It marks what it checked and what is left for you. What comes out, with invented data:

   ```text
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
   ```

3. Stop there. You will know if this is for you. When you want it fitted to your company, or built into your agents, [that is what we do](https://fullypowered.ai/pricing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-readme&from=gh-hardware-readme).

A person starts every workflow, supplies the inputs and decides; the template only prepares and checks, and engineers and the quality owner keep every technical call.

These are samples and a starting point, made to be changed to fit how your company works. Your own work may not appear here, and a workflow can be a single step or many steps built for you.

## The workflow templates here today

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

The [FullyPowered Workflows Directory](https://fullypowered.ai/workflows/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-readme&from=gh-hardware-readme) lists every workflow template across functions and industries, with search. A machine-readable list of this repository is in [index.json](index.json).

For the work these templates come from, by area of the business and by task, see [AI workflow examples for hardware companies](https://fullypowered.ai/industries/hardware-and-physical-technology/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-readme&from=gh-hardware-readme).

## Licence and credits

MIT, in [LICENSE](LICENSE) and in every folder. Each folder's SOURCES.md names what the workflow template drew on. Published by [FullyPowered AI](https://fullypowered.ai/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-readme&from=gh-hardware-readme).
