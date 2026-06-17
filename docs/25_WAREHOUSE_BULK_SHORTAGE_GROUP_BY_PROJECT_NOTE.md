# 25 Warehouse — Bulk Shortage Group by Project Note

## 10.247. Warehouse keeper shortage summary grouping

Decision: shortage entries in the warehouse keeper summary should be grouped by source project.

Rules:
- show shortages under the project where they were detected;
- project group should include project name/ID and event context if available;
- each shortage row should show what item/row is missing;
- each shortage row should show planned quantity, confirmed quantity, and missing quantity;
- warehouse keeper can open the project group and resolve or assign entries from there.

Example display:
- Project: Event A
  - XLR 10 m: missing 3 pcs
  - PowerCON 5 m: missing 2 pcs

Purpose:
- preserve project context;
- make investigation easier;
- avoid one unsorted problem pile across all projects.

MVP approach:
- group shortage list by source project;
- inside each group, list missing rows and missing quantities;
- allow opening each shortage item for follow-up.
