# 25 Warehouse — Problem Report Resolution Note

## 10.198. Problem/loss report resolution field

Decision: the internal warehouse problem/loss report should include a resolution/action field.

Rules:
- record what was done or what decision was made for each problem;
- if multiple problems are combined into one report, each problem can have its own resolution/action;
- the resolution can be selected or written depending on future UI implementation;
- keep the report internal by default.

Example resolutions/actions:
- write off;
- send to repair;
- found in warehouse;
- return to active stock;
- charge responsible party;
- wait for review;
- move to quarantine;
- replace item;
- no action needed.

Purpose:
- document not only the problem, but also the follow-up decision;
- support accountability and warehouse cleanup;
- make the report useful as an operational close-out document.

MVP approach:
- add resolution/action field to the internal problem/loss report;
- allow empty/pending state if the decision is not known yet;
- keep created-by, source rows, attachments, cause, and resolution together in the report history.
