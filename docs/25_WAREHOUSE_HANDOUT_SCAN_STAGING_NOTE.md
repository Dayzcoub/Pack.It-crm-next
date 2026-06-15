# 25 Warehouse — Handout Scan Staging Note

## 10.233. Handout scanner staging behavior

Decision: in project handout mode, scanning an item should not immediately perform the final handout action. Scanned items first go to a scanned/staged list, and the final handout is confirmed with a separate button.

Rules:
- scanner launched from handout works in handout context;
- successful scan adds the item to a scanned/staged list;
- item is not finally handed out immediately on scan;
- user confirms final handout with a separate action/button;
- staged list allows review before committing;
- all confirmed handout actions must be logged.

Purpose:
- prevent accidental handout from a wrong scan;
- allow user to review scanned equipment before final confirmation;
- keep mobile scanning fast but safe.

MVP approach:
- scan item ID;
- add to scanned/staged handout list;
- final confirmation updates handout/picking state.
