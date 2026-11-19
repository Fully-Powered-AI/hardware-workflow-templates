# Product configuration margin sheet

One worksheet for a quoted configuration: price, costed parts, assembly and freight, margin against your floor, and open assumptions. People decide.

> [!TIP]
> **Missing a template that is not listed here, or want these customized for your organization? Reach out to us.** This is a template, made to be customized and deployed. FullyPowered AI customizes and builds AI workflows, connects them to your business systems, installs them in your agents and puts them in the hands of the people who own the work. [See Product configuration margin sheet on our website](https://fullypowered.ai/workflows/product-configuration-margin-sheet/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-product-configuration-margin-sheet&from=gh-product-configuration-margin-sheet). Not sure where to start? Email hello@fullypowered.ai and a person will answer.

**Quick start**

1. Read EXAMPLE.md to see what a good result looks like.
2. Copy all of TEMPLATE.md into your assistant, then give it your own inputs, or the invented ones from EXAMPLE.md.
3. Read what comes back. It marks what it checked and what is left for you.

*Workflow template · Hardware and physical technology · Finance and accounting · version 0.1.0 · [Workflows Directory](https://fullypowered.ai/workflows/product-configuration-margin-sheet/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-product-configuration-margin-sheet&from=gh-product-configuration-margin-sheet)*

## The outcome

Before a configuration is quoted, the people who own the price see what it rests on. The worksheet sets the proposed unit price beside the cost of the parts, the assembly time, the freight and any one-off charges your own rules spread over the units, and shows the margin that is left and where it stands against your margin floor.

What the costs do not yet cover is written down, not hidden. A part with no quote, a tooling charge with no rule for spreading it, a volume that is only a forecast, a cost older than your limit and a cost type nobody supplied each appear as a numbered assumption, with the amount at stake where one can be worked out. The worksheet shows how much room the margin leaves before the floor, so the owner can see whether the open items could change the answer.

Finance validates how each cost was treated. The commercial owner decides the price. Engineering confirms the configuration. The worksheet does none of these, and nothing in it goes to the customer.

## Who starts the work, and when

Whoever prepares the quote in sales, or the sales operations coordinator, starts it when a configuration is about to be quoted, using the costed bill of materials and the estimates on hand that day. It is run again when a part is quoted, the quantity moves or the proposed price changes, so the sheet follows the quote as it stands.

## What they supply

- The quote request: the configuration, the quantity, the proposed unit price and whether the volume is committed or only forecast.
- The costed bill of materials: each part, how many go into one unit, its unit cost, how that cost is known and the date of the cost.
- The assembly estimate: the steps, the minutes for each and the hourly rate.
- The freight inputs: units per shipment and the cost of a shipment.
- Other costs: tooling, certification, support, warranty and similar charges.
- Your approved allocation rules for those costs.
- The settings: today's date, the currency, your margin floor, the age at which a cost is stale, an optional second volume and the people who decide.

## What comes out

One worksheet in a fixed order: the quote, the materials, the assembly, the freight, the other costs and how each was allocated, the margin and its position against the floor, the volume case if one was supplied, the numbered assumptions, and the decisions for the finance lead and the commercial owner. A section with nothing in it says "None."; a file that was not supplied, a margin floor that is not set and a volume case that was not asked for are each said so plainly.

The worksheet stops rather than guesses when a column header does not match, a unit cost is missing for a line that says it has one, or the currency differs between files. A part with no cost is never counted as zero.

See the worked example with invented data in [EXAMPLE.md](EXAMPLE.md).

## Where it fits

- [Finance and accounting](https://fullypowered.ai/functions/finance-and-accounting/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-product-configuration-margin-sheet&from=gh-product-configuration-margin-sheet), where cost treatment and margin are validated before a price is approved.
- [Sales](https://fullypowered.ai/functions/sales/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-product-configuration-margin-sheet&from=gh-product-configuration-margin-sheet), where the quote is prepared and the question "what does this configuration really cost us" arrives.
- [Hardware and physical technology](https://fullypowered.ai/industries/hardware-and-physical-technology/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-product-configuration-margin-sheet&from=gh-product-configuration-margin-sheet), where one product ships in many configurations and some parts are still unquoted when the customer asks.
- [Manufacturing](https://fullypowered.ai/industries/manufacturing/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-product-configuration-margin-sheet&from=gh-product-configuration-margin-sheet), where assembly time and freight belong in the price.
- [Consumer brands](https://fullypowered.ai/industries/consumer-brands/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-product-configuration-margin-sheet&from=gh-product-configuration-margin-sheet), where bundles and variants are quoted to retail and trade buyers.
- [Established businesses](https://fullypowered.ai/situations/established-businesses/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-product-configuration-margin-sheet&from=gh-product-configuration-margin-sheet), where standard costs were set long ago and quietly aged.
- [Growth & scaling](https://fullypowered.ai/situations/growth-and-scaling/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-product-configuration-margin-sheet&from=gh-product-configuration-margin-sheet), when quotes multiply faster than finance can review them one by one.

It prices one configuration for one quote. It is a different piece of work from [Range margin by channel review](https://fullypowered.ai/workflows/range-margin-by-channel-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-product-configuration-margin-sheet&from=gh-product-configuration-margin-sheet), which compares margin across a range and its channels, from [Discount request review](https://fullypowered.ai/workflows/discount-request-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-product-configuration-margin-sheet&from=gh-product-configuration-margin-sheet), which tests a request to go below list against your policy, from [Price change review](https://fullypowered.ai/workflows/price-change-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-product-configuration-margin-sheet&from=gh-product-configuration-margin-sheet), which weighs a change to published prices, and from [Product landed cost worksheet](https://fullypowered.ai/workflows/product-landed-cost-worksheet/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-product-configuration-margin-sheet&from=gh-product-configuration-margin-sheet), which works out the cost of goods after a shipment arrives.

## What has to change for your company

Fix the column headers of your six inputs once, or map your system's names to the defaults. Decide your margin floor and the age at which a cost counts as stale. Write your allocation rules: how tooling is spread, what percentage of price stands in for support, and which cost types have no rule yet. Name who validates cost treatment, who approves the price and who confirms the configuration. Decide whether an estimate belongs in the total, since the worksheet includes estimates and flags them.

## What has been checked

FullyPowered AI wrote this workflow template. It was editorially reviewed on 10 November 2026. It was tried on its invented example on 10 November 2026 in Claude, by the person who revised it, not blind; the record is published with it, and covers the revised version only for the cases that example contains (an unquoted part, estimates in the total, a stale cost, an unallocated charge, a missing cost type and a volume case below the spread rule's). Rules for a header mismatch, a contradicting line, a duplicate line, a differing currency and missing files have not been run. It has not yet been tested in a client environment. It has not yet been tested as a packaged version in ChatGPT, Claude, Copilot or Gemini.

Testing in your environment means running it on a past quote your finance lead already knows, with cases written in advance: a part with no cost, a tooling charge with no rule, a forecast volume below the volume the tooling was spread over. The finance lead checks every figure against the source files before anyone relies on the sheet. [Pilot acceptance-test preparation](https://fullypowered.ai/workflows/pilot-acceptance-test-preparation/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-product-configuration-margin-sheet&from=gh-product-configuration-margin-sheet) sets those cases up.

- Written by FullyPowered AI.
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

- [Product landed cost worksheet](https://fullypowered.ai/workflows/product-landed-cost-worksheet/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-product-configuration-margin-sheet&from=gh-product-configuration-margin-sheet)
- [Discount request review](https://fullypowered.ai/workflows/discount-request-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-product-configuration-margin-sheet&from=gh-product-configuration-margin-sheet)
- [Price change review](https://fullypowered.ai/workflows/price-change-review/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-product-configuration-margin-sheet&from=gh-product-configuration-margin-sheet)

## Make it yours

This workflow template is an example and a starting point. FullyPowered AI adapts it to how your company works, proves it on real work and rolls it out to the roles that use it. We can also build any other workflow for your company, including one that runs several steps, in a Workflow Sprint or a scoped implementation. [Talk with us](https://fullypowered.ai/contact/?utm_source=github&utm_medium=referral&utm_campaign=workflow-collections&utm_content=hardware-product-configuration-margin-sheet&from=gh-product-configuration-margin-sheet).
