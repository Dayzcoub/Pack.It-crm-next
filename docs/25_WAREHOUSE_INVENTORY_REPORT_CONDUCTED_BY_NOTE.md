# 25 Warehouse — Inventory Report Conducted By Note

## 10.185. Inventory report responsible person

Decision: the inventory report only needs a general field showing who conducted the inventory count.

Rules:
- do not require a separate responsible person for every equipment category;
- show the user or users who conducted the inventory;
- store date and time of the inventory session;
- keep category grouping for discrepancy rows, but not category-level responsibility.

Purpose:
- keep the report simple;
- avoid unnecessary management overhead;
- support small teams where one person may check multiple categories.

MVP approach:
- add conducted-by field to the inventory report;
- allow one or multiple users where practical;
- keep the report internal and without prices by default.
