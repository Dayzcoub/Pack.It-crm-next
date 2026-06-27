# 25 Warehouse — Shortage Status Badge Note

## 10.267. Large current status in shortage detail card

Decision: shortage detail card should show current status prominently at the top.

Statuses:
- open;
- partially found;
- awaiting write-off approval;
- awaiting accounting correction approval;
- closed.

Rules:
- current status is shown as a large badge/label near the top of the card;
- status updates automatically after actions and approval state changes;
- open summary should focus on non-closed statuses;
- closed status is shown in history/detail views;
- status should be readable on mobile.

Purpose:
- make shortage state immediately clear;
- reduce confusion between open, partially resolved, pending approval, and closed records;
- improve warehouse keeper daily workflow.

MVP approach:
- add top status badge to shortage detail card;
- update badge from shortage status field;
- use short labels suitable for mobile UI.
