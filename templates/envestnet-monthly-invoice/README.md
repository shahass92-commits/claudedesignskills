# Envestnet Monthly Invoice — Email Template

Compass Nexus iQ HTML email that sends the monthly tax invoice and the MIS summary in one message (dark glass cards, blue/gold, pill buttons like Apple's).

- Built so it works in email clients: tables, inline styles, no JS, 600px wide, stacks on phones
- Buttons: Approve (mailto), Request Clarification (mailto), Call (tel), website link
- Every business value is a `{{PLACEHOLDER}}`. Filled copies are **not** kept in this repo because they contain PAN/GSTIN and billing data.

## Placeholders

| Group | Placeholders | Source |
|---|---|---|
| Invoice | `INVOICE_NO`, `INVOICE_DATE` (e.g. 25 Sep 2026), `INVOICE_DATE_LONG` | Invoice register |
| Cycle | `CYCLE_START`, `CYCLE_END`, `CYCLE_START_LONG`, `CYCLE_END_LONG`, `CYCLE_MONTH` (e.g. September 2026), `CYCLE_MONTH_NAME`, `CYCLE_MONTH_URL` (URL-encoded, e.g. `September%202026`), `MIS_FILENAME` | MIS workbook |
| Totals | `TOTAL` (74,102 style), `TOTAL_2DP`, `TOTAL_IN_WORDS`, `TRIPS`, `BILLABLE_KM`, `VEHICLES`, `EMPLOYEES` (sum of Pax) | MIS `Dashboard` / `Trip Log` |
| KPIs | `EV_PCT`, `AVG_KM_TRIP`, `AVG_COST_KM` | MIS `Vehicle Consolidation` |
| Per vehicle type (`EV`, `MARAZZO`, `ERTIGA`, `DZIRE`) | `*_TRIPS`, `*_KM`, `*_RATE`, `*_AMOUNT`, `*_PCT` (also sets the bar width) | MIS `Trip Data` |
| Reconciliation | `DEDUCTED_KM`, `NIL_KM_COUNT`, `NIL_KM_DATES` | MIS `Trip Log` |
| Vendor | `VENDOR_PROPRIETOR`, `VENDOR_ADDRESS_LINE1/2`, `VENDOR_PAN`, `VENDOR_GSTIN` (full 15-char, incl. state code), `SIGNATORY_NAME`, `SIGNATORY_TITLE` | Business profile |
| Customer | `CUSTOMER_LEGAL_NAME`, `CUSTOMER_ADDRESS_LINE1/2/3`, `CUSTOMER_GSTIN` | Customer account |
| Contact | `REPLY_TO_EMAIL`, `CC_EMAIL`, `PHONE_E164`, `PHONE_DISPLAY`, `WEBSITE_URL`, `WEBSITE_LABEL`, `WEBSITE2_URL`, `WEBSITE2_LABEL` | Business profile |

## Monthly checklist
1. Fill every placeholder from the verified MIS workbook. No `{{` may remain.
2. Line-item amounts must add up to `TOTAL`, and `*_PCT` must add up to about 100.
3. Confirm the billing entity: use the PAN/GSTIN of the entity that holds the Envestnet agreement. Don't mix up the proprietor and firm identities.
4. Attach the invoice PDF and the MIS workbook, then send as the HTML body.
