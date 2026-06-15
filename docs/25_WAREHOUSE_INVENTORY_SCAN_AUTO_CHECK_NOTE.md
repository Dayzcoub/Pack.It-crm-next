# 25 Warehouse — Inventory Scan Auto Check Note

## 10.231. Inventory scanner auto-check behavior

Decision: in inventory mode, scanning an item should immediately mark it as checked. No extra confirmation card is required by default.

Rules:
- scanner launched from inventory works in inventory context;
- successful scan immediately marks the item as checked;
- no additional confirmation screen is shown for normal scan;
- system should give clear feedback that the item was checked;
- duplicate scan should not create duplicate count errors and should show already checked state;
- exceptions or mismatches can still open a warning/problem flow.

Purpose:
- make mobile inventory fast;
- reduce unnecessary taps;
- support continuous scanning workflow.

MVP approach:
- scan item ID;
- mark as checked in current inventory session;
- show success feedback and remain ready for the next scan.
