# 25 Warehouse — Return Scan Staging Note

## 10.234. Return scanner staging behavior

Decision: in project return mode, scanning an item should first add it to a scanned/staged return list. Final return acceptance is confirmed with a separate button.

Rules:
- scanner launched from return works in return context;
- successful scan adds the item to a scanned/staged return list;
- scan alone does not finalize return acceptance;
- user confirms final return with a separate action/button;
- staged return list allows review before committing;
- all confirmed return actions must be logged.

Purpose:
- prevent accidental return acceptance from a wrong scan;
- allow user to review scanned items before final confirmation;
- keep mobile return scanning fast but safe.

MVP approach:
- scan item ID;
- add to scanned/staged return list;
- final confirmation updates return/warehouse state.
