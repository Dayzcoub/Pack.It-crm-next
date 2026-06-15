# 25 Warehouse — Inventory Report History Note

## 10.188. Inventory report history

Decision: generated inventory reports should be stored in document history.

Rules:
- do not treat the inventory report as a one-time PDF download only;
- each generated report is stored as a history record;
- store who generated the report and when;
- store the inventory session or source data reference;
- store PDF/file reference if a file is generated;
- keep the report internal and without prices by default.

Purpose:
- keep an audit trail of generated inventory reports;
- allow managers to reopen earlier reports;
- avoid losing important inventory discrepancy records after download.

MVP approach:
- add inventory report document history;
- show generated reports in the warehouse document center or related inventory session;
- reuse general warehouse document history patterns where possible.
