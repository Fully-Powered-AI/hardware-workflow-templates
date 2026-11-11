# Component end-of-life exposure brief

When a supplier announces a component constraint or end-of-life date, the sourcing lead gets one brief: where the part is used, stock and demand set against the stated dates, and questions about replacements, with unverified availability kept apart from approved supply.

*Capability template · Hardware and physical technology · Supply chain and inventory · version 0.1.0 · [Capabilities Directory](https://fullypowered.ai/capabilities/component-end-of-life-exposure-brief/)*

## The outcome

A supplier notice arrives as a short message with a date in it, and the first hours go to finding out what it touches. This capability template does that reading. It takes the notice, your where-used export, your stock and your demand plan, and puts them in one brief: which of your assemblies use the part, how much of it you hold and have on a dated order, how much your plan will need, and the month in which approved supply runs short.

Every date in the brief comes from the notice and is shown with the days remaining. Nothing is assumed where the notice is silent; it says "not stated". Supply is counted only when it is held or on an order with a due date. A distributor's phone promise, an alternate still being evaluated and the replacement the supplier suggests all appear in their own section, beside the gap and never subtracted from it.

The brief ends with questions for component engineering and program management, the gaps in your own records, and the decisions that belong to sourcing. It qualifies no alternative, approves no design change, orders nothing and writes to nobody. For a supplier problem that is not about a named part, use [supplier risk alert brief](https://fullypowered.ai/capabilities/supplier-risk-alert-brief/); for routine buying, use [inventory reorder plan](https://fullypowered.ai/capabilities/inventory-reorder-plan/); to see what can be built from the components on hand, use [kit component availability check](https://fullypowered.ai/capabilities/kit-component-availability-check/).

## Who starts the work, and when

A sourcing lead, or a buyer for them, starts it the day a supplier notice about a constraint or an end-of-life date arrives, and again when the notice is updated or the stock and demand records change. Sourcing owns the brief and decides what, if anything, to propose.

## What they supply

- **The supplier notice,** pasted as received, with the dates it states for each part.
- **The affected part list,** mapping your part numbers to the supplier's.
- **The where-used export** from your bill of materials system.
- **The inventory export,** with stock held, reserved and on order.
- **The demand plan,** by assembly and month.
- **The alternates list,** with the status of each and who approved it.
- **Availability notes,** if you have any: what a distributor or the supplier has said is available, however informal.
- **Their settings:** today's date, the date of the stock export, whether reserved stock is already counted in the demand plan, and the sourcing lead's role.

## What comes out

One brief in a fixed order: what the notice says, with days remaining; where each part is used; approved supply against demand by month, with the first month it runs short and the size of the gap; everything not approved or not verified, kept apart; the replacement questions; the gaps in your records; and what is left to sourcing. Every empty section says so.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Supply chain and inventory](https://fullypowered.ai/functions/supply-chain-and-inventory/), where one end-of-life date can reach several builds at once.
- [Procurement and suppliers](https://fullypowered.ai/functions/procurement-and-suppliers/), where the notice arrives and the purchasing proposals are made.
- [Hardware and physical technology](https://fullypowered.ai/industries/hardware-and-physical-technology/), where one small part can stop a whole product.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/), where purchased components feed the build plan.
- [Consumer brands](https://fullypowered.ai/industries/consumer-brands/), where a connected or electronic product depends on a few bought-in components.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/), where notices land in a buyer's inbox and the where-used picture lives in a few heads.
- [Growth and scaling](https://fullypowered.ai/situations/growth-and-scaling/), when more products share more parts than one person can hold in mind.

## What has to change for your company

Check that your exports have the default column headers listed in the template, or rename them before you run it. Say which roles answer replacement questions (usually component engineering) and which decide purchases (sourcing). Decide whether reserved stock is already counted in your demand plan; the template assumes it is not. Keep your alternates list current, with a status and an approver for every row, because the brief treats only approved alternates as approved. It runs in ChatGPT, Claude, Copilot or Gemini from the files you paste in; it needs no access to any system.

## What has been checked

Fully Powered AI wrote this capability template. It was editorially reviewed on 10 November 2026. It was tried on its invented example in Claude on 10 November 2026, and the record is published with it. It has not yet been tested in a client environment, and it has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past notice your sourcing lead already knows well, plus cases written in advance: a part in the notice that is not on your list, a lifecycle record that disagrees with the notice, an order with no due date, a header that does not match. The sourcing lead checks every figure against the exports before anyone relies on it. [Pilot acceptance-test preparation](https://fullypowered.ai/capabilities/pilot-acceptance-test-preparation/) builds that test set, and [what we test before we call an AI workflow ready](https://fullypowered.ai/insights/what-we-test-before-a-workflow-is-ready/) describes the record we keep.

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

- [Supplier risk alert brief](https://fullypowered.ai/capabilities/supplier-risk-alert-brief/)
- [Inventory reorder plan](https://fullypowered.ai/capabilities/inventory-reorder-plan/)
- [Kit component availability check](https://fullypowered.ai/capabilities/kit-component-availability-check/)

## Make it yours

This is the starting version. Fully Powered AI adapts capabilities to how your company works, proves them on real work and rolls them out to the roles that use them. [Talk with us](https://fullypowered.ai/contact/).
