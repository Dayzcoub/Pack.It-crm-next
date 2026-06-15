# 25 Warehouse — Problem Report History Retention Note

## 10.197. Internal problem/loss report history and retention

Decision: internal warehouse problem/loss reports should be stored in warehouse document history, with limited retention for MVP.

Rules:
- store generated internal problem/loss reports in warehouse document history;
- keep a limited amount of history rather than storing these reports forever;
- default MVP retention guideline: last 6 months;
- the exact retention period can later become an admin setting;
- store created-by, created-at, source problem rows, and file reference where available.

Purpose:
- keep recent warehouse problems available for review;
- avoid unlimited growth of operational problem documents;
- support practical management review without overcomplicating storage.

MVP approach:
- keep reports from the last 6 months by default;
- allow older records to be hidden, archived, or cleaned according to future admin settings;
- keep the report internal by default.
