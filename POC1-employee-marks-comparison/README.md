# POC1 - Employee Marks Comparison

## Problem
Given multiple employees' marks across several subjects/modules for a given week, identify who scored the highest and summarize their scores.

## Approach
- Input Dialogs collect employee names (Employee 1, Employee 2, ...) as text input
- Reads marks data from an Excel source (`EmployeeMarksComparision.xlsx`) covering subjects: RPA, SDLC, QA, AI
- Compares total/individual marks across the entered employees for the specified week
- Outputs the result via a Message Box, e.g.: "Austin has the highest marks in Week3! RPA: 45, SDLC: 43, QA: 28, AI: 73"

## What I'd do differently
- Replace the Message Box output with a written Excel/report output for better auditability
- Add input validation (e.g. handle employee names not found in the source file)
- Parameterize the week instead of relying on a fixed structure, if not already done

## Screenshot / Demo
See recorded run: bot takes employee names as input, reads the marks workbook, and displays the highest scorer with a per-subject breakdown.
