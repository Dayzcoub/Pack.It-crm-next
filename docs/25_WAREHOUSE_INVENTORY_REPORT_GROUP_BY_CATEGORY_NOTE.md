# 25 Warehouse — Inventory Report Group by Category Note

## 10.184. Grouping inventory discrepancies by category

Decision: inventory report discrepancies should be grouped by equipment category.

Rules:
- group discrepancy rows by category in the main inventory report;
- use the same category logic as warehouse items and project equipment where possible;
- examples include sound, light, LED, stage, truss, commutation, cables, cases, power, tools, and other warehouse categories;
- if a category is unknown, place the row in an uncategorized or other group.

Purpose:
- keep the discrepancy report readable;
- make it easier for responsible teams to review their own areas;
- avoid one long unsorted list.

MVP approach:
- apply category grouping to the discrepancies-only report;
- keep the optional full-check checkpoint list grouped where practical;
- keep the report internal and without prices by default.
