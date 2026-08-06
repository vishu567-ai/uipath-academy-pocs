# POC3 - Invoice Generator Bot

## Problem
Automate invoice creation on invoice-generator.com by reading invoice data (biller, client, line items) from Excel and filling out the web form automatically.

## Approach
- Reads invoice data from `Invoicing.xlsx` (From, Bill To, line items with description/quantity/rate)
- Navigates to `https://invoice-generator.com/` via browser automation
- Types billing details (From: "TSP", Bill To: client name), date, payment terms, and due date into form fields
- Loops through line items, adding rows dynamically ("+ Line Item") and filling description, quantity, and rate for each — amount and subtotal calculate automatically on the page
- Uses a Tab-key navigation workaround for moving between dynamically-added line item fields, since selectors for newly-created rows were unreliable

## What broke (and how it got fixed)
- Selectors for line-item fields broke when new rows were added dynamically (the site generates new DOM elements per line item) — worked around by using Tab-key navigation to move focus between fields instead of relying on fresh selectors for each new row

## What I'd do differently
- Investigate a more robust selector strategy (e.g. dynamic/wildcard selectors, anchoring to row index) instead of relying on Tab order, which is fragile if the page layout changes
- Add error handling for cases where the page structure or field count differs from expected

## Screenshot / Demo
[Watch demo](./poc3-demo.mp4) — bot reads invoice data from Excel and fills out the invoice-generator.com form, including multiple line items, using a Tab-key navigation workaround.
