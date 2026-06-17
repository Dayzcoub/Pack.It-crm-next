# 25 Warehouse — Open Shortage and History Visibility Note

## 10.248. Open shortages and resolved history visibility

Decision: warehouse keeper summary should show only open shortage entries by default. Resolved/closed history should be hidden in a collapsible section or moved to a separate history page.

Rules:
- main warehouse keeper summary shows only open/current shortages;
- shortage groups remain grouped by source project;
- closed/resolved shortage entries do not clutter the main summary;
- resolved history is still available for audit and investigation;
- history can be shown in a collapsible history block or on a separate page.

Purpose:
- keep the warehouse keeper daily view clean;
- focus attention on unresolved shortages;
- preserve history without overloading the main workspace.

MVP approach:
- default filter: open only;
- optional history access via collapsible block or separate history screen;
- keep project grouping for open shortages.
