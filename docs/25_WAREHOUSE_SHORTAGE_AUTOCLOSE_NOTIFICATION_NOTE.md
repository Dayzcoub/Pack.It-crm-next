# 25 Warehouse — Shortage Auto-close Notification Note

## 10.254. Notification after approved write-off auto-close

Decision: after approved write-off automatically closes a shortage entry, the system should notify the assigned warehouse keeper and the assigned responsible person.

Rules:
- notification is sent after final approved write-off confirmation;
- assigned warehouse keeper receives notification;
- assigned responsible person receives notification if one was assigned;
- notification includes source project, item/row, missing quantity, and closure result;
- shortage no longer appears in open summary after auto-close;
- closure remains available in history.

Purpose:
- keep warehouse keeper informed about final resolution;
- inform responsible person that follow-up is complete;
- avoid stale open tasks after approved write-off.

MVP approach:
- on approved write-off confirmation, close linked shortage;
- send notification/update to warehouse keeper and responsible person;
- move entry to history.
