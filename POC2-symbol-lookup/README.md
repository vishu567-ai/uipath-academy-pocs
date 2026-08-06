# POC2 - Symbol Lookup

## Problem
Given one or more stock symbols as input, look up their market data and output the results to a separate Excel file.

## Approach
- Reads source stock data from an Excel workbook (`Symbol Da...xlsx`) with columns: Symbol Name, LTP, CHNG, %CHNG, OPEN, HIGH, LOW, PREV. CLOSE, VOLUME (shares), VALUE (₹ Lakhs), 52W H, 52W L, 30D %CHNG
- Input Dialog ("Symbol Lookup") takes one or more symbol names, comma-separated
- Looks up each entered symbol's row of data from the source
- Writes results to `SymbolOutput.xlsx`, creating a separate sheet per symbol (e.g. NBCC, SUZLON, HUDCO)

## What I'd do differently
- Add validation/error handling for symbols not found in the source data
- Consolidate output into a single sheet with rows per symbol instead of one sheet per symbol, for easier downstream use
- Parameterize the source file path instead of a hardcoded local path

## Screenshot / Demo
[Watch demo](./poc2-demo.mp4) — bot takes comma-separated stock symbols as input, looks up each symbol's market data, and writes results to a per-symbol sheet in the output workbook.
