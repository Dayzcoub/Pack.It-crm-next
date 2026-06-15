# 25 Warehouse — Handout Act Outdated Reason Note

## 10.166. Reason for outdated handout act version

Decision: when a handout act version becomes outdated, the history should show the reason.

Rules:
- older generated act versions remain in history;
- when a new version is generated, the previous version is marked as outdated;
- outdated versions should have a reason field;
- the reason may be entered manually or generated from the change context where possible.

Examples:
- items were added;
- recipient was changed;
- the handout was corrected;
- the document was regenerated after warehouse changes.

Purpose:
- make document history easier to understand;
- show why a new version exists;
- avoid confusion between current and outdated act versions.

MVP approach:
- add outdated reason field to generated handout act history;
- show the reason in the document history list/card;
- keep the previous PDF or metadata available for users with proper permissions.
