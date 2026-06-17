# 25 Warehouse — Bulk Shortage Project Problem Note

## 10.245. Bulk shortage in project/warehouse problem list

Decision: bulk item shortage should be added to the common project/warehouse problem list as a follow-up item.

Rules:
- if confirmed quantity is less than planned quantity, create shortage problem entry;
- problem entry must reference the project after which shortage was detected;
- problem entry should include item/row name, planned quantity, confirmed quantity, and missing quantity;
- shortage remains open until resolved;
- resolution may be: item found, quantity corrected, or formal removal/write-off process completed;
- problem entry should be visible to users responsible for warehouse follow-up.

Purpose:
- make shortages visible after project return/handout processing;
- preserve project context for later investigation;
- avoid silent loss of bulk quantities.

MVP approach:
- create problem entry when document is confirmed with bulk shortage;
- store source project ID/name;
- show label: shortage after project;
- close only after follow-up action.
