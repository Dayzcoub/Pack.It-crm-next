# 25 Warehouse — Inventory Report Internal Only Note

## 10.182. Inventory report visibility and prices

Decision: the inventory report is an internal warehouse document only.

Rules:
- no client-facing version is needed for MVP;
- do not include prices by default;
- the report is intended for warehouse, management, and internal audit workflows;
- access is controlled by internal roles and permissions.

Purpose:
- keep inventory reporting focused on stock control;
- avoid exposing internal warehouse data to clients;
- avoid mixing inventory count data with commercial documents.

MVP approach:
- generate inventory report as internal PDF/print/document;
- exclude prices by default;
- keep client quote/commercial documents separate.
