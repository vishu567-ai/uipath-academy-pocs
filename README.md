# UiPath Academy POCs

A collection of 5 proof-of-concept automations built while completing UiPath Academy coursework during my internship at TSP. These are academy-assigned training exercises, not self-scoped projects — documented here as a record of the work and the debugging that came with it.

| # | POC | Focus |
|---|-----|-------|
| 1 | [POC1-employee-marks-comparison](./POC1-employee-marks-comparison) | Compares employee marks/scores and outputs results |
| 2 | [POC2-symbol-lookup](./POC2-symbol-lookup) | Takes symbol(s) as input via dialog, processes and writes results to an output Excel file |
| 3 | [POC3-invoice-generator](./POC3-invoice-generator) | Automated invoice generation on invoice-generator.com, with a Tab-key navigation workaround for unreliable selectors |
| 4 | [POC4-delhi-metro](./POC4-delhi-metro) | Delhi Metro fare/route simulation, hand-authored XAML |
| 5 | [POC5-vendor-inventory](./POC5-vendor-inventory) | Vendor inventory processing loop with Try/Catch handling, partially converted to REFramework |

## Stack
UiPath Studio, Excel/DataTable activities, Orchestrator (queues, Config.xlsx-based settings)

## Note
These were built as structured training exercises, so the "problem" in each README is the academy's assignment brief — the interesting part is usually in the "what broke" section.
