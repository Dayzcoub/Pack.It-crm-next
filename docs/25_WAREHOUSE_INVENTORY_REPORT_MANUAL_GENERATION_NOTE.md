# 25 Warehouse — Inventory Report Manual Generation Note

## 10.181. Inventory report generation

Decision: the inventory report should be generated manually by button when needed.

Rules:
- do not automatically generate an inventory report after every inventory count;
- allow manual generation from a completed or selected inventory session;
- the report is created only when the user needs a document;
- keep the report internal by default.

Purpose:
- avoid unnecessary documents;
- support small teams that do not need formal paperwork every time;
- still provide a document for review, audit, or management when needed.

MVP approach:
- add a manual Generate report button where appropriate;
- use the selected inventory data as the report source;
- store generated reports in document history if document history is implemented for warehouse reports.
