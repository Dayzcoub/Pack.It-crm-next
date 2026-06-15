# 25 Warehouse — Block Available for Service Issue Note

## 10.211. Blocking available status for service issue items

Decision: if a returned item has an open service issue that affects working condition, the system must block moving it to available until the issue is resolved.

Rules:
- service issues that affect working condition block returned -> available transition;
- warning-only behavior is not enough for these issue types;
- the item must stay unavailable, in repair, quarantine, or another non-available status until the issue resolution is closed;
- after resolution, the system may update the warehouse status according to the selected resolution/action;
- all final transitions should be logged.

Purpose:
- prevent items with unresolved working-condition issues from being booked again;
- keep availability logic reliable;
- require resolution before returning such items to active stock.

MVP approach:
- define working-condition issue categories as blocking;
- prevent available status while such issues remain open;
- allow available only after resolution confirms the item can return to active stock.
