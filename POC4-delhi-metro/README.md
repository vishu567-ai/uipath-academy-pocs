# POC4 - Delhi Metro Self-Service Machine Simulation

## Problem
Simulate a Delhi Metro self-service ticket machine ("Journey Planner"): take a source/destination station, look up the fare, check it against the available card balance, and either issue the ticket or reject the transaction if the balance is insufficient. Support booking multiple tickets in one session.

## Approach
- Built with hand-authored XAML (not fully drag-and-drop through the Studio designer)
- "Journey Planner" input dialog collects the source station (and destination)
- Reads fare/station data from `Metro Self-Service Machine Assignment.xlsx` into a DataTable
- Compares the required fare against current balance; if balance is insufficient, shows a Message Box (e.g. "Insufficient Balance! Current Balance: ₹28, Fare Required: ₹72") and blocks the booking
- Wraps the whole flow in Try/Catch for error handling
- Uses a Do-While loop with a "Continue Booking" prompt ("Do you want to book another ticket? Yes/No") to support multiple bookings per run

## What broke (and how it got fixed)
- Hit a `CollectionConverter` error while working with the DataTable/collection data during development — this was the main blocker on this POC (note: confirm here whether this was fully resolved or worked around by the time of the final recording)

## What I'd do differently
- Move more of the logic from hand-authored XAML into Studio's visual designer where possible, for easier maintenance
- Add input validation for station names not present in the source data

## Screenshot / Demo
[Watch demo](./poc4-demo.mp4) — bot takes a source station as input, checks the fare against balance, blocks booking on insufficient balance, and loops to support multiple ticket bookings.
