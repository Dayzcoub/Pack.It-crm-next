# 25 Warehouse — Problem Report Status Change Confirmation Note

## 10.202. Confirmation before automatic warehouse status change

Decision: before applying an automatic warehouse item status change from a problem report resolution, the system should ask the user for confirmation.

Rules:
- show a confirmation step before changing the warehouse status;
- the confirmation text should clearly describe the consequence of the selected action;
- examples: write off item, send item to repair, move item to quarantine, return item to active stock;
- do not silently change warehouse status after resolution selection;
- log the confirmed status change with user, date, time, source report/problem row, and selected resolution.

Purpose:
- prevent accidental write-off or wrong stock status changes;
- make the user aware of the operational consequence;
- keep problem resolution and warehouse status synchronized, but controlled.

MVP approach:
- display a simple confirmation dialog before status change;
- after confirmation, apply the mapped warehouse status automatically;
- keep the report internal by default.
