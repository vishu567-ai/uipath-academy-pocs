# POC5 - Vendor Inventory Automation (REFramework)

## Problem
For each vendor code in a queue, log into ACME System 1's Vendor Inventory portal, look up that vendor's inventory (supplier, item, quantity, cost/unit), and export the results — processing multiple vendor codes as a batch of transactions, with resilience against failures.

## Approach
- Converted into full REFramework structure: `Login`, `VendorDataExtraction`, `Process`, `GetTransactionData`, `SetTransactionStatus`, `InitAllSettings`, `KillAllProcesses`, `InitAllApplications`, `SendEmail`
- Logs into `acme-test.uipath.com`, navigates to the Vendors - Vendor Inventory page
- For each transaction (vendor code, e.g. DE325476), selects the code from a dropdown, clicks "Check Inventory," and extracts the resulting table (Supplier code, Supplier, Item, Unit, QTY, COST/Unit)
- Writes extracted data to `Output.xlsx`
- Each transaction wrapped in Try/Catch inside "Process Transaction," logging Success / Business Exception / System Exception per item
- Loop terminates gracefully once all transaction items are processed

## What broke (and how it got fixed)
- Hit a strict selector failure logging in (`Type Into 'Email'` target not found) — resolved by adjusting the selector to match the actual login form element
- Hit an "Index was outside the bounds of the array" exception when the transaction loop tried to fetch the next item after the queue was exhausted — this is expected REFramework behavior signaling the end of the transaction list, not a real failure, but worth noting for anyone reading the logs
- Cascade of file-locking issues while iterating (OneDrive/output file) — resolved by ensuring the output file wasn't open elsewhere during writes

## What I'd do differently
- Move from a local Excel-driven queue to actual Orchestrator queues for a closer-to-production REFramework setup
- Add more specific exception handling to distinguish "queue exhausted" from genuine system exceptions, rather than relying on the array-index error as an implicit signal

## Screenshot / Demo
[Watch demo](./poc5-demo.mp4) — bot logs into ACME System 1, loops through vendor codes, extracts inventory data per vendor, and writes results to Output.xlsx using full REFramework transaction handling.
