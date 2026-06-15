# 25 Warehouse — Problem Report Pending Resolution Note

## 10.199. Creating a report before final resolution

Decision: an internal warehouse problem/loss report can be created before the final resolution is known.

Rules:
- resolution/action is not mandatory before report creation;
- if no final resolution is set, the report should have a pending resolution status;
- use a clear status such as requires resolution;
- the report can later be updated or linked to an updated problem row when the resolution is known;
- keep the report internal by default.

Purpose:
- allow the team to document the problem immediately;
- avoid delaying report creation while waiting for a decision;
- keep unresolved warehouse problems visible and controlled.

MVP approach:
- allow creating a report with empty resolution/action;
- mark such reports as requires resolution;
- show this status in the warehouse document history or problem report list.
