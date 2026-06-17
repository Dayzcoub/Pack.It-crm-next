# 25 Warehouse — Bulk Shortage Warehouse Summary Note

## 10.246. Bulk shortage assignment and warehouse summary

Decision: bulk shortage is added to the summary for the assigned warehouse keeper. The warehouse keeper then resolves it personally or assigns another responsible person.

Rules:
- shortage entry is linked to the project after which it was detected;
- shortage appears in the assigned warehouse keeper summary/task area;
- system does not automatically assign a separate responsible person at creation;
- assigned warehouse keeper can investigate personally;
- assigned warehouse keeper can delegate/assign a responsible person manually;
- shortage remains open until resolved.

Resolution options:
- missing quantity found;
- quantity corrected manually after review;
- formal removal/write-off process completed.

Purpose:
- keep shortage ownership clear;
- avoid automatic wrong assignments;
- preserve project context for investigation.

MVP approach:
- create shortage problem entry;
- attach source project ID/name;
- route to assigned warehouse keeper summary;
- allow manual responsible assignment.
