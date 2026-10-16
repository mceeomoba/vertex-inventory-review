# Vertex inventory change review

A local-first tool for Shopify inventory operators. Compare a fresh All states inventory CSV against an edited copy before import. Download a review report, not an import file. No store access or account needed.

## Choose a tool

| Weekly task | Free browser tool | What it does not do |
| --- | --- | --- |
| Review quantities you edited before import | [Inventory edit reviewer](https://mceeomoba.github.io/vertex-inventory-review/) | No store connection or import approval |
| Compare earlier and later inventory exports | [Snapshot comparison](https://mceeomoba.github.io/vertex-inventory-review/snapshots.html) | No live monitoring, sale attribution or proof of deletion |
| Preflight a product catalog CSV | [Product CSV preflight](https://mceeomoba.github.io/vertex-inventory-review/products.html) | No automatic cleanup, file rewriting or full Shopify validation |
| Review omitted Ecwid option and variation rows | [Ecwid Import Scope Check](https://mceeomoba.github.io/vertex-inventory-review/ecwid-scope.html) | No store connection, corrected import file or import approval |

[Quick start and fictional inventory sample downloads](https://mceeomoba.github.io/vertex-inventory-review/guide.html). Each tool has a fictional example button. No store is needed to try it. Use the tool's Scope and privacy section before choosing real files.

## Ecwid CSV imports: review the rows you leave out

A small variation update can have a wider scope than the rows you changed. Ecwid's [variation-import guide](https://support.ecwid.com/hc/en-us/articles/8678710875164-Case-study-3-Importing-a-product-with-options-and-variations) says that importing variation data deletes existing variations for that product that are not present in the file. Its [option and input-field guide](https://support.ecwid.com/hc/en-us/articles/8678451883036-Case-study-2-Importing-a-product-with-options-or-input-fields) describes replacement of omitted options, input fields and variations when importing new option or input-field data.

For example, suppose a fictional product has Size=S, Size=M and Size=L variations. A planned variation import containing only S and L leaves M out. That missing row deserves review even if the intended change was just a price update. This is a fictional example, not a customer result.

Before importing:

1. Keep an untouched, fresh, complete export from the same store, including relevant product, option and variation rows.
2. Compare that export with the planned current-format, comma-separated CSV.
3. Review omitted identities against Ecwid's current documentation. Do not treat a clean report as permission to import. Back up and test changes in Ecwid.

[Try the free Ecwid Import Scope Check](https://mceeomoba.github.io/vertex-inventory-review/ecwid-scope.html), or use its fictional example without real files. The page compares files in your browser without uploading their contents or connecting to your store. It lists omitted options, input fields and variation combinations within supported replacement scopes. It does not rewrite files, validate prices, stock or images, or check every import rule. Incomplete exports, changed IDs/SKUs, translated option headers and ambiguous matches need manual review. For straightforward edits, Ecwid's native Bulk Product Editor may avoid a CSV import entirely.

Vertex's free experiment is for store owners in the US, UK, Canada and Australia. Independent of Ecwid and Lightspeed. No paid service, merchant validation or revenue is claimed. Documentation checked October 16, 2026.

## Public feedback

Posted for the Vertex project; AI-assisted.

[Project feedback issue](https://github.com/mceeomoba/vertex-inventory-review/issues/1) or [structured feedback form](https://github.com/mceeomoba/vertex-inventory-review/issues/new?template=feedback.yml). GitHub account required. Your username and everything submitted, including screenshots and links, are public. Do not include identifying details, store exports, customer or order data, credentials, private links, or confidential information. Fictional examples only. This is not a support or security-reporting channel. Respondents' identities will not be reused for outreach. Independent of Shopify, not an official Shopify app. No customer use or demand is claimed.

## Use

Open https://mceeomoba.github.io/vertex-inventory-review/ . Export steps and fictional sample downloads: https://mceeomoba.github.io/vertex-inventory-review/guide.html .

Download `index.html` and open it in a modern browser. Choose your fresh export and edited file, then select Review changes. The fictional example works without files. Selected files stay in that browser; the tool has no network calls, external scripts or analytics. Do not upload private inventory exports into this repository or issues.

Flags stale snapshot quantities, unmatched identities, invalid new quantities and not-stocked/current-value exceptions. Stops on duplicate identities, missing required columns, malformed CSV and missing variant fields. Uses handle + option values + case-sensitive location, never SKU alone.

Blank new quantities are skipped, zero and negative whole numbers are explicit instructions. This is a review aid, not import approval. Keep Shopify's On hand (current) safety validation and review Shopify's own import summary. Available-only exports are not supported.

## Version 0.2

Review counts, exceptions-only view, exact-case location filter and case-insensitive handle/option search. Filters affect the screen only; the full CSV report always contains every compared instruction. Changing either file clears old results so an earlier review is not mistaken for the newly selected files.

## Test

Run `node test.cjs` (34 edit-review tests), `node snapshot-test.cjs` (28 snapshot tests), and `node product-test.cjs` (38 product-preflight tests). All 100 are synthetic-fixture tests, not merchant validation. No live merchant file, store import, revenue or customer deployment is claimed. Each HTML file contains its own engine and can be opened locally in a modern browser. Test scripts must sit beside their matching HTML files.

## Product decision - October 14, 2026

Vertex is moving away from custom diagnosis and institutional bids to small self-serve operations tools for retailers. The first piece is a free, offline inventory-change reviewer. It addresses the public operational request to inspect bulk inventory edits without changing a store. This is an initial product experiment, not proof of a unique market or paid demand. No payment collection is enabled. The next commercial gate is real operator use and feedback, not more unrelated prototypes.

Initial audience: remote operators for US, UK, Canadian and Australian stores. The release contains no regional compliance claims. Independent of Shopify, not an official Shopify app.

## Sources and limits

- Shopify inventory CSV format, checked October 14, 2026: https://help.shopify.com/en/manual/products/inventory/getting-started-with-inventory/inventory-csv
- Public operator request for bulk inventory edits, discovery only, not an identified customer: https://www.reddit.com/r/shopify/comments/1ure2dg/mass_editing_inventory_quantities_help/

The official format already includes stale-value protection. This tool makes a separate human-readable change review; it does not replace that protection. No claim is made that other tools do not offer similar checks.

## Additional sources

- Product CSV checks: https://help.shopify.com/en/manual/products/import-export/using-csv

Product preflight supports a limited set of current and common legacy headers, required product fields, variant-option dependencies, price/status formats, packed-size completeness and clearing risks, and review notes for repeated variants or reused SKUs. It does not modify an export. Blank continuation titles and intentional repeated/image rows require care, not automatic deletion. Snapshot added/missing labels describe export membership, not a store event.

Product CSV preflight v0.2 also checks the four packed-product fields, cm/in unit values, blank-size clearing on variant-like rows and the Requires shipping=false clearing rule. It does not validate dimensional ranges or actual store shipping settings.
