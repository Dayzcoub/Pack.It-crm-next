# 25 Warehouse — Inventory Report No Versioning Note

## 10.189. Inventory report versioning

Decision: inventory reports should be stored in history, but they do not need versioning or outdated status.

Rules:
- store each generated inventory report as a separate history record;
- do not mark previous inventory reports as outdated when a new one is generated;
- do not require version numbers for reports generated from the same inventory session;
- keep generated date, author, source inventory session, and file reference where available.

Purpose:
- keep inventory report history simple;
- avoid unnecessary document version logic;
- allow multiple reports to exist without treating older reports as invalid.

MVP approach:
- document history yes;
- versioning no;
- outdated status no;
- each generated report is a separate internal document record.
