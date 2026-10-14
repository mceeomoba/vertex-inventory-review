# Vertex inventory change review

A local-first tool for Shopify inventory operators. Compare a fresh All states inventory CSV against an edited copy before import. Download a review report, not an import file. No store access or account needed.

## Use

Download `index.html` and open it in a modern browser. Choose your fresh export and edited file, then select Review changes. The fictional example works without files. Selected files stay in that browser; the tool has no network calls, external scripts or analytics. Do not upload private inventory exports into this repository or issues.

Flags stale snapshot quantities, unmatched identities, invalid new quantities and not-stocked/current-value exceptions. Stops on duplicate identities, missing required columns, malformed CSV and missing variant fields. Uses handle + option values + case-sensitive location, never SKU alone.

Blank new quantities are skipped, zero and negative whole numbers are explicit instructions. This is a review aid, not import approval. Keep Shopify's On hand (current) safety validation and review Shopify's own import summary. Available-only exports are not supported.

## Test

Run `node test.cjs`. Version 0.1 passes 24 synthetic-fixture tests. No live merchant file, store import, revenue or customer deployment is claimed.

## Product decision - October 14, 2026

Vertex is moving away from custom diagnosis and institutional bids to small self-serve operations tools for retailers. The first piece is a free, offline inventory-change reviewer. It addresses the public operational request to inspect bulk inventory edits without changing a store. This is an initial product experiment, not proof of a unique market or paid demand. No payment collection is enabled. The next commercial gate is real operator use and feedback, not more unrelated prototypes.

Initial audience: remote operators for US, UK, Canadian and Australian stores. The release contains no regional compliance claims. Independent of Shopify, not an official Shopify app.

## Sources and limits

- Shopify inventory CSV format, checked October 14, 2026: https://help.shopify.com/en/manual/products/inventory/getting-started-with-inventory/inventory-csv
- Public operator request for bulk inventory edits, discovery only, not an identified customer: https://www.reddit.com/r/shopify/comments/1ure2dg/mass_editing_inventory_quantities_help/

The official format already includes stale-value protection. This tool makes a separate human-readable change review; it does not replace that protection. No claim is made that other tools do not offer similar checks.
