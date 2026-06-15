# 25 Warehouse — Inventory Report Summary Note

## 10.187. Inventory report summary

Decision: the inventory report should include a short summary at the top.

Rules:
- show total number of discrepancies;
- show missing items count where applicable;
- show extra items count where applicable;
- show rows requiring review where applicable;
- keep the summary compact and internal.

Purpose:
- make the inventory result visible at a glance;
- help managers and warehouse users quickly understand the scale of discrepancies;
- avoid reading the whole report just to understand the overall result.

MVP approach:
- add a compact summary block near the top of the inventory report;
- keep the detailed discrepancy rows grouped by category;
- keep the report internal and without prices by default.
